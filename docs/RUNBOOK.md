# RUNBOOK

_Verified: 2026-09-17_

## Deploying

There is no build step. Commit to `main` and GitHub Pages publishes the repo root.

```bash
git add -A && git commit -m "…" && git push origin main
```

Pages takes **30–90 seconds**. Poll for the change rather than guessing:

```bash
curl -s "https://zviki-locksmith.github.io/?cb=$(date +%s)" | grep -c "<a string from your change>"
```

The CDN caches hard, so always append a cache-buster when checking. A `curl` without one will show you the old page and you will think the deploy failed.

## Verifying after a change

Run these against the **live URL**, never the local file. A check that passes locally and not live is a fail.

**1. Files and assets all serve**

```bash
U=https://zviki-locksmith.github.io
for f in assets/zviki.webp assets/og.jpg assets/wdm-parrot.webp \
         assets/fonts/fr-heb.woff2 assets/fonts/as-heb.woff2 assets/fonts/as-num.woff2 \
         assets/fonts/wdm-archivo.woff2 assets/fonts/wdm-mono.woff2 \
         favicon.svg robots.txt sitemap.xml humans.txt; do
  printf "%-34s %s\n" "$f" "$(curl -s -o /dev/null -w '%{http_code}' "$U/$f")"
done
```

All must be 200.

**2. Structured data still parses**

Three JSON-LD blocks: `WebSite` (the studio seal), `Locksmith`, `FAQPage`. Any edit to the FAQ section must be mirrored in the `FAQPage` block — they are two copies of the same text and they drift silently.

```bash
curl -s $U/ | python -c "
import sys,re,json
h=sys.stdin.read()
for b in re.findall(r'<script type=\"application/ld\+json\">(.*?)</script>',h,re.S):
    d=json.loads(b); print('OK', d.get('@type'))
"
```

**3. Contrast and target sizes** — in the browser console on the live page:

```js
// composite every background layer before measuring, or a translucent
// panel like .night reads as a false failure
function parse(c){const m=c.match(/[\d.]+/g).map(Number);return{r:m[0],g:m[1],b:m[2],a:m.length>3?m[3]:1}}
function over(f,b){const a=f.a;return{r:f.r*a+b.r*(1-a),g:f.g*a+b.g*(1-a),b:f.b*a+b.b*(1-a),a:1}}
function lum(c){const f=v=>{v/=255;return v<=.03928?v/12.92:Math.pow((v+.055)/1.055,2.4)};return .2126*f(c.r)+.7152*f(c.g)+.0722*f(c.b)}
function bgOf(el){const s=[];let e=el;while(e){const b=parse(getComputedStyle(e).backgroundColor);if(b.a>0)s.push(b);e=e.parentElement}
  let acc={r:255,g:255,b:255,a:1};for(let i=s.length-1;i>=0;i--)acc=over(s[i],acc);return acc}
const fails=[];
document.querySelectorAll('h1,h2,p,li,summary,a,.row i,.row span,.lbl,.kick').forEach(el=>{
  const t=(el.innerText||'').trim(); if(!t||el.children.length>2) return;
  const cs=getComputedStyle(el),fs=parseFloat(cs.fontSize),fw=parseInt(cs.fontWeight)||400;
  const L1=lum(parse(cs.color)),L2=lum(bgOf(el));
  const r=(Math.max(L1,L2)+.05)/(Math.min(L1,L2)+.05);
  if(r<((fs>=24||(fs>=18.66&&fw>=700))?3:4.5)) fails.push([t.slice(0,28),r.toFixed(2)]);
});
console.log('contrast failures:',fails);
```

Baseline on 2026-09-17: **74 elements, minimum 6.79:1, zero failures.**

**4. No horizontal scroll at any width** — 375, 768 and 1440:

```js
const d=document.documentElement;
console.log({w:d.clientWidth, overflow:d.scrollWidth>d.clientWidth,
  tooWide:[...document.querySelectorAll('body *')].filter(e=>e.getBoundingClientRect().width>d.clientWidth+1).length});
```

Both must be `false` and `0`.

**5. The studio seal is live**

```bash
curl -s $U/ | grep -c "WDM-SEAL"      # expect 2
curl -sI $U/humans.txt | head -1      # expect 200
```

## Traps found the hard way

- **`.hero > *` cancelled the cylinder's positioning.** A child selector is more specific than the element's own class rule, so `position:relative` on every child overrode `.cyl{position:absolute}`, dropped a 190px circle into normal flow and pushed the headline and the call button below the fold on a phone. Scope wrapper rules to the wrapper.
- **Screenshots come back blank when the browser pane is hidden** or a different tab is fronted. The DOM is fine; the capture is not. Check the pane state before believing a blank image, and fall back to measuring the DOM.
- **Translucent panels break naive contrast scripts.** `.night` uses `rgba(201,162,39,.16)`; a script that treats the first non-transparent background as opaque reports 1.91:1 when the real composited value is about 11:1. Composite the stack.
- **The Hebrew subsets carry no digits.** Hebrew and Latin are separate `unicode-range` files. `as-num.woff2` exists because the arrival table is nothing but numbers and they would otherwise fall back to a system face mid-table.

## If a font looks wrong

The five woff2 files are pinned instances, not full families:

| file | what it is |
|---|---|
| `fr-heb.woff2` | Frank Ruhl Libre, Hebrew, variable 400–900 |
| `as-heb.woff2` | Assistant, Hebrew, variable 300–700 |
| `as-num.woff2` | Assistant, digits and punctuation only |
| `wdm-archivo.woff2` | Archivo frozen at `wdth 125 / wght 740`, only the letters in "WILD DIGITAL MOMENTS" |
| `wdm-mono.woff2` | Martian Mono, only the characters in "Webdesign-Studio · Tirol" |

Change the studio wordmark's text and the glyphs will not exist. Re-cut with `fontTools.varLib.instancer` then `fontTools.subset`.
