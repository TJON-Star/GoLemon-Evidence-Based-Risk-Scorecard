<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GoLemon — Evidence-Based Risk Scorecard &amp; Remediation Tracker</title>
<style>
  :root{
    --paper:#EFF1EC;
    --panel:#F8F9F5;
    --ink:#1B211D;
    --ink-soft:#4A534C;
    --rule:#D3D6C9;
    --rule-strong:#B4B8A7;
    --tier1:#1F5C4B;
    --tier1-bg:#E4EEE9;
    --tier2:#8F5E10;
    --tier2-bg:#F3E9D6;
    --tier3:#48546A;
    --tier3-bg:#E7E9EE;
    --critical:#8F2B20;
    --font-display: Iowan Old Style, Palatino Linotype, Georgia, "Times New Roman", serif;
    --font-mono: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
    --font-sans: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif;
  }
  *{box-sizing:border-box;}
  body{
    margin:0;
    background:var(--paper);
    color:var(--ink);
    font-family:var(--font-sans);
    line-height:1.55;
    padding:0 0 6rem;
  }
  .wrap{max-width:920px;margin:0 auto;padding:0 24px;}

  header.masthead{
    border-bottom:1px solid var(--rule-strong);
    padding:56px 0 32px;
  }
  .eyebrow{
    font-family:var(--font-mono);
    font-size:12.5px;
    color:var(--ink-soft);
    letter-spacing:0.02em;
  }
  h1{
    font-family:var(--font-display);
    font-weight:400;
    font-size:38px;
    margin:10px 0 14px;
    max-width:16ch;
  }
  .dek{
    font-size:16px;
    color:var(--ink-soft);
    max-width:60ch;
    margin:0;
  }

  section{padding:40px 0;border-bottom:1px solid var(--rule);}
  section:last-of-type{border-bottom:none;}
  h2{
    font-family:var(--font-display);
    font-weight:400;
    font-size:22px;
    margin:0 0 6px;
  }
  .section-note{
    font-size:14.5px;
    color:var(--ink-soft);
    max-width:62ch;
    margin:0 0 28px;
  }

  /* causal chain */
  .chain{
    display:flex;
    align-items:center;
    gap:0;
    flex-wrap:wrap;
    margin-top:24px;
  }
  .chain-node{
    font-family:var(--font-mono);
    font-size:13.5px;
    border:1px solid var(--rule-strong);
    background:var(--panel);
    padding:10px 16px;
    border-radius:3px;
  }
  .chain-node.retain{border-color:var(--tier1);color:var(--tier1);}
  .chain-arrow{
    padding:0 14px;
    color:var(--ink-soft);
    font-size:14px;
  }

  /* tier heading strip */
  .tier-head{
    display:flex;
    align-items:baseline;
    gap:12px;
    margin:44px 0 18px;
  }
  .tier-head:first-child{margin-top:0;}
  .tier-tag{
    font-family:var(--font-mono);
    font-size:11.5px;
    padding:3px 9px;
    border-radius:2px;
  }
  .tier1 .tier-tag{background:var(--tier1-bg);color:var(--tier1);}
  .tier2 .tier-tag{background:var(--tier2-bg);color:var(--tier2);}
  .tier3 .tier-tag{background:var(--tier3-bg);color:var(--tier3);}
  .tier-title{font-family:var(--font-display);font-size:18px;}
  .tier-desc{
    font-size:13.5px;
    color:var(--ink-soft);
    margin:0 0 20px;
    max-width:64ch;
  }

  /* risk block */
  .risk{
    background:var(--panel);
    border:1px solid var(--rule);
    border-left:3px solid var(--rule-strong);
    border-radius:2px;
    padding:22px 26px;
    margin-bottom:16px;
  }
  .risk.tier1{border-left-color:var(--tier1);}
  .risk.tier2{border-left-color:var(--tier2);}
  .risk.tier3{border-left-color:var(--tier3);}

  .risk-top{
    display:flex;
    justify-content:space-between;
    align-items:baseline;
    gap:16px;
    flex-wrap:wrap;
    margin-bottom:4px;
  }
  .risk-id{
    font-family:var(--font-mono);
    font-size:13px;
    color:var(--ink-soft);
  }
  .risk-name{
    font-family:var(--font-display);
    font-size:19px;
    margin:2px 0 2px;
  }
  .score-pill{
    font-family:var(--font-mono);
    font-size:12.5px;
    padding:4px 10px;
    border-radius:2px;
    white-space:nowrap;
  }
  .score-critical{background:#F4E4E1;color:var(--critical);}
  .score-provisional{background:var(--tier2-bg);color:var(--tier2);}
  .score-unscored{background:var(--tier3-bg);color:var(--tier3);}

  .finding-status{
    font-size:13.5px;
    color:var(--ink-soft);
    font-style:italic;
    margin:0 0 18px;
  }

  .grid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:0 32px;
    border-top:1px solid var(--rule);
    padding-top:14px;
  }
  .field{
    padding:9px 0;
    border-bottom:1px solid var(--rule);
  }
  .field .k{
    font-family:var(--font-mono);
    font-size:11px;
    color:var(--ink-soft);
    text-transform:uppercase;
    letter-spacing:0.03em;
    display:block;
    margin-bottom:3px;
  }
  .field .v{font-size:14px;}
  .flag{color:var(--tier2);}
  .na{color:var(--ink-soft);font-style:italic;}

  .metrics{
    display:flex;
    gap:24px;
    margin:16px 0 4px;
    font-family:var(--font-mono);
    font-size:13px;
  }
  .metric .k{color:var(--ink-soft);font-size:11px;text-transform:uppercase;letter-spacing:0.03em;display:block;margin-bottom:2px;}

  footer{
    max-width:920px;margin:0 auto;padding:32px 24px 0;
    font-size:12.5px;color:var(--ink-soft);
    border-top:1px solid var(--rule);
    margin-top:16px;
  }

  @media (max-width:640px){
    .grid{grid-template-columns:1fr;}
    h1{font-size:30px;}
  }
