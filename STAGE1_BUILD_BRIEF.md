# TIGERIS AI OS — Stage 1 Build Brief

**Version:** 1.0 (for review) · **Date:** 26 October 2026 · **Delivery date:** not set (see DECISIONS.md D-03)

## 1. Purpose in one paragraph

Stage 1 is a **clickable demonstrator** that shows the TIGERIS operating loop working end to end on one case: a Strait of Hormuz disruption. A user can follow a signal into a case, inspect where every number comes from, see how the disruption propagates (including resilience links), watch an illustrative ship move on a small map, compare four time horizons, review ranked options (one of them a synthetic capital-allocation option), see PASS / HOLD / BLOCK rule results, and record a simulated human approval that lands in an audit log and institutional memory. Everything runs locally from labelled fixture data. It proves the **shape of the product**, not production readiness, live data or forecast accuracy.

## 2. Scope

### In Stage 1

| # | Capability | Notes |
|---|---|---|
| S1 | App shell and design system | Foundation palette and fonts (provisional), left navigation, top context bar, persistent Demonstration Mode banner, data-label badges, RTL-ready layout. |
| S2 | Demo role switcher | Seeded, labelled roles. No real login. |
| S3 | Command Centre | Attention queue: the Hormuz signal, the open case, pending approval, source freshness. |
| S4 | Signal detail | Source/freshness/validation display; disposition actions (corroborate, challenge, monitor, dismiss, open case). |
| S5 | Case workspace | Tabs: Situation · Evidence · Impact Graph · Map · Scenarios · Options · Decision & Memory. |
| S6 | Evidence and lineage panel | Every number and object opens its lineage. |
| S7 | Impact graph | Hormuz → route/shipping → energy → dependencies → resilience → institution. Each edge typed. |
| S8 | Hormuz map with one illustrative moving ship | See §6. |
| S9 | Scenarios | Baseline plus what-if; 72h · 90d · 1y · 5y; deterministic. |
| S10 | Options | Ranked options with evidence, assumptions, confidence band, owner and authority. Includes one SYNTHETIC capital-allocation option. |
| S11 | Policy checks | PASS / HOLD / BLOCK with rule IDs and explanations (demo rules, §8). |
| S12 | Simulated human approval | Approve, reject, defer or request evidence, with rationale. Separation of duties enforced. |
| S13 | Audit log and memory | Append-only event list; approved decision becomes a memory record. |

### Not in Stage 1 (deferred)

Trucks and land logistics · live or licensed feeds (AIS, TankerMap, Bloomberg, Aladdin, OPEC, OFAC) · real source import/validation pipeline · database or backend · real login, SSO or MFA · AI/LLM model calls and agents · full separate resilience case · Arabic content (layout stays RTL-ready) · air-gap packaging · back-testing · Priority docs 04, 06 and 07 (data marketplace, policy simulator, briefing agent) · decision-drift detection (only the memory record is in scope).

## 3. Data rules for Stage 1

### 3.1 The five labels

| Label | Meaning | Stage 1 use |
|---|---|---|
| `OBSERVED` | Directly present in an approved, recorded source | **Not used** unless a real source record exists. None is planned. |
| `INFERRED` | A derived relationship or conclusion | Graph edges derived by a stated rule. |
| `ASSUMPTION` | A user- or scenario-entered condition | Scenario drivers and calculation coefficients. |
| `SYNTHETIC` | Fabricated demonstration value | Signal, institution, exposures, vessel, track, capital portfolio. |
| `ILLUSTRATIVE` | Visual/example content, not evidence | Map geometry, shipping-lane line, template narrative text. |

### 3.2 Hard rules

1. **No real-world statistics.** Stage 1 contains no real oil-flow, price, traffic or percentage figures. All numbers are SYNTHETIC or ASSUMPTION.
2. **The Hormuz signal is synthetic.** It is modelled on a generic chokepoint disruption. It is not a real event and has no real date. Its UI text says so. A real event window is a client decision (DECISIONS.md C-03).
3. **Lineage or nothing.** If a value lacks lineage, the UI must not display it.
4. **Labels travel.** Labels appear on cards, charts, the map, lineage panels, the audit log and memory records.
5. **Synthetic register.** Every fixture file starts with a header comment stating that it is synthetic, what it represents, and its fixture ID. `docs/SYNTHETIC_DATA_REGISTER.md` is created in Step 3 and lists every fixture.

### 3.3 Lineage panel (what it shows)

For any number or object: label · value and units · fixture/source record ID · assumption IDs used · calculation ID and version · input values · time window · "why this exists" note · a reminder line: *"Demonstration value — not evidence of real-world conditions."*

## 4. Users and demo roles

