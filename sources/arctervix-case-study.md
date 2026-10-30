# Arctervix — Value is not funding feasibility

Private portfolio design study. Not a client deployment.

## Problem and decision user

A positive investment valuation can conceal an inability to fund the next operating or investment step. The proposed user is investment analyst and capital-allocation decision owner.

## Operating and economic approach

Capital allocation and financing decisions under operational and liquidity constraints. The package joins the business question, product scope, operating handoffs, technology/data assumptions and financial consequences. Existing tools and simpler alternatives remain part of the decision.

## Checked result

A positive project NPV can coexist with an immediate cash shortfall. Across 85 synthetic baseline/sensitivity cases, financing and maturity change which fixed schedules remain feasible. Thirteen repository tests cover accounting identities, downside cases and invalid input.

## Capabilities illustrated

Cash-flow timing; financing; risk constraints; decision governance. These are demonstrated documentary/model mechanisms, not a certification of personal independent mastery.

## Limits and next use

Annual timing may hide intra-year cash shortfalls; synthetic assumptions cannot establish economic superiority. Use the detailed specification and validation memo to scope a real mandate, identify missing data and define the smallest decisive test. Publication and deployment require separate review.

## Delivery specification


Private design study. This specification complements MANAGEMENT-DOSSIER.md and MODEL-VALIDATION-MEMO.md. It does not describe a launched investment service.

## Mandate and product boundary

The first product is an internal investment-screening package for an analyst and a capital-allocation decision owner. It answers: which stated investment schedules have positive operating value, which are fundable, and which assumption changes reverse the conclusion? It does not choose a security, estimate an investable strategy's return or issue a financing commitment.

The management proposition is a controlled chain from an economic idea to a reviewable decision. The portfolio engine remains one supporting module. Internal Model connects economic state, observations, institutional dependencies, financing, liquidity, available actions and inference. Only the financing–liquidity–fixed-action slice is exercised in this release. DIM and other original theoretical constructs remain research hypotheses, not validated economic laws.

## Required input contract

| Input | Type/unit | Control | Missing-data treatment |
|---|---|---|---|
| Mandate and decision owner | Text / stable ID | Identify decision rights and prohibited actions | Pause recommendation |
| Source record | ID, version, date, confidentiality | Preserve original and content hash | Quarantine unsupported claim |
| Operating cash flows | Six finite values, EUR thousands | Incremental net operating cash, not accounting profit; disclose taxes and working-capital treatment | No imputed zero |
| Capital expenditure | Six nonnegative finite values, EUR thousands | Match payment period and scope | No value or feasibility conclusion |
| Equity | Nonnegative EUR thousands | Treat as opening funding, not operating value | No feasibility conclusion |
| Debt principal/coupon | EUR thousands / fraction per year | Contractual assumption, not inferred from market availability | Evaluate equity-only explicitly, not as substitute fact |
| Maturity | Integer years from initial draw | Must remain inside model horizon | Reject unsupported horizon; never shorten silently |
| Buffer | Nonnegative EUR thousands | Explain reserve policy and operating obligations excluded | No feasibility approval |
| Discount rate | Fraction per year, greater than -1 | Same time/currency basis as cash flows | No NPV assertion |
| Regime | Normal/restricted | Normal permits one assumed refinancing; restricted prohibits it | Present both scenarios, not invented likelihoods |

The reference interface accepts already normalized synthetic inputs. Importing business data requires an analyst to reconcile gross revenue, cost, tax, working capital and capex into those inputs. The current model is not a full company valuation or accounting system.

## Process ownership and controls

1. The decision owner defines the mandate and acceptable loss of liquidity. Output: signed-off scope, not a transaction instruction.
2. The analyst prepares source and assumption records, identifies correlated assumptions and constructs the no-investment baseline. A finance reviewer checks units, timing and excluded cash obligations.
3. The model owner runs identical operating assumptions across financing regimes. Output: immutable run with model hash, parameter set, ledger, infeasible actions and sensitivity results.
4. The reviewer reconciles cash and debt identities and reproduces at least one boundary case independently. Until that review actually occurs, the package says agent review, not independent review.
5. The decision owner receives feasible alternatives, counterfactual rejected schedules, downside conditions and information gaps. The decision log records continue/pause/pivot/stop with rationale.
6. A changed source or financing term reopens affected runs and communication outputs. Historical versions remain available; no dashboard may silently retain old numbers.

