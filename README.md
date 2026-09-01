# GoLemon - Evidence-Based Risk Scorecard & Remediation Tracker

[![License: GPL-2.0](https://img.shields.io/badge/License-GPL--2.0-blue.svg)](LICENSE)
![Status](https://img.shields.io/badge/status-active-brightgreen)
![Type](https://img.shields.io/badge/type-GRC%20risk%20assessment-informational)

Six risks reconciled against verified evidence, existing control evidence, and control gaps, scored only where the underlying evidence supports a number, and flagged everywhere it doesn't.

> Two funding and scale pressures roll up into one liquidity exposure. The chain is reflected in the remediation sequencing below:
> **R-006 Strategic funding dependency -> R-001 Liquidity / operational continuity <- R-002 Operating model / scale**

---

## Files in this repository

This README is the narrative layer. The working data lives in one workbook, in this tab order, matching the chain below:

| Tab | Contents |
|---|---|
| `Risk Register` | The six risks, inherent L x I scores, evidence position and evidence tier |
| `Evidence Register` | All 22 evidence requests, status, ownership, evidence traceability, and tester conclusions |
| `Testing Procedures` | Test procedure, pass criteria and exception criteria for every ER-ID |
| `Legend & Instructions` | Status codes, methodology definitions, and the discipline this project is built on |

**[`GoLemon_Evidence_Collection_Testing_Register.xlsx`](./GoLemon_Evidence_Collection_Testing_Register.xlsx)**

If you're looking for the Risk Register specifically: it is the first tab of that workbook, not a separate file. Earlier drafts of this project kept it only in this README, which is one of the mistakes documented below.

---

## Evidence Tiers

| Tier | Risks | Meaning |
|---|---|---|
| **Tier 1 - Evidence-supported** | R-001, R-006 | Direct evidence basis is sufficient to retain the risk. Control evidence has not been independently verified, so residual risk is not yet assessable. |
| **Tier 2 - Material, verification-constrained** | R-002 | Thesis is supported by independent analyses, but the primary evidence source (GL-003) is unavailable. Retained, with the limitation disclosed. |
| **Tier 3 - Risk hypotheses** | R-003, R-004, R-005 | Plausible, potentially material exposures. No adverse event or control failure is established, so no score is manufactured. |

---

## Risk Scorecard

| ID | Risk | Primary Cause / Driver | Potential Consequence | Evidence Position | Control Evidence | L | I | Inherent | Finding Status |
|---|---|---|---|---|---|---|---|---|---|
| R-001 | Liquidity / Operational Continuity | Dependence on continued funding and available liquidity | Inability to sustain operations / shutdown | Supported by GL-001 & GL-004 | Not directly verified | 4 | 5 | **20 - Critical** | Evidence-supported risk; control deficiency not confirmed |
| R-002 | Operating Model / Scale | Exposure to insufficient scale/order density and economic pressure | Reduced economic sustainability and increased funding pressure | Material risk supported by independent analyses; GL-003 unavailable | Not verified | 4* | 5* | **20\* - Critical (provisional)** | Retain; evidence verification required |
| R-003 | Supply Chain / Fulfilment | Dependency on suppliers and fulfilment arrangements | Supply disruption, service degradation, operational interruption | Dependency evidenced; adverse event not established | Not verified | - | - | Not scored | Risk hypothesis |
| R-004 | Technology / Operational Resilience | Reliance on internally developed technology/systems | Operational disruption following system failure | Technology dependency evidenced; failure not established | Not verified | - | - | Not scored | Risk hypothesis |
| R-005 | Third-Party / Channel Dependency | Dependence on external channel/partner arrangements | Loss of distribution/revenue channel or reduced operational flexibility | Relationship/exclusivity evidenced; materiality/failure not established | Not verified | - | - | Not scored | Risk hypothesis |
| R-006 | Strategic Funding Dependency | Reliance on continued access to external capital | Funding shortfall, strategic contraction or business discontinuity | Supported by GL-001 & GL-004 | Not directly verified | 4 | 5 | **20 - Critical** | Evidence-supported risk; control deficiency not confirmed |

\* R-002's numerical score is provisional; the underlying GL-003 source cannot currently be directly verified.

---

## Control & Remediation Matrix

<details>
<summary><strong>R-001 - Liquidity / operational continuity</strong> (Critical)</summary>

| Field | Detail |
|---|---|
| **Control Objective** | Management maintains sufficient liquidity visibility and contingency capacity to sustain critical operations during funding disruption. |
| **Control Test** | Verify liquidity forecasting, cash runway monitoring, thresholds, escalation and contingency actions. |
| **Evidence Required** | Cash-flow forecasts, runway analysis, board/management reports, funding contingency plan, escalation records. |
| **Current Gap** | Control effectiveness not verifiable. |
| **Remediation** | Establish rolling cash-flow forecasting, minimum liquidity thresholds, funding trigger levels, and documented escalation/contingency procedures. |
| **Priority** | Critical |

</details>

<details>
<summary><strong>R-002 - Operating model / scale</strong> (High/Critical, provisional)</summary>

| Field | Detail |
|---|---|
| **Control Objective** | Management continuously monitors unit economics and operating scale against defined sustainability thresholds. |
| **Control Test** | Test whether order density, contribution margin, fixed costs and break-even assumptions are monitored and escalated. |
| **Evidence Required** | Unit-economic model, order-volume data, contribution margins, fixed-cost analysis, KPI dashboards, management reviews. |
| **Current Gap** | GL-003 unavailable; control evidence not verified. |
| **Remediation** | Recover/validate the underlying economic analysis and establish documented scale, margin and break-even KRIs with escalation thresholds. |
| **Priority** | High/Critical* - provisional pending direct verification of the underlying evidence |

</details>

<details>
<summary><strong>R-006 - Strategic funding dependency</strong> (Critical)</summary>

| Field | Detail |
|---|---|
| **Control Objective** | Management identifies funding dependency and maintains alternative financing/continuity strategies. |
| **Control Test** | Review funding concentration, financing pipeline, runway scenarios, contingency funding and escalation mechanisms. |
| **Evidence Required** | Funding strategy, investor pipeline, financing agreements, scenario analysis, board minutes, contingency plans. |
| **Current Gap** | Funding-contingency controls not directly verified. |
| **Remediation** | Establish funding concentration monitoring, financing scenarios, trigger points and contingency options aligned to strategic runway requirements. |
| **Priority** | Critical |

</details>

> **Note on terminology:** findings are recorded as *"control not evidenced / effectiveness not verifiable"* - never *"control absent."* An audit-ready assessment cannot infer a control didn't exist simply because public evidence of it wasn't found.

**GRC chain:** `Risk -> Cause -> Consequence -> Control Objective -> Test -> Evidence -> Gap -> Remediation -> Priority`

---

## Evidence Request List

<details>
<summary><strong>R-001 - Liquidity / operational continuity</strong></summary>

| ID | Evidence Request | What It Tests | Evidence Type | Priority |
|---|---|---|---|---|
| ER-001 | Monthly cash-flow forecasts, 6-12 months preceding shutdown | Whether liquidity was actively forecast | Financial record | Critical |
| ER-002 | Historical cash balances and monthly cash-burn figures | Actual liquidity trajectory and runway | Financial data | Critical |
| ER-003 | Board/management liquidity reports | Whether liquidity exposure reached management | Governance record | Critical |
| ER-004 | Documented minimum cash/liquidity thresholds | Whether objective escalation triggers existed | Policy/control | Critical |
| ER-005 | Liquidity escalation records and management actions | Whether identified liquidity pressure triggered action | Governance record | Critical |
| ER-006 | Funding contingency plan | Whether management had a defined response to funding failure | Business continuity / strategy | Critical |
| ER-007 | Going-concern or financial-sustainability assessments | Whether continuity risk was formally assessed | Financial/governance | High |

</details>

<details>
<summary><strong>R-006 - Strategic funding dependency</strong></summary>

| ID | Evidence Request | What It Tests | Evidence Type | Priority |
|---|---|---|---|---|
| ER-008 | Funding strategy and capital requirements | Degree of dependence on external funding | Strategy | Critical |
| ER-009 | Investor/funding pipeline records | Availability and diversification of financing sources | Transactional record | Critical |
| ER-010 | Financing agreements / term sheets / investment commitments | Confirmed funding sources and conditions | Legal/financial | Critical |
| ER-011 | Funding concentration analysis | Whether the organisation relied on a limited number of funding sources | Risk analysis | High |
| ER-012 | Scenario analysis for delayed/failed fundraising | Whether management modelled funding disruption | Risk analysis | Critical |
| ER-013 | Board minutes discussing fundraising and runway | Whether strategic funding risk was escalated | Governance record | Critical |
| ER-014 | Contingency financing options | Whether alternative funding mechanisms were identified | Strategy | High |

</details>

<details>
<summary><strong>R-002 - Operating model / scale</strong></summary>

| ID | Evidence Request | What It Tests | Evidence Type | Priority |
|---|---|---|---|---|
| ER-015 | Original GL-003 analysis | Validate the actual source behind the R-002 assessment | Source evidence | Critical |
| ER-016 | Unit economics model | Test contribution economics per order/customer | Financial model | Critical |
| ER-017 | Order-volume and order-density data | Test whether scale assumptions were achieved | Operational data | Critical |
| ER-018 | Contribution margin by product/order/channel | Determine economic contribution | Financial data | Critical |
| ER-019 | Fixed and variable operating-cost analysis | Determine cost structure and scale sensitivity | Financial data | Critical |
| ER-020 | Break-even analysis and management assumptions | Determine required scale for sustainability | Financial model | Critical |
| ER-021 | Operating KPI dashboards/reports | Determine whether economic performance was monitored | Management reporting | High |
| ER-022 | Management/board discussions regarding scale economics | Determine whether scale risk was recognized | Governance record | High |

</details>

> These are **requested** evidence items, not evidence currently possessed. Their inclusion does not imply GoLemon had the control in place.

### Evidence evaluation criteria

Each item, once obtained, is assessed against four dimensions:

1. **Existence** - Does the document/record actually exist?
2. **Completeness** - Does it cover the relevant period and population?
3. **Accuracy** - Can the underlying figures or assertions be reconciled?
4. **Operating effectiveness** - Does the evidence show the control actually *operated*, not just that a policy existed?

Design effectiveness and operating effectiveness are tested separately: design asks whether a control, as described, would adequately address the risk; operating effectiveness asks whether it actually ran, consistently, over the relevant period. A document describing a policy is design evidence. It is not, on its own, operating-effectiveness evidence.

### Evidence status coding

| Code | Meaning |
|---|---|
| `EV-0` | Not requested |
| `EV-1` | Requested |
| `EV-2` | Received |
| `EV-3` | Validated |
| `EV-4` | Insufficient / exception identified |
| `Missing` | Source unavailable, distinct from "not requested" - recovery was attempted or the source is known to be inaccessible |

Each evidence item also carries an **Evidence Owner**, an accountable individual, so a gap is a tracked action rather than a research note. Evidence is also tracked at two levels: the **ER-ID** (what was requested) and a separate **Evidence ID** (what was actually received against that request, e.g. `EV-016-01`), because more than one artefact can partially satisfy a single request and the two should never be conflated.

---

## Workflow

```
Risk Register -> Evidence Request List -> Evidence Collection -> Evidence Validation
-> Control Testing -> Finding -> Remediation -> Retest -> Residual Risk
```

## Risk hypotheses (Tier 3 - not scored)

<details>
<summary><strong>R-003 - Supply chain / fulfilment</strong></summary>

Dependency on suppliers and fulfilment arrangements - dependency evidenced, adverse event not established. Monitoring item pending evidence-gathering.

</details>

<details>
<summary><strong>R-004 - Technology / operational resilience</strong></summary>

Reliance on internally developed technology/systems - technology dependency evidenced, failure not established. Monitoring item pending evidence-gathering.

</details>

<details>
<summary><strong>R-005 - Third-party / channel dependency</strong></summary>

Dependence on external channel/partner arrangements - relationship/exclusivity evidenced, materiality/failure not established. Monitoring item pending evidence-gathering.

</details>

---

## What we discovered, why we made these choices, and what we learned

This project went through several rounds of self-correction. Documenting them is deliberate: an assessment methodology is more credible when it shows its own mistakes and how they were caught, not just the finished tables.

**1. We initially risked conflating "risk assessment" with "confirmed control finding."**
Early on, evidence that merely supported a risk's *existence* could have been read as evidence that a *control had failed*. Those are different claims. The fix was structural, not just wording: every risk now carries both an Evidence Position and a separate Finding Status, and the register enforces the rule that a control is recorded as "not evidenced / effectiveness not verifiable," never "absent," unless testing actually established that.

**2. We chose not to manufacture scores for unevidenced risks.**
R-003, R-004 and R-005 are plausible and potentially material. It would have been easy to assign them an L x I score anyway, using judgment instead of evidence, just to make the scorecard look complete. We chose the opposite: no adverse event or control failure is established for these, so they carry no score and are labelled as Tier 3 hypotheses instead. A missing number is more honest than an invented one.

**3. A worked example was left mixed into live data, and that was a real mistake, not a cosmetic one.**
An early version of the Evidence Register included a sample row (`EX-001`) demonstrating what a completed test should look like. It was clearly labelled, but it still sat in the same table as the real GoLemon evidence rows. On review, we recognized that an assessor skimming the register could mistake sample data for actual findings. We removed it from the live register entirely and moved the worked example into the Legend tab as text only, where it cannot be confused with real evidence.

**4. Some of our own pass/fail criteria were too absolute, and would have penalized legitimate business decisions.**
Our original test criteria for the funding-pipeline and financing-agreement evidence requests were written so that having a single primary funding source, or not yet having every prospective source under executed agreement, would read as an automatic exception. That is not a fair test: a company can deliberately rely on one primary funding source and still have that concentration understood and managed. We rewrote both tests to be risk-based - the exception is *unmanaged* concentration or *unverifiable* claims of commitment, not concentration or informality by itself.

**5. Our "Validated" status definition originally blurred two different questions together.**
The first version of the EV-3 status folded existence, completeness, accuracy and operating effectiveness into a single line. That made it too easy to conclude a control "worked" just because a supporting document existed. We separated design effectiveness (would this control, as designed, address the risk) from operating effectiveness (did it actually run, consistently, over the period) as two distinct, explicitly defined tests in the Legend, and stated directly that operating effectiveness should not be inferred from documentation alone.

**6. We had no way to distinguish what was requested from what was actually received.**
Once evidence starts arriving, a single ER-ID is not enough: more than one document can partially answer the same request, and a reviewer needs to trace exactly which artefact was tested. We added a separate Evidence ID field and an Evidence Location / Reference field, so a finding can point to something as specific as a named document and page range, not just "the finance team provided this."

**7. We built the first version assuming GitHub would render custom styling in a README, and it does not.**
The original scorecard was built as a single HTML file with an embedded stylesheet, pasted into `README.md`. GitHub strips `<style>` tags and most custom CSS from README rendering for security reasons, so the entire styled dashboard displayed as raw, unstyled text instead of the intended layout. The content was fine; the delivery mechanism was wrong for the platform. The lesson was to separate presentation from content: plain GitHub-flavored Markdown for anything meant to render on the repository page, and a real HTML file behind GitHub Pages for anything that actually needs custom styling.

**8. Splitting the same information across a README and a workbook created confusion about where the source of truth lived.**
For a period, the Risk Register existed only as a Markdown table in this README, while everything downstream of it (Evidence Register, Testing Procedures) lived in a separate spreadsheet. That is how we ended up needing to ask "where is the Risk Register" partway through the project. The fix was to consolidate the full chain, Risk Register through Testing Procedures, into one workbook in the order the methodology actually runs, and to make the README a narrative front door to that workbook rather than a second copy of the data.

**The broader pattern across all of this:** most of the mistakes were not factual errors, they were places where the structure of the document made an unsupported claim easier to make than a supported one. The fix, each time, was to change the structure (separate columns, separate tabs, separate fields) rather than just rewording a sentence, so the discipline is enforced by the format itself and does not depend on remembering to write it correctly every time.

---

## License

[GPL-2.0](LICENSE)