| Demo role | Can do | Cannot do |
|---|---|---|
| Analyst (demo) | Disposition the signal, edit scenario drivers, prepare and submit options | Approve |
| Domain Expert (demo) | Challenge an edge or evidence item; endorse or request revision | Approve (unless separately granted) |
| Approver (demo) | Approve, reject, defer or request evidence on submitted options | Approve an option they prepared |
| Auditor (demo) | Read audit log, lineage and memory | Change anything |

Institution name: **"Demonstration Institution (synthetic)"**. No real names of people or organisations.

## 5. The journey (what a reviewer clicks through)

1. **Choose a role** → Demonstration Mode banner shows role, institution, environment "Local demo" and data mode "Synthetic".
2. **Command Centre** → the Hormuz signal sits at the top, with why it is surfaced, freshness and status.
3. **Signal detail** → the analyst marks it "Corroborate" (or "Challenge") with a rationale and opens a case.
4. **Case: Situation** → what changed, why it matters, unknowns, owner, state.
5. **Case: Evidence** → evidence cards, each labelled; click any value to see lineage.
6. **Case: Impact Graph** → first-, second- and third-order paths, including resilience nodes (alternative route, buffer stock, recovery time). Edge labels: INFERRED or ASSUMPTION, with a reason.
7. **Case: Map** → the strait, an illustrative lane, one synthetic vessel moving along a synthetic track, and a disruption marker. Clicking the vessel opens its lineage.
8. **Case: Scenarios** → baseline vs what-if, four horizons; changing a driver reruns the calculation; the same inputs always give the same result.
9. **Case: Options** → three to four ranked options, including the SYNTHETIC capital-allocation option; each shows evidence, assumptions, confidence band, owner, required authority and its policy result.
10. **Submit for review** → switch to Approver; HOLD/BLOCK results are visible; approve, reject, defer or request evidence, with rationale.
11. **Decision & Memory** → the audit log shows every step; the approved decision appears as a memory record. Handoff is shown as **"Simulated — no action executed."**

## 6. Hormuz map specification (Stage 1)

| Item | Requirement |
|---|---|
| Geography | Strait of Hormuz region only (approximately the Persian Gulf exit into the Gulf of Oman). |
| Base map | Simplified coastline **bundled locally**. No tile server or runtime network call. Geometry source is decision D-07. Base map label: **ILLUSTRATIVE**. |
| Objects | One illustrative shipping lane (ILLUSTRATIVE). One vessel, **"Synthetic Vessel A"** (SYNTHETIC). One disruption marker (SYNTHETIC). One or two port/terminal nodes with generic names (ILLUSTRATIVE). |
| Movement | The vessel moves along a SYNTHETIC timestamped track by interpolating between fixture points. When the track ends it stops; it never extrapolates. |
| Persistent map label | **"SYNTHETIC DEMO MOVEMENT — not live AIS or real vessel data"** is always visible on the map. |
| Controls | Play / pause, time scrubber, speed (1× / 4×), reset. No autoplay on first load. |
| Reduced motion | If the user prefers reduced motion, or toggles it, show static positions with timestamps and no animation. |
| Accessible alternative | A list or table view of track points and events, operable by keyboard. |
| Selection | Clicking (or keyboard-selecting) the vessel, lane or marker opens its lineage panel and its linked graph nodes. |
| Visual tone | Light, calm palette consistent with the app. Motion is subtle: a short fading trail and one bounded pulse on the disruption marker. No perpetual glow. |
| No real data | No real vessel names, IMO or MMSI numbers, real positions or real port statistics. |

## 7. Scenarios and calculations

- **Drivers** (all ASSUMPTION, each with an ID, units, allowed range and default):
  - disruption duration (days)
  - route availability (%)
  - oil price assumption (USD/bbl, synthetic)
  - substitution lag (days)
- **Horizons:** 72 hours, 90 days, 1 year, 5 years. Each panel shows the time window, baseline vs what-if, drivers used and the confidence band.
- **Outputs:** a small set of synthetic indicators (for example, an "exposure-affected index" for the synthetic institution, rerouting delay in days, and a resilience recovery estimate). Each output has a calculation ID, formula version, inputs and units.
- **Rules:**
  - Calculations are pure, deterministic functions with unit tests.
  - Coefficients are ASSUMPTION records, not hidden constants.
  - What-if runs never overwrite the baseline.
  - Outputs are described as "conditional scenario results", never as forecasts.
- **Confidence band:** derived deterministically from components (source quality, corroboration, graph completeness, assumption load). It is shown as Low / Moderate / High with its basis, never as a percentage.

## 8. Demo policy rules (PASS / HOLD / BLOCK)

All rules are labelled **"DEMO POLICY — not client-approved"**.

