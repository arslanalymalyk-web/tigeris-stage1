# Step 3 — Domain model, synthetic fixtures and the lineage test

```text
Read CLAUDE.md, docs/STAGE1_BUILD_BRIEF.md (sections 3, 6, 7, 8, 9, 10) and docs/DECISIONS.md.

Task: Step 3 only — data model and labelled synthetic data. No new screens.

1. src/domain: typed models for Source, EvidenceItem, Entity, Relationship, Signal, Case, CaseEvent, Assumption, ScenarioRun, ScenarioResult, Recommendation, PolicyDecision, HumanDecision, MemoryRecord, AuditEvent and VesselTrack (with TrackPoint).
   - Every value-bearing type carries: label (the 5-value enum), lineage { fixtureId, sourceRecordIds[], assumptionIds[], calculationId?, calculationVersion?, units?, note }.
   - Confidence is stored as components and displayed as a band (Low / Moderate / High). No percentage field is exposed to the UI.
2. src/fixtures: SYNTHETIC data for the Hormuz case. Every file starts with a header comment: "SYNTHETIC DEMONSTRATION DATA — not real-world data", plus the fixture ID and what it represents.
   - One synthetic signal (a generic chokepoint disruption; no real event date and no reference to a real event, per D-10). Use relative synthetic times such as "T+0h", "T+6h".
   - The institution "Demonstration Institution (synthetic)" and its synthetic exposures/dependencies.
   - Graph entities and edges: chokepoint → shipping lane → energy flow → dependency → resilience nodes (alternative route, buffer stock, recovery time) → institution and synthetic portfolio. Each edge typed INFERRED or ASSUMPTION, with a reason.
   - Scenario drivers as ASSUMPTION records (ID, units, range, default) per brief §7, plus calculation coefficients as ASSUMPTION records.
   - Map data per D-07: a polished, simplified Hormuz schematic drawn as local SVG path data for this project. Do not trace or copy any copyrighted or licensed map. Label it ILLUSTRATIVE with the note "schematic — not to scale, not for navigation". Also: one ILLUSTRATIVE lane, one or two generic ILLUSTRATIVE port nodes, one SYNTHETIC disruption marker, and "Synthetic Vessel A" with a SYNTHETIC timestamped track (about 20–40 points).
   - No real-world statistics, organisation names, vessel names, IMO or MMSI numbers.
3. src/services: read-only service interfaces (CaseService, GraphService, MapService, ScenarioInputService) with fixture-backed implementations, so a backend can replace them later.
4. docs/SYNTHETIC_DATA_REGISTER.md: a table of every fixture (ID, file, what it represents, label, why it is synthetic).
5. Tests (replace the Step 1 todo):
   - "lineage/label test": walks all fixtures and fails if any numeric value or map object lacks a label or lineage.
   - "no real identifiers" test: fails if fixtures contain any name from a denylist (PIF, Mubadala, ADIA, Aramco), or IMO/MMSI-like numbers.
   - Graph test: at least one first → second → third-order path exists and includes a resilience node.

Do NOT build screens, calculations, policy rules or the approval flow.

At the end, report: files changed, commands actually run and results, the fixture list, any assumptions, and open questions. Then stop and wait for my review.
```

**You review:** the synthetic data register. Check that every value is labelled and nothing looks real.
