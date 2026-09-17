# AI readiness

_Verified: 2026-09-17_

Whether AI assistants and search engines can find, read and recommend this business. Scored by [Is Agentic](https://is-agentic.com/), Business profile.

## Score

| scan | score |
|---|---|
| baseline, 17.09.2026 21:22 UTC | **75 / 100** — Essential 4/6 · Recommended 3/7 · Bonus +2 |
| after the fixes below | **80 / 100** |

The remaining gap is not code. Every open check below is blocked on the same
thing: a domain of his own.

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

## Still open — all three unlock together, with a domain

| check | status |
|---|---|
| `Markdown content negotiation` | **Blocked on GitHub Pages, not impossible.** The check wants `Accept: text/markdown` answered with a markdown body and `Vary: Accept`. That is a decision taken per request, and GitHub Pages runs no code at request time — it returns the file on disk with fixed headers. |
| `Agent-friendly 404s` | Half credit. The 404 status is already correct; the markdown error body needs the same per-request decision. |
| `Brand name discoverability` | The scan searches the brand and resolves `*.github.io` as "github". Nothing in the repo changes that. |

### It is a hosting limit, not a "static site" limit

The studio's own site is proof. `digital.wildmoments.at` is hand-written HTML with
no framework, and it passes content negotiation — verified 17.09.2026:

```
curl -H 'Accept: text/markdown' https://digital.wildmoments.at/
  → 200 · Content-Type: text/markdown; charset=utf-8 · Vary: Accept
  → body begins "# Webdesign Tirol — handgebaute Websites…"
curl -H 'Accept: text/markdown' https://digital.wildmoments.at/__probe-xyz
  → 404 · Content-Type: text/markdown; charset=utf-8 · Vary: Accept
```

It works there because that host runs Apache with PHP and `.htaccess`, so the
server can branch on the request header. The difference is who controls the
response, not whether the pages are hand-written.

### The path, when the domain is bought

A domain on Cloudflare in front of GitHub Pages: Cloudflare's free plan proxies
the domain, a small Worker inspects `Accept` and returns markdown when asked,
and GitHub Pages keeps serving the files behind it. Cloudflare cannot proxy
`zviki-locksmith.github.io` — it needs a domain whose DNS Zviki controls.

**So one ~₪50–100/year purchase closes all three checks at once**, and also
removes the trust cost of a `github.io` address on a tradesman's business card.

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
