# INTERVIEW.md — how to interview Zviki so we can build a site that wins

**Who this file is for:** the agent that works with Zviki on this repo.
**Your job:** interview Zviki and turn his answers into `docs/FACTS.md`.
**Not your job:** designing or rewriting the site. Get the facts first. Everything else is blocked until `docs/FACTS.md` is filled.

---

## Why this matters — read this before you ask anything

On 2026-09-17 we scanned 10 locksmith websites that rank on page 1 for `מנעולן קריות` and the Krayot city queries. The findings below are measured, not assumed. They decide which questions matter.

| Finding | Count |
|---|---|
| Publish a license / certification number | **0 of 10** |
| Show a real, named technician's face (not stock) | **0 of 10** |
| Have `FAQPage` schema | **0 of 10** |
| Have `Offer` / price schema | **0 of 10** |
| Publish real prices | 2 of 10 |
| Have a WhatsApp link | 3 of 10 |
| Have `LocalBusiness` / `Locksmith` schema | 2 of 10 |
| Promise "up to 20 minutes" | 8 of 10 — **and none proves it** |

Every single one of them writes the words "מנעולן מוסמך" or "מורשה משטרת ישראל" — one of them 24 times on a single page — and **not one publishes a number you could check.** Meanwhile one of those same sites tells readers that the top risk in this trade is *"מנעולנים מתחזים שסייעו לפורצים"* and instructs them to demand the technician's ID.

That gap is the whole opportunity. It is why question 1 below is question 1.

Also measured: the business holding the #1 map-pack slot across all three Krayot queries has the **weakest** website in the set — 62 KB, no schema, no city pages, no prices. It wins on its Google Business Profile. Treat the Google profile as the main channel and this site as the thing that backs it up and catches the city searches.

---

## How to run the interview

**Talk. Do not send a form.** Forms sent as homework are where this dies. Call him, or sit with him, and you type while he talks. If he has to fill it alone, that is the fallback — never the opening ask.

**Give before you ask.** Open by telling him the table above — specifically that not one competitor publishes a license number, and that he already has something none of them have: a real photo of a real person. Two minutes of that, then start asking.

**One question at a time.** Never paste a list at him. Ask, listen, dig, write it down, move on.

**Hebrew, spoken register.** The way you'd talk to a person, not a questionnaire.

**Dig when the answer is thin.** A vague answer is worse than no answer, because it ends up as vague copy. Every section below has an "enough / not enough" bar. Hold it.

**Never invent.** If he doesn't know or doesn't have it, write `חסר` in `docs/FACTS.md` and move on. A missing field is fine. A made-up field is a liability — this is a trade where a false credential claim is a real problem.

**Save as you go.** Commit `docs/FACTS.md` after every section. He may do this over three sittings across a week. Never lose a sitting.

**He's a working locksmith.** He takes emergency calls. Expect to be interrupted. Keep sections short enough to finish one in ten minutes.

---

## Section 1 — Identity and license  ⭐ HIGHEST VALUE

*This is the one thing no competitor has. If you get nothing else, get this.*

> **"יש לך מספר רישיון או תעודת מנעולן? אני רוצה לשים אותו על האתר."**

Dig:
- What exactly does the certificate say — issuing body, number, date?
- Is he a member of ארגון המנעולנים בישראל? Membership number?
- Does he have police authorization (אישור משטרה)? What is the reference?
- How many years has he actually worked as a locksmith? Not "a lot" — a number and a start year.
- Did he train under someone, or take a course? Where?

**Not enough:** "אני מוסמך", "יש לי תעודה", "הרבה שנים".
**Enough:** a number you can photograph, an issuing body, and a start year.

**Ask him to photograph the certificate.** That image is worth more than any paragraph on the page.

If he genuinely has no number: say so plainly in `docs/FACTS.md`. We will then lead with years + reviews + face instead, and we will **not** write "מוסמך" without something behind it.

---

## Section 2 — Hours and arrival time

> **"מה השעות האמיתיות שלך? אם מישהו מתקשר ב-2 בלילה ביום שלישי — אתה עונה?"**

Dig:
- Exact hours per day. Nights? Fridays? Saturday night after Shabbat ends? Holidays?
- The current site says `השירות אינו כולל שבתות וחגים`. Every competitor advertises 24/7. Is that line accurate? Is it a hard rule?
- Realistic arrival time to each city — not the best case, the normal case.
- How does that change at 3am vs 3pm?
- Is there anywhere in his service area he can't reach quickly?

**Not enough:** "מהר", "תלוי".
**Enough:** a number of minutes per city, and honest hours we can put in schema.

**Do not let him claim 24/7 if he isn't.** A no-show against a published promise costs more than the promise gains. If he's not 24/7, we turn the real hours into a feature — see the note in Section 10.

**Then ask:** *"אתה יכול לתעד זמן הגעה? צילום מסך של שעת השיחה ושעת ההגעה, כמה פעמים?"* Eight of ten competitors promise "20 minutes" and not one proves it. If he'll timestamp even five real jobs, we can show something nobody else shows.

---

## Section 3 — Cities

