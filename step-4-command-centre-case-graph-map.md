# Step 4 — Command Centre, signal, case workspace, graph and map

```text
Read CLAUDE.md, docs/STAGE1_BUILD_BRIEF.md (sections 5, 6, 9, 11) and docs/DECISIONS.md.

Task: Step 4 only — the first real screens, using the Step 3 services. No scenarios, options, policy or approval yet.

1. Command Centre: attention queue with the Hormuz signal (why surfaced, freshness, status), open cases and a "pending approvals" area (empty for now). No vanity KPI tiles.
2. Signal detail: source/fixture, freshness and validation status, labels; disposition actions (corroborate, challenge, monitor, dismiss, open case), each requiring a rationale and writing an audit event (in-memory).
3. Case workspace with tabs: Situation · Evidence · Impact Graph · Map · Scenarios · Options · Decision & Memory. Scenarios, Options and Decision show "Built in Step 5".
4. Lineage panel (drawer): opens from any number or object and shows the fields in brief §3.3, including the line "Demonstration value — not evidence of real-world conditions."
5. Impact graph: first/second/third-order view with hop filter; edges show their label and reason; resilience nodes are visually grouped; a keyboard-accessible list view of the same paths. A Domain Expert (demo) can "challenge" an edge with a rationale (audit event; edge shows "Challenged").
6. Map (brief §6), implemented exactly:
   - local geometry only, no tiles or network calls
   - permanent label "SYNTHETIC DEMO MOVEMENT — not live AIS or real vessel data"
   - Synthetic Vessel A moves along its synthetic track by interpolation and stops at the last point (no extrapolation)
   - play / pause / scrubber / speed (1×, 4×) / reset; no autoplay
   - reduced motion: static positions with timestamps
   - a track-and-events table as an accessible alternative
   - selecting the vessel, lane or marker opens lineage and highlights linked graph nodes
   - subtle fading trail and one bounded pulse on the disruption marker
7. Tests: the journey from Command Centre → signal → case → evidence → lineage panel works by keyboard; the map label is always present; reduced motion disables animation; the vessel stops at its final point.

Do NOT implement scenarios, options, policy rules, approval or memory.

At the end, report: files changed, commands actually run and results, what you rendered and checked (desktop/mobile/RTL, reduced motion) or that you could not, and open questions. Then stop and wait for my review.
```

**You review:** does the story read clearly? Can you click any number to see where it came from? Does the map feel alive but clearly synthetic?
