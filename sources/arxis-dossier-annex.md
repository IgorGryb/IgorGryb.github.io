# ARXIS — management and operating dossier

Project: `PRJ-ARXIS-PROTOTYPE`. Authored 2026-10-26. Status: internally specified design; not a deployed service. Source concept: `SRC-PRJ-ARXIS-DOC`. Methods: M-SIPOC, M-RACI, M-MOSCOW, M-FEASIBILITY, M-MEASURE.

## Decision and business model

An operating model for traceable design documentation and controlled project change.

**Problem:** A changed requirement can leave inconsistent decisions, versions and deliverables in circulation.
**Customer / decision user:** Design lead, documentation coordinator and project reviewer
**Payer:** Project organization; external service pricing untested
**Value proposition (hypothesis):** Visible ownership, approval status and downstream impact for every material change.

**Alternatives:**

- Shared folders and email: low friction, weak approval trace
- Existing document-management product: preferred when integration requirements are established
- Full CAD/BIM/GIS platform: out of scope

**Selected design decision:** Use one synthetic residential case and document handoffs before adding integrations or AI beyond assistance.

Market size, paid demand, channel conversion and real service delivery are not established. First access channel is a controlled review with the target decision user. Scale only after the problem and acceptance criteria survive that review.

## Product scope and acceptance

| ID | Must requirement | Acceptance evidence |
|---|---|---|
| ARXIS-REQ-01 | Every released artifact has an approved version | Reviewer checks the corresponding model/process step; records source, exception and outcome. |
| ARXIS-REQ-02 | Every Must requirement has a decision and deliverable link | Reviewer checks the corresponding model/process step; records source, exception and outcome. |
| ARXIS-REQ-03 | A changed requirement identifies affected downstream artifacts | Reviewer checks the corresponding model/process step; records source, exception and outcome. |

Should: export a decision memo and traceability view. Could: automate repetitive updates after correctness is established.
**Will not do:** Certified architectural design, full CAD/BIM/GIS integration, autonomous approval.

## Operating model — SIPOC

- Supplier: Client brief, design team and reviewers
- Inputs: Requirement IDs, versioned design artifacts, constraints and change requests
- Process: Register requirements and authority → Map requirements to decisions and deliverables → Assign version and review owner → Check traceability and resolve conflicts → Release baseline and propagate change
- Outputs: Reviewed documentation baseline and change-impact matrix
- Customer: Design lead, documentation coordinator and project reviewer

### Control and exception handoffs

| Step | Responsible | Accountable | Control / handoff |
|---|---|---|
| 1. Register requirements and authority | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |
| 2. Map requirements to decisions and deliverables | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |
| 3. Assign version and review owner | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |
| 4. Check traceability and resolve conflicts | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |
| 5. Release baseline and propagate change | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |

Roles are proposed functions, not claims of an existing staffed organization. Reviewer is consulted; downstream owner is informed. A single person may hold several roles, but cannot claim independent review of their own work.

**Exception policy:** An unapproved change cannot silently enter the baseline; stale dependent deliverables are explicitly withheld.

## End-to-end operationalization

| Stage | Input | Owner | Method | Tool | Artifact | Gate | Next owner |
|---|---|---|---|---|---|---|---|
| Initiation | Mandate and source record | Decision owner | M-RACI | Obsidian | Problem/mandate brief | Alternative of no action stated | Analyst |
| Analysis | Brief and approved sources | Analyst | M-SIPOC | Obsidian | Source and assumption map | Facts separated from hypotheses | Model owner |
| Modeling | Assumptions and baseline | Model owner | M-SCENARIO | Excel | Economic and operational model | Units, population and perspective explicit | Product owner |
| Design | Model and user needs | Product owner | M-FEASIBILITY | FigJam / local flow | Requirements and data flow | Every Must links to acceptance test | Delivery owner |
| Planning | Requirements and dependencies | Delivery owner | M-MOSCOW | Linear / local backlog | Prioritized handoff plan | Single accountable owner and next action | Implementer or analyst |
| Execution | Approved scope | Analyst / implementer | M-FEASIBILITY | Local documents/model | Controlled artifact version | No undocumented scope expansion | Reviewer |
| Testing | Artifact, baseline and forecast | Reviewer | M-SCENARIO | Excel / targeted tests | Test report | Normal and negative cases documented | Decision owner |
| Evaluation | Results and limitations | Decision owner | M-MEASURE | Dashboard + PowerPoint storyboard | Decision memo | Recommendation conditional on evidence | Change owner |
| Change management | New source, exception or decision | Change owner | M-RACI | Git + local change log | Impact and revised baseline | Dependent outputs marked stale/rechecked | Next stage owner |

Tool configuration is proposed, not connected. Local Markdown/YAML is authoritative. Cloud tools require a separate data-sharing decision. See [toolchain](../../../../00.%20ARCHIVE%20SYSTEM/portfolio/TOOLCHAIN-AND-HANDOFF.md).

## Financial and operating economics

Estimate coordination and rework cost from hours per change × loaded rate. Avoided rework is only a scenario until measured in a real project; no construction liability or certified-design claim.

Estimates must disclose cost population, currency, horizon and baseline. Sensitivity changes one driver or a declared scenario while other external assumptions remain equal. Missing required input makes the result unavailable. No forecast is reported as a realized business result.

## Technology management and build/buy/partner

Keep a source/assumption register, a model layer, a review layer and derived communication outputs. Stable IDs connect them. Access labels travel with the data. Maintain exportable local records and a documented exit path before selecting a hosted service.