> **"תגיד לי בדיוק לאילו ערים אתה נוסע. שם מלא של כל אחת."**

Dig each one:
- קריית ביאליק · קריית מוצקין · קריית ים · קריית אתא · קריית חיים · חיפה · נשר · טירת כרמל · עכו — for each: yes, no, or "only if it's worth it"?
- Any neighbourhood he works in a lot? (Specific neighbourhoods are searched and nobody targets them.)
- Any city he'd rather **not** get calls from? We leave those out.
- Where does he actually live / base himself?

**Not enough:** "הקריות והסביבה" — that is what the site says now, and it is not a search term.
**Enough:** a list of city names, each marked yes/no, with a realistic arrival time.

We will build one page per city he says yes to. Cities he says no to get no page.

---

## Section 4 — Services and prices  ⭐ HIGH VALUE

*Only 2 of 10 competitors publish prices. Zero have price schema. This is uncontested ground.*

> **"בוא נעבור שירות-שירות. כמה אתה לוקח על פתיחת דלת רגילה — מהכי זול שיצא לך עד הכי יקר?"**

Go through each, one at a time. A range is fine. "מ-X ₪" is fine. Get the number:

- פריצת / פתיחת דלת רגילה
- דמי ביקור או קריאה
- החלפת צילינדר
- התקנת מנעול חדש
- פתיחת רכב
- שחזור מפתח לרכב (עם שבב / בלי)
- פריצת כספת
- כיוון צירי דלת פלדלת
- דלת טרוקה
- החלפת מנעול לדלת פלדלת
- מנעולים חכמים — מתקין? איזה?

For each, also ask:
- Does the price change at night / weekend? By how much?
- Is VAT included in the number he just said?
- What makes it go to the top of the range?
- Anything he **doesn't** do? (Just as useful — it stops wasted calls.)

**Not enough:** "תלוי במקרה".
**Enough:** a range in shekels, and whether it includes VAT.

If he refuses to publish prices, push back once: two of the top-ranking competitors publish them and it is the most-searched question in the trade. If he still says no, write `סירב לפרסם` and move on — his call.

---

## Section 5 — Lock brands

> **"עם אילו מנעולים אתה עובד? רב בריח, פלדלת, מולטי לוק, שריונית חסם, פנדור — מה מזה?"**

Dig:
- Which brands does he install? Which does he only open?
- Anything he's specifically trained or certified on by a manufacturer?
- Anything he keeps in stock in the van?
- Which brand does he recommend and why? (His real opinion — that becomes a page nobody else has.)

Each brand name is a search term. This section is cheap and directly useful.

---

## Section 6 — Real questions he gets asked

*Zero of ten competitors have FAQ schema, and Bing is already writing AI answers on these queries and citing sources. Extractable answers get cited.*

> **"מה השאלות שלקוחות שואלים אותך שוב ושוב? תן לי את זה במילים שלך, כמו שאתה עונה בטלפון."**

Get 8–12. Push for the real ones, including the uncomfortable ones:
- "כמה זה עולה?"
- "בעוד כמה זמן אתה פה?"
- "אתה תשבור לי את הדלת?"
- "איך אני יודע שאתה לא נוכל?"
- "אפשר לפתוח בלי להחליף את המנעול?"
- "ננעלתי עם תינוק בפנים / עם הרכב דולק — מה עושים?"
- "מה עושים אם שכחתי מפתח בתוך הבית?"
- "מקבלים חשבונית?"
- "אפשר לשלם באשראי / ביט?"

**Write his exact words.** Do not clean them up. His phrasing is the thing a template can't fake.

**Also ask:** *"ספר לי על קריאה אחת מיוחדת שהייתה לך."* One real story, with the city and what happened. One true story beats a page of adjectives.

---

## Section 7 — Photos

Ask him to send these to WhatsApp, then commit them to `assets/`:

- [ ] **A better portrait.** The current one is 459×563px and gets stretched on desktop — it looks soft. Need 1200px wide minimum, good light.
- [ ] **The van**, with signage if it has any.
- [ ] **Hands at work** on a lock — face not required.
- [ ] **Before / after** of a door he opened without damaging it. This answers the #1 fear directly.
- [ ] **The certificate**, photographed clearly.
- [ ] **Locks and cylinders** he installs, laid out.
- [ ] **Logo**, if one exists.

**No stock photos, ever.** Two of the competitors use Shutterstock — one of them 25 times. A real photo of a real van is worth more than all of it.

Also ask: *"יש לך תמונות מעבודות קודמות בטלפון?"* Most tradespeople do. They are usually better than anything staged.

---

## Section 8 — Reviews and proof

> **"יש לקוחות שיכתבו עליך משהו? אני צריך 3 עד 5, עם שם פרטי ועיר."**

Dig:
- Names he can actually ask. Ask him to ask them today, not "sometime".
- Has anyone already written him something on WhatsApp? A screenshot counts.
- Does he work with building committees (ועדי בתים), property managers, insurance companies, a locksmith chain? Names.
- Any repeat business, contracts, businesses he services regularly?

**Real names and real cities only.** Two competitors publish self-declared review counts of 1,050 and 6,452 with perfect 5.0 ratings. Anyone who checks stops believing the rest of the page. Three genuine reviews beat any number we can't back.

