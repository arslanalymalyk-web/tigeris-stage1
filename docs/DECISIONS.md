# TIGERIS AI OS — Decision Log

Statuses: **CONFIRMED** (by product owner) · **PROVISIONAL** (accepted for now, may change) · **PROPOSED** (recommended; needs confirmation) · **OPEN** (no answer; do not choose silently).

Rule for builders: you may build on CONFIRMED and PROVISIONAL items. If work depends on a PROPOSED or OPEN item, stop and ask. PROVISIONAL items may change later, so keep them easy to replace (one config value, one token file, one service interface).

## A. Product owner decisions (updated 26 Oct 2026)

| ID | Decision | Status |
|---|---|---|
| D-01 | Stage 1 is a **clickable demonstrator**, not a complete production MVP. | CONFIRMED |
| D-02 | Stage 1 scope: Hormuz signal-to-decision journey; resilience links in the graph; one synthetic capital-allocation option; PASS/HOLD/BLOCK rules; simulated human approval; visible source/assumption lineage. | CONFIRMED |
| D-03 | **No delivery date** is set. | CONFIRMED |
| D-04 | Use the Foundation Decisions palette and fonts (ivory/emerald/sage/gold; Source Serif 4 + Inter). | PROVISIONAL |
| D-05 | Include a small Hormuz map with one illustrative moving ship in Stage 1. All simulated movement is labelled SYNTHETIC or ILLUSTRATIVE. | CONFIRMED |
| D-06 | Trucks and live data feeds are deferred. | CONFIRMED |
| D-07 | Map: a **polished, simplified Hormuz schematic**, drawn for TIGERIS and bundled locally as SVG. Labelled ILLUSTRATIVE ("schematic — not to scale, not for navigation"). Not traced from any copyrighted or licensed map. No tile server or map service. Ship movement on it is clearly labelled SYNTHETIC. | PROVISIONAL |
| D-08 | Stack: **Vite + React + TypeScript, front end only.** No backend, database or server. Vitest for unit tests; Playwright for journey/accessibility checks. | PROVISIONAL |
| D-09 | **No external AI calls** in Stage 1. Narrative text is fixed, labelled templates. | PROVISIONAL |
| D-10 | The Hormuz signal is a **generic synthetic disruption** with **no real event date** and no reference to a real event. Synthetic timestamps are relative (for example "T+0h", "T+6h") or clearly synthetic. | PROVISIONAL |
| D-11 | English only; layout RTL-ready. | PROVISIONAL (from source docs) |
| D-12 | Repository name/owner and team size: **intentionally unspecified.** No Stage 1 file needs them. Do not invent them in package.json, README, CI or anywhere else; use a neutral package name such as `tigeris-ai-os-stage1`. | PROVISIONAL |
| D-13 | Demo hosting: **local preview only** (`npm run dev` / `npm run preview` on the developer's machine). No deployment, hosting service or shared link in Stage 1. | PROVISIONAL |

## B. Client decisions (not blocking Stage 1)

| ID | Decision needed |
|---|---|
| C-01 | Final product name and spelling (TIGERIS / Tigris / Sovereign Intelligence OS) and tagline approval. |
| C-02 | Patent-pending architecture blueprint, under NDA; which elements are mandatory. |
| C-03 | Case mix confirmation; the real Hormuz event window; who signs off factual validity. |
| C-04 | Approved public sources and rights (including TankerMap). |
| C-05 | Demo environment: cloud, local isolated or air-gapped. |
| C-06 | Permitted AI models; whether remote model calls are prohibited. |
| C-07 | Roles, approval thresholds, confidence semantics, audit and memory retention. |
| C-08 | Arabic release requirement and terminology reviewer. |
| C-09 | Budget, acceptance owner and definition of "MVP accepted". |
| C-10 | Final brand palette (Foundation ivory/emerald vs PRD/UI brief navy/teal). |

## C. Conflicts found across source documents

These are recorded, not resolved, unless a decision above resolves them.

| # | Topic | Conflict | Resolution |
|---|---|---|---|
| X-01 | Timeline | 8 weeks (Blueprint, PRD, TRD, Foundation) vs 12 + 4 weeks (Implementation Plan) vs 1–2 + 6–8 weeks (Consolidated) vs "no fixed timeline" (Priority Index) | D-03: no date |
| X-02 | Palette | Foundation ivory/emerald/sage/gold vs PRD "royal midnight-navy" vs UI brief navy + teal vs Map Spec dark canvas | D-04 provisional; C-10 open |
| X-03 | Fonts | Foundation serif + sans vs UI brief sans only | D-04 provisional |
| X-04 | Product name | Foundation treats it as decided but also lists it as open; Consolidated lists variants | "TIGERIS AI OS" in one config value; C-01 open |
| X-05 | Use cases | Hormuz + resilience + capital vs Consolidated's oil at USD 45 and cross-sector supply shock | D-02 |
| X-06 | Navigation | Three different module lists (Foundation, PRD, UI brief) | Stage 1 shows only screens it uses; full menu deferred |
| X-07 | Tech stack | Consolidated (Neo4j, LangGraph, Temporal, Qdrant, OPA, K8s) vs TRD / Implementation Plan / Schema (modular monolith, PostgreSQL) | Stage 1 is front-end only (D-08); backend choice deferred to a later stage |
| X-08 | Demo hosting | Cloud acceptable (Consolidated) vs local, no egress (Blueprint, TRD) | Stage 1: local preview only (D-13); client hosting decision C-05 still open |
| X-09 | Map and trucks | PRD FR-29 map MUST incl. land logistics vs Map Spec trucks in Expansion vs Blueprint map unscheduled | D-05, D-06 |
| X-10 | Industries | Foundation's 8 packs (incl. insurance) vs Target Industries (FO/VC priority, no insurance) | Not needed for Stage 1 |
| X-11 | Agent count | 9 described / 7 named vs 6 vs 5 agent types | No agents or AI calls in Stage 1 (D-09) |
| X-12 | Login | PRD FR-01/02 MUST SSO/MFA vs its own scope cuts | Demo roles only |
| X-13 | Confidence | No naked percentages (Foundation) vs numeric `confidence` fields (Schema) | Store components; display bands only |

## D. Source-document issues to report to the client

- Referenced but missing from the project: meeting-minute PDFs, the patent-pending blueprint, `TIGERIS_Backend_Schema_MVP.sql`, the Manufacturing Command Centre reference image, and the product demonstration PDF.
- Priority docs 01, 02, 04, 05 and 07: the Risk/Control tables appear misaligned (controls are paired with the wrong risks).
