# zviki-locksmith-krayot

Website for Zviki Kirsh, locksmith serving the Krayot.
Live: https://zviki-locksmith.github.io/zviki-locksmith-krayot/

---

## Read this before changing anything

**The build is blocked on facts, not on design.**

`docs/FACTS.md` is currently empty. Until it is filled, the site cannot get the things that would actually make it rank and convert — schema, real prices, per-city pages, verifiable credentials. More passes on the layout or the portrait will not move any of those.

**Next action:** interview Zviki using [`INTERVIEW.md`](INTERVIEW.md), and write his answers into [`docs/FACTS.md`](docs/FACTS.md).

`INTERVIEW.md` is a conversation script, not a form. One question at a time, in Hebrew, you type while he talks. It carries the follow-up probes and the bar for what counts as a complete answer. Commit after every section — he takes emergency calls and will be interrupted.

---

## Why these questions and not others

On 2026-09-17 we scanned the 10 locksmith sites ranking on page 1 for `מנעולן קריות` and the Krayot city queries:

| | |
|---|---|
| Publish a license / certification number | **0 of 10** |
| Show a real, named technician (not stock) | **0 of 10** |
| Have `FAQPage` schema | **0 of 10** |
| Have `Offer` / price schema | **0 of 10** |
| Publish real prices | 2 of 10 |
| Have a WhatsApp link | 3 of 10 |
| Have `LocalBusiness` schema | 2 of 10 |
| Promise "up to 20 minutes" | 8 of 10 — none proves it |

Every one of them writes "מנעולן מוסמך" or "מורשה משטרת ישראל" — one of them 24 times on a single page — and not one publishes a number anyone could check. One of those same sites tells readers the main risk in this trade is *"מנעולנים מתחזים שסייעו לפורצים"* and to demand the technician's ID.

That gap is the opening. It is why the license number is question one.

Separately: the business holding the #1 map-pack slot across all three Krayot queries has the **weakest** site in the set — 62 KB, no schema, no city pages, no prices. It wins on its Google Business Profile. Treat the Google profile as the primary channel and this site as what backs it up and catches the city searches.

---

## Current state

```
index.html        the whole site — one page, plain HTML, CSS inline, no JS, no build step
INTERVIEW.md      the interview script  ← start here
docs/FACTS.md     the answers           ← empty
```

What the site already does well: correct RTL (`lang="he" dir="rtl"`), click-to-call in 5 places including a fixed mobile bar, WhatsApp beside every call link, and a real photo of a real person — which, per the table above, none of the competitors have.

What it is missing, and why each needs `docs/FACTS.md` first:

| Missing | Blocked on |
|---|---|
| `LocalBusiness` / `Locksmith` schema | hours, address or service area, phone |
| `FAQPage` schema | his real answers, in his words |
| `Offer` schema + a price table | his prices |
| Per-city pages | which cities he actually serves |
| og: / twitter: tags | a share image — the site is shared over WhatsApp and currently renders no card |
| robots.txt, sitemap.xml, canonical, favicon | nothing — these can be done any time |
| Credibility layer | license number, certificate photo, reviews, van and work photos |
| A real domain | see `INTERVIEW.md` §11 — cheapest to settle before the Google profile is verified |

## Hard rules

1. Never invent a license number, a review, a price, or a year. `חסר` is always the right answer when you don't have it.
2. Never write "מוסמך" without a number behind it — that word is what every competitor uses to say nothing.
3. Never publish 24/7 unless Zviki confirmed it.
4. Never copy a competitor's claim, price, or wording.
5. Reviews must be real, with real names. Two competitors publish self-declared counts of 1,050 and 6,452 at a perfect 5.0; anyone who checks stops believing the rest of the page.
6. His words over polished words.
7. Photos must be real. No stock — two competitors use Shutterstock, one of them 25 times.
