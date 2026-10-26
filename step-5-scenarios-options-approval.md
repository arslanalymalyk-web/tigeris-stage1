# Step 5 — Scenarios, options, policy, simulated approval, audit and memory

```text
Read CLAUDE.md, docs/STAGE1_BUILD_BRIEF.md (sections 7, 8, 9, 11) and docs/DECISIONS.md.

Task: Step 5 only — complete the Stage 1 loop.

1. src/calc: pure deterministic functions for the four horizons (72h, 90d, 1y, 5y), using the ASSUMPTION driver and coefficient records. Each output carries a calculation ID, version, inputs, units, label and lineage. Confidence band derived from components (no percentage).
2. Scenarios tab: baseline vs what-if; sliders/inputs for the drivers within their ranges; four horizon panels with time windows; "conditional scenario result — not a forecast" wording; save a run (in-memory) with its manifest; reruns never overwrite the baseline.
3. Options tab: 3–4 ranked options with rationale, evidence/assumption refs, confidence band and basis, constraints, owner, required authority and expected effect (with lineage). Include exactly one SYNTHETIC capital-allocation option labelled "Synthetic portfolio — not investment advice". Include one option of type "Execute external action" so that BLOCK can be demonstrated.
4. src/policy: implement POL-DEMO-001 to 006 from the brief as a pure function returning { result: PASS | HOLD | BLOCK, ruleIds, explanation, policyVersion }. Label "DEMO POLICY — not client-approved". The UI cannot override BLOCK.
5. Workflow (src/state): case and decision states from brief §9.
   - Analyst submits options for review.
   - Approver (demo) can approve, reject, defer or request evidence, with a required rationale and a confirmation step.
   - Separation of duties: the preparer cannot approve.
   - "Approved (simulated)" creates a simulated handoff marked "Simulated — no action executed" and a MemoryRecord.
6. Decision & Memory tab, plus the Governance & Audit and Institutional Memory screens: the append-only audit list (filterable by case) and memory records with their evidence snapshot, rationale and labels.
7. Tests (replace the Step 1 todo):
   - "no option reaches Approved without a human decision record"
   - scenario determinism (same inputs → identical outputs)
   - each POL-DEMO rule triggers correctly
   - BLOCK cannot be bypassed
   - self-approval is blocked
   - audit events are written for disposition, run, policy check and decision
   - full keyboard journey from Command Centre to a memory record

No AI/LLM calls, no network calls, no real execution of anything.

At the end, report against every acceptance criterion ST1-01 to ST1-13 in the brief: pass / fail / not verified, with evidence. Include files changed, commands actually run and results, and remaining gaps. Then stop and wait for my review.
```

**You review:** the full loop, from signal to approved decision to memory entry, and the acceptance checklist.
