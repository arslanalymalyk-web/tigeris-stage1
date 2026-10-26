# TIGERIS AI OS — Stage 1 Demonstrator

> **Status:** Stage 1 clickable demonstrator. This is **not** a production MVP, pilot or sovereign deployment.
> All data in this repository is **SYNTHETIC** or **ILLUSTRATIVE** unless a record is explicitly labelled **OBSERVED** with a source.

TIGERIS AI OS is an institution-owned intelligence and decision layer for sovereign institutions. Stage 1 shows one connected journey:

**Hormuz signal → evidence → impact graph (incl. resilience links) → illustrative ship map → four-horizon scenarios → ranked options → PASS / HOLD / BLOCK → simulated human approval → audit + memory record.**

## Read these first

| File | What it is |
|---|---|
| `CLAUDE.md` | Rules for Claude Code (and humans) working in this repo. |
| `docs/STAGE1_BUILD_BRIEF.md` | What Stage 1 builds, what it does not, and how it is accepted. |
| `docs/DECISIONS.md` | Confirmed, provisional and open decisions; conflicts between source documents. |
| `docs/prompts/` | Paste-ready prompts for each build step, used one at a time. |

## How we build

1. One step at a time, in order (`docs/prompts/step-1` → `step-5`).
2. Each step ends with a report and a human review. Do not start the next step until the previous one is reviewed.
3. If a step needs a decision that `docs/DECISIONS.md` lists as **OPEN**, stop and ask. Do not choose silently.

## Not in Stage 1

Live data feeds, trucks, real AIS/vessel tracking, real client or institution data, external AI model calls, production login (SSO/MFA), database, Arabic content, air-gap packaging, delivery dates.