---

## Section 9 — Google Business Profile

He is setting this up now. These answers must match the site **exactly** — the same name, the same phone, the same area. Inconsistency between the profile and the site hurts map ranking.

> **"מה בדיוק כתבת בפרופיל העסקי בגוגל? שם, טלפון, כתובת, שעות."**

Record:
- The exact business name as typed into the profile
- The phone number on the profile (current site uses 055-665-7708 — do they match?)
- **Address**: a street address in a Krayot city, or service-area only? *The three businesses holding the map pack all show a street address and "פתוח 24 שעות".* If he has any legitimate address to use, this matters.
- Hours as entered
- Categories selected
- The profile link and Place ID once it's live

Then: **make the site match the profile, character for character.** Not approximately.

---

## Section 10 — Business details and positioning

- Exact business name, as it should appear everywhere
- עוסק מורשה / ח.פ number
- Email address
- Payment methods — cash, credit, Bit, invoice?
- Does he give a warranty? On what, for how long?
- Insurance / liability cover?

Then the positioning question:

> **"למה שמישהו יבחר בך ולא במנעולן הראשון בגוגל?"**

Let him answer in his own words, then push past the first answer, which is always "שירות ואמינות". Ask what he does that others don't. Ask what he refuses to do. Ask what annoys him about other locksmiths in the area.

**Note if he isn't 24/7:** that is not necessarily a weakness. "מנעולן שומר שבת" or "אני לא עונה בשבת" is a real differentiator in parts of this market, and nobody in the scanned set claims it. Ask him directly whether he wants that stated.

---

## What you produce

Create `docs/FACTS.md` with every field below. Mark each `✅` when answered, `חסר` when not. Commit after every section.

```markdown
# FACTS — Zviki Kirsh, locksmith, Krayot
_Last updated: YYYY-MM-DD · Interviewed by: <agent>_

## Identity
License number:            [ ]
Issuing body:              [ ]
Locksmith association #:   [ ]
Police authorization:      [ ]
Years in trade / start:    [ ]
Certificate photo:         [ ] assets/

## Hours
Weekday hours:             [ ]
Nights:                    [ ]
Friday / Shabbat / holidays: [ ]
Arrival time per city:     [ ]
Arrival proof available:   [ ]

## Cities  (yes / no / arrival minutes)
קריית ביאליק [ ]  קריית מוצקין [ ]  קריית ים [ ]  קריית אתא [ ]
קריית חיים [ ]  חיפה [ ]  נשר [ ]  טירת כרמל [ ]  עכו [ ]
Base location:             [ ]

## Prices  (range in ₪, VAT yes/no)
פתיחת דלת [ ]   דמי ביקור [ ]   החלפת צילינדר [ ]   מנעול חדש [ ]
פתיחת רכב [ ]   שחזור מפתח רכב [ ]   כספת [ ]   צירי פלדלת [ ]
דלת טרוקה [ ]   מנעול לפלדלת [ ]   מנעול חכם [ ]
Night / weekend surcharge: [ ]
Does not do:               [ ]

## Brands
Installs:                  [ ]
Opens only:                [ ]
Certified on:              [ ]
In the van:                [ ]
Recommends + why:          [ ]

## FAQ  (his exact words)
1. Q: / A:
...
Story:                     [ ]

## Photos in assets/
portrait 1200px [ ]  van [ ]  hands [ ]  before-after [ ]
certificate [ ]  locks [ ]  logo [ ]

## Reviews
1. name / city / text
...
B2B clients:               [ ]

## Google Business Profile
Exact name:                [ ]
Phone:                     [ ]
Address or service-area:   [ ]
Hours:                     [ ]
Categories:                [ ]
Profile link / Place ID:   [ ]
Matches the site exactly:  [ ]

## Business
Business name:             [ ]
עוסק מורשה / ח.פ:          [ ]
Email:                     [ ]
Payment methods:           [ ]
Warranty:                  [ ]
Insurance:                 [ ]
Why him (his words):       [ ]
Wants Shabbat stated:      [ ]
```

---

## Hard rules

1. **Never invent a license number, a review, a price, or a year.** `חסר` is always the correct answer when you don't have it.
2. **Never write "מוסמך" without a number behind it.** That word is what every competitor uses to say nothing.
3. **Never publish 24/7 unless he confirmed it.** Check Section 2 before any copy says it.
4. **Never copy a competitor's claim, price, or text.**
5. **Reviews must be real, with real names.** No aggregate rating we can't stand behind.
6. **His words over polished words.** Where you have his phrasing, keep it.
7. **Prices are his decision.** Push back once, then respect the answer.

## When it's done

`docs/FACTS.md` filled means we can build:
`LocalBusiness` + `Locksmith` schema · `FAQPage` schema · `Offer` schema with real prices · one linked page per city · og tags so WhatsApp shares render · robots + sitemap + canonical · favicon · a real price table · the certificate and the van on the page · timestamped arrival proof if he can supply it.

Four of those exist on **zero** of the ten sites we scanned. Get the facts and the rest is straightforward.
