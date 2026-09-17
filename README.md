# zviki-locksmith.github.io

Website for Zviki Kirsh, locksmith serving the Krayot and Haifa.
**Live:** https://zviki-locksmith.github.io/

One page, plain HTML, CSS inline, no JavaScript beyond a single console line, no build step. GitHub Pages serves the repo root on `main`.

---

## Start here

| you want to | read |
|---|---|
| know where the project stands and what is still open | [`docs/HANDOFF.md`](docs/HANDOFF.md) |
| deploy, or verify a change on the live site | [`docs/RUNBOOK.md`](docs/RUNBOOK.md) |
| find a fact before writing copy | [`docs/FACTS.md`](docs/FACTS.md) |
| change text on the site (for Zviki) | [`EDITING.md`](EDITING.md) |
| collect facts that are still missing | [`INTERVIEW.md`](INTERVIEW.md) |

---

## The one rule

**Everything on the page comes from `docs/FACTS.md`.** If a fact is not recorded there, it does not go on the site — not a price, not a review, not a year, not a credential. `חסר` is always a better answer than an invented one, and in a trade where the customer's main fear is being conned, a claim that cannot be backed is a liability rather than a selling point.

Six things are settled and should not be reopened: no prices, no lock brands, no competitor comparisons, no "why choose me" copy, Saturday closed, and no business number on the page (he has none, and displaying one that is not his is a consumer-protection offence).

---

## Why the page is shaped the way it is

From a scan of the ten locksmith sites ranking on page 1 for `מנעולן קריות` and the Krayot city queries (2026-09-17):

| | |
|---|---|
| publish a license number | 0 / 10 |
| show a real, named technician | 0 / 10 |
| have `FAQPage` schema | 0 / 10 |
| have `Offer` / price schema | 0 / 10 |
| publish real prices | 2 / 10 |
| have a WhatsApp link | 3 / 10 |
| promise "up to 20 minutes" | 8 / 10, none proves it |

The business holding the #1 map-pack slot across all three Krayot queries has the **weakest** site in the set — it wins on its Google Business Profile. So the profile is the main channel and this site has a narrower job: back the profile with identical details, and catch the per-city searches.

Three things carry the page, each because the competitors lack it:

1. **Phone-first service**, right under the hero — Zviki explains the fix on the phone when the job does not need a locksmith. Nobody else offers to save the customer the call-out, and it answers the trade's central trust objection directly.
2. **Per-city arrival estimates**, with an explicit caveat that they move with traffic and where he is. Admitting Haifa takes an hour is what makes the rest believable.
3. **Real hours, Saturday closed.** All ten competitors advertise 24/7.

---

## Layout

```
index.html              the whole site
assets/                 portrait, studio parrot, og card
assets/fonts/           5 subset woff2 files, 32KB total
favicon.svg  robots.txt  sitemap.xml  humans.txt
docs/FACTS.md           every answer, every refusal, and the legal section
docs/HANDOFF.md         state and open items
docs/RUNBOOK.md         deploy and verify
EDITING.md              for Zviki, in Hebrew
INTERVIEW.md            the interview protocol
```

No third-party requests: no Google Fonts, no analytics, no CDN. Everything loads from this origin, which is also why it works on one bar of signal.

---

## Accessibility

Built to WCAG AA — keyboard focus, 6.79:1 minimum measured contrast across 74 elements, 44px targets, skip link, semantic landmarks, reduced-motion. Zviki is an עוסק פטור and therefore exempt under reg. 35(ו)(7); the exemption removes the regulatory duty but not the civil claim under s.19(51), which allows up to ₪50,000 with no proof of damage. Reg. 34(ה) requires publishing that the exemption exists plus an alternative contact route, which is the footer paragraph. Citations are in `docs/FACTS.md`.
