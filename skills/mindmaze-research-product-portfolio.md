---
name: Research the MindMaze product and evidence portfolio
description: Retrieve MindMaze Therapeutics product, platform, clinical-evidence and research pages, plus media-library attachments such as investor presentations, from the public content API.
api: openapi/mindmaze-content-openapi.yml
operations: [searchContent, listPages, getPage, listMedia, listPosts]
generated: '2026-08-01'
method: generated
---

# Research the MindMaze product and evidence portfolio

MindMaze Therapeutics ships six named neurotherapeutics — **Companion**, **MindMotion GO**,
**MindPod**, **Izar**, **Physilog** and **TOAP Run** — plus a clinical-evidence programme and
the MindMaze Labs research arm. All of that lives as WordPress pages and posts readable over the
public content API. Use this skill for grounded answers about what MindMaze sells and what
evidence it publishes, instead of scraping rendered HTML.

**Base URL:** `https://mindmazetherapeutics.com/wp-json`
**Auth:** none.
**Content signals:** `search=yes, ai-train=no, use=reference` — reference-only, no training use.

## Steps

1. **Find the relevant documents** — `searchContent`
   `GET /wp/v2/search?search=MindMotion&per_page=20`
   Returns `id`, `title`, `url`, `type` and `subtype` per hit. Cheapest way to locate a product
   or evidence page without knowing its id.

2. **Enumerate the page tree** — `listPages`
   `GET /wp/v2/pages?per_page=100&_fields=id,slug,link,title,parent,menu_order`
   49 pages on 2026-08-01. `parent` gives the hierarchy — product pages sit under
   `/therapy-and-monitoring/`, research under `/research-and-innovation/mindmaze-labs/`,
   and the platform and clinical-evidence pages under `/mindmaze-platform/`.

3. **Read a page** — `getPage`
   `GET /wp/v2/pages/{id}`
   `content.rendered` carries the HTML body. Strip tags before summarising.

4. **Pull attachments** — `listMedia`
   `GET /wp/v2/media?mime_type=application/pdf&per_page=100&_fields=id,date,title,source_url,post`
   1,070 media records on 2026-08-01. The PDFs behind investor presentations, financial reports
   and product collateral resolve through `source_url`. `post` links an attachment back to the
   page or announcement it was uploaded to.

5. **Cross-reference announcements** — `listPosts` with `categories=16` (Products) or
   `categories=8` (Press releases) to pair a product page with the announcement that launched it.

## Rules

- Ground every product claim in a retrieved `link` — cite the page URL, not a summary.
- Regulatory claims (FDA-listed, CE-marked) come from MindMaze's own about page. Report them as
  the company's published claim; this repo has not verified a 510(k) or notified-body record.
  See `conformance/mindmaze-conformance.yml`.
- Instructions for Use are **not** on the API. They are supplied only through the IFU request
  form at `/therapy-and-monitoring/instructions-for-use/`.
- `per_page` maxes at 100; walk with the `Link: rel="next"` header. Never call `/wp/v2/users`.
