[index (1).html](https://github.com/user-attachments/files/25611638/index.1.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Finite State · Competitive Overview</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg:       #08090C;
      --surface:  #0F1117;
      --surface2: #141720;
      --border:   #1A1F2E;
      --border2:  #242B3D;
      --text:     #E6EDF6;
      --muted:    #55607A;
      --dim:      #2A3340;
      --cyan:     #00C8FF;
      --orange:   #FF6B2B;
      --green:    #00D68F;
      --yellow:   #FFB800;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { font-size: 14.5px; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Inter', system-ui, sans-serif;
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 48px 24px;
    }

    /* subtle grid */
    body::after {
      content: '';
      position: fixed; inset: 0;
      background-image:
        linear-gradient(rgba(0,200,255,0.014) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,200,255,0.014) 1px, transparent 1px);
      background-size: 44px 44px;
      pointer-events: none;
      z-index: 0;
    }

    /* ambient top glow */
    body::before {
      content: '';
      position: fixed;
      top: -200px; left: 50%; transform: translateX(-50%);
      width: 800px; height: 500px;
      background: radial-gradient(ellipse, rgba(0,200,255,0.04), transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    .card {
      position: relative; z-index: 1;
      width: 100%; max-width: 860px;
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 4px;
      overflow: hidden;
    }

    /* top color bar */
    .card::before {
      content: '';
      display: block; height: 2px;
      background: linear-gradient(90deg, var(--orange), var(--cyan) 50%, transparent);
    }

    /* ── HEADER ── */
    .card-hdr {
      padding: 28px 32px 24px;
      border-bottom: 1px solid var(--border);
    }

    .eyebrow {
      font-family: 'IBM Plex Mono', monospace;
      font-size: 10px; letter-spacing: .14em; text-transform: uppercase;
      color: var(--cyan); margin-bottom: 10px;
      display: flex; align-items: center; gap: 8px;
    }
    .eyebrow::before {
      content: ''; width: 5px; height: 5px; border-radius: 50%;
      background: var(--cyan); box-shadow: 0 0 7px var(--cyan);
    }

    .card-hdr h1 {
      font-size: 22px; font-weight: 700;
      letter-spacing: -.02em; color: var(--text);
      margin-bottom: 10px;
    }
    .card-hdr h1 span { color: var(--cyan); }

    .blurb {
      font-size: 13.5px; color: var(--muted);
      line-height: 1.72; max-width: 680px;
    }
    .blurb b  { color: var(--text); font-weight: 500; }
    .blurb .o { color: var(--orange); font-weight: 500; }

    /* ── TABLE ── */
    .tbl-wrap { overflow-x: auto; }

    table {
      width: 100%; border-collapse: collapse;
      font-size: 13px;
    }

    thead tr {
      background: var(--surface2);
      border-bottom: 1px solid var(--border2);
    }

    th {
      padding: 11px 16px; text-align: left;
      font-family: 'IBM Plex Mono', monospace;
      font-size: 9.5px; letter-spacing: .12em; text-transform: uppercase;
      color: var(--muted); font-weight: 400; white-space: nowrap;
    }
    th.col-fs {
      color: var(--cyan);
      background: rgba(0,200,255,0.06);
      border-left: 1px solid rgba(0,200,255,.18);
      border-right: 1px solid rgba(0,200,255,.18);
    }

    td {
      padding: 10px 16px;
      border-bottom: 1px solid var(--border);
      color: var(--muted); vertical-align: middle;
    }
    td.row-label {
      color: var(--text); font-weight: 500;
      white-space: nowrap; font-size: 13px;
    }
    td.col-fs {
      background: rgba(0,200,255,.03);
      border-left: 1px solid rgba(0,200,255,.1);
      border-right: 1px solid rgba(0,200,255,.1);
      color: var(--text); font-weight: 500;
    }
    tr:last-child td { border-bottom: none; }
    tr:hover td       { background: rgba(255,255,255,.012); }
    tr:hover td.col-fs { background: rgba(0,200,255,.06); }

    /* ── ORANGE HIGHLIGHT: review gap rows ── */
    tr.gap td {
      background: rgba(255,107,43,.06) !important;
      border-top: 1px solid rgba(255,107,43,.16) !important;
      border-bottom: 1px solid rgba(255,107,43,.16) !important;
    }
    tr.gap td.col-fs {
      background: rgba(255,107,43,.12) !important;
      border-left: 1px solid rgba(255,107,43,.32) !important;
      border-right: 1px solid rgba(255,107,43,.32) !important;
    }
    tr.gap td.row-label { color: var(--orange); }
    tr.gap:hover td { background: rgba(255,107,43,.09) !important; }

    /* section divider row */
    tr.section-divider td {
      background: rgba(255,107,43,.08);
      border-top: 1px solid rgba(255,107,43,.25);
      border-bottom: 1px solid rgba(255,107,43,.25);
      padding: 7px 16px;
    }
    .section-divider-label {
      font-family: 'IBM Plex Mono', monospace;
      font-size: 9.5px; letter-spacing: .16em; text-transform: uppercase;
      color: var(--orange); font-weight: 500;
    }

    /* pills */
    .pill {
      display: inline-flex; align-items: center; gap: 4px;
      font-family: 'IBM Plex Mono', monospace;
      font-size: 10px; padding: 2px 7px;
      border-radius: 2px; border: 1px solid; white-space: nowrap;
    }
    .p-g  { color: var(--green);  border-color: rgba(0,214,143,.3);  background: rgba(0,214,143,.07); }
    .p-c  { color: var(--cyan);   border-color: rgba(0,200,255,.3);  background: rgba(0,200,255,.06); }
    .p-o  { color: var(--orange); border-color: rgba(255,107,43,.35); background: rgba(255,107,43,.08); font-weight: 600; }
    .p-y  { color: var(--yellow); border-color: rgba(255,184,0,.3);  background: rgba(255,184,0,.07); }
    .p-gr { color: var(--muted);  border-color: var(--border2);      background: transparent; }

    .stars     { color: var(--cyan);  letter-spacing: 1.5px; font-size: 12px; }
    .stars-off { color: var(--dim);   letter-spacing: 1.5px; font-size: 12px; }

    /* ── FOOTER ── */
    .card-ftr {
      padding: 14px 32px;
      border-top: 1px solid var(--border);
      display: flex; justify-content: space-between; align-items: center;
      flex-wrap: wrap; gap: 8px;
    }
    .ftr-sig {
      font-size: 12px; color: var(--muted);
      font-family: 'IBM Plex Mono', monospace; letter-spacing: .03em;
    }
    .ftr-sig b { color: var(--text); font-weight: 500; }
    .ftr-date {
      font-family: 'IBM Plex Mono', monospace;
      font-size: 10px; color: var(--dim); letter-spacing: .06em;
    }

    /* gap legend note */
    .gap-note {
      display: flex; align-items: center; gap: 7px;
      font-size: 11px; color: var(--muted);
      padding: 10px 32px;
      border-top: 1px solid var(--border);
      background: rgba(255,107,43,.03);
    }
    .gap-note::before {
      content: '';
      display: inline-block; width: 10px; height: 10px;
      border-radius: 1px; background: var(--orange); opacity: .6;
      flex-shrink: 0;
    }
    .gap-note b { color: var(--orange); font-weight: 500; }

  </style>
</head>
<body>

<div class="card">

  <!-- HEADER + BLURB -->
  <div class="card-hdr">
    <div class="eyebrow">30 · 60 · 90 · Supplemental</div>
    <h1>Finite State · <span>Competitive Overview</span></h1>
    <p class="blurb">
      The competitive gap is not product — Finite State's platform, particularly with AgentOS and the reachability engine reducing vulnerability noise by up to 90%, is genuinely differentiated. The gap is <b>market visibility</b>. Buyers who would choose Finite State aren't finding them in the places they go to validate. That's a solvable marketing problem, not a product problem. The 30-60-90 addresses it directly: <span class="o">Concierge</span> routes the right buyer to the right conversation, <span class="o">PeerSpot</span> <span class="o">gives them third-party validation</span>, and the <span class="o">AEO</span> work ensures Finite State shows up when buyers ask <span class="o">AI tools</span> the questions that lead to this category.
    </p>
  </div>

  <!-- TABLE -->
  <div class="tbl-wrap">
    <table>
      <thead>
        <tr>
          <th>Capability</th>
          <th class="col-fs">Finite State</th>
          <th>Cybellum</th>
          <th>ONEKEY</th>
          <th>Black Duck</th>
          <th>Medcrypt</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="row-label">Binary analysis depth</td>
          <td class="col-fs"><span class="stars">★★★★★</span></td>
          <td><span class="stars">★★★★</span><span class="stars-off">★</span></td>
          <td><span class="stars">★★★★</span><span class="stars-off">★</span></td>
          <td><span class="stars">★★</span><span class="stars-off">★★★</span></td>
          <td><span class="stars">★★★</span><span class="stars-off">★★</span></td>
        </tr>
        <tr>
          <td class="row-label">Reachability / vuln triage</td>
          <td class="col-fs"><span class="pill p-c">Up to 90% noise cut</span></td>
          <td><span class="pill p-y">Moderate</span></td>
          <td><span class="pill p-y">Moderate</span></td>
          <td><span class="pill p-gr">Minimal</span></td>
          <td><span class="pill p-y">Partial</span></td>
        </tr>
        <tr>
          <td class="row-label">FDA 524B</td>
          <td class="col-fs"><span class="pill p-g">✓ Native + Advisory</span></td>
          <td><span class="pill p-y">Partial</span></td>
          <td><span class="pill p-gr">Limited</span></td>
          <td><span class="pill p-gr">None</span></td>
          <td><span class="pill p-g">✓ Core focus</span></td>
        </tr>
        <tr>
          <td class="row-label">EU CRA / NIS 2</td>
          <td class="col-fs"><span class="pill p-g">✓ Supported</span></td>
          <td><span class="pill p-g">✓ Strong</span></td>
          <td><span class="pill p-g">✓ EU-native</span></td>
          <td><span class="pill p-gr">None</span></td>
          <td><span class="pill p-gr">Minimal</span></td>
        </tr>
        <tr>
          <td class="row-label">Automotive ISO 21434</td>
          <td class="col-fs"><span class="pill p-g">✓ AUTOSAR support</span></td>
          <td><span class="pill p-g">✓ Core vertical</span></td>
          <td><span class="pill p-y">Partial</span></td>
          <td><span class="pill p-gr">None</span></td>
          <td><span class="pill p-gr">None</span></td>
        </tr>
        <tr>
          <td class="row-label">Source code SCA</td>
          <td class="col-fs"><span class="pill p-g">✓ Via MergeBase</span></td>
          <td><span class="pill p-g">✓ Supported</span></td>
          <td><span class="pill p-g">✓ Supported</span></td>
          <td><span class="pill p-g">✓ Core strength</span></td>
          <td><span class="pill p-y">Limited</span></td>
        </tr>
        <tr>
          <td class="row-label">Gov-grade advisory services</td>
          <td class="col-fs"><span class="pill p-g">✓ Differentiated</span></td>
          <td><span class="pill p-y">Prof. services</span></td>
          <td><span class="pill p-gr">Limited</span></td>
          <td><span class="pill p-gr">Limited</span></td>
          <td><span class="pill p-g">✓ FDA specialists</span></td>
        </tr>
        <!-- SECTION DIVIDER ROW -->
        <tr class="section-divider">
          <td colspan="6">
            <span class="section-divider-label">Third-Party Validation</span>
          </td>
        </tr>
        <!-- GAP ROWS — orange highlight -->
        <tr class="gap">
          <td class="row-label">PeerSpot presence</td>
          <td class="col-fs"><span class="pill p-o">⚠ Zero presence</span></td>
          <td><span class="pill p-gr">Limited</span></td>
          <td><span class="pill p-gr">Limited</span></td>
          <td><span class="pill p-g">Active</span></td>
          <td><span class="pill p-gr">None</span></td>
        </tr>
        <tr class="gap">
          <td class="row-label">G2 presence / reviews</td>
          <td class="col-fs"><span class="pill p-o">⚠ 2 reviews · stale</span></td>
          <td><span class="pill p-y">Moderate</span></td>
          <td><span class="pill p-y">Active</span></td>
          <td><span class="pill p-g">Strong</span></td>
          <td><span class="pill p-gr">Minimal</span></td>
        </tr>
        <tr class="gap">
          <td class="row-label">Review volume</td>
          <td class="col-fs"><span class="pill p-o">🚨 Critical gap</span></td>
          <td><span class="pill p-y">Moderate</span></td>
          <td><span class="pill p-y">Growing</span></td>
          <td><span class="pill p-g">Strong</span></td>
          <td><span class="pill p-gr">Minimal</span></td>
        </tr>
      </tbody>
    </table>
  </div>

  <!-- GAP NOTE -->
  <div class="gap-note">
    <b>Highlighted rows</b> — the GTM priority.
  </div>

  <!-- FOOTER -->
  <div class="card-ftr">
    <div class="ftr-sig"><b>Amber Bogie</b> · Sr. Marketing Executive · GTM Transformation</div>
    <div class="ftr-date">February 2026</div>
  </div>

</div>

</body>
</html>