| Rule ID | Condition | Result |
|---|---|---|
| POL-DEMO-001 | Option has a number without lineage, or no evidence/assumption references | HOLD — "missing lineage" |
| POL-DEMO-002 | Option depends on evidence marked Challenged or Unverified | HOLD — "evidence under challenge" |
| POL-DEMO-003 | Option action class is "Capital reallocation" | HOLD until reviewed by Approver (demo) with capital authority |
| POL-DEMO-004 | Approver is the same demo user who prepared the option | BLOCK — separation of duties |
| POL-DEMO-005 | Option type is "Execute external action" | BLOCK — no execution in Stage 1 |
| POL-DEMO-006 | Supporting evidence is older than its freshness limit | HOLD — "stale evidence" |

Policy evaluation is a pure function that returns the result, rule IDs, explanation and policy version. **The UI cannot override BLOCK.**

## 9. Case and decision states

`Draft → In analysis → Ready for review → Under review → { Approved (simulated) | Rejected | Deferred | Evidence requested }`

- "Evidence requested" and "Deferred" return the case to "In analysis".
- "Approved (simulated)" creates a **simulated handoff** (owner and status only; nothing executes) and a **memory record**.
- Every transition writes an append-only audit event: actor role, time, from/to state, rationale and policy result.
- **Invariant:** no option reaches "Approved (simulated)" without a human decision record from an authorised demo approver.

## 10. Architecture (Stage 1 only)

- Front-end-only app; typed fixtures; a service layer (`src/services/`) with interfaces so a backend can replace the fixtures later.
- Suggested modules: `domain/` (types), `fixtures/` (synthetic data), `calc/` (deterministic calculations), `policy/` (rules), `services/` (fixture-backed repositories), `state/` (case workflow and audit), `ui/` (components and screens), `map/`.
- In-memory audit log and memory for the session. Optional local persistence only for convenience, never as the source of truth.
- No network calls at runtime.
- Domain type names follow the backend schema design so they can map later: Source, EvidenceItem, Entity, Relationship, Signal, Case, CaseEvent, ScenarioRun, Assumption, ScenarioResult, Recommendation, PolicyDecision, HumanDecision, MemoryRecord, AuditEvent, VesselTrack.

## 11. Acceptance criteria (Stage 1)

| ID | Pass condition |
|---|---|
| ST1-01 | The Demonstration Mode banner, institution, role, environment and data mode are visible on every screen. |
| ST1-02 | Every displayed number and map object shows a label and opens a lineage panel. An automated test enforces this. |
| ST1-03 | No real-world statistic, real organisation name or real vessel identifier appears anywhere. |
| ST1-04 | A user can go from the Command Centre to a recorded simulated approval and memory record for the Hormuz case. |
| ST1-05 | The impact graph shows at least one first → second → third-order path, including at least one resilience node; every edge is typed and has a reason. |
| ST1-06 | The map shows the synthetic vessel moving along its synthetic track with play, pause, scrubber and reduced motion; the synthetic label stays visible; selecting the vessel opens lineage. |
| ST1-07 | Changing a scenario driver reruns all four horizons deterministically; the same inputs give identical outputs (unit test). |
| ST1-08 | The options include one SYNTHETIC capital-allocation option labelled "not investment advice; synthetic portfolio". |
| ST1-09 | Policy results show PASS/HOLD/BLOCK with rule IDs; BLOCK cannot be overridden in the UI; separation of duties is enforced. |
| ST1-10 | No option reaches Approved without a human decision record (automated test). |
| ST1-11 | The audit log records every disposition, scenario run, policy check and decision. |
| ST1-12 | The core journey works keyboard-only; status is never shown by colour alone; layout tokens are RTL-ready. |
| ST1-13 | The app runs with the network disabled. |

## 12. Build steps

Use the prompts in `docs/prompts/`, one at a time, with a human review between each.

| Step | Prompt file | Result to review |
|---|---|---|
| 1 | `step-1-repo-setup.md` | Project scaffold, checks and docs in place; nothing visible yet |
| 2 | `step-2-shell-and-design.md` | App frame, banner, labels, role switcher |
| 3 | `step-3-domain-and-fixtures.md` | Types, synthetic fixtures, register, lineage test |
| 4 | `step-4-command-centre-case-graph-map.md` | Command Centre, signal, case, evidence, graph, map |
| 5 | `step-5-scenarios-options-approval.md` | Scenarios, options, policy, approval, audit, memory |

## 13. Known risks

| Risk | Control |
|---|---|
| A polished demo is mistaken for real intelligence | Persistent banner, labels on every object, "not live AIS" map label, no real figures |
| Scope creep (trucks, live feeds, more cases) | Deferred list above; changes go through DECISIONS.md |
| Map looks "live" | Synthetic label, no extrapolation, no autoplay, track list alternative |
| Rework if client blueprint or palette changes | Tokens in one place; service interfaces; provisional decisions logged |
