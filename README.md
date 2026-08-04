# MindMaze

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

MindMaze Therapeutics Holding SA (SIX: MMTX) is a Swiss precision-neurotherapeutics company
headquartered in Lausanne, with a Geneva holding entity and a US base in Charlotte, North
Carolina. Founded in 2012 by Tej Tadi as an EPFL spin-off, it became Switzerland's first unicorn;
in December 2025 its successor entity NeuroX completed a business combination with Relief
Therapeutics to form the SIX-listed MindMaze Therapeutics. It builds digital neurotherapeutics —
gamified therapy software paired with proprietary sensors and AI-driven analytics — for stroke,
Parkinson's disease and at-risk aging, across hospital, outpatient and home care, deployed in
more than 250 clinics and rehabilitation centers globally. The FDA-listed and CE-marked portfolio
is Companion, MindMotion GO, MindPod, Izar, Physilog and TOAP Run.

- https://mindmazetherapeutics.com/ (mindmaze.com redirects here)
- https://forgeglobal.com/mindmaze_stock/

## API posture

MindMaze publishes **no developer portal, no API documentation, no SDKs, no CLI and no product
API contract**. There is no MCP server, no GraphQL surface, no A2A agent card and no GitHub
organization, and no developer-shaped subdomain resolves on either domain.

The one machine-readable surface it serves is the anonymous **WordPress core REST API** behind
its corporate site at `https://mindmazetherapeutics.com/wp-json/` — 450 posts (309 of them EQS
regulatory and investor-relations disclosure), 49 pages, 1,070 media records and cross-content
search. It is captured here as a derived OpenAPI 3.1.0 with 17 verified anonymous operations. It
is a corporate content and investor-relations API; it carries no clinical, device or patient data.

`robots.txt` on this host publishes a Content Signals policy of `search=yes, ai-train=no,
use=reference` with an Article 4 EU DSM reservation of rights. Treat retrieved content as
reference-only.
