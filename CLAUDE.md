# CLAUDE.md — TIGERIS AI OS (Stage 1 Demonstrator)

You are helping build **TIGERIS AI OS**, an AI-native sovereign intelligence operating system. This repository currently holds **Stage 1: a clickable demonstrator**. It is not a production system.

Read `docs/STAGE1_BUILD_BRIEF.md` and `docs/DECISIONS.md` before any change.

## 1. Working rules

- Work only on the step you were asked to do. Do not broaden scope.
- Before editing, inspect the repository and report what exists. Never claim you inspected, ran or tested something you did not.
- If a task depends on a decision marked **OPEN** in `docs/DECISIONS.md`, stop and ask. Do not pick an answer silently.
- If source documents conflict and `docs/DECISIONS.md` has no resolution, list the conflict and ask.
- At the end of every step, report: files changed, commands run and their results, assumptions made, what you could not verify, and remaining blockers. Then stop.
- Keep changes small and reviewable. Prefer clear code over clever code.

## 2. Product guardrails (non-negotiable)

1. **No unlabelled data.** Every displayed fact, number, map object, track and chart carries one of these labels:
   `OBSERVED` · `INFERRED` · `ASSUMPTION` · `SYNTHETIC` · `ILLUSTRATIVE`
   In Stage 1, nothing is `OBSERVED` unless it has a real, recorded source. Expect almost everything to be `SYNTHETIC`, `ASSUMPTION` or `ILLUSTRATIVE`.
2. **Every number has lineage.** A displayed number must open a lineage panel showing its source record or assumption ID, formula/calculation ID, units, inputs and label. If lineage is missing, do not show the number.
3. **No real-world statistics invented.** Do not add real-world figures (oil flows, prices, vessel counts, percentages) from memory. If a real figure is needed, it must come from an approved, recorded source, which Stage 1 does not have.
4. **No real organisations as customers.** Do not show PIF, Mubadala, ADIA, Aramco or any real institution's name or logo. Use "Demonstration Institution (synthetic)".
5. **No real vessels.** Do not use real ship names, IMO or MMSI numbers. Use generic names such as "Synthetic Vessel A".
6. **Human authority.** Recommendations are proposals. Only a named demo approver can move an option to "Approved (simulated)". Nothing executes. No external action, transaction or message is ever sent.
7. **No naked AI confidence percentages.** Show a confidence band (Low / Moderate / High) plus its basis.
8. **Deterministic numbers.** All numbers come from typed, deterministic calculation functions. No AI/LLM model calls in Stage 1. Any "AI narrative" text is a fixed, labelled template.
9. **Demonstration Mode is always visible.** A persistent banner appears on every screen.
10. **No unsupported claims.** Do not write "predicts", "real-time", "live", "fully autonomous", "guaranteed" or similar in UI copy.

## 3. Technical rules

- Stack (D-08, provisional): Vite + React + TypeScript, front end only. Build on CONFIRMED or PROVISIONAL decisions; stop and ask on PROPOSED or OPEN ones.
- Stage 1 runs as a local preview only (D-13). Do not add deployment or hosting configuration.
- Do not invent a repository name, owner, organisation or team details (D-12).
- No backend, database, login provider, external AI calls or network calls in Stage 1. Data lives in typed fixtures behind a service interface (`src/services/`) so it can be replaced later.
- No external map tiles, CDNs, analytics, fonts or APIs at runtime. Bundle all assets locally. The app must work with the network off.
- Store design tokens in one place. Do not hard-code colours in components.
- Layout must be RTL-ready: use logical CSS properties (`margin-inline-start`, not `margin-left`) and avoid direction-specific assumptions. English only for now.
- Accessibility target: WCAG 2.2 AA. Keyboard operable, visible focus, labels for controls, status shown with text/icon (not colour alone), reduced-motion support.
- Never commit secrets, real credentials or client material.

## 4. Visual system (PROVISIONAL — see DECISIONS.md D-04)

| Token | Value | Use |
|---|---|---|
| ivory | `#F7F6F0` | App canvas |
| white | `#FFFFFF` | Panels, cards, tables |
| emerald | `#176348` | Navigation, active state, primary action |
| sage | `#DDE9DF` | Calm positive / secondary surfaces |
| gold | `#B7995D` | Rare accent only; never the primary action |
| charcoal | `#25312D` | Body text |
| amber | `#B86F24` | Warning / HOLD / review required |
| red | `#A9443C` | Critical / BLOCK |
| border | `#D9DDD5` | Fine boundaries |

Fonts: **Source Serif 4** (headings), **Inter** (UI/body), tabular numerals for figures. Bundle the font files locally, with Georgia / Arial / system fallbacks.

Style: calm, institutional, thin borders, restrained radius. No dark "AI dashboard" look, neon, glassmorphism, heavy shadows or decorative AI imagery.

## 5. Checks

Every step must keep these passing, once they exist:
- lint, type check, unit tests
- the **lineage/label test** (fails if any displayed number or map object lacks a label or lineage)
- the **approval-gate test** (fails if any option can reach Approved without a human decision record)
