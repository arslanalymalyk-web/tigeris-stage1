# Step 2 — App shell and design system

```text
Read CLAUDE.md, docs/STAGE1_BUILD_BRIEF.md (sections 2, 4, 11) and docs/DECISIONS.md.

Task: Step 2 only — the app frame and design system. Use placeholder content only; no case data yet.

Build:
1. Design tokens in one file (colours, type scale, spacing, radius, border), using the PROVISIONAL palette in CLAUDE.md §4. Components must use tokens, never raw hex values.
2. Fonts: bundle Source Serif 4 and Inter locally (check that their licences allow bundling and report what you found), with Georgia/Arial/system fallbacks. Tabular numerals for figures.
3. Layout:
   - persistent left navigation (Command Centre, Intelligence Cases, Governance & Audit, Institutional Memory — only the screens Stage 1 uses)
   - top context bar showing institution "Demonstration Institution (synthetic)", the current demo role, environment "Local demo" and data mode "Synthetic"
   - a persistent DEMONSTRATION MODE banner on every route, which cannot be dismissed
4. DataLabel badge component for OBSERVED, INFERRED, ASSUMPTION, SYNTHETIC and ILLUSTRATIVE. Each uses text plus an icon or pattern (not colour alone) and has an accessible name.
5. Status components for PASS, HOLD and BLOCK, and for case states, using text plus icon.
6. Demo role switcher (Analyst, Domain Expert, Approver, Auditor — all "(demo)"), stored in app state and clearly labelled "Simulated role — not real authentication".
7. RTL readiness: logical CSS properties only; a dev-only toggle that sets dir="rtl" so we can check mirroring. English text only.
8. Accessibility: skip link, visible focus, landmarks, keyboard-operable navigation, prefers-reduced-motion respected globally.
9. Tests: the banner renders on every route; role switch updates the context bar; DataLabel renders all five labels with accessible names.

Do NOT add case data, fixtures, graph, map or calculations.

At the end, report: files changed, commands actually run and results, screenshots or a description of desktop and mobile widths if you could render them (say clearly if you could not), the LTR/RTL check result, font licence findings, and open questions. Then stop and wait for my review.
```

**You review:** look and feel on desktop and mobile; the banner on every screen; the labels; the role switcher; the RTL toggle.
