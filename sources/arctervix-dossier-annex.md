# Arctervix — management and operating dossier

Project: `PRJ-ARCTERVIX-PROTOTYPE`. Authored 2026-10-26. Status: internally specified design; not a deployed service. Source concept: `SRC-ARCTERVIX-IM-CHAT-001`. Methods: M-SIPOC, M-RACI, M-DCF, M-SCENARIO, M-FEASIBILITY, M-MEASURE.

## Decision and business model

Capital allocation and financing decisions under operational and liquidity constraints.

**Problem:** A positive investment valuation can conceal an inability to fund the next operating or investment step.
**Customer / decision user:** Investment analyst and capital-allocation decision owner
**Payer:** Internal investment function; external research-service demand remains untested
**Value proposition (hypothesis):** An auditable explanation of which investment policies remain feasible and why.

**Alternatives:**

- NPV-only spreadsheet: simple, but no explicit liquidity path
- Existing portfolio engine: useful liquid-market module, insufficient for industrial funding
- Full adaptive optimizer: defer until fixed-policy ledgers reconcile

**Selected design decision:** Use the fixed-policy synthetic financing case as the first management model; keep the portfolio engine as a supporting module.

Market size, paid demand, channel conversion and real service delivery are not established. First access channel is a controlled review with the target decision user. Scale only after the problem and acceptance criteria survive that review.

## Product scope and acceptance

| ID | Must requirement | Acceptance evidence |
|---|---|---|
| ARCTERVIX-REQ-01 | Every plan separates operating and financing cash | Reviewer checks the corresponding model/process step; records source, exception and outcome. |
| ARCTERVIX-REQ-02 | Infeasible plans are excluded from recommendation | Reviewer checks the corresponding model/process step; records source, exception and outcome. |
| ARCTERVIX-REQ-03 | Every changed assumption identifies affected claims | Reviewer checks the corresponding model/process step; records source, exception and outcome. |

Should: export a decision memo and traceability view. Could: automate repetitive updates after correctness is established.
**Will not do:** Live trading, fund launch, production financing decisions, adaptive ML optimizer.

## Operating model — SIPOC

- Supplier: Company assumptions and approved market sources
- Inputs: Operating cash flows, capex, equity, debt terms, maturity and cash buffer
- Process: Register mandate and financing constraints → Separate operating assumptions from capital structure → Compare invest, stage, defer and reject → Check debt service and funding gaps → Document conditional decision and escalation
- Outputs: Scenario ledger, eligible actions and investment memo
- Customer: Investment analyst and capital-allocation decision owner

### Control and exception handoffs

| Step | Responsible | Accountable | Control / handoff |
|---|---|---|
| 1. Register mandate and financing constraints | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |
| 2. Separate operating assumptions from capital structure | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |
| 3. Compare invest, stage, defer and reject | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |
| 4. Check debt service and funding gaps | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |
| 5. Document conditional decision and escalation | Analyst / process owner | Decision owner | Record input version, output ID and reviewer; exceptions escalate before the next release. |

Roles are proposed functions, not claims of an existing staffed organization. Reviewer is consulted; downstream owner is informed. A single person may hold several roles, but cannot claim independent review of their own work.

**Exception policy:** Negative cash or buffer breach excludes the schedule; do not treat later contractual flows as realized.

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

Unlevered project NPV is separate from funding cash flows. Do not add debt proceeds to project value. Research-service cost would be analyst hours × loaded rate plus data/review costs; no service revenue is assumed.

Estimates must disclose cost population, currency, horizon and baseline. Sensitivity changes one driver or a declared scenario while other external assumptions remain equal. Missing required input makes the result unavailable. No forecast is reported as a realized business result.

## Technology management and build/buy/partner

Keep a source/assumption register, a model layer, a review layer and derived communication outputs. Stable IDs connect them. Access labels travel with the data. Maintain exportable local records and a documented exit path before selecting a hosted service.

Buy or reuse commodity task management, presentation and modeling tools. Build only a narrow calculation or validator when it resolves a decision-critical uncertainty. Partner for specialist legal, domain or security validation when the scope requires it. Proposed interfaces exchange artifact ID, version, owner, status and source IDs; no integration is claimed as implemented.

