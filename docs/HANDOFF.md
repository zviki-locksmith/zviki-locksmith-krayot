# HANDOFF

_Verified: 2026-09-17_

## Where this stands

The site is **built and live** at https://zviki-locksmith.github.io/ — a home page plus three trust anchor pages, plain HTML, one shared stylesheet, no JavaScript beyond a single console line, no build step. GitHub Pages serves the repo root on `main`.

The content came out of a structured interview with Zviki recorded in [`FACTS.md`](FACTS.md). **Nothing on the page was invented.** If a fact is not in `FACTS.md`, it is not on the site.

## What drove the design

A scan of the ten locksmith sites ranking on page 1 for `מנעולן קריות` and the Krayot city queries (2026-09-17):

| | |
|---|---|
| publish a license number | 0 / 10 |
| show a real, named technician | 0 / 10 |
| have `FAQPage` schema | 0 / 10 |
| have `Offer` / price schema | 0 / 10 |
| publish real prices | 2 / 10 |
| have a WhatsApp link | 3 / 10 |
| promise "up to 20 minutes" | 8 / 10, none proves it |

The business holding the #1 map-pack slot on all three Krayot queries has the **weakest** site in the set. It wins on its Google Business Profile. So the site's job is narrow: back the Google profile with consistent details, and catch the per-city searches the profile does not.

Three things carry the page, and each of them exists because the competitors do not have it:

1. **Phone-first service**, directly under the hero. Zviki explains the fix on the phone when the fault does not need a locksmith, and drives out only when it is really needed. Nobody else offers to save the customer the call-out, and it answers the trade's main trust objection head-on.
2. **Per-city arrival estimates** with an explicit caveat that they move with traffic and his current position. A table that admits Haifa takes an hour reads as credible precisely because it does not flatter.
3. **Real hours, Saturday closed.** Every competitor advertises 24/7. Stating the truth is the differentiator.

## Decisions that are settled — do not reopen

- **No prices on the page.** Zviki refused. Also the safe default: consumer-law s.17(d) requires any published price to be the total including every unavoidable add-on, so a number without the call-out fee folded in would be an offence. "Night rate is higher" with no number is compliant.
- **No lock brands, no competitor comparisons, no "why choose me" copy.** His decision.
- **"מנעולן מוסמך" stays.** He holds a certification; the certificate itself was lost in a move. Beri decided to keep the claim, and the Google Business Profile already uses it. Worth getting a replacement certificate from the issuing body.
- **Warranty is 30 days on the direct work**, with the limits stated in the same breath and promised upfront. The earlier "no fixed period" was an open-ended liability and weaker copy — a number is a commitment, a word is not.
- **Static hosting, no editor.** The studio's in-place `site-editor` needs PHP; GitHub Pages serves static files only. Zviki has an agent on this repo, so text changes go through it.
- **No domain purchase.** He chose the free `zviki-locksmith.github.io` and renamed the repo to get it. A `.co.il` remains the first thing to revisit — it costs him trust, and the Google profile points at this URL.

## Legal position

He is an **עוסק פטור**, so he is exempt from the whole internet-accessibility chapter under reg. 35(ו)(7). The site is built to WCAG AA anyway: the exemption removes the regulatory duty, not the civil claim under s.19(51), which allows up to ₪50,000 with no proof of damage. Reg. 34(ה) still requires publishing that the exemption exists together with an alternative contact route — that is the accessibility paragraph in the footer, and it deliberately does not state his turnover.

No privacy policy is required because the page collects nothing. **Adding Google Analytics or a contact form changes that** — Privacy Amendment 13, in force 14.08.2025, treats online identifiers as personal data.

Full citations: the legal section of [`FACTS.md`](FACTS.md).

## Open items

| item | note |
|---|---|
| Google Business Profile link + Place ID | submitted 17.09.2026, awaiting Google review |
| **Profile name says "מנעולן מוסמך"** | consistent with the site — fine, but confirm it matches character for character once the profile is live |
| **Profile hours say 24/7** | the site says 08:00–22:00, and Zviki said nights are not reliable. A mismatch hurts map ranking, and a missed 2am call earns the review he can least afford. Fix the profile. |
| Reviews | none yet. He said "not right now" — ask again once he has a few jobs behind him. |
| Arrival-time proof | he agreed to timestamp the next 5 jobs (call time + arrival time). Nobody in the market proves the claim; this would be a first. |
| Work photos | only the portrait exists. No van (he has none), no before/after, no certificate photo. |
| **Domain** | not bought. This is now the highest-value open item: it is the single purchase that closes all three remaining Is Agentic checks, and it removes a `github.io` address from a tradesman's business card. ~₪50–100/year. |
| **Google Search Console** | not verified. Google retired the sitemap ping in 2023, so only Zviki can submit, from the account that owns the business profile. This is the biggest remaining blocker to showing up in Google. |
| **Bing Webmaster Tools** | not verified, same reason. IndexNow submission succeeded meanwhile (HTTP 200). |

## AI and search readiness

Is Agentic: **75/100 at baseline, 80/100 after the trust-anchor and schema fixes.** The three checks still open are all blocked on one thing — a domain of his own — and none of them is a code change. Details, including proof that the limit is the host and not hand-written HTML: [`AI-READINESS.md`](AI-READINESS.md).

## Files

```
index.html          the home page
about/ contact/ privacy/   trust anchor pages
404.html
assets/base.css     the shared palette, type and chrome
assets/             portrait, studio parrot, og card, 5 subset woff2 files
favicon.svg  robots.txt  sitemap.xml  humans.txt  llms.txt
INTERVIEW.md        the interview protocol, if more facts are needed
docs/FACTS.md       every answer, every refusal, the legal section
docs/AI-READINESS.md  the scan and what it means
EDITING.md          for Zviki — what he can change himself
```

## Studio signature

All five layers of the WDM seal are in place, the visible credit included, because Beri asked for it on his brother's site. The two brand faces are frozen to one instance and subset to the wordmark's characters — 3KB for both instead of 113KB.
