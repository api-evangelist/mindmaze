# MindMaze

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
