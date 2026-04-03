<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Northeast US Firewood — BTU Reference</title>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  /* ── Forest green / amber naturalist palette ── */
  :root {
    --bg:        #f0ecd4;   /* warm parchment */
    --bg2:       #e2edbc;   /* light meadow green */
    --bg3:       #d5e5ac;   /* mid meadow */
    --bg-page:   #e8e4c8;   /* outer page wash */
    --text:      #182e06;   /* deep forest */
    --text2:     #3a5814;   /* medium forest */
    --text3:     #6a8838;   /* sage */
    --border:    rgba(36,64,8,0.14);
    --border2:   rgba(36,64,8,0.28);
    --accent:         #3a6a10;
    --accent-bg:      #cce898;
    --accent-text:    #162a06;
    /* Tier badges */
    --b-p-bg:    #1a4006;   --b-p-tx:  #b0e060;
    --b-h-bg:    #356010;   --b-h-tx:  #ccf090;
    --b-m-bg:    #eaf4b0;   --b-m-tx:  #263a06;
    --b-lo-bg:   #f4dc80;   --b-lo-tx: #462e06;
    --b-ll-bg:   #e2d4a0;   --b-ll-tx: #3e300a;
    /* New badge */
    --new-bg:    #e8b820;   --new-tx:  #1e1004;
    /* Scrollbar */
    --scroll:    rgba(36,64,8,0.25);
  }

  @media (prefers-color-scheme: dark) {
    :root {
      --bg:        #0c1606;
      --bg2:       #141f0a;
      --bg3:       #1c2c10;
      --bg-page:   #080e04;
      --text:      #c4e48a;
      --text2:     #86aa4e;
      --text3:     #507030;
      --border:    rgba(96,154,40,0.15);
      --border2:   rgba(96,154,40,0.30);
      --accent:         #78c038;
      --accent-bg:      #182e08;
      --accent-text:    #9ede60;
      --b-p-bg:    #b4e060;   --b-p-tx:  #0a1e02;
      --b-h-bg:    #78c038;   --b-h-tx:  #081602;
      --b-m-bg:    #1e3408;   --b-m-tx:  #b0d870;
      --b-lo-bg:   #3a2806;   --b-lo-tx: #e8c060;
      --b-ll-bg:   #221c06;   --b-ll-tx: #b8a050;
      --new-bg:    #906010;   --new-tx:  #f8e8b0;
      --scroll:    rgba(96,154,40,0.28);
    }
  }

  html { background: var(--bg-page); }

  body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    font-size: 14px;
    line-height: 1.6;
    color: var(--text);
    background: var(--bg);
    max-width: 1100px;
    margin: 0 auto;
    padding: 32px 20px 60px;
    border-left: 1px solid var(--border2);
    border-right: 1px solid var(--border2);
    min-height: 100vh;
  }

  /* ── Header ── */
  header {
    background: #152a0a;
    border-radius: 10px;
    padding: 28px 30px 24px;
    margin-bottom: 24px;
  }
  header h1 {
    font-family: Playfair Display, Georgia, "Times New Roman", serif;
    font-size: 32px;
    font-weight: 700;
    color: #e8f0d0;
    margin-bottom: 7px;
    letter-spacing: -0.3px;
    line-height: 1.25;
  }
  header > p {
    font-size: 13px;
    color: #8aaa60;
    margin-bottom: 20px;
  }
  .hdr-meta {
    display: flex;
    gap: 32px;
    flex-wrap: wrap;
    border-top: 1px solid rgba(255,255,255,0.10);
    padding-top: 14px;
  }
  .hdr-item { min-width: 160px; }
  .hdr-label {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 0.8px;
    text-transform: uppercase;
    color: #6a8840;
    margin-bottom: 3px;
  }
  .hdr-value {
    font-size: 12.5px;
    color: #c8e090;
    font-weight: 500;
    line-height: 1.4;
  }
  @media (prefers-color-scheme: dark) {
    header { background: #0c1e06; border: 1px solid rgba(96,154,40,0.20); }
  }

  /* ── Controls ── */
  .controls { display: flex; gap: 10px; align-items: center; flex-wrap: wrap; margin-bottom: 12px; }
  .controls label { font-size: 12px; color: var(--text2); font-weight: 600; letter-spacing: 0.3px; }
  select {
    font-size: 12px; padding: 4px 8px;
    border: 1px solid var(--border2);
    border-radius: 6px;
    background: var(--bg2); color: var(--text);
    cursor: pointer;
  }
  .filter-group { display: flex; gap: 6px; flex-wrap: wrap; }
  .fb {
    font-size: 11.5px; padding: 4px 12px;
    border: 1px solid var(--border2);
    border-radius: 20px; cursor: pointer;
    background: var(--bg2); color: var(--text2);
    transition: background 0.12s, color 0.12s;
    font-weight: 500;
  }
  .fb:hover { background: var(--bg3); color: var(--text); }
  .fb.active {
    background: var(--accent-bg);
    color: var(--accent-text);
    border-color: var(--accent);
    font-weight: 600;
  }
  .count { font-size: 12px; color: var(--text3); margin-left: auto; font-style: italic; }

  /* ── Legend ── */
  .legend { display: flex; gap: 14px; flex-wrap: wrap; margin-bottom: 14px; }
  .li { display: flex; align-items: center; gap: 5px; font-size: 12px; color: var(--text2); }
  .ld { width: 10px; height: 10px; border-radius: 50%; flex-shrink: 0; }

  /* ── Table wrapper ── */
  .tbl-wrap {
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
    border: 1px solid var(--border2);
    border-radius: 10px;
    max-height: 580px;
    overflow-y: auto;
    scrollbar-width: thin;
    scrollbar-color: var(--scroll) transparent;
  }
  .tbl-wrap::-webkit-scrollbar { height: 8px; width: 6px; }
  .tbl-wrap::-webkit-scrollbar-track { background: var(--bg2); border-radius: 4px; }
  .tbl-wrap::-webkit-scrollbar-thumb { background: var(--scroll); border-radius: 4px; }
  .scroll-hint {
    font-size: 11.5px; color: var(--text3);
    text-align: right; margin-bottom: 5px;
    display: none; font-style: italic;
  }
  @media (max-width: 700px) { .scroll-hint { display: block; } }

  table { width: 100%; border-collapse: collapse; min-width: 560px; }

  thead th {
    padding: 9px 10px;
    text-align: left;
    font-size: 11.5px;
    font-weight: 700;
    color: var(--text2);
    background: var(--bg3);
    border-bottom: 2px solid var(--border2);
    cursor: pointer;
    user-select: none;
    white-space: nowrap;
    position: sticky; top: 0; z-index: 5;
    letter-spacing: 0.2px;
  }
  thead th.num { text-align: right; }
  thead th:hover { color: var(--text); background: var(--bg2); }
  thead th.sorted { color: var(--text); }
  thead th .arrow { margin-left: 3px; font-size: 9px; opacity: 0.4; }
  thead th.sorted .arrow { opacity: 1; }

  tbody tr { border-bottom: 0.5px solid var(--border); }
  tbody tr:last-child { border-bottom: none; }
  tbody tr:nth-child(even) { background: rgba(180,210,100,0.08); }
  tbody tr:hover { background: var(--bg2) !important; }

  td { padding: 6px 10px; color: var(--text); vertical-align: middle; }
  td.sci { font-style: italic; color: var(--text2); font-size: 11.5px; white-space: nowrap; }
  td.num { text-align: right; font-variant-numeric: tabular-nums; font-size: 12.5px; }

  .bar-cell { display: flex; align-items: center; gap: 6px; justify-content: flex-end; }
  .bar { height: 6px; border-radius: 3px; flex-shrink: 0; min-width: 2px; }

  /* ── Tier badges ── */
  .badge { display: inline-block; padding: 2px 7px; border-radius: 3px; font-size: 11px; font-weight: 600; white-space: nowrap; }
  .b-p  { background: var(--b-p-bg);  color: var(--b-p-tx); }
  .b-h  { background: var(--b-h-bg);  color: var(--b-h-tx); }
  .b-m  { background: var(--b-m-bg);  color: var(--b-m-tx); }
  .b-lo { background: var(--b-lo-bg); color: var(--b-lo-tx); }
  .b-ll { background: var(--b-ll-bg); color: var(--b-ll-tx); }

  /* ── Source & new tags ── */
  .src-tag {
    font-size: 10px; color: var(--text3);
    padding: 1px 5px;
    border: 0.5px solid var(--border2);
    border-radius: 3px;
    background: var(--bg2);
    font-weight: 600;
  }
  .new-tag {
    font-size: 10px; padding: 1px 6px;
    border-radius: 3px;
    background: var(--new-bg); color: var(--new-tx);
    margin-left: 5px; font-weight: 700;
    letter-spacing: 0.2px;
  }

  /* ── Category text ── */
  .cat-c   { color: var(--text);  font-size: 11.5px; font-weight: 500; }
  .cat-s   { color: var(--text2); font-size: 11.5px; }
  .cat-r   { color: var(--text3); font-size: 11.5px; font-style: italic; }
  .cat-con { color: #5a7830;      font-size: 11.5px; font-style: italic; font-weight: 500; }

  /* Conifer row — very subtle resin-amber tint */
  tr.con-row { background: rgba(200,160,10,0.06) !important; }
  tr.con-row:hover { background: var(--bg2) !important; }

  /* ── Notes / cards ── */
  .sections { margin-top: 32px; display: grid; gap: 20px; }
  .card {
    border: 1px solid var(--border2);
    border-radius: 10px;
    padding: 18px 20px;
    background: var(--bg2);
  }
  .card h2 {
    font-family: Georgia, "Times New Roman", serif;
    font-size: 15px; font-weight: 700;
    margin-bottom: 10px; color: var(--text);
    border-bottom: 1px solid var(--border);
    padding-bottom: 6px;
  }
  .card p, .card li { font-size: 13px; color: var(--text2); line-height: 1.65; }
  .card ul { padding-left: 18px; display: grid; gap: 5px; }
  .card li strong { color: var(--text); }

  .sources-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 12px; margin-top: 12px; }
  .src-item {
    border: 1px solid var(--border2);
    border-radius: 8px; padding: 12px 14px;
    background: var(--bg);
    border-left: 3px solid var(--accent);
  }
  .src-item .src-code { font-size: 13px; font-weight: 700; color: var(--accent-text); margin-bottom: 4px; font-family: Georgia, serif; }
  .src-item p { font-size: 12px; color: var(--text2); line-height: 1.5; }

  .coef-note {
    margin-top: 10px; padding: 12px 14px;
    background: var(--bg);
    border: 1px solid var(--border2);
    border-left: 3px solid var(--accent);
    border-radius: 8px;
    font-size: 12.5px; color: var(--text2); line-height: 1.65;
  }
  .coef-note strong { color: var(--text); }

  footer {
    margin-top: 36px;
    border-top: 1px solid var(--border2);
    padding-top: 14px;
    font-size: 11.5px; color: var(--text3); line-height: 1.6;
  }
</style>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400..900;1,400..900&display=swap" rel="stylesheet">
</head>
<body>

<header>
  <h1>Northeastern US Firewood BTU Reference</h1>
  <p>Heat output and other info for native &amp; naturalized species</p>
  <div class="hdr-meta">
    <div class="hdr-item">
      <div class="hdr-label">Cord standard</div>
      <div class="hdr-value">128 ft³ stacked &middot; (4'x4'x8') &middot; 20% moisture content</div>
    </div>
    <div class="hdr-item">
      <div class="hdr-label">Cords for common lengths:</div>
      <div class="hdr-value"><strong>18" logs:</strong> 4' high by 21.3' long. <strong>16" logs: 4' high x 24" long</div>
    </div>
  </div>
</header>

<div class="controls">
  <label>Search</label>
  <input type="search" id="searchInput" placeholder="Common or scientific name…" style="font-size:12px;padding:4px 9px;border:1px solid var(--border2);border-radius:6px;background:var(--bg2);color:var(--text);width:200px;">
  <label style="margin-left:6px">Category</label>
  <div class="filter-group">
    <button class="fb active" data-cat="all">All species</button>
    <button class="fb" data-cat="common">Common firewood</button>
    <button class="fb" data-cat="secondary">Less common</button>
    <button class="fb" data-cat="rare">Rare / small</button>
    <button class="fb" data-cat="conifer">Conifers</button>
  </div>
  <label style="margin-left:10px">Sort by</label>
  <select id="sortSel">
    <option value="btu">BTU/cord (high → low)</option>
    <option value="sg">Specific gravity (high → low)</option>
    <option value="wt">Dry weight (high → low)</option>
    <option value="name">Species name (A → Z)</option>
  </select>
  <span class="count" id="cnt"></span>
</div>

<div class="legend">
  <div class="li"><div class="ld" style="background:#1a4006"></div>Premium ≥27M BTU</div>
  <div class="li"><div class="ld" style="background:#4a8818"></div>High 24–27M</div>
  <div class="li"><div class="ld" style="background:#96b830"></div>Mid 20–24M</div>
  <div class="li"><div class="ld" style="background:#c8a010"></div>Lower 17–20M</div>
  <div class="li"><div class="ld" style="background:#a09050"></div>Low &lt;17M</div>
</div>

<p class="scroll-hint">← scroll to see all columns →</p>
<div class="tbl-wrap">
<table id="mainTbl">
<thead>
<tr>
  <th style="min-width:175px" data-key="name">Common name <span class="arrow">↕</span></th>
  <th class="num" style="width:120px" data-key="btu">BTU/cord (M) <span class="arrow">↕</span></th>
  <th style="min-width:160px">Scientific name</th>
  <th class="num" style="width:110px" data-key="wt">Dry wt (lbs) <span class="arrow">↕</span></th>
  <th style="width:80px">Tier</th>
  <th style="width:85px">Category</th>
  <th style="width:42px">Src</th>
</tr>
</thead>
<tbody id="tbody"></tbody>
</table>
</div>

<div class="sections">

  <div class="card">
    <h2>Fun facts</h2>
    <ul>
      <li><strong>Serviceberry</strong> (<em>Amelanchier</em> spp., 28.3M BTU) rivals pignut hickory and black locust — one of the most underrated firewood species in NE, extremely common as an understory tree across MA and the region, yet almost never discussed because individual trees are too small to sell commercially. Worth harvesting in woodland management.</li>
      <li><strong>Swamp white oak</strong> (<em>Quercus bicolor</em>, 30.8M) tops all other NE oaks due to an unusually high specific gravity of 0.72 (USDA FPL). It outperforms white oak by roughly 20% per cord. Common in bottomland sites throughout the Pioneer Valley and coastal New England.</li>
      <li><strong>Chestnut oak</strong> (<em>Q. prinus</em>, 28.3M) and <strong>post oak</strong> (<em>Q. stellata</em>, 26.6M) both significantly outperform red oak. Chestnut oak is common on rocky upland sites throughout CT, MA, NY, and RI.</li>
      <li><strong>Apple and crabapple</strong> (<em>Malus</em> spp., 26.1M) are genuinely premium firewood, in the same tier as bitternut hickory. Old orchard trees and dooryard specimens throughout NE are an excellent source.</li>
      <li><strong>Hawthorn</strong> (<em>Crataegus</em> spp., 26.6M) is dense and hot-burning but thorny and rarely large enough to yield significant volume. Worth adding to a mixed load when clearing.</li>
      <li><strong>Black walnut</strong> (<em>Juglans nigra</em>, 21.9M) is solid mid-tier firewood, though its lumber value typically far exceeds its firewood value — always worth checking before splitting.</li>
      <li><strong>Tree of heaven</strong> (<em>Ailanthus altissima</em>, 19.7M) is a legitimate mid-tier fuel, comparable to American elm. Given its invasive abundance in disturbed and urban NE, it is a freely available resource.</li>
      <li><strong>Black oak</strong> (<em>Q. velutina</em>, 24.4M) and <strong>scarlet oak</strong> (<em>Q. coccinea</em>, 25.7M) both outperform red oak yet are rarely listed separately in firewood guides.</li>
    </ul>
  </div>

  <div class="card">
    <h2>BTU/lb coefficient — why it matters</h2>
    <p>All species in this table cluster tightly at approximately <strong>6,380–6,410 BTU per pound</strong> of seasoned wood (at ~20% moisture content). This is not a coincidence — it reflects the physical reality that all wood species have essentially the same energy density per unit of dry mass (~8,600 BTU/lb oven-dry; ~6,400 BTU/lb at 20% MC after accounting for heat lost to residual moisture evaporation).</p>
    <div class="coef-note">
      <strong>Practical implication:</strong> The entire spread in this table — from basswood at 13.7M to swamp white oak at 30.8M BTU/cord — is almost entirely a function of how many pounds of wood fit into a stacked cord. A cord of basswood and a cord of swamp white oak contain roughly the same energy per pound; the oak cord just contains more than twice as much wood by weight. If you were to somehow weigh your wood purchase rather than buying by cord, species identity matters much less. Conversely, species density is the single most important variable when buying by the cord.
    </div>
  </div>

  <div class="card">
    <h2>Data sources</h2>
    <div class="sources-grid">
      <div class="src-item">
        <div class="src-code">S — Spike's VM</div>
        <p><em>Firewood BTU Chart</em>, spikevm.com. Calculated directly from USDA-sourced basic specific gravity (SG) using the formula: Weight@20%MC = SG × 85 ft³ × 62.4 lb/ft³ × 1.2; BTU = Weight × 0.833 × 8,084. The most methodologically consistent source for cross-species comparison.</p>
      </div>
      <div class="src-item">
        <div class="src-code">C — Calculated</div>
        <p>Same formula as Spike's, applied to species not directly listed in their BTU table. Specific gravity values sourced from USDA Forest Products Laboratory <em>Wood Handbook</em> (2010, Table 5-3) or Spike's own SG table (spikevm.com/list/pulp-wood-metric.php).</p>
      </div>
      <div class="src-item">
        <div class="src-code">A — A1/USDA</div>
        <p>A1 Country Firewood BTU chart, attributed to the USDA Forest Products Laboratory. Traditional firewood table using measured seasoned cord weights and reported BTU values. Slightly lower figures than Spike's for some species due to different cord stacking assumptions.</p>
      </div>
      <div class="src-item">
        <div class="src-code">H — Hale 1933</div>
        <p>J.D. Hale, <em>Heating Value of Wood Fuels</em> (1933), compiled by CDL Inc. Reports gross heating value for Canadian air-dry cord. Systematically 15–25% higher than US sources due to gross vs. net methodology. Widely cited in Canadian firewood literature.</p>
      </div>
    </div>
    <p style="margin-top:12px;font-size:12px;color:var(--text3)">
      <strong>Cord definition:</strong> Spike's and the calculated values assume 85 ft³ of solid wood per stacked cord (128 ft³ total volume), which is standard for split, stacked firewood. Traditional USDA tables use similar assumptions. All BTU values are for air-dried wood at approximately 20% moisture content (MC). Green wood values will be substantially lower.
    </p>
  </div>

  <div class="card">
    <h2>Caveats and limitations</h2>
    <ul>
      <li>BTU/cord figures are calculated from average species-level specific gravity. Individual trees vary significantly based on growth rate, soil conditions, and site — a slow-grown sugar maple on thin rocky soil will be noticeably denser than one from rich bottomland.</li>
      <li>Cord stacking geometry affects actual solid wood content. A cord of small, irregular pieces (e.g., hawthorn) contains less solid wood than a cord of uniformly split billets, even if nominally the same 128 ft³ stack. Figures assume well-stacked split wood.</li>
      <li>Several species noted as "rare" or "rare/small" (witch-hazel, striped maple, serviceberry, hop-hornbeam) rarely provide full cord volumes in practice, but their BTU data is useful for evaluating mixed loads or woodlot management decisions.</li>
      <li>Three ash species (white, green, black) are now heavily impacted by emerald ash borer (EAB) throughout NE. Black ash is critically endangered. Ash BTU data is included for completeness and because EAB-killed material is currently widely available.</li>
      <li>American chestnut (<em>Castanea dentata</em>) is listed as a historical reference — the species is functionally extinct as a canopy tree due to chestnut blight, though root-sprouting coppice is common.</li>
    </ul>
  </div>

</div>

<footer>
  Compiled 2025–2026 | Data: Spike's VM / USDA FPL, A1 Country Firewood / USDA FPL, Hale (1933) | All BTU values at ~20% moisture content, per standard cord (128 ft³ stacked, ~85 ft³ solid wood). Hover any table row for NE range notes.
</footer>

<script>
const DATA = [
  // [name, sci, sg, wt20, btu, src, isNew, cat, rangeNote]
  ["Swamp White Oak","Quercus bicolor",0.720,4577,30.83,"C",true,"secondary","Common in NE bottomlands; significantly denser than white oak (SG 0.72, USDA FPL)"],
  ["Serviceberry","Amelanchier spp.",0.660,4201,28.29,"S",true,"secondary","Extremely common NE understory — almost never discussed as firewood despite premium BTU"],
  ["Pignut Hickory","Carya glabra",0.660,4201,28.29,"S",true,"secondary","S. NE to NY; often misidentified as shagbark; smoother bark, smaller nuts"],
  ["Black Locust","Robinia pseudoacacia",0.660,4201,28.29,"S",false,"secondary","Throughout NE in disturbed areas; excellent coaling, very rot-resistant"],
  ["Chestnut Oak","Quercus prinus",0.660,4196,28.25,"C",true,"secondary","Rocky upland sites throughout NE; large wavy-lobed leaves"],
  ["Shagbark Hickory","Carya ovata",0.640,4073,27.43,"S",false,"common","Throughout NE to SW Maine; shaggy peeling bark; classic premium firewood"],
  ["Mockernut Hickory","Carya tomentosa",0.640,4073,27.43,"S",true,"secondary","S. NE — CT, RI, coastal MA; large thick-shelled nuts"],
  ["Flowering Dogwood","Cornus florida",0.640,4073,27.43,"S",true,"rare","S. NE edge only (CT, RI, coastal NY); small ornamental tree"],
  ["Post Oak","Quercus stellata",0.620,3946,26.57,"S",true,"rare","S. NE edge — CT, RI, Long Island; sandy/dry soils"],
  ["Apple / Crabapple","Malus spp.",0.610,3878,26.13,"C",true,"secondary","Old orchards and dooryards throughout NE; excellent aromatic firewood"],
  ["Hop-Hornbeam (Ironwood)","Ostrya virginiana",0.630,4005,26.97,"C",false,"secondary","Common NE understory; very dense but rarely grows large enough for significant volume"],
  ["Hawthorn","Crataegus spp.",0.620,3946,26.57,"S",true,"secondary","Very common NE edges and old fields; thorny, dense, small-trunked"],
  ["Honey Locust","Gleditsia triacanthos",0.600,3819,25.72,"S",true,"secondary","Planted throughout NE; native to S. NE; vicious thorns on trunk and branches"],
  ["Sweet Birch (Black Birch)","Betula lenta",0.600,3819,25.72,"S",false,"common","Central-S. NE — CT, MA, NY, VT; wintergreen scent; excellent BTU for a birch"],
  ["Bitternut Hickory","Carya cordiformis",0.600,3819,25.72,"S",false,"common","Throughout S. NE; bitter inedible nuts; yellow bud scales diagnostic"],
  ["White Oak","Quercus alba",0.600,3814,25.69,"C",false,"common","Throughout NE to S. Maine; the standard against which other oaks are compared"],
  ["Scarlet Oak","Quercus coccinea",0.600,3814,25.69,"C",true,"secondary","Sandy soils throughout NE; deeply cut leaves turn brilliant red in fall"],
  ["Bur Oak","Quercus macrocarpa",0.580,3687,24.84,"C",true,"secondary","W. NE margin, NY; large fringed acorn cups; drought-tolerant"],
  ["Blue Beech (Musclewood)","Carpinus caroliniana",0.580,3692,24.86,"S",false,"secondary","Common NE understory; smooth sinewy bark; rarely large but very dense"],
  ["Eastern Redbud","Cercis canadensis",0.580,3692,24.86,"C",true,"rare","S. NE edge (CT, RI); mostly planted as ornamental north of its native range"],
  ["American Beech","Fagus grandifolia",0.560,3564,24.00,"S",false,"common","Throughout NE; smooth gray bark; under heavy pressure from beech leaf disease"],
  ["Sugar Maple (Hard Maple)","Acer saccharum",0.560,3564,24.00,"S",false,"common","Throughout NE; 4th most abundant eastern US tree; excellent BTU and coaling"],
  ["Witch-Hazel","Hamamelis virginiana",0.560,3564,24.00,"S",true,"secondary","Very common NE understory; late-blooming flowers; small tree/large shrub"],
  ["Black Oak","Quercus velutina",0.570,3623,24.40,"C",true,"secondary","Throughout NE; often confused with red oak; slightly denser"],
  ["Yellow Birch","Betula alleghaniensis",0.550,3501,23.57,"S",false,"common","Throughout NE uplands; golden-bronze peeling bark; best of the common birches"],
  ["White Ash","Fraxinus americana",0.550,3501,23.57,"S",false,"common","Throughout NE — now critically impacted by emerald ash borer (EAB)"],
  ["Black Maple","Acer nigrum",0.520,3310,22.29,"S",true,"secondary","W. NE margin, NY/VT; very similar to sugar maple; drooping leaf lobes"],
  ["Green Ash","Fraxinus pennsylvanica",0.530,3373,22.72,"S",true,"common","Throughout NE, esp. wet sites — heavily impacted by EAB; widely planted"],
  ["Red Oak","Quercus rubra",0.560,3560,23.97,"C",false,"common","Ubiquitous throughout NE; the most commercially harvested NE timber tree"],
  ["Black Walnut","Juglans nigra",0.510,3246,21.86,"S",true,"secondary","Throughout S. NE; lumber value usually far exceeds firewood value — check first"],
  ["Red Maple (Soft Maple)","Acer rubrum",0.490,3119,21.00,"S",false,"common","Most abundant tree in eastern North America; fast-growing, easy to season"],
  ["River Birch","Betula nigra",0.490,3119,21.00,"S",true,"secondary","Riparian NE; flaky salmon-colored bark; range expanding northward with warming"],
  ["Hackberry","Celtis occidentalis",0.490,3119,21.00,"S",false,"secondary","S. NE, NY; corky warty bark; often found in disturbed urban/suburban areas"],
  ["Black Gum (Tupelo)","Nyssa sylvatica",0.500,3179,21.41,"C",true,"secondary","Throughout NE to S. Maine; brilliant red fall color; interlocked grain — hard to split"],
  ["Slippery Elm","Ulmus rubra",0.480,3051,20.55,"C",true,"secondary","Throughout NE; inner bark mucilaginous; now declining alongside American elm"],
  ["Paper Birch","Betula papyrifera",0.480,3055,20.57,"S",false,"common","Throughout NE; iconic white bark; rots rapidly from inside if not split promptly"],
  ["American Holly","Ilex opaca",0.500,3182,21.43,"S",true,"rare","S. NE coastal areas; broadleaf evergreen; rarely available as firewood"],
  ["American Elm","Ulmus americana",0.460,2924,19.70,"C",false,"secondary","Throughout NE; largely eliminated by Dutch elm disease; occasional survivors"],
  ["Ailanthus (Tree-of-Heaven)","Ailanthus altissima",0.460,2924,19.70,"S",true,"secondary","Invasive throughout NE; freely available in urban and disturbed areas"],
  ["Gray Birch","Betula populifolia",0.450,2864,19.29,"S",false,"common","Throughout NE; white bark with black chevrons; pioneer species, short-lived"],
  ["Black Ash","Fraxinus nigra",0.450,2864,19.29,"S",false,"common","NE wetlands; critically endangered by EAB; important to Indigenous basketmaking"],
  ["Striped Maple (Moosewood)","Acer pensylvanicum",0.440,2801,18.86,"S",true,"rare","Common NE understory; green-striped bark; small tree, rarely provides much volume"],
  ["Silver Maple","Acer saccharinum",0.440,2801,18.86,"S",false,"common","Throughout NE, esp. riverbanks; widely planted in towns; fast-growing"],
  ["Mountain Maple","Acer spicatum",0.440,2801,18.86,"S",true,"rare","Highland NE understory; very small tree; upright flower clusters"],
  ["Sassafras","Sassafras albidum",0.420,2670,17.99,"C",true,"secondary","Throughout S.-Central NE; mitten-shaped leaves; aromatic orange inner bark"],
  ["Boxelder","Acer negundo",0.416,2648,17.83,"S",false,"secondary","Riparian NE; weedy fast-growing maple; poor coaling but easy to ignite"],
  ["American Chestnut","Castanea dentata",0.400,2546,17.14,"S",true,"rare","Functionally extinct as canopy tree (chestnut blight); coppice sprouts persist"],
  ["Pin Cherry","Prunus pensylvanica",0.360,2291,15.43,"C",true,"secondary","Very common NE pioneer species after disturbance; small and short-lived"],
  ["Bigtooth Aspen","Populus grandidentata",0.360,2291,15.43,"C",true,"common","Common NE, often with quaking aspen; larger leaf than quaking aspen"],
  ["Quaking Aspen","Populus tremuloides",0.350,2228,15.00,"S",false,"common","Common NE disturbed forests; distinctive fluttering leaves; pale smooth bark"],
  ["Butternut","Juglans cinerea",0.360,2291,15.43,"S",false,"secondary","Throughout NE; now seriously threatened by Sirococcus canker fungus"],
  ["Basswood (American Linden)","Tilia americana",0.320,2034,13.72,"S",false,"secondary","Throughout NE, esp. rich sites; very soft; excellent for carving; poor firewood"],
  ["Norway Maple","Acer platanoides",0.530,3373,22.72,"C",false,"secondary","Highly invasive throughout NE urban and suburban forest; municipalities removing at scale; BTU intermediate between red and sugar maple; SG estimated from European forestry data for NE-grown specimens"],
  ["White Mulberry","Morus alba",0.590,3755,25.29,"C",false,"secondary","Naturalized throughout NE disturbed areas, roadsides, and urban edges; premium fuel comparable to white oak; native red mulberry (M. rubra, similar SG) also present in S. NE"],
  ["Common Buckthorn","Rhamnus cathartica",0.611,3889,26.19,"C",false,"secondary","Highly invasive NE woodland edges and disturbed sites; small tree but very dense; cleared in large quantities by land managers — excellent opportunistic firewood; SG from Spike's / European data"],
  ["Osage Orange","Maclura pomifera",0.800,5092,34.29,"S",false,"secondary","Not native to NE but widely planted as hedgerow throughout the region; heaviest and highest-BTU wood on this list by a wide margin — nearly identical BTU/cord to anthracite coal; very hard on chainsaw chains; sparks moderately"],
  ["Tamarack (Eastern Larch)","Larix laricina",0.490,3119,21.00,"S",false,"conifer","Deciduous conifer found in NE bogs and wetlands; by far the best conifer firewood — rivals soft hardwoods in BTU"],
  ["Eastern Hemlock","Tsuga canadensis",0.400,2546,17.14,"C",false,"conifer","Very common NE forest tree; sparks significantly — use caution in open fireplaces; moderate BTU"],
  ["Red Spruce","Picea rubens",0.410,2610,17.58,"C",false,"conifer","Dominant high-elevation NE conifer; slightly denser than white spruce; resinous"],
  ["Eastern White Pine","Pinus strobus",0.350,2228,15.00,"C",false,"conifer","Most abundant NE conifer; poor firewood but valuable as kindling; seasons quickly"],
  ["Balsam Fir","Abies balsamea",0.330,2100,14.14,"S",false,"conifer","Ubiquitous NE boreal conifer; aromatic; burns fast with poor coaling; moderate creosote risk if unseasoned"]
];

const MAXBTU = 35.5;

function tierInfo(b) {
  if (b >= 27) return ["Premium", "b-p", "#1a4006"];
  if (b >= 24) return ["High",    "b-h", "#4a8818"];
  if (b >= 20) return ["Mid",     "b-m", "#96b830"];
  if (b >= 17) return ["Lower",   "b-lo","#c8a010"];
  return              ["Low",     "b-ll","#a09050"];
}

function catLabel(c) {
  if (c === "common")    return "<span class='cat-c'>Common</span>";
  if (c === "secondary") return "<span class='cat-s'>Secondary</span>";
  if (c === "conifer")   return "<span class='cat-con'>Conifer</span>";
  return                        "<span class='cat-r'>Rare/small</span>";
}

let activeCat = "all";

document.querySelectorAll('.fb').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.fb').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    activeCat = btn.dataset.cat;
    render();
  });
});