Buy or reuse commodity task management, presentation and modeling tools. Build only a narrow calculation or validator when it resolves a decision-critical uncertainty. Partner for specialist legal, domain or security validation when the scope requires it. Proposed interfaces exchange artifact ID, version, owner, status and source IDs; no integration is claimed as implemented.

NFR design: outputs must be traceable and reproducible; invalid inputs must be visible; sensitive data must not leave the approved boundary. Response-time, uptime and capacity targets remain uncalibrated until a real user/process requires them.

## Metrics and dashboard specification

| Metric | Unit | Calculation | Source | Decision |
|---|---|---|---|---|
| Requirement coverage | fraction | Must requirements with valid decision and artifact / total Must | traceability register | Block incomplete release |
| Stale deliverables | count | released versions affected by unresolved change | change register | Withdraw or re-review |
| Change lead time | hours | approved_at - requested_at for completed changes | change timestamps | Inspect review bottleneck |

Metric owner: process/model owner. Review event: new result, changed assumption or operating incident, not an imposed calendar. For fractions, zero/missing denominator means unavailable. Actual metrics need a defined reporting period and event population; none are invented here.

Dashboard layout: decision/status at top, scenario comparison in the center, assumptions and exceptions below. Use a line chart for time, bars for comparable alternatives, and a table for exact constraints. Do not combine projected and realized values without explicit labeling.

## Validation and risk

**Hypothesis:** Explicit ownership and dependency mapping reduce uncontrolled version drift.

**Negative scenario:** Delete a decision link or change a requirement; release gate must fail and identify affected artifacts.

**Material limitation:** Traceability completeness does not prove correctness of engineering design or compliance with building law.

Validation layers: structural document review; arithmetic/model tests; scenario/exception walkthrough; external validation only when an appropriate recipient participates. Existing technical-baseline tests remain bounded evidence. User practice is optional and not a release gate for documentation.

## Delivery and stop conditions

Sequence: source and mandate → explicit model and handoffs → targeted validation → decision memo → review-ready case study. Continue if the model answers the decision with traceable assumptions. Pivot if the decision or economics changes. Pause if a necessary source is unavailable. Stop if the best supported option is no action or a simpler existing solution.

**Next event-triggered action:** Walk through a cross-discipline change and test whether each handoff preserves approval authority.

## Presentation storyboard

1. Decision and user problem. 2. Alternatives and source basis. 3. Product and operating model. 4. Economics and scenarios. 5. Architecture and ownership. 6. Validation result and limitations. 7. Recommendation and next decision.

Each slide and dashboard number must point back to this dossier and its model/run. Storyboard is not a delivered slide deck. No public publishing or external application is performed.

## Provenance and authoring boundary

This management model was authored with an AI agent from existing project sources, course materials and the approved user direction. It demonstrates the documented design and review process, not independent proof that the user performed every implementation step. All economic sample cases are synthetic.

## Multidimensional reinforcement and technical depth

Management connects technical/domain depth to product, operating and capital decisions; it does not replace that depth. The following application mappings are candidate design hypotheses, not proven benefits or claims of independent competence.

[Canonical mechanisms and evidence boundaries](../../../../00.%20ARCHIVE%20SYSTEM/portfolio/REINFORCEMENT-MAP.yaml). [Full qualification records and source links](../../../../00.%20ARCHIVE%20SYSTEM/portfolio/QUALIFICATION-INVENTORY.yaml). Program metadata has been reviewed; module-level support is not asserted for these candidate links.

### RF-04 — Infrastructure design and traceable change governance

**Career anchors:** EXP-SDG-2021, EXP-PORTFOLIO-2023.
**Learning sources (official titles):** Construction Management; Commercial Real Estate Modeling; IBM Systems Analyst; IBM AI Product Manager.

| Dimension | Proposed application |
|---|---|
| Technical | Requirements/decision/version graph, classification confidence, document lineage and access boundaries. |
| Product | A controlled coordination package for one design/change use case, not claimed full BIM integration. |
| Operating | Define authority to approve changes, affected deliverables and the downstream recipient. |
| Finance | Estimate rework/coordination cost and delay exposure; distinguish estimates from achieved savings. |

**Reinforcement mechanism (hypothesis):** Domain-aware change control can make documentation decisions visible to cost, schedule and delivery owners.

**Failure/cost of integration:** Incomplete document coverage or wrong automated classification can hide a material dependency.

**Comparison to run:** Compare file-list review with traceable change review on the same synthetic change set, including missing and misclassified documents.

**Next option and activation condition:** Expand the document class only after traceability and exception handling survive a review.

### RF-06 — Management metrics backed by financial and data controls

**Career anchors:** EXP-BNP-2025, EXP-SANTANDER-2022.
**Learning sources (official titles):** Microsoft Power BI Data Analyst; Microsoft Power BI Developer and Architect; BI Essentials for Finance Analysts (Power BI Edition); IBM Data Architecture; Business Analytics with Excel.

| Dimension | Proposed application |
|---|---|
| Technical | Metric lineage, schema/grain, denominator, reconciliation, access and stale-data controls. |
| Product | A decision dashboard and memo derived from canonical models, not an independent narrative. |
| Operating | Metric owner handles exceptions and version changes; decision owner accepts the reporting scope. |
| Finance | Separate cash, value, revenue, volume and estimates; define perspective and period before aggregation. |

**Reinforcement mechanism (hypothesis):** Shared definitions connect technical data quality with management interpretation and financial control.

**Failure/cost of integration:** A polished dashboard can conceal incompatible populations or denominators; centralization creates common-mode errors.

**Comparison to run:** Compare dashboard output to underlying records; inject missing/duplicate/stale data and test invalidation.

**Next option and activation condition:** Reuse a metric across projects only when its unit, grain and decision meaning match.
