---
name: Track MindMaze Therapeutics regulatory disclosure
description: Pull MindMaze Therapeutics (SIX:MMTX) EQS ad-hoc announcements, investor-relations news and press releases from the public content API, newest first, with correct pagination and date filtering.
api: openapi/mindmaze-content-openapi.yml
operations: [listCategories, listPosts, getPost]
generated: '2026-08-01'
method: generated
---

# Track MindMaze Therapeutics regulatory disclosure

MindMaze Therapeutics Holding SA trades on the SIX Swiss Exchange as **MMTX** and publishes its
ad-hoc and other regulatory announcements through EQS onto `mindmazetherapeutics.com`. That
corpus is anonymously readable over the WordPress REST API. Use this skill to build a
disclosure feed or answer "what has MindMaze announced" questions from primary sources.

**Base URL:** `https://mindmazetherapeutics.com/wp-json`
**Auth:** none. Do not send credentials — every operation below is anonymous.

## Before you start

`robots.txt` on this host publishes a Content Signals policy of `search=yes, ai-train=no,
use=reference` and disallows GPTBot, ClaudeBot, CCBot, Google-Extended and peers. Treat what
you retrieve as **reference material only** — do not use it as training data — and honour the
published `Crawl-delay: 10`.

## Steps

1. **Resolve the disclosure categories** — `listCategories`
   `GET /wp/v2/categories?per_page=20`
   Term ids are stable on this site but confirm them rather than hardcoding. On 2026-08-01:
   `24` Ad hoc news (EQS), `23` EQS, `25` Other IR news, `8` Press releases,
   `9` In the media, `10` Events, `11` Testimonials, `16` Products.
   Ignore the three zero-count legacy duplicates (`20`, `22`, `1`).

2. **List the disclosure stream** — `listPosts`
   `GET /wp/v2/posts?categories=24,25,8&orderby=date&order=desc&per_page=100&_fields=id,date,slug,link,title,categories`
   - `per_page` is capped at **100**; exceeding it returns `400 rest_invalid_param`.
   - Use `_fields` to keep payloads small — full post bodies are large HTML blobs.
   - Read `X-WP-Total` and `X-WP-TotalPages` from the response headers to size the walk, and
     follow the `Link: rel="next"` header rather than incrementing `page` blindly.

3. **Fetch the announcement body** — `getPost`
   `GET /wp/v2/posts/{id}`
   `content.rendered` is HTML. `date_gmt` is the authoritative timestamp for a disclosure feed;
   `date` is site-local.

4. **Incremental sync** — re-run step 2 with `after=<last date_gmt seen, ISO 8601>` and drop the
   full-page walk. Combine with `before` for a bounded historical backfill.

## Rules

- **Never** call `/wp/v2/users` — it returns author personal data anonymously and is
  deliberately excluded from this API's captured contract.
- Administrative routes (`/wp/v2/settings`, `/themes`, `/plugins`, `/menus`) return
  `401 rest_forbidden`. There is no public credential that unlocks them; do not retry with auth.
- Errors are the WordPress envelope `{code, message, data:{status}}`, **not** RFC 9457. Branch on
  `code`, not on the message string. See `errors/mindmaze-problem-types.yml`.
- This is a corporate content API. It carries **no** clinical, device or patient data, and
  MindMaze makes no stability commitment about it — there is no versioning or deprecation policy.
