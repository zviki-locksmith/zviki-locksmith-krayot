# AI readiness

_Verified: 2026-09-17_

Whether AI assistants and search engines can find, read and recommend this business. Scored by [Is Agentic](https://is-agentic.com/), Business profile.

## Baseline scan — 17.09.2026, 21:22 UTC

**75 / 100 — "Ready with a few material gaps."** Essential 4/6 · Recommended for Business 3/7 · Bonus +2.

The evaluator's own note, after asking an agent to explain the business back from the site alone:

> "The agent successfully extracted and synthesized all key information about Zviki's locksmith service from the homepage alone. The site is highly navigable for this task — it publishes service description, pricing philosophy, hours, and differentiation directly on the main page, requiring no secondary navigation."

### What the scan misidentifies — read this before acting on any result

The tool resolved the **brand as "github"**, because the site is hosted on `*.github.io`. Five bonus checks therefore passed on GitHub's signals, not Zviki's: `ChatGPT app listed` ("GitHub"), `CLI tool available` (`github-cli`), `MCP server / manifest` (`@github/mcp-registry`), `Developer resource discoverability` (an OpenAPI spec), and the MCP surface score of 83%.

**Do not "fix" the MCP, CLI or developer-resource rows.** They are noise. The same misidentification is what fails `Brand name discoverability`: a search for "github" returns seven results and this domain is not among them.

That check has one real fix, and it is not a code change: **a domain of his own.**

## Fixed in this pass

| check | what was done |
|---|---|
| `Trust anchor pages` | `/about/`, `/contact/`, `/privacy/` created — 1405, 835 and 1131 characters of real content, all traceable to `FACTS.md` |
| `Organization schema completeness` | `contactPoint` added with phone, `contactType` and language |
| `Schema type breadth` | the four Offers now carry described `Service` entities instead of name-only stubs |
| `llms.txt formatting` | markdown links and a page index added |
| 404 | `404.html` returns a real 404 with the site's navigation on it |
| sitemap | all four pages listed |

## Still open, and why

| check | status |
|---|---|
| `Markdown content negotiation` | **Not fixable on GitHub Pages.** It requires responding to `Accept: text/markdown` with a markdown body and `Vary: Accept`. Static hosting gives no control over response headers. A host that does (Cloudflare Pages with a Function, or any PHP host) would close it. |
| `Agent-friendly 404s` | Half credit. The 404 status is correct; the markdown error body needs the same content negotiation. |
| `Brand name discoverability` | Needs a domain. See above. |

## What passed, and is worth not breaking

- `Content is available without JavaScript` — 2519 chars, 1 H1 + 6 H2s, 25.3% content ratio
- `Agent crawler reachability` — ChatGPT-User, ClaudeBot, Google-Extended, ora-agent, DeepSeekBot all reach the site
- `Not blocked by bot detection` · `Redirects resolve cleanly` · `Page token budget`
- `Metadata completeness` — canonical, `lang="he"`, `og:image`, `og:type`
- `Accessible document structure` · `Native interactive controls` (10/10) · `Accessible names on controls` (10/10)
- `Accessibility-tree injection safety` — no hidden instruction text

Keeping the page free of JavaScript-rendered content is what carries most of this. If a future change moves content behind a script, the first four checks fail together.

## Submission status

- **IndexNow: submitted**, HTTP 200 for all four URLs. This feeds Bing, which is what ChatGPT searches.
- **Google Search Console: not done.** Google retired the sitemap ping endpoint in 2023, so submission now requires verifying ownership in Search Console. Only Zviki can do that, from the Google account that owns the business profile. **Until he does, indexing will happen eventually rather than promptly** — this is the single biggest remaining blocker to showing up in Google.
- **Bing Webmaster Tools: not done**, same reason.

## Re-running the scan

`https://is-agentic.com/scan/zviki-locksmith.github.io`

Run it from a normal browser window. In an automated or backgrounded tab the result stream stalls at "Finalizing the report" and never completes.
