# GoLemon - Evidence-Based Risk Scorecard & Remediation Tracker

[![License: GPL-2.0](https://img.shields.io/badge/License-GPL--2.0-blue.svg)](LICENSE)
![Status](https://img.shields.io/badge/status-active-brightgreen)
![Type](https://img.shields.io/badge/type-GRC%20risk%20assessment-informational)

Six risks reconciled against verified evidence, existing control evidence, and control gaps scored only where the underlying evidence supports a number, and flagged everywhere it doesn't.

> Two funding and scale pressures roll up into one liquidity exposure. The chain is reflected in the remediation sequencing below:
> **R-006 Strategic funding dependency → R-001 Liquidity / operational continuity ← R-002 Operating model / scale**

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
| R-003 | Supply Chain / Fulfilment | Dependency on suppliers and fulfilment arrangements | Supply disruption, service degradation, operational interruption | Dependency evidenced; adverse event not established | Not verified | — | — | Not scored | Risk hypothesis |
| R-004 | Technology / Operational Resilience | Reliance on internally developed technology/systems | Operational disruption following system failure | Technology dependency evidenced; failure not established | Not verified | — | — | Not scored | Risk hypothesis |
| R-005 | Third-Party / Channel Dependency | Dependence on external channel/partner arrangements | Loss of distribution/revenue channel or reduced operational flexibility | Relationship/exclusivity evidenced; materiality/failure not established | Not verified | — | — | Not scored | Risk hypothesis |
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

> **Note on terminology:** findings are recorded as *"control not evidenced / effectiveness not verifiable"* — never *"control absent."* An audit-ready assessment cannot infer a control didn't exist simply because public evidence of it wasn't found.

**GRC chain:** `Risk → Cause → Consequence → Control Objective → Test → Evidence → Gap → Remediation → Priority`

---

## Evidence Request List

<details>
<summary><strong>R-001 - Liquidity / operational continuity</strong></summary>

| ID | Evidence Request | What It Tests | Evidence Type | Priority |
|---|---|---|---|---|
| ER-001 | Monthly cash-flow forecasts, 6–12 months preceding shutdown | Whether liquidity was actively forecast | Financial record | Critical |
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

### Evidence status coding

| Code | Meaning |
|---|---|
| `EV-0` | Not requested |
| `EV-1` | Requested |
| `EV-2` | Received |
| `EV-3` | Validated |
| `EV-4` | Insufficient / exception identified |

Each evidence item also carries an **Evidence Owner** an accountable individual, so a gap is a tracked action rather than a research note.

---

## Workflow

```
Risk Register → Evidence Request List → Evidence Collection → Evidence Validation
→ Control Testing → Finding → Remediation → Retest → Residual Risk
```

## Risk hypotheses (Tier 3 - not scored)

<details>
<summary><strong>R-003 - Supply chain / fulfilment</strong></summary>

Dependency on suppliers and fulfilment arrangements - dependency evidenced, adverse event not established. Monitoring item pending evidence-gathering.

</details>

<details>
<summary><strong>R-004 - Technology / operational resilience</strong></summary>

Reliance on internally developed technology/systems technology dependency evidenced, failure not established. Monitoring item pending evidence-gathering.

</details>

<details>
<summary><strong>R-005 - Third-party / channel dependency</strong></summary>

Dependence on external channel/partner arrangements relationship/exclusivity evidenced, materiality/failure not established. Monitoring item pending evidence-gathering.

</details>

---

## License

[GPL-2.0](LICENSE)