Roles are proposed functions. The current evidence does not establish that a staffed investment committee or client has used this workflow.

## Architecture and sourcing choices

Layer 1 preserves source documents and assumptions. Layer 2 normalizes units and time conventions. Layer 3 computes separate operating value and financing ledgers. Layer 4 validates identities, limits and scenarios. Layer 5 produces the memo, dashboard and portfolio case. IDs and hashes connect these layers.

Use local Markdown/YAML and Git for controlled narrative and models; a controlled spreadsheet is the intended analyst-facing calculation view. Python is retained only as the independent deterministic reference and regression check. Existing collaboration and presentation products can be reused after access and confidentiality review. No SaaS connection, paid license or production integration is assumed.

A future data adapter must preserve source timestamps, missingness, currency, period grain and revision history. A future optimizer must first demonstrate improved decisions against these fixed rules, net of modeling, review and maintenance cost. ML, programmable contracts and blockchain remain optional; none resolves an identified first-release need.

## Service economics and adoption

No demand, revenue or willingness-to-pay estimate is claimed. An internal pilot can measure analyst preparation time, reviewer correction time, rejected invalid inputs and decision turnaround. Loaded hourly costs, data fees and maintenance must be supplied before estimating delivery economics. Compare the integrated workflow with an NPV-only sheet and a manual financing review using the same cases.

Potential reinforcement is conditional: liquidity controls may prevent a superficially attractive but unfinanceable recommendation. The cost is extra input collection and review. The release demonstrates this mechanism on synthetic schedules; it does not prove a net economic benefit in an organization.

## Risk register and stop rules

| Risk | Proposed owner | Control | Residual limitation / escalation |
|---|---|---|---|
| Annual aggregation hides shortfall | Finance reviewer | Require a finer cash calendar before real commitment | Current six-period model cannot approve intra-year liquidity |
| Optimistic common assumptions bias both value and liquidity | Decision owner | Downside cash/capex cases and explicit source challenge | No probabilistic calibration |
| Refinancing unavailable | Treasury/finance function | Restricted regime; confirmed terms required for use | Synthetic regime not a credit offer |
| Funding counted as value | Model owner | Unlevered NPV excludes equity, draw and refinancing | Equity return is not calculated |
| Invalid input or silent horizon change | Model owner | Finite-value checks and explicit maturity rejection | No automatic horizon extension |
| Confidential sources in presentation | Publication reviewer | Allowlisted claims; no source-document export | Requires separate approval |
| A polished study mistaken for deployment | Portfolio owner | Maturity labels in every format | No client, revenue or performance claim |

Pause if required source, owner or financing term is unavailable. Pivot if a simpler review achieves the same decision quality at lower total cost. Stop an investment schedule that breaches its required buffer; this does not automatically stop the research project.

## Acceptance and release evidence

ARCTERVIX-REQ-01 is checked by ledger identities and the financing-independent NPV regression test. ARCTERVIX-REQ-02 is checked by explicit infeasible status, first breach and the memo's exclusion rule. ARCTERVIX-REQ-03 is supported by model/source hashes and archive change-impact checks; a change requires a new reviewed run rather than an assertion of automatic economic correctness.

The bounded review covers 16 baseline and 69 sensitivity cases, plus 13 repository tests. It includes no refinancing, earlier maturity, delayed operating flows, negative operations, insufficient cash, capex changes and invalid inputs. The evidence supports the design-study claims only. Production security, regulatory suitability, external demand and observed business outcomes are not acceptance claims of this package.

## Interview narrative and next options

Problem: a positive project valuation can hide a funding constraint. Decision: separate operating value from the cash and debt path before considering adaptive optimization. Difficulty: timing conventions and horizon boundaries can silently change the financial question. Correction: reject maturity outside the modeled horizon and non-finite inputs; expose counterfactual flows after a breach. Result: a reproducible synthetic distinction between value and feasible action. Limit: not a calibrated real-options price or an observed investment achievement.

Next options are a working-capital bridge, finer cash timing, empirical assumption review or an adaptive policy comparison. Activate an option only for a concrete mandate and evidence gap. Preserve broader technical knowledge without making every possible technology a requirement.

## Validation evidence and reflection


Private design-study evidence. All monetary values are synthetic EUR thousands; years 0–5. Not an investment recommendation.