NFR design: outputs must be traceable and reproducible; invalid inputs must be visible; sensitive data must not leave the approved boundary. Response-time, uptime and capacity targets remain uncalibrated until a real user/process requires them.

## Metrics and dashboard specification

| Metric | Unit | Calculation | Source | Decision |
|---|---|---|---|---|
| Funding gap to buffer | EUR thousands | max(0, buffer - minimum scheduled cash) | scenario ledger | Exclude or redesign financing |
| Eligible strategies | count | count(plans satisfying all required constraints) | scenario comparison | Restrict recommendation set |
| Project NPV | EUR thousands | sum((OCF-capex)/(1+r)^t) | assumptions and model | Compare value separately from feasibility |

Metric owner: process/model owner. Review event: new result, changed assumption or operating incident, not an imposed calendar. For fractions, zero/missing denominator means unavailable. Actual metrics need a defined reporting period and event population; none are invented here.

Dashboard layout: decision/status at top, scenario comparison in the center, assumptions and exceptions below. Use a line chart for time, bars for comparable alternatives, and a table for exact constraints. Do not combine projected and realized values without explicit labeling.

## Validation and risk

**Hypothesis:** Financing constraints change feasible actions without changing the same plan's operating NPV.

**Negative scenario:** Remove refinancing and shorten maturity; recommendation must not retain an infeasible plan.

**Material limitation:** Annual timing may hide intra-year cash shortfalls; synthetic assumptions cannot establish economic superiority.

Validation layers: structural document review; arithmetic/model tests; scenario/exception walkthrough; external validation only when an appropriate recipient participates. Existing technical-baseline tests remain bounded evidence. User practice is optional and not a release gate for documentation.

## Delivery and stop conditions

Sequence: source and mandate → explicit model and handoffs → targeted validation → decision memo → review-ready case study. Continue if the model answers the decision with traceable assumptions. Pivot if the decision or economics changes. Pause if a necessary source is unavailable. Stop if the best supported option is no action or a simpler existing solution.

**Next event-triggered action:** Interpret sensitivity to maturity and capex; document decision boundaries before adding adaptive control.

## Presentation storyboard

1. Decision and user problem. 2. Alternatives and source basis. 3. Product and operating model. 4. Economics and scenarios. 5. Architecture and ownership. 6. Validation result and limitations. 7. Recommendation and next decision.

Each slide and dashboard number must point back to this dossier and its model/run. Storyboard is not a delivered slide deck. No public publishing or external application is performed.

## Provenance and authoring boundary

This management model was authored with an AI agent from existing project sources, course materials and the approved user direction. It demonstrates the documented design and review process, not independent proof that the user performed every implementation step. All economic sample cases are synthetic.

## Multidimensional reinforcement and technical depth

Management connects technical/domain depth to product, operating and capital decisions; it does not replace that depth. The following application mappings are candidate design hypotheses, not proven benefits or claims of independent competence.

[Canonical mechanisms and evidence boundaries](../../../../00.%20ARCHIVE%20SYSTEM/portfolio/REINFORCEMENT-MAP.yaml). [Full qualification records and source links](../../../../00.%20ARCHIVE%20SYSTEM/portfolio/QUALIFICATION-INVENTORY.yaml). Program metadata has been reviewed; module-level support is not asserted for these candidate links.

### RF-01 — Financing-constrained capital allocation

**Career anchors:** EXP-SANTANDER-2022, EXP-BNP-2025.
**Learning sources (official titles):** Financial Engineering and Risk Management; Valuation Modeling; Advanced Statistics for Data Science; Business and Financial Modeling.

| Dimension | Proposed application |
|---|---|
| Technical | Cash-flow ledgers, stochastic assumptions, sensitivity, constraints, separation of forecast and decision. |
| Product | A decision package comparing immediate investment, staging, deferral and abandonment. |
| Operating | Model owner reconciles inputs; reviewer checks liquidity and maturity before capital authorization. |
| Finance | Project value and financing feasibility are separate outputs; test debt service and refinancing restrictions. |

**Reinforcement mechanism (hypothesis):** Valuation identifies potential value; financing and operating constraints filter actions that can actually be funded.