document.getElementById('sortSel').addEventListener('change', render);
document.getElementById('searchInput').addEventListener('input', render);

document.querySelectorAll('thead th[data-key]').forEach(th => {
  th.addEventListener('click', () => {
    const sel = document.getElementById('sortSel');
    sel.value = th.dataset.key;
    render();
  });
});

function render() {
  const sortKey   = document.getElementById('sortSel').value;
  const query     = document.getElementById('searchInput').value.trim().toLowerCase();
  let data = [...DATA];

  if      (activeCat === "common")    data = data.filter(r => r[7] === "common");
  else if (activeCat === "secondary") data = data.filter(r => r[7] === "secondary");
  else if (activeCat === "rare")      data = data.filter(r => r[7] === "rare");
  else if (activeCat === "conifer")   data = data.filter(r => r[7] === "conifer");

  if (query) {
    data = data.filter(r =>
      r[0].toLowerCase().includes(query) ||
      r[1].toLowerCase().includes(query)
    );
  }

  data.sort((a, b) => {
    if (sortKey === "name") return a[0].localeCompare(b[0]);
    if (sortKey === "btu")  return b[4] - a[4];
    if (sortKey === "sg")   return b[2] - a[2];
    if (sortKey === "wt")   return b[3] - a[3];
    return b[4] - a[4];
  });

  document.getElementById('cnt').textContent = data.length + " species shown";

  document.querySelectorAll('thead th[data-key]').forEach(th => {
    th.classList.toggle('sorted', th.dataset.key === sortKey);
  });

  const tbody = document.getElementById('tbody');
  tbody.innerHTML = data.map(r => {
    const [name, sci, sg, wt, btu, src, isNew, cat, note] = r;
    const [tLabel, tClass, barColor] = tierInfo(btu);
    const barW = Math.round((btu / MAXBTU) * 110);

    return `<tr title="${note}" class="${cat === 'conifer' ? 'con-row' : ''}">
      <td>${name}</td>
      <td class="num">
        <div class="bar-cell">
          <span>${btu.toFixed(2)}</span>
          <div class="bar" style="width:${barW}px;background:${barColor}"></div>
        </div>
      </td>
      <td class="sci">${sci}</td>
      <td class="num">${wt.toLocaleString()}</td>
      <td><span class="badge ${tClass}">${tLabel}</span></td>
      <td>${catLabel(cat)}</td>
      <td><span class="src-tag">${src}</span></td>
    </tr>`;
  }).join('');
}

render();
</script>
</body>
</html>
