<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>GoLemon - Evidence-Based Risk Scorecard &amp; Remediation Tracker</title>
<meta name="description" content="Evidence-based GRC risk assessment and control-testing workpaper for GoLemon: risk register, evidence register, testing procedures, and audit-ready methodology.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Source+Serif+4:opsz,wght@8..60,400;8..60,600;8..60,700&family=Inter:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#0E1116;
    --panel:#161A22;
    --panel-2:#12151C;
    --rule:#262B36;
    --ink:#EDEAE2;
    --ink-dim:#9CA0AC;
    --ink-faint:#5A6070;
    --verified:#3F9C82;
    --critical:#C25B4A;
    --provisional:#C9A227;
    --serif: "Source Serif 4", Georgia, serif;
    --sans: "Inter", -apple-system, sans-serif;
    --mono: "IBM Plex Mono", ui-monospace, monospace;
    --maxw: 880px;
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:var(--bg);
    color:var(--ink);
    font-family:var(--sans);
    font-size:15.5px;
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
  }
  ::selection{background:var(--verified); color:#0E1116;}
  a{color:var(--verified); text-decoration:none; border-bottom:1px solid rgba(63,156,130,0.35);}
  a:hover{border-bottom-color:var(--verified);}
  :focus-visible{outline:2px solid var(--verified); outline-offset:2px;}

  /* ---------- Sticky nav ---------- */
  .topbar{
    position:sticky; top:0; z-index:50;
    background:rgba(14,17,22,0.92);
    backdrop-filter: blur(8px);
    border-bottom:1px solid var(--rule);
  }
  .topbar-inner{
    max-width:var(--maxw); margin:0 auto; padding:14px 24px;
    display:flex; align-items:center; justify-content:space-between; gap:16px;
    flex-wrap:wrap;
  }
  .brand{font-family:var(--serif); font-size:15px; font-weight:600; color:var(--ink); white-space:nowrap;}
  .navlinks{display:flex; gap:18px; flex-wrap:wrap;}
  .navlinks a{
    font-family:var(--sans); font-size:13px; color:var(--ink-dim);
    border-bottom:none; white-space:nowrap;
  }
  .navlinks a:hover{color:var(--verified);}

  /* ---------- Shell ---------- */
  main{max-width:var(--maxw); margin:0 auto; padding:0 24px 100px;}
  section{padding-top:56px;}
  .rule{border:0; border-top:1px solid var(--rule); margin:56px 0 0;}

  h1{font-family:var(--serif); font-weight:700; font-size:clamp(28px,4vw,38px); line-height:1.18; margin:0 0 14px;}
  h2{font-family:var(--serif); font-weight:600; font-size:23px; margin:0 0 6px; color:var(--ink);}
  h3{font-family:var(--serif); font-weight:600; font-size:17px; margin:24px 0 8px;}
  .section-lede{color:var(--ink-dim); font-size:14.5px; max-width:62ch; margin:0 0 26px;}
  p{margin:0 0 14px;}

  code{font-family:var(--mono); font-size:0.88em; background:var(--panel-2); padding:1px 6px; border-radius:3px; color:var(--provisional);}

  /* ---------- Hero ---------- */
  .hero{padding-top:64px;}
  .badges{display:flex; gap:8px; flex-wrap:wrap; margin:20px 0 30px;}
  .badge{
    font-family:var(--mono); font-size:11px; letter-spacing:0.02em;
    padding:4px 10px; border-radius:3px; border:1px solid var(--rule); color:var(--ink-dim);
  }
  .badge.status{color:var(--verified); border-color:rgba(63,156,130,0.4);}

  .chain{
    background:var(--panel); border:1px solid var(--rule); border-radius:6px;
    padding:28px 24px; margin-top:8px;
  }
  .chain-caption{font-size:13.5px; color:var(--ink-dim); margin-bottom:18px;}
  .chain-row{display:flex; align-items:center; gap:10px; flex-wrap:wrap; justify-content:center;}
  .chain-node{
    font-family:var(--serif); font-size:14.5px; text-align:center;
    padding:14px 16px; border-radius:5px; min-width:150px;
    border:1px solid; line-height:1.35;
  }
  .chain-node .id{display:block; font-family:var(--mono); font-size:11px; margin-bottom:4px; letter-spacing:0.02em;}
  .chain-node.critical{border-color:rgba(194,91,74,0.55); background:rgba(194,91,74,0.09); color:var(--ink);}
  .chain-node.critical .id{color:var(--critical);}
  .chain-node.provisional{border-color:rgba(201,162,39,0.55); background:rgba(201,162,39,0.09); color:var(--ink);}
  .chain-node.provisional .id{color:var(--provisional);}
  .chain-arrow{font-family:var(--mono); color:var(--ink-faint); font-size:18px;}

  /* ---------- Files table ---------- */
  table{width:100%; border-collapse:collapse; font-size:14px;}
  .table-wrap{overflow-x:auto; border:1px solid var(--rule); border-radius:6px;}
  th{
    text-align:left; font-family:var(--sans); font-weight:600; font-size:12.5px;
    color:var(--ink-dim); padding:10px 14px; background:var(--panel-2);
    border-bottom:1px solid var(--rule); white-space:nowrap;
  }
  td{padding:12px 14px; border-bottom:1px solid var(--rule); vertical-align:top; color:var(--ink);}
  tr:last-child td{border-bottom:none;}
  td.mono, th.mono{font-family:var(--mono); font-size:12.5px;}

  .tier-dot{display:inline-block; width:7px; height:7px; border-radius:50%; margin-right:7px;}
  .tier-dot.t1{background:var(--verified);}
  .tier-dot.t2{background:var(--provisional);}
  .tier-dot.t3{background:var(--ink-faint);}

  /* ---------- Tier cards ---------- */
  .tiers{display:grid; grid-template-columns:repeat(3,1fr); gap:14px; margin-top:8px;}
  .tier-card{background:var(--panel); border:1px solid var(--rule); border-radius:6px; padding:18px;}
  .tier-card h4{font-family:var(--serif); font-size:15px; margin:0 0 6px; display:flex; align-items:center;}
  .tier-card .risks{font-family:var(--mono); font-size:11.5px; color:var(--ink-dim); margin-bottom:10px;}
  .tier-card p{font-size:13px; color:var(--ink-dim); margin:0;}
  @media (max-width:700px){.tiers{grid-template-columns:1fr;}}

  /* ---------- Score badge ---------- */
  .score{font-weight:600; white-space:nowrap;}
  .score.critical{color:var(--critical);}
  .score.provisional{color:var(--provisional);}
  .score.none{color:var(--ink-faint);}

  /* ---------- Accordion ---------- */
  details{
    background:var(--panel); border:1px solid var(--rule); border-radius:6px;
    margin-bottom:10px; overflow:hidden;
  }
  summary{
    cursor:pointer; padding:14px 16px; font-family:var(--serif); font-size:15px;
    display:flex; align-items:center; justify-content:space-between; list-style:none;
  }
  summary::-webkit-details-marker{display:none;}
  summary::after{content:"+"; font-family:var(--mono); color:var(--ink-faint); font-size:16px; margin-left:12px;}
  details[open] summary::after{content:"\2212";}
  summary .priority{font-family:var(--mono); font-size:11px; color:var(--critical); font-weight:400; margin-left:10px;}
  .details-body{padding:0 16px 18px;}
  .kv{display:grid; grid-template-columns:150px 1fr; gap:4px 16px; font-size:13.5px;}
  .kv dt{color:var(--ink-dim); font-family:var(--sans); font-weight:500; padding:8px 0; border-top:1px solid var(--rule);}
  .kv dd{margin:0; padding:8px 0; border-top:1px solid var(--rule); color:var(--ink);}
  .kv dt:first-of-type, .kv dd:first-of-type{border-top:none;}

  .note{
    border-left:3px solid var(--provisional); background:rgba(201,162,39,0.07);
    padding:12px 16px; font-size:13.5px; color:var(--ink-dim); border-radius:0 4px 4px 0; margin:18px 0;
  }
  .grc-chain{font-family:var(--mono); font-size:12.5px; color:var(--ink-dim); margin-top:14px;}

  /* ---------- Definition dims ---------- */
  .dims{list-style:none; margin:0 0 16px; padding:0;}
  .dims li{padding:10px 0; border-top:1px solid var(--rule); font-size:14px;}
  .dims li:first-child{border-top:none;}
  .dims b{font-family:var(--serif); font-weight:600;}

  /* ---------- Workflow ---------- */
  .workflow{
    font-family:var(--mono); font-size:12.5px; color:var(--ink-dim);
    background:var(--panel-2); border:1px solid var(--rule); border-radius:6px;
    padding:16px; line-height:1.9; white-space:pre-wrap;
  }
  .workflow b{color:var(--verified); font-weight:500;}

  /* ---------- Hypothesis cards ---------- */
  .hypo{display:grid; gap:10px; margin-top:8px;}
  .hypo-card{background:var(--panel); border:1px solid var(--rule); border-left:3px solid var(--ink-faint); border-radius:0 6px 6px 0; padding:14px 16px;}
  .hypo-card h4{font-family:var(--serif); font-size:14.5px; margin:0 0 4px;}
  .hypo-card p{font-size:13px; color:var(--ink-dim); margin:0;}

  /* ---------- Lessons (numbered = real sequence) ---------- */
  .lessons{counter-reset:lesson;}
  .lesson{
    counter-increment:lesson; position:relative; padding:18px 0 18px 44px;
    border-top:1px solid var(--rule);
  }
  .lessons > .lesson:first-child{border-top:none;}
  .lesson::before{
    content:counter(lesson); position:absolute; left:0; top:18px;
    font-family:var(--mono); font-size:13px; color:var(--verified);
    width:28px; height:28px; border:1px solid rgba(63,156,130,0.4); border-radius:50%;
    display:flex; align-items:center; justify-content:center;
  }
  .lesson h4{font-family:var(--serif); font-size:15.5px; margin:0 0 6px; font-weight:600;}
  .lesson p{font-size:13.8px; color:var(--ink-dim); margin:0;}
  .lesson-close{
    margin-top:22px; padding:16px; background:var(--panel); border:1px solid var(--rule);
    border-radius:6px; font-size:13.8px; color:var(--ink-dim);
  }
  .lesson-close b{color:var(--ink); font-family:var(--serif); font-weight:600;}

  footer{
    max-width:var(--maxw); margin:0 auto; padding:32px 24px 60px;
    border-top:1px solid var(--rule); margin-top:56px;
    font-size:13px; color:var(--ink-faint); display:flex; justify-content:space-between; flex-wrap:wrap; gap:10px;
  }

  @media (max-width:640px){
    .kv{grid-template-columns:1fr;}
    .kv dt{border-top:1px solid var(--rule); padding-bottom:2px;}
    .kv dd{border-top:none; padding-top:0; padding-bottom:10px;}
    th, td{font-size:13px;}
  }
</style>
</head>
<body>

<div class="topbar">
  <div class="topbar-inner">
    <span class="brand">GoLemon Risk Scorecard</span>
    <nav class="navlinks">
      <a href="#register">Risk Register</a>
      <a href="#evidence">Evidence</a>
      <a href="#testing">Testing</a>
      <a href="#lessons">Lessons</a>
      <a href="https://github.com/TJON-Star/GoLemon-Evidence-Based-Risk-Scorecard">Repo</a>
    </nav>
  </div>
</div>

<main>

  <section class="hero">
    <h1>GoLemon - Evidence-Based Risk Scorecard &amp; Remediation Tracker</h1>
    <p class="section-lede">
      Six risks reconciled against verified evidence, existing control evidence, and control gaps.
      Scored only where the underlying evidence supports a number, and flagged everywhere it doesn't.
    </p>
    <div class="badges">
      <span class="badge status">status: active</span>
      <span class="badge">license: GPL-2.0</span>
      <span class="badge">type: GRC risk assessment</span>
    </div>

    <div class="chain">
      <div class="chain-caption">Two funding and scale pressures roll up into one liquidity exposure. Remediation sequencing follows this chain:</div>
      <div class="chain-row">
        <div class="chain-node critical"><span class="id">R-006</span>Strategic funding<br>dependency</div>
        <span class="chain-arrow">&#8594;</span>
        <div class="chain-node critical"><span class="id">R-001</span>Liquidity /<br>operational continuity</div>
        <span class="chain-arrow">&#8592;</span>
        <div class="chain-node provisional"><span class="id">R-002</span>Operating model /<br>scale (provisional)</div>
      </div>
    </div>
  </section>

  <hr class="rule">
  <section id="files">
    <h2>Files in this repository</h2>
    <p class="section-lede">This page is the narrative layer. The working data lives in one workbook, in this tab order, matching the chain below.</p>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Tab</th><th>Contents</th></tr></thead>
        <tbody>
          <tr><td class="mono">Risk Register</td><td>The six risks, inherent L&nbsp;&times;&nbsp;I scores, evidence position and evidence tier</td></tr>
          <tr><td class="mono">Evidence Register</td><td>All 22 evidence requests, status, ownership, evidence traceability, and tester conclusions</td></tr>
          <tr><td class="mono">Testing Procedures</td><td>Test procedure, pass criteria and exception criteria for every ER-ID</td></tr>
          <tr><td class="mono">Legend &amp; Instructions</td><td>Status codes, methodology definitions, and the discipline this project is built on</td></tr>
        </tbody>
      </table>
    </div>
    <p style="margin-top:14px; font-size:13.5px;">
      <a href="./GoLemon_Evidence_Collection_Testing_Register.xlsx">GoLemon_Evidence_Collection_Testing_Register.xlsx</a>
      &nbsp;-&nbsp;if you're looking for the Risk Register specifically, it's the first tab of that workbook, not a separate file.
    </p>
  </section>

  <hr class="rule">
  <section id="tiers">
    <h2>Evidence Tiers</h2>
    <p class="section-lede">Every risk is placed in exactly one tier, based on what the evidence actually supports.</p>
    <div class="tiers">
      <div class="tier-card">
        <h4><span class="tier-dot t1"></span>Tier 1</h4>
        <div class="risks">R-001 &middot; R-006</div>
        <p>Evidence-supported. Direct evidence basis is sufficient to retain the risk. Control evidence has not been independently verified, so residual risk is not yet assessable.</p>
      </div>
      <div class="tier-card">
        <h4><span class="tier-dot t2"></span>Tier 2</h4>
        <div class="risks">R-002</div>
        <p>Material, verification-constrained. Supported by independent analyses, but the primary source (GL-003) is unavailable. Retained, with the limitation disclosed.</p>
      </div>
      <div class="tier-card">
        <h4><span class="tier-dot t3"></span>Tier 3</h4>
        <div class="risks">R-003 &middot; R-004 &middot; R-005</div>
        <p>Risk hypotheses. Plausible, potentially material. No adverse event or control failure established, so no score is manufactured.</p>
      </div>
    </div>
  </section>

  <hr class="rule">
  <section id="register">
    <h2>Risk Scorecard</h2>
    <p class="section-lede">Inherent score = Likelihood &times; Impact, computed only where the evidence position supports it.</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr><th>ID</th><th>Risk</th><th>Evidence Position</th><th>L</th><th>I</th><th>Inherent</th></tr>
        </thead>
        <tbody>
          <tr>
            <td class="mono">R-001</td>
            <td>Liquidity / Operational Continuity</td>
            <td>Supported by GL-001 &amp; GL-004</td>
            <td>4</td><td>5</td>
            <td class="score critical">20 &middot; Critical</td>
          </tr>
          <tr>
            <td class="mono">R-002</td>
            <td>Operating Model / Scale</td>
            <td>Independent analyses; GL-003 unavailable</td>
            <td>4*</td><td>5*</td>
            <td class="score provisional">20* &middot; Critical (provisional)</td>
          </tr>
          <tr>
            <td class="mono">R-003</td>
            <td>Supply Chain / Fulfilment</td>
            <td>Dependency evidenced; adverse event not established</td>
            <td>-</td><td>-</td>
            <td class="score none">Not scored</td>
          </tr>
          <tr>
            <td class="mono">R-004</td>
            <td>Technology / Operational Resilience</td>
            <td>Dependency evidenced; failure not established</td>
            <td>-</td><td>-</td>
            <td class="score none">Not scored</td>
          </tr>
          <tr>
            <td class="mono">R-005</td>
            <td>Third-Party / Channel Dependency</td>
            <td>Evidenced; materiality/failure not established</td>
            <td>-</td><td>-</td>
            <td class="score none">Not scored</td>
          </tr>
          <tr>
            <td class="mono">R-006</td>
            <td>Strategic Funding Dependency</td>
            <td>Supported by GL-001 &amp; GL-004</td>
            <td>4</td><td>5</td>
            <td class="score critical">20 &middot; Critical</td>
          </tr>
        </tbody>
      </table>
    </div>
    <p style="margin-top:12px; font-size:13px; color:var(--ink-faint);">* R-002's numerical score is provisional; the underlying GL-003 source cannot currently be directly verified.</p>
  </section>

  <hr class="rule">
  <section id="matrix">
    <h2>Control &amp; Remediation Matrix</h2>
    <p class="section-lede">What control should address each risk, and what we'd need to see to confirm it operates.</p>

    <details>
      <summary>R-001 &middot; Liquidity / operational continuity <span class="priority">Critical</span></summary>
      <div class="details-body">
        <dl class="kv">
          <dt>Control Objective</dt><dd>Management maintains sufficient liquidity visibility and contingency capacity to sustain critical operations during funding disruption.</dd>
          <dt>Control Test</dt><dd>Verify liquidity forecasting, cash runway monitoring, thresholds, escalation and contingency actions.</dd>
          <dt>Evidence Required</dt><dd>Cash-flow forecasts, runway analysis, board/management reports, funding contingency plan, escalation records.</dd>
          <dt>Current Gap</dt><dd>Control effectiveness not verifiable.</dd>
          <dt>Remediation</dt><dd>Establish rolling cash-flow forecasting, minimum liquidity thresholds, funding trigger levels, and documented escalation/contingency procedures.</dd>
        </dl>
      </div>
    </details>

    <details>
      <summary>R-002 &middot; Operating model / scale <span class="priority" style="color:var(--provisional);">High/Critical, provisional</span></summary>
      <div class="details-body">
        <dl class="kv">
          <dt>Control Objective</dt><dd>Management continuously monitors unit economics and operating scale against defined sustainability thresholds.</dd>
          <dt>Control Test</dt><dd>Test whether order density, contribution margin, fixed costs and break-even assumptions are monitored and escalated.</dd>
          <dt>Evidence Required</dt><dd>Unit-economic model, order-volume data, contribution margins, fixed-cost analysis, KPI dashboards, management reviews.</dd>
          <dt>Current Gap</dt><dd>GL-003 unavailable; control evidence not verified.</dd>
          <dt>Remediation</dt><dd>Recover/validate the underlying economic analysis and establish documented scale, margin and break-even KRIs with escalation thresholds.</dd>
        </dl>
      </div>
    </details>

    <details>
      <summary>R-006 &middot; Strategic funding dependency <span class="priority">Critical</span></summary>
      <div class="details-body">
        <dl class="kv">
          <dt>Control Objective</dt><dd>Management identifies funding dependency and maintains alternative financing/continuity strategies.</dd>
          <dt>Control Test</dt><dd>Review funding concentration, financing pipeline, runway scenarios, contingency funding and escalation mechanisms.</dd>
          <dt>Evidence Required</dt><dd>Funding strategy, investor pipeline, financing agreements, scenario analysis, board minutes, contingency plans.</dd>
          <dt>Current Gap</dt><dd>Funding-contingency controls not directly verified.</dd>
          <dt>Remediation</dt><dd>Establish funding concentration monitoring, financing scenarios, trigger points and contingency options aligned to strategic runway requirements.</dd>
        </dl>
      </div>
    </details>

    <div class="note">
      <b>Note on terminology:</b> findings are recorded as "control not evidenced / effectiveness not verifiable" - never "control absent." An audit-ready assessment cannot infer a control didn't exist simply because public evidence of it wasn't found.
    </div>
    <div class="grc-chain">GRC chain: Risk &#8594; Cause &#8594; Consequence &#8594; Control Objective &#8594; Test &#8594; Evidence &#8594; Gap &#8594; Remediation &#8594; Priority</div>
  </section>

  <hr class="rule">
  <section id="evidence">
    <h2>Evidence Request List</h2>
    <p class="section-lede">These are requested evidence items, not evidence currently possessed. Their inclusion does not imply GoLemon had the control in place.</p>

    <details>
      <summary>R-001 &middot; Liquidity / operational continuity <span class="priority" style="color:var(--ink-faint);">7 items</span></summary>
      <div class="details-body">
        <div class="table-wrap">
        <table>
          <thead><tr><th>ID</th><th>Evidence Request</th><th>What It Tests</th><th>Priority</th></tr></thead>
          <tbody>
            <tr><td class="mono">ER-001</td><td>Monthly cash-flow forecasts, 6-12 months preceding shutdown</td><td>Whether liquidity was actively forecast</td><td>Critical</td></tr>
            <tr><td class="mono">ER-002</td><td>Historical cash balances and monthly cash-burn figures</td><td>Actual liquidity trajectory and runway</td><td>Critical</td></tr>
            <tr><td class="mono">ER-003</td><td>Board/management liquidity reports</td><td>Whether liquidity exposure reached management</td><td>Critical</td></tr>
            <tr><td class="mono">ER-004</td><td>Documented minimum cash/liquidity thresholds</td><td>Whether objective escalation triggers existed</td><td>Critical</td></tr>
            <tr><td class="mono">ER-005</td><td>Liquidity escalation records and management actions</td><td>Whether identified pressure triggered action</td><td>Critical</td></tr>
            <tr><td class="mono">ER-006</td><td>Funding contingency plan</td><td>Whether management had a defined response to funding failure</td><td>Critical</td></tr>
            <tr><td class="mono">ER-007</td><td>Going-concern / financial-sustainability assessments</td><td>Whether continuity risk was formally assessed</td><td>High</td></tr>
          </tbody>
        </table>
        </div>
      </div>
    </details>

    <details>
      <summary>R-006 &middot; Strategic funding dependency <span class="priority" style="color:var(--ink-faint);">7 items</span></summary>
      <div class="details-body">
        <div class="table-wrap">
        <table>
          <thead><tr><th>ID</th><th>Evidence Request</th><th>What It Tests</th><th>Priority</th></tr></thead>
          <tbody>
            <tr><td class="mono">ER-008</td><td>Funding strategy and capital requirements</td><td>Degree of dependence on external funding</td><td>Critical</td></tr>
            <tr><td class="mono">ER-009</td><td>Investor/funding pipeline records</td><td>Availability and diversification of financing sources</td><td>Critical</td></tr>
            <tr><td class="mono">ER-010</td><td>Financing agreements / term sheets / commitments</td><td>Confirmed funding sources and conditions</td><td>Critical</td></tr>
            <tr><td class="mono">ER-011</td><td>Funding concentration analysis</td><td>Whether reliant on a limited number of sources</td><td>High</td></tr>
            <tr><td class="mono">ER-012</td><td>Scenario analysis for delayed/failed fundraising</td><td>Whether management modelled funding disruption</td><td>Critical</td></tr>
            <tr><td class="mono">ER-013</td><td>Board minutes discussing fundraising and runway</td><td>Whether strategic funding risk was escalated</td><td>Critical</td></tr>
            <tr><td class="mono">ER-014</td><td>Contingency financing options</td><td>Whether alternative funding mechanisms were identified</td><td>High</td></tr>
          </tbody>
        </table>
        </div>
      </div>
    </details>

    <details>
      <summary>R-002 &middot; Operating model / scale <span class="priority" style="color:var(--ink-faint);">8 items</span></summary>
      <div class="details-body">
        <div class="table-wrap">
        <table>
          <thead><tr><th>ID</th><th>Evidence Request</th><th>What It Tests</th><th>Priority</th></tr></thead>
          <tbody>
            <tr><td class="mono">ER-015</td><td>Original GL-003 analysis</td><td>Validate the actual source behind the R-002 assessment</td><td>Critical</td></tr>
            <tr><td class="mono">ER-016</td><td>Unit economics model</td><td>Contribution economics per order/customer</td><td>Critical</td></tr>
            <tr><td class="mono">ER-017</td><td>Order-volume and order-density data</td><td>Whether scale assumptions were achieved</td><td>Critical</td></tr>
            <tr><td class="mono">ER-018</td><td>Contribution margin by product/order/channel</td><td>Economic contribution</td><td>Critical</td></tr>
            <tr><td class="mono">ER-019</td><td>Fixed and variable operating-cost analysis</td><td>Cost structure and scale sensitivity</td><td>Critical</td></tr>
            <tr><td class="mono">ER-020</td><td>Break-even analysis and management assumptions</td><td>Required scale for sustainability</td><td>Critical</td></tr>
            <tr><td class="mono">ER-021</td><td>Operating KPI dashboards/reports</td><td>Whether economic performance was monitored</td><td>High</td></tr>
            <tr><td class="mono">ER-022</td><td>Management/board discussions on scale economics</td><td>Whether scale risk was recognized</td><td>High</td></tr>
          </tbody>
        </table>
        </div>
      </div>
    </details>
  </section>

  <hr class="rule">
  <section id="testing">
    <h2>Evidence evaluation criteria</h2>
    <p class="section-lede">Each item, once obtained, is assessed against four dimensions.</p>
    <ul class="dims">
      <li><b>Existence</b> - Does the document/record actually exist?</li>
      <li><b>Completeness</b> - Does it cover the relevant period and population?</li>
      <li><b>Accuracy</b> - Can the underlying figures or assertions be reconciled?</li>
      <li><b>Operating effectiveness</b> - Does the evidence show the control actually operated, not just that a policy existed?</li>
    </ul>
    <p style="font-size:13.8px; color:var(--ink-dim);">Design effectiveness and operating effectiveness are tested separately: design asks whether a control, as described, would adequately address the risk; operating effectiveness asks whether it actually ran, consistently, over the relevant period. A document describing a policy is design evidence - it is not, on its own, operating-effectiveness evidence.</p>

    <h3>Evidence status coding</h3>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Code</th><th>Meaning</th></tr></thead>
        <tbody>
          <tr><td class="mono">EV-0</td><td>Not requested</td></tr>
          <tr><td class="mono">EV-1</td><td>Requested</td></tr>
          <tr><td class="mono">EV-2</td><td>Received</td></tr>
          <tr><td class="mono">EV-3</td><td>Validated</td></tr>
          <tr><td class="mono">EV-4</td><td>Insufficient / exception identified</td></tr>
          <tr><td class="mono">Missing</td><td>Source unavailable - distinct from "not requested"; recovery was attempted or the source is known to be inaccessible</td></tr>
        </tbody>
      </table>
    </div>
    <p style="margin-top:14px; font-size:13.5px; color:var(--ink-dim);">Every evidence item also carries an Evidence Owner, and is tracked at two levels: the <code>ER-ID</code> (what was requested) and a separate <code>Evidence ID</code> (what was actually received, e.g. <code>EV-016-01</code>) - because more than one artefact can partially satisfy a single request, and the two should never be conflated.</p>

    <h3 id="workflow-h">Workflow</h3>
    <div class="workflow"><b>Risk Register</b> &#8594; Evidence Request List &#8594; Evidence Collection &#8594; Evidence Validation
&#8594; Control Testing &#8594; Finding &#8594; Remediation &#8594; Retest &#8594; Residual Risk</div>

    <h3>Risk hypotheses (Tier 3 &middot; not scored)</h3>
    <div class="hypo">
      <div class="hypo-card">
        <h4>R-003 &middot; Supply chain / fulfilment</h4>
        <p>Dependency on suppliers and fulfilment arrangements - dependency evidenced, adverse event not established. Monitoring item pending evidence-gathering.</p>
      </div>
      <div class="hypo-card">
        <h4>R-004 &middot; Technology / operational resilience</h4>
        <p>Reliance on internally developed technology/systems - dependency evidenced, failure not established. Monitoring item pending evidence-gathering.</p>
      </div>
      <div class="hypo-card">
        <h4>R-005 &middot; Third-party / channel dependency</h4>
        <p>Dependence on external channel/partner arrangements - relationship/exclusivity evidenced, materiality/failure not established. Monitoring item pending evidence-gathering.</p>
      </div>
    </div>
  </section>

  <hr class="rule">
  <section id="lessons">
    <h2>What we discovered, why we made these choices, and what we learned</h2>
    <p class="section-lede">This project went through several rounds of self-correction. Documenting them is deliberate: a methodology is more credible when it shows its own mistakes and how they were caught, not just the finished tables.</p>

    <div class="lessons">
      <div class="lesson">
        <h4>We initially risked conflating "risk assessment" with "confirmed control finding."</h4>
        <p>Evidence that merely supported a risk's existence could have been read as evidence that a control had failed. The fix was structural: every risk carries both an Evidence Position and a separate Finding Status, and a control is recorded as "not evidenced," never "absent," unless testing actually established that.</p>
      </div>
      <div class="lesson">
        <h4>We chose not to manufacture scores for unevidenced risks.</h4>
        <p>R-003, R-004 and R-005 are plausible and potentially material. It would have been easy to score them with judgment instead of evidence. We chose the opposite: no score, labelled as Tier 3 hypotheses. A missing number is more honest than an invented one.</p>
      </div>
      <div class="lesson">
        <h4>A worked example was left mixed into live data - a real mistake, not a cosmetic one.</h4>
        <p>An early Evidence Register included a clearly-labelled sample row. On review, we recognized an assessor skimming the register could still mistake it for real evidence. It was removed entirely and moved into the Legend as text only.</p>
      </div>
      <div class="lesson">
        <h4>Some of our own pass/fail criteria were too absolute.</h4>
        <p>Original test criteria for funding-pipeline and financing-agreement evidence would have flagged a single primary funding source as an automatic exception. That's not a fair test - concentration can be deliberate and managed. We rewrote both tests around whether the risk is understood and managed, not whether it exists.</p>
      </div>
      <div class="lesson">
        <h4>Our "Validated" status definition originally blurred two different questions together.</h4>
        <p>The first EV-3 definition folded existence, completeness, accuracy and operating effectiveness into one line, making it too easy to conclude a control "worked" just because a document existed. We separated design effectiveness from operating effectiveness as two distinct, explicitly defined tests.</p>
      </div>
      <div class="lesson">
        <h4>We had no way to distinguish what was requested from what was actually received.</h4>
        <p>A single ER-ID isn't enough once real evidence arrives - more than one document can partially answer the same request. We added a separate Evidence ID and an Evidence Location / Reference field, so a finding can point to a named document and page range.</p>
      </div>
      <div class="lesson">
        <h4>We built the first version assuming GitHub would render custom styling in a README, and it does not.</h4>
        <p>The original scorecard was a single HTML file with an embedded stylesheet, pasted into README.md. GitHub strips &lt;style&gt; tags from README rendering, so the styled dashboard displayed as raw text. This page exists because of that lesson: presentation now lives here, on GitHub Pages, where it can actually render.</p>
      </div>
      <div class="lesson">
        <h4>Splitting the same information across a README and a workbook created confusion about the source of truth.</h4>
        <p>For a period, the Risk Register existed only in the README while everything downstream lived in a spreadsheet - which is how we ended up needing to ask where the Risk Register even was. The fix was to consolidate the full chain into one workbook and make written pages a narrative front door to it, not a second copy of the data.</p>
      </div>
    </div>

    <div class="lesson-close">
      <b>The broader pattern:</b> most of the mistakes were not factual errors - they were places where the structure of the document made an unsupported claim easier to make than a supported one. The fix, each time, was to change the structure rather than reword a sentence, so the discipline is enforced by the format itself.
    </div>
  </section>

</main>

<footer>
  <span>GPL-2.0 License</span>
  <span><a href="https://github.com/TJON-Star/GoLemon-Evidence-Based-Risk-Scorecard">View source on GitHub</a></span>
</footer>

<script>
  // Only one accordion group open at a time within each <section>, for a calmer reading flow.
  document.querySelectorAll('section').forEach(function(section){
    var groups = section.querySelectorAll('details');
    groups.forEach(function(d){
      d.addEventListener('toggle', function(){
        if(d.open){
          groups.forEach(function(other){ if(other !== d) other.open = false; });
        }
      });
    });
  });
</script>

</body>
</html>