## Decision

Retain the fixed-policy ledger as a screening tool. Separate project value from funding feasibility. Reject schedules after a buffer breach; do not rank their later counterfactual cash flows as achievable returns. An adaptive optimizer is not justified by this test.

## Baseline results

| Policy | Funding | Regime | Project NPV | Minimum cash | Buffer gap | Status |
|---|---|---|---:|---:|---:|---|
| invest | equity | normal | 13.72 | -20.00 | 30.00 | infeasible |
| invest | equity | restricted | 13.72 | -20.00 | 30.00 | infeasible |
| invest | mixed | normal | 13.72 | 20.00 | 0.00 | feasible |
| invest | mixed | restricted | 13.72 | 20.00 | 0.00 | feasible |
| stage | equity | normal | 2.68 | -22.00 | 32.00 | infeasible |
| stage | equity | restricted | 2.68 | -22.00 | 32.00 | infeasible |
| stage | mixed | normal | 2.68 | 14.80 | 0.00 | feasible |
| stage | mixed | restricted | 2.68 | 6.60 | 3.40 | infeasible |
| defer | equity | normal | 5.40 | -25.00 | 35.00 | infeasible |
| defer | equity | restricted | 5.40 | -25.00 | 35.00 | infeasible |
| defer | mixed | normal | 5.40 | 15.00 | 0.00 | feasible |
| defer | mixed | restricted | 5.40 | 15.00 | 0.00 | feasible |
| reject | equity | normal | 0.00 | 80.00 | 0.00 | feasible |
| reject | equity | restricted | 0.00 | 80.00 | 0.00 | feasible |
| reject | mixed | normal | 0.00 | 80.00 | 0.00 | feasible |
| reject | mixed | restricted | 0.00 | 80.00 | 0.00 | feasible |

## Prior forecast and observed model result

The archived agent forecast is preserved unchanged. H-IM-01, H-IM-02 and H-IM-03 all match the reference calculation: {'H-IM-01': True, 'H-IM-02': True, 'H-IM-03': True}.
Stage with restricted refinancing is infeasible at maturity 1 (minimum cash -25.20) and feasible at maturity 4 (minimum cash 14.80).
These are deterministic implications of selected assumptions, not estimated population effects. The user forecast remains separate and optional.

## Sensitivity and decision boundaries

Reviewed 69 sensitivity scenarios plus 16 baselines. One input changes at a time: discount rate, cash buffer, initial equity, coupon, maturity, capex scale or one-year operating delay. Full ledgers are in artifacts/management-review.json.
The delay scenario drops cash flows beyond year 5; it combines timing loss with a shorter observed operating horizon, not a perpetual loss estimate.
A higher buffer can remove financing feasibility without changing unlevered NPV. More equity can restore feasibility without proving that the extra capital earns an attractive return. Higher capex can impair both value and liquidity. Refinancing availability changes financing cash, not the operating cash-flow schedule.

## Operating handoff

Decision owner: proposed investment lead. Model preparer: proposed analyst. Independent check: finance/risk reviewer; no staffed team is claimed.
Intake requires dated operating assumptions, capex schedule, funding commitments, maturity, coupon, buffer and unit conventions. The reviewer reconciles cash and debt identities, checks timing and compares an explicit no-investment baseline.
Escalate any missing commitment, horizon mismatch, negative liquidity or unreviewed source change. No capital commitment follows automatically.

## Source application

Local Wharton C419-193 transcripts on time value and alternative scenarios support time-indexed discounting, what-if analysis, break-even reasoning and the need to check working capital and capacity. They do not validate the synthetic parameter choices or establish empirical financing effects.
Source-reading details and hashes belong to the archive reading register. Future real inputs must identify nominal/real basis, taxes, working capital, within-year timing and terminal treatment before a consequential valuation.

## Post-mortem

Review exposed silent maturity clipping and acceptance of non-finite inputs. Both were replaced with explicit errors and regression tests. This improves input control; it does not make the model production-ready.
Alternative explanation: the observed financing difference follows mechanically from the selected cash buffer and repayment dates. A different operating schedule or initial capitalization can reverse the feasible set.
Bounded conclusion: the model is suitable to explain the distinction between value and feasibility under stated assumptions. It is not a calibrated real-options price, optimal policy, evidence of market demand or personal investment performance.