**Failure/cost of integration:** Common optimistic assumptions can bias valuation and liquidity together; integration does not remove model risk.

**Comparison to run:** Compare NPV-only ranking with liquidity-constrained fixed rules under identical external scenarios; include no refinancing and delayed cash flows.

**Next option and activation condition:** Extend to another asset or staged industrial decision only after the ledger and action constraints pass checks.

### RF-02 — Evidence infrastructure for capital and research decisions

**Career anchors:** EXP-BNP-2025, EXP-PORTFOLIO-2023.
**Learning sources (official titles):** IBM Data Architecture; IBM Data Engineering; IBM RAG and Agentic AI; Vector Database Fundamentals; Financial Modeling and Analysis.

| Dimension | Proposed application |
|---|---|
| Technical | Lineage, schemas, retrieval, lexical/semantic comparison, citation validation and abstention. |
| Product | A source-grounded research pack, not an unreviewed recommendation engine. |
| Operating | Source steward controls ingest/access; reviewer resolves contradictions and approves reuse. |
| Finance | Compare total research and review cost; record cost of undetected error separately from time saved. |

**Reinforcement mechanism (hypothesis):** Retrieval can reduce search effort only if provenance and review keep the decision evidence usable.

**Failure/cost of integration:** Faster retrieval can amplify stale or correlated sources; semantic relevance is not truth.

**Comparison to run:** Compare manual, lexical and assisted retrieval on the same questions; score citations, missing evidence, contradictions and review time.

**Next option and activation condition:** Introduce a new approved corpus only after source isolation and citation tests pass.

### RF-05 — Industrial data translated into staged operating investment

**Career anchors:** EXP-SDG-2021, EXP-SANTANDER-2022, EXP-PORTFOLIO-2023.
**Learning sources (official titles):** IBM Machine Learning; Data Science Decisions in Time; Microsoft Data Architecture for Modern Data Stacks; Financial Management; Valuation Modeling.

| Dimension | Proposed application |
|---|---|
| Technical | Time-aware validation, data quality, prediction thresholds, maintenance actions and constrained scenarios. |
| Product | Decision support for one maintenance or supply-chain intervention, not a general industrial platform. |
| Operating | The model must lead to an executable intervention with capacity, owner, timing and fallback. |
| Finance | Include false positives, missed failures, downtime and intervention cost; assess staged investment and liquidity separately. |

**Reinforcement mechanism (hypothesis):** Forecast accuracy has business value only through an executable action and its net operating/financing consequences.

**Failure/cost of integration:** A better predictive metric may worsen operating cost; distribution shifts and scarce intervention capacity can reverse the result.

**Comparison to run:** Compare fixed rule, forecast-only rule and cost/capacity-constrained action on the same cases with degraded data.

**Next option and activation condition:** Add an asset or data source only after action-level benefit and failure bounds are understood.

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

### RF-07 — Advanced technical options with explicit activation conditions

**Career anchors:** EXP-PORTFOLIO-2023.
**Learning sources (official titles):** Algorithms; Probabilistic Graphical Models; Statistical Methods for Computer Science; IBM AI Engineering; IBM DevOps and Software Engineering; Decentralized Finance (DeFi): The Future of Finance; Building AI Cloud Apps with Microsoft Azure.

| Dimension | Proposed application |
|---|---|
| Technical | Algorithmic complexity, probabilistic inference, ML evaluation, reproducible delivery and optional programmable-contract design. |
| Product | A menu of technical options attached to explicit unmet requirements; no automatic blockchain/ML requirement. |
| Operating | Assess skill/resource needs, maintenance, failure recovery, security review and vendor exit before activation. |
| Finance | Compare incremental decision benefit with integration, operating and switching cost; preserve a simpler baseline. |

**Reinforcement mechanism (hypothesis):** Technical breadth supplies alternative solution paths; governance makes selection conditional on a demonstrated bottleneck.

**Failure/cost of integration:** Complexity can exceed the value of the problem; a course does not establish production security or deployability.

**Comparison to run:** Specify a bottleneck first, then benchmark the candidate against the simplest adequate approach with negative and resource-limit cases.

**Next option and activation condition:** Activate one technical extension only when it resolves a material assumption and its cost/risk is justified; otherwise retain as observing.