</style>
</head>
<body>

<div class="wrap">
<header class="masthead">
  <div class="eyebrow">GoLemon — GRC risk assessment</div>
  <h1>Evidence-based risk scorecard &amp; remediation tracker</h1>
  <p class="dek">Six risks reconciled against verified evidence, existing control evidence, and control gaps — scored only where the underlying evidence supports a number, and flagged everywhere it doesn't.</p>
</header>

<section>
  <h2>Reconciled causal chain</h2>
  <p class="section-note">Two funding and scale pressures roll up into a single liquidity exposure. The chain is reflected in remediation sequencing below.</p>
  <div class="chain">
    <span class="chain-node retain">R-006 — Strategic funding dependency</span>
    <span class="chain-arrow">&#8594;</span>
    <span class="chain-node retain">R-001 — Liquidity / operational continuity</span>
    <span class="chain-arrow">&#8592;</span>
    <span class="chain-node retain">R-002 — Operating model / scale</span>
  </div>
</section>

<section>

  <div class="tier-head tier1">
    <span class="tier-tag">Tier 1</span>
    <span class="tier-title">Evidence-supported</span>
  </div>
  <p class="tier-desc">Direct evidence basis sufficient to retain the risk. Control evidence has not been independently verified, so residual risk is not yet assessable.</p>

  <div class="risk tier1">
    <div class="risk-top">
      <div>
        <span class="risk-id">R-001</span>
        <h3 class="risk-name">Liquidity / operational continuity</h3>
      </div>
      <span class="score-pill score-critical">20 — Critical</span>
    </div>
    <p class="finding-status">Evidence-supported risk; control deficiency not confirmed</p>
    <div class="metrics">
      <div class="metric"><span class="k">Likelihood</span>4 — Likely</div>
      <div class="metric"><span class="k">Impact</span>5 — Severe</div>
      <div class="metric"><span class="k">Residual risk</span><span class="na">Not assessable</span></div>
    </div>
    <div class="grid">
      <div class="field"><span class="k">Cause / driver</span><span class="v">Dependence on continued funding and available liquidity</span></div>
      <div class="field"><span class="k">Consequence</span><span class="v">Inability to sustain operations / shutdown</span></div>
      <div class="field"><span class="k">Evidence position</span><span class="v">Supported by GL-001 &amp; GL-004</span></div>
      <div class="field"><span class="k">Evidence verification</span><span class="v">Not directly verified</span></div>
      <div class="field"><span class="k">Control objective</span><span class="v">Ensure liquidity runway and continuity planning are actively managed and monitored</span></div>
      <div class="field"><span class="k">Control test</span><span class="v">Review liquidity/cash-runway reporting, funding agreements, and continuity plans</span></div>
      <div class="field"><span class="k">Control evidence</span><span class="v">Not directly verified</span></div>
      <div class="field"><span class="k">Control gap</span><span class="v">Not confirmed — verification pending</span></div>
      <div class="field"><span class="k">Remediation</span><span class="v">Obtain and independently verify liquidity/funding documentation and continuity controls</span></div>
      <div class="field"><span class="k">Owner / priority / target</span><span class="v">Finance &amp; Treasury — Critical — current assessment cycle</span></div>
    </div>
  </div>

  <div class="risk tier1">
    <div class="risk-top">
      <div>
        <span class="risk-id">R-006</span>
        <h3 class="risk-name">Strategic funding dependency</h3>
      </div>
      <span class="score-pill score-critical">20 — Critical</span>
    </div>
    <p class="finding-status">Evidence-supported risk; control deficiency not confirmed</p>
    <div class="metrics">
      <div class="metric"><span class="k">Likelihood</span>4 — Likely</div>
      <div class="metric"><span class="k">Impact</span>5 — Severe</div>
      <div class="metric"><span class="k">Residual risk</span><span class="na">Not assessable</span></div>
    </div>
    <div class="grid">
      <div class="field"><span class="k">Cause / driver</span><span class="v">Reliance on continued access to external capital</span></div>
      <div class="field"><span class="k">Consequence</span><span class="v">Funding shortfall, strategic contraction, or business discontinuity</span></div>
      <div class="field"><span class="k">Evidence position</span><span class="v">Supported by GL-001 &amp; GL-004</span></div>
      <div class="field"><span class="k">Evidence verification</span><span class="v">Not directly verified</span></div>
      <div class="field"><span class="k">Control objective</span><span class="v">Ensure funding-access planning and capital-raise contingencies are actively managed</span></div>
      <div class="field"><span class="k">Control test</span><span class="v">Review funding pipeline documentation, investor commitments, and contingency plans</span></div>
      <div class="field"><span class="k">Control evidence</span><span class="v">Not directly verified</span></div>
      <div class="field"><span class="k">Control gap</span><span class="v">Not confirmed — verification pending</span></div>
      <div class="field"><span class="k">Remediation</span><span class="v">Obtain and independently verify funding pipeline and contingency documentation</span></div>
      <div class="field"><span class="k">Owner / priority / target</span><span class="v">Finance &amp; Executive — Critical — current assessment cycle</span></div>
    </div>
  </div>

  <div class="tier-head tier2">
    <span class="tier-tag">Tier 2</span>
    <span class="tier-title">Material — verification-constrained</span>
  </div>
  <p class="tier-desc">Thesis supported by independent analyses, but the primary evidence item is unavailable. Retained, with the limitation disclosed rather than absorbed.</p>

  <div class="risk tier2">
    <div class="risk-top">
      <div>
        <span class="risk-id">R-002</span>
        <h3 class="risk-name">Operating model / scale</h3>
      </div>
      <span class="score-pill score-provisional">20 — Critical (provisional)</span>
    </div>
    <p class="finding-status">Retain; evidence verification required</p>
    <div class="metrics">
      <div class="metric"><span class="k">Likelihood</span>4* — Likely</div>
      <div class="metric"><span class="k">Impact</span>5* — Severe</div>
      <div class="metric"><span class="k">Residual risk</span><span class="na">Not assessable</span></div>
    </div>
    <div class="grid">
      <div class="field"><span class="k">Cause / driver</span><span class="v">Exposure to insufficient scale/order density and associated economic pressure</span></div>
      <div class="field"><span class="k">Consequence</span><span class="v">Reduced economic sustainability and increased funding pressure</span></div>
      <div class="field"><span class="k">Evidence position</span><span class="v">Independent analyses reportedly supporting the thesis; primary source GL-003 unavailable</span></div>
      <div class="field"><span class="k">Evidence verification</span><span class="v flag">Not verified — GL-003 unavailable for direct verification</span></div>
      <div class="field"><span class="k">Control objective</span><span class="v">Confirm scale/unit-economics assumptions and monitor operating-model sustainability</span></div>
      <div class="field"><span class="k">Control test</span><span class="v flag">Cannot be executed until GL-003, or an equivalent primary source, is recovered</span></div>
      <div class="field"><span class="k">Control evidence</span><span class="v">Not verified</span></div>
      <div class="field"><span class="k">Control gap</span><span class="v">Not confirmed — evidence recovery required before a gap can be assessed</span></div>
      <div class="field"><span class="k">Remediation</span><span class="v">Recover GL-003 (or equivalent) and independently validate the operating/economic assumptions before control testing</span></div>
      <div class="field"><span class="k">Owner / priority / target</span><span class="v">GRC Lead &amp; Operations — High, pending evidence recovery — next assessment cycle</span></div>
    </div>
  </div>

  <div class="tier-head tier3">
    <span class="tier-tag">Tier 3</span>
    <span class="tier-title">Risk hypotheses</span>
  </div>
  <p class="tier-desc">Plausible, potentially material exposures. No adverse event or control failure is established, so no score is manufactured — these are monitoring items pending evidence.</p>

  <div class="risk tier3">
    <div class="risk-top">
      <div>
        <span class="risk-id">R-003</span>
        <h3 class="risk-name">Supply chain / fulfilment</h3>
      </div>
      <span class="score-pill score-unscored">Not scored</span>
    </div>
    <p class="finding-status">Risk hypothesis — monitoring item</p>
    <div class="grid">
      <div class="field"><span class="k">Cause / driver</span><span class="v">Dependency on suppliers and fulfilment arrangements</span></div>
      <div class="field"><span class="k">Consequence</span><span class="v">Supply disruption, service degradation, operational interruption</span></div>
      <div class="field"><span class="k">Evidence position</span><span class="v">Dependency evidenced; adverse event not established</span></div>
      <div class="field"><span class="k">Control objective</span><span class="v">Establish an evidence base to confirm or rule out material supply-chain exposure</span></div>
      <div class="field"><span class="k">Control test</span><span class="v na">Not applicable — pending evidence collection</span></div>
      <div class="field"><span class="k">Control gap</span><span class="v na">Not assessable — hypothesis stage</span></div>
      <div class="field"><span class="k">Remediation</span><span class="v">Collect supplier-concentration data, contracts, and incident history to confirm or deny the hypothesis</span></div>
      <div class="field"><span class="k">Owner / priority / target</span><span class="v">Operations — Monitor — next evidence-gathering cycle</span></div>
    </div>
  </div>

  <div class="risk tier3">
    <div class="risk-top">
      <div>
        <span class="risk-id">R-004</span>
        <h3 class="risk-name">Technology / operational resilience</h3>
      </div>
      <span class="score-pill score-unscored">Not scored</span>
    </div>
    <p class="finding-status">Risk hypothesis — monitoring item</p>
    <div class="grid">
      <div class="field"><span class="k">Cause / driver</span><span class="v">Reliance on internally developed technology/systems</span></div>
      <div class="field"><span class="k">Consequence</span><span class="v">Operational disruption following system failure</span></div>
      <div class="field"><span class="k">Evidence position</span><span class="v">Technology dependency evidenced; failure not established</span></div>
      <div class="field"><span class="k">Control objective</span><span class="v">Establish an evidence base to confirm or rule out resilience exposure</span></div>
      <div class="field"><span class="k">Control test</span><span class="v na">Not applicable — pending evidence collection</span></div>
      <div class="field"><span class="k">Control gap</span><span class="v na">Not assessable — hypothesis stage</span></div>
      <div class="field"><span class="k">Remediation</span><span class="v">Collect architecture review, incident/outage history, and DR/BCP documentation to confirm or deny the hypothesis</span></div>
      <div class="field"><span class="k">Owner / priority / target</span><span class="v">Technology — Monitor — next evidence-gathering cycle</span></div>
    </div>
  </div>

  <div class="risk tier3">
    <div class="risk-top">
      <div>
        <span class="risk-id">R-005</span>
        <h3 class="risk-name">Third-party / channel dependency</h3>
      </div>
      <span class="score-pill score-unscored">Not scored</span>
    </div>
    <p class="finding-status">Risk hypothesis — monitoring item</p>
    <div class="grid">
      <div class="field"><span class="k">Cause / driver</span><span class="v">Dependence on external channel/partner arrangements</span></div>
      <div class="field"><span class="k">Consequence</span><span class="v">Loss of distribution/revenue channel, or reduced operational flexibility</span></div>
      <div class="field"><span class="k">Evidence position</span><span class="v">Relationship/exclusivity evidenced; materiality/failure not established</span></div>
      <div class="field"><span class="k">Control objective</span><span class="v">Establish an evidence base to confirm or rule out channel-concentration exposure</span></div>
      <div class="field"><span class="k">Control test</span><span class="v na">Not applicable — pending evidence collection</span></div>
      <div class="field"><span class="k">Control gap</span><span class="v na">Not assessable — hypothesis stage</span></div>
      <div class="field"><span class="k">Remediation</span><span class="v">Collect partner agreements, revenue-concentration data, and contract terms to confirm or deny the hypothesis</span></div>
      <div class="field"><span class="k">Owner / priority / target</span><span class="v">Commercial &amp; Partnerships — Monitor — next evidence-gathering cycle</span></div>
    </div>
  </div>

</section>
</div>

<footer>
  GoLemon evidence-based risk scorecard v1 — inherent scores marked provisional remain pending evidence verification; no residual score is assigned without independently verified control evidence.
</footer>

</body>
</html>
