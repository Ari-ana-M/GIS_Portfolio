<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ariana Mansingh | GIS & Remote Sensing Analyst</title>
<meta name="description" content="Ariana Mansingh: GIS and remote sensing analyst. Lake ice research, coastal field monitoring, and municipal planning GIS.">
<meta property="og:title" content="Ariana Mansingh | GIS & Remote Sensing Analyst">
<meta property="og:description" content="Interactive portfolio: spatial analysis, remote sensing, field data collection, and cartography.">
<meta property="og:type" content="website">
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>
<style>
/* ── Base ── */
body { margin: 0; padding: 16px; font-family: Arial, sans-serif; box-sizing: border-box; }

/* ── Skill tags ── */
.skill-pill {
  display: inline-block;
  font-size: 13px;
  padding: 8px 14px;
  border-radius: 18px;
  margin: 5px 6px 0 0;
  border: 1px solid transparent;
  white-space: nowrap;
}
.skill-pill:focus-visible { outline: 2px solid #0d6b75; outline-offset: 2px; }

/* Core = strong teal (primary expertise) */
.skill-pill.expert {
  background: #d6f6f8;
  border-color: #38C6D0;
  color: #0d6b75;
  font-weight: 600;
}

/* Working knowledge = softer green-blue */
.skill-pill.proficient {
  background: #e7f7ef;
  border-color: #90E2BF;
  color: #2f6b4f;
}

/* Currently building = neutral gray */
.skill-pill.familiar {
  background: #f2f2f2;
  border-color: #ccc;
  color: #444;
}

/* Small tags used inside project panels and the timeline */
.skill-tag {
  display: inline-block; font-size: 10px; padding: 2px 8px; border-radius: 10px;
  background: #eef6f7; border: 1px solid #cfe3e6; margin: 2px 2px 0 0;
}

/* ── Interactive skill buttons ── */
.skill-filter-btn {
  background:#f4f4f4;
  border:1px solid #ddd;
  border-radius:20px;
  padding:7px 12px;
  margin:4px;
  cursor:pointer;
  font-size:12px;
  transition:all .15s ease;
}

.skill-filter-btn:hover {
  background:#38C6D0;
  color:white;
  border-color:#38C6D0;
}

/* ── Project list sidebar ── */
.project-link {
  cursor: pointer; font-weight: 600; font-size: 12px; color: #38C6D0;
  text-decoration: underline; display: inline-block; margin-bottom: 4px; line-height: 1.4;
}
.project-link:hover { color: #F19FB4; }

/* ── ArcGIS-style popup ── */
.arcgis-popup { font-family: Arial, sans-serif; font-size: 13px; }
.arcgis-popup-header {
  background: #4a4a4a; color: white; padding: 10px 12px;
  display: flex; justify-content: space-between; align-items: center;
}
.arcgis-popup-header h3 { margin: 0; font-size: 13px; font-weight: bold; line-height: 1.3; }
.arcgis-popup-header button {
  background: none; border: none; color: white;
  font-size: 16px; cursor: pointer; padding: 0 0 0 8px; line-height: 1;
}
.arcgis-popup-subheader {
  padding: 6px 12px; font-size: 11px; font-weight: bold;
  text-transform: uppercase; letter-spacing: 0.05em; color: white;
}
.arcgis-table { width: 100%; border-collapse: collapse; font-size: 12px; }
.arcgis-table tr:nth-child(odd)  { background: #f5f5f5; }
.arcgis-table tr:nth-child(even) { background: #ffffff; }
.arcgis-table td { padding: 6px 10px; vertical-align: top; border-bottom: 1px solid #e0e0e0; }
.arcgis-table td:first-child { font-weight: bold; color: #555; width: 40%; white-space: nowrap; }
.arcgis-table td:last-child { color: #222; }
.arcgis-popup-link {
  display: block; padding: 8px 12px; font-size: 12px;
  color: #0079c1; text-decoration: none; border-top: 1px solid #ddd;
}
.arcgis-popup-link:hover { text-decoration: underline; }
.preview-btn {
  display: block; margin: 10px 12px 12px; padding: 7px 12px;
  background: #38C6D0; color: white; border: none; border-radius: 5px;
  font-size: 12px; font-weight: bold; cursor: pointer; text-align: center;
  width: calc(100% - 24px);
}
.preview-btn:hover { background: #2fb0ba; }

/* ── View toggle buttons ── */
.view-toggle {
  display: flex; gap: 8px; padding: 10px 12px;
  background: #f0f0f0; border-bottom: 2px solid #333;
}
.view-btn {
  padding: 6px 14px; font-size: 12px; font-weight: bold;
  border: 1px solid #bbb; border-radius: 5px; cursor: pointer;
  background: white; color: #444;
}
.view-btn.active { background: #4a4a4a; color: white; border-color: #4a4a4a; }

/* ── Timeline ── */
#timelinePanel {
  display: none; padding: 28px 32px; overflow-x: auto;
  background: #fafafa; min-height: 400px;
}
.tl-container {
  position: relative; min-width: 700px;
}
.tl-line {
  position: absolute; top: 38px; left: 0; right: 0;
  height: 3px; background: #ddd; z-index: 0;
}
.tl-items {
  display: flex; justify-content: space-between;
  position: relative; z-index: 1;
}
.tl-item {
  display: flex; flex-direction: column; align-items: center;
  flex: 1; cursor: pointer; padding: 0 6px;
}
.tl-dot {
  width: 18px; height: 18px; border-radius: 50%;
  border: 3px solid white; box-shadow: 0 0 0 2px #ccc;
  margin-bottom: 8px; flex-shrink: 0; transition: transform .15s;
}
.tl-item:hover .tl-dot { transform: scale(1.3); }
.tl-item.selected .tl-dot { box-shadow: 0 0 0 3px #FFD700; transform: scale(1.2); }
.tl-year {
  font-size: 11px; font-weight: bold; color: #888; margin-bottom: 6px;
}
.tl-card {
  background: white; border: 1px solid #ddd; border-radius: 7px;
  padding: 8px 10px; font-size: 11px; text-align: center;
  max-width: 130px; line-height: 1.4; box-shadow: 0 1px 4px rgba(0,0,0,.07);
  transition: box-shadow .15s;
}
.tl-item:hover .tl-card { box-shadow: 0 3px 10px rgba(0,0,0,.13); }
.tl-item.selected .tl-card { border-color: #FFD700; box-shadow: 0 0 0 2px #FFD700; }
.tl-cat {
  font-size: 9px; font-weight: bold; text-transform: uppercase;
  letter-spacing: .04em; margin-bottom: 3px;
}
.tl-skills { margin-top: 6px; display: flex; flex-wrap: wrap; justify-content: center; gap: 2px; }

/* ── PDF export button ── */
#exportBtn {
  position: fixed; bottom: 22px; right: 22px;
  background: #4a4a4a; color: white;
  border: none; border-radius: 8px;
  padding: 10px 18px; font-size: 13px; font-weight: bold;
  cursor: pointer; box-shadow: 0 3px 10px rgba(0,0,0,.25);
  z-index: 9999;
}
#exportBtn:hover { background: #222; }

/* ── Small screens: stack the map dashboard ── */
@media (max-width: 760px) {
  #mapRow { flex-direction: column; height: auto !important; }
  #map { height: 420px; flex: none !important; width: 100%; }
  #leftPanel { width: auto !important; border-right: none; border-bottom: 1px solid #ccc; max-height: 220px; }
  #infoPanel { width: auto !important; border-left: none; border-top: 2px solid #333; }
  #exportBtn { bottom: 12px; right: 12px; padding: 8px 12px; }
  .view-toggle { flex-wrap: wrap; }
}

/* ── Print / PDF styles ── */
@media print {
  #exportBtn, #webViewerPanel, .view-toggle { display: none !important; }
  #timelinePanel { display: block !important; page-break-before: always; }
  #dashboardWrap { display: none !important; }
  body { padding: 0; }
}
</style>
</head>
<body>

<noscript>
  <p>Ariana Mansingh is a GIS and remote sensing analyst with an MSc in Geography from the University of Waterloo.
  This portfolio is interactive and needs JavaScript. Contact:
  <a href="mailto:ariana.mansingh.pro@gmail.com">ariana.mansingh.pro@gmail.com</a>,
  <a href="https://linkedin.com/in/ariana-mansingh">LinkedIn</a>.</p>
</noscript>

<!-- ═══════════════════════════════════════════════
     HERO PANEL
════════════════════════════════════════════════ -->
<div style="
  display:flex;
  flex-wrap:wrap;
  gap:40px;
  align-items:flex-start; border:2px solid #333; padding:30px; border-radius:10px; margin-top:20px;">

  <!-- LEFT SIDE -->
  <div style="flex:1; min-width:320px;">

    <h1 style="margin-top:0; margin-bottom:5px;">
      GIS & Spatial Data Portfolio
    </h1>

    <p style="margin-top:0;">
      <b>
        GIS and spatial data analyst working across climate research,
        environmental monitoring, and applied planning
      </b>
    </p>

    <p style="font-size:13px; color:#444; line-height:1.6;">
      I'm a GIS and spatial data analyst with an MSc in Geography from the
      University of Waterloo, working across municipal, academic, and
      environmental projects. I integrate, validate, and analyze large
      spatial datasets using ArcGIS Pro, ArcGIS Enterprise/Online, SQL, and
      Python, and turn that analysis into cartographic products and
      decision-ready findings, from research supporting a peer-reviewed
      climate publication to policy-ready municipal recommendations. I build
      the QA/QC workflows and documentation that let findings hold up under
      scrutiny, and I'm currently pursuing
      <b>Geoscientist-in-Training (GIT)</b>
      registration with Professional Geoscientists Ontario (PGO).
    </p>

    <p style="font-size:13px;">
      Open to GTA-area roles ·
      <a href="mailto:ariana.mansingh.pro@gmail.com">Email</a> ·
      <a href="https://linkedin.com/in/ariana-mansingh" target="_blank" rel="noopener">LinkedIn</a>
    </p>

    <h3>Education</h3>

    <ul style="list-style-type: disc; padding-left: 20px; line-height:1.6;">

      <li>
        <b>MSc Geography</b>, University of Waterloo
        <span style="color:#888; font-size:12px;">
          (Sep 2022 to Dec 2025)
        </span>

        <ul style="margin-top:5px;">
          <li>Focus: Climate data, lake ice systems & remote sensing</li>
          <li>GPA: 3.93 / 4.0</li>
        </ul>
      </li>

      <li>
        <b>Honours BA Environmental Studies</b>,
        Wilfrid Laurier University

        <span style="color:#888; font-size:12px;">
          (Sep 2018 to Apr 2022)
        </span>

        <ul style="margin-top:5px;">
          <li>Option in Geomatics; Minor in Sociology</li>
          <li>GPA: 3.8 / 4.0 · Dean's List 2018 to 2022</li>
        </ul>
      </li>

    </ul>

  </div>

  <!-- RIGHT SIDE SVG -->
  <div style="flex:1; display:flex; justify-content:center; align-items:flex-start; min-width:0;">

    <svg width="520" height="475" viewBox="0 0 520 480" style="max-width:100%; height:auto;">

      <rect x="10" y="60" width="500" height="395"
            fill="none" stroke="#333"
            stroke-width="1" rx="10"/>

      <text x="260" y="25"
            text-anchor="middle"
            font-size="18"
            font-weight="bold">
        Communication & Translation
      </text>

      <text x="260" y="45"
            text-anchor="middle"
            font-size="12">
        Presenting to stakeholders • Interdisciplinary collaboration • Reporting
      </text>

      <circle cx="170" cy="210" r="110"
              fill="#38C6D0" fill-opacity="0.7"/>

      <circle cx="350" cy="210" r="110"
              fill="#90E2BF" fill-opacity="0.6"/>

      <circle cx="260" cy="320" r="110"
              fill="#F19FB4" fill-opacity="0.7"/>

      <text x="150" y="95"
            text-anchor="middle"
            font-size="14"
            font-weight="bold">
        Data Acquisition
      </text>

      <text x="370" y="95"
            text-anchor="middle"
            font-size="14"
            font-weight="bold">
        Geospatial Analysis & Modeling
      </text>

      <text x="260" y="445"
            text-anchor="middle"
            font-size="14"
            font-weight="bold">
        Applied Systems
      </text>

      <!-- LEFT CIRCLE DETAILS -->
      <text x="170" y="160"
            text-anchor="middle"
            font-size="13">

        <tspan x="170" dy="0">Field Surveying</tspan>
        <tspan x="170" dy="16">Remote Sensing</tspan>
        <tspan x="170" dy="16">Data Sourcing</tspan>

      </text>

      <!-- RIGHT CIRCLE DETAILS -->
      <text x="350" y="150"
            text-anchor="middle"
            font-size="13">

        <tspan x="350" dy="0">GIS (ArcGIS, QGIS)</tspan>
        <tspan x="350" dy="16">Python</tspan>
        <tspan x="350" dy="16">Spatial Analysis</tspan>
        <tspan x="350" dy="16">Climate modelling</tspan>
        <tspan x="350" dy="16">workflows</tspan>

      </text>

      <!-- BOTTOM CIRCLE DETAILS -->
      <text x="260" y="315"
            text-anchor="middle"
            font-size="13">

        <tspan x="260" dy="0">Policy</tspan>
        <tspan x="260" dy="16">Planning</tspan>
        <tspan x="260" dy="16">Environmental Systems</tspan>
        <tspan x="260" dy="16">Municipal Applications</tspan>

      </text>

      <!-- CENTER BOX -->
      <rect x="210" y="230" width="100" height="45"
            rx="8" fill="white" opacity="0.40"/>

      <text x="260" y="245"
            text-anchor="middle"
            font-size="11"
            font-weight="bold">

        <tspan x="260" dy="0">End-to-End</tspan>
        <tspan x="260" dy="13">Geospatial</tspan>
        <tspan x="260" dy="13">Workflows</tspan>

      </text>

    </svg>

  </div>

</div>

<!-- Preset banner: filled in by applyPreset() when the link ends in #field, #data, #planning, or #water -->
<div id="presetBanner" style="display:none; margin-top:16px; padding:12px 16px; background:#e7f7ef; border-left:5px solid #38C6D0; border-radius:6px; font-size:13px;"></div>

<!-- ═══════════════════════════════════════════════
     CAREER AT A GLANCE (stat strip)
════════════════════════════════════════════════ -->
<div id="statsStrip" style="display:flex; flex-wrap:wrap; gap:14px; margin-top:16px;"></div>

<!-- ═══════════════════════════════════════════════
     SKILLS / TOOLS / AWARDS PANEL
════════════════════════════════════════════════ -->
<div style="border:2px solid #333; border-radius:10px; padding:30px; margin-top:24px;">

  <h2 style="margin-top:0;">Core Skills & Technologies</h2>
  <p style="font-size:12px; color:#666; margin:4px 0 0;">Click a skill to see where I used it. Dashed skills are certificate-backed, with a project in progress.</p>
  <div id="skillsGrid"></div>

  <!-- AWARDS -->
  <h3>Awards</h3>

  <ul style="font-size:13px; padding-left:1.2em; color:#333; line-height:1.7;">

    <li>
      <b>Barry Goodison Graduate Scholarship</b>:
      Cryospheric Research Excellence (2023)
    </li>

    <li>
      <b>Lorne Russwurm Award</b>:
      Best BA Thesis in Urban Geography (2022)
    </li>

    <li>
      <b>Paul & Louise Puopolo Award</b>:
      Urban Planning Solution selected by City of Cambridge (2022)
    </li>

    <li>
      <b>CAG Undergraduate Award</b>:
      Canadian Association of Geographers (2022)
    </li>

    <li>
      <b>NSERC Undergraduate Student Research Award</b>:
      Lake ice thesis funding (2021)
    </li>

  </ul>

</div>

<!-- ═══════════════════════════════════════════════
     WHERE THE ANALYSIS MADE A DIFFERENCE
════════════════════════════════════════════════ -->
<div style="border:2px solid #333; border-radius:10px; padding:30px; margin-top:24px;">
  <h2 style="margin-top:0;">Where the Analysis Made a Difference</h2>
  <div id="impactGrid" style="display:flex; flex-wrap:wrap; gap:16px; margin-top:14px;"></div>
</div>

<!-- ═══════════════════════════════════════════════
     DASHBOARD
════════════════════════════════════════════════ -->
<div id="dashboardWrap" style="display:flex; flex-direction:column; margin-top:40px; border:2px solid #333; border-radius:10px; overflow:hidden;">

  <!-- VIEW TOGGLE -->
  <div class="view-toggle">
    <button class="view-btn active" id="btnMap"      onclick="switchView('map')">🗺 Map View</button>
    <button class="view-btn"        id="btnTimeline" onclick="switchView('timeline')">📅 Timeline</button>
  </div>

  <!-- MAP ROW -->
  <div id="mapRow" style="display:flex; height:780px;">

    <!-- LEFT PANEL -->
    <div id="leftPanel" style="width:160px; background:#fafafa; border-right:1px solid #ccc; padding:10px; overflow-y:auto; flex-shrink:0;">
      <button onclick="toggleLeftPanel()" style="margin-bottom:10px;">☰</button>
      <h4 style="margin:0 0 6px;">Filter</h4>
      <div style="margin-bottom:4px;">
        <label style="display:flex;align-items:center;gap:6px;cursor:pointer;font-size:13px;">
          <input type="checkbox" checked onchange="toggleCategory('Applied GIS')">
          <span style="display:inline-block;width:10px;height:10px;border-radius:50%;background:#F19FB4;flex-shrink:0;"></span>
          Applied GIS
        </label>
      </div>
      <div style="margin-bottom:4px;">
        <label style="display:flex;align-items:center;gap:6px;cursor:pointer;font-size:13px;">
          <input type="checkbox" checked onchange="toggleCategory('Technical')">
          <span style="display:inline-block;width:10px;height:10px;border-radius:50%;background:#90E2BF;flex-shrink:0;"></span>
          Technical
        </label>
      </div>
      <div style="margin-bottom:4px;">
        <label style="display:flex;align-items:center;gap:6px;cursor:pointer;font-size:13px;">
          <input type="checkbox" checked onchange="toggleCategory('Research')">
          <span style="display:inline-block;width:10px;height:10px;border-radius:50%;background:#38C6D0;flex-shrink:0;"></span>
          Research
        </label>
      </div>
      <hr>
      <h4 style="margin:6px 0;">Projects</h4>
      <div id="project-list"></div>
    </div>

    <!-- MAP -->
    <div id="map" style="flex:1; min-width:0;"></div>

    <!-- RIGHT PANEL -->
    <div id="infoPanel" style="width:260px; background:white; border-left:2px solid #333; padding:0; overflow-y:auto; display:none; flex-shrink:0; font-family:Arial,sans-serif;">
      <div id="panelContent"></div>
    </div>

  </div>

  <!-- TIMELINE PANEL -->
  <div id="timelinePanel">
    <h3 style="margin:0 0 24px; color:#333; font-size:15px; letter-spacing:.02em;">Career Arc</h3>
    <div class="tl-container">
      <div class="tl-line"></div>
      <div class="tl-items" id="tl-items"></div>
    </div>
    <!-- Detail card below timeline -->
    <div id="tl-detail" style="margin-top:32px; padding:18px 20px; background:white; border:1px solid #ddd; border-radius:8px; display:none; max-width:600px; font-size:13px;">
      <div id="tl-detail-content"></div>
    </div>
  </div>

  <!-- WEB VIEWER ROW -->
  <div id="webViewerPanel" style="display:none; border-top:2px solid #333; flex-direction:column; height:500px;">
    <div style="display:flex; align-items:center; gap:10px; padding:8px 12px; background:#4a4a4a; color:white; font-family:Arial,sans-serif; font-size:13px; flex-shrink:0;">
      <span id="viewerLabel" style="flex:1; white-space:nowrap; overflow:hidden; text-overflow:ellipsis;">Web Preview</span>
      <a id="viewerOpenBtn" href="#" target="_blank" rel="noopener" style="color:#90E2BF; text-decoration:none; white-space:nowrap; font-size:12px;">↗ Open in new tab</a>
      <button onclick="closeViewer()" style="background:none; border:none; color:white; font-size:16px; cursor:pointer; padding:0; line-height:1;">✕</button>
    </div>
    <div id="viewerFallback" style="display:none; padding:24px; font-family:Arial,sans-serif; font-size:13px; color:#555; text-align:center; background:#f9f9f9; border-bottom:1px solid #ddd;">
      <div style="font-size:28px; margin-bottom:10px;">🔒</div>
      <p style="margin:0 0 6px;"><b>This site can't be previewed here.</b></p>
      <p style="margin:0 0 14px; font-size:12px; color:#888;">Many sites block iframe embedding for security reasons.</p>
      <a id="fallbackLink" href="#" target="_blank" rel="noopener"
         style="display:inline-block; background:#38C6D0; color:white; padding:8px 18px; border-radius:6px; text-decoration:none; font-size:13px; font-weight:bold;">
        Open in New Tab →
      </a>
    </div>
    <iframe id="webViewerFrame" src="about:blank"
      style="flex:1; border:none; width:100%;"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
      allowfullscreen title="Project preview">
    </iframe>
  </div>

</div>

<!-- ── Floating export button ── -->
<button id="exportBtn" onclick="exportPDF()">⬇ Download Summary PDF</button>

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script>
document.addEventListener("DOMContentLoaded", function () {
try {

/* ════════════════════════════════════════════
   PROJECT DATA
   Keep each skills list to the 5 or 6 that matter most.
   Dates match the resume.
════════════════════════════════════════════ */
const projects = [
  {
    title: "Assessment of ERA5-Land Lake Ice Variables (MSc Thesis)",
    category: "Research",
    subcategory: "Climate & Cryosphere Analysis",
    year: 2025,
    dateRange: "Sep 2022 to Dec 2025",
    summary: "Evaluated ERA5-Land lake ice variables against satellite observations across seven Canadian lakes using spatial and statistical analysis workflows. Assessed freeze-up, break-up, ice fraction, and surface temperature variability to identify environmental model biases and climate system trends.",
    description: "Evaluated ERA5-Land lake ice fraction, timing, and surface temperature against satellite observations across seven Canadian lakes (2004 to 2023). Quantified spatial and temporal biases using MBE and MAE during freeze-up and break-up periods. Identified key model limitations related to snow cover omission and partial ice representation, with implications for climate modelling accuracy.",
    result: "Quantified model-observation bias across seven lakes and 20 years; identified snow cover omission and partial ice representation as key limitations.",
    skills: ["Spatial Statistics (MBE, MAE)", "ArcGIS Pro", "QGIS", "Python", "Satellite Remote Sensing", "Cartographic Visualization"],
    context: ["MSc Geography thesis project", "Multi-year environmental dataset analysis (2004 to 2023)", "Combined ERA5-Land + IMS satellite observations", "Focused on cryosphere and environmental systems interpretation"],
    links: [
      { url: "https://uwspace.uwaterloo.ca/items/b983d97f-d2ec-4c1a-a6d0-82be963c476a", label: "Thesis (UW Space)" },
      { url: "https://ari-ana-m.github.io/lake-ice-animations/", label: "Supplementary Animations" }
    ],
    locations: [
      { name: "Great Bear Lake",  coords: [66, -121] },
      { name: "Great Slave Lake", coords: [61, -114] },
      { name: "Lake Athabasca",   coords: [59, -109] },
      { name: "Lake Winnipeg",    coords: [52, -97] },
      { name: "Lake Superior",    coords: [47.7, -87.5] },
      { name: "Lake Huron",       coords: [45, -82.4] },
      { name: "Lake Erie",        coords: [42.2, -81.2] }
    ]
  },
  {
    title: "Research Analyst: Environmental & Climate Data Analysis",
    category: "Technical",
    subcategory: "Research Analytics",
    year: 2023,
    dateRange: "Jan 2023 to Apr 2023",
    summary: "Conducted a structured scoping review of climate resilience research using SQL-based workflows, and produced graphs, statistical summaries, and workflow diagrams that supported a peer-reviewed publication.",
    description: "Conducted a scoping review of 50+ studies on climate resilience in smallholder agricultural systems. Extracted and validated study-level data using SQL-based querying and systematic workflows to identify trends across dominant intervention strategies. Produced graphs, statistical summaries, and workflow diagrams for interdisciplinary research reporting.",
    result: "Findings were synthesized into graphs and workflow diagrams that supported a peer-reviewed publication.",
    skills: ["SQL Querying", "Data Validation & QA/QC", "Statistical Summaries", "Research Synthesis", "Scientific Visualization"],
    context: ["University of Waterloo research role", "Supported interdisciplinary environmental research", "Focused on structured analytical workflows and reporting"],
    links: [
      { url: "https://ecologyandsociety.org/vol29/iss3/art22/", label: "Published Article (Ecology & Society)" }
    ],
    locations: [{ name: "Africa" }]
  },
  {
    title: "Lake Ice Projections under Climate Scenarios (Undergraduate Thesis)",
    category: "Research",
    subcategory: "Climate Projection Analysis",
    year: 2022,
    dateRange: "Sep 2021 to Apr 2022",
    summary: "Analyzed projected air temperature and lake ice conditions for two large northern lakes under multiple RCP climate scenarios.",
    description: "Analyzed projected air temperature and surface water and ice conditions for Great Bear and Great Slave Lakes under multiple RCP climate scenarios, using rolling averages and statistical summaries. Conducted trend and scenario analysis to assess climate-driven changes in ice duration and thickness, and produced cartographic and statistical outputs summarizing projected change.",
    result: "Scenario-based summaries of projected change in ice duration and thickness for Great Bear and Great Slave Lakes.",
    skills: ["Climate Projections", "Scenario & Trend Analysis", "Python", "Statistical Summaries", "Cartographic Outputs"],
    context: ["Undergraduate honours thesis, Wilfrid Laurier University", "Funded by an NSERC Undergraduate Student Research Award (2021)", "Linked to the lake ice work in the ReSEC group"],
    locations: [
      { name: "Great Bear Lake",  coords: [66, -121] },
      { name: "Great Slave Lake", coords: [61, -114] }
    ]
  },
  {
    title: "Student Planner: Housing Policy & GIS Analysis",
    category: "Applied GIS",
    subcategory: "Planning",
    year: 2022,
    dateRange: "Sep 2021 to Sep 2022",
    summary: "Supported municipal housing and planning analysis through GIS-based spatial workflows, census integration, and cartographic visualization. Produced stakeholder-focused planning outputs supporting housing and development assessment.",
    description: "Integrated GIS, census, and land-use datasets into planning maps for the City of Cambridge, and maintained corporate GIS databases cross-referenced against SharePoint records. Applied spatial analysis to identify priority areas where zoning and development policy change would have the greatest impact. Presented maps and findings to planning staff. Recognized with the Paul & Louise Puopolo Award.",
    result: "Maps and findings presented to planning staff; the planning solution was selected by the City of Cambridge.",
    skills: ["GIS Spatial Analysis", "Census Data Integration", "Cartography", "ArcGIS Pro", "Stakeholder Communication", "GIS Database Maintenance"],
    context: ["Collaboration with City of Cambridge", "Applied GIS within municipal planning context", "Contributed to award-recognized planning project"],
    links: [
      { url: "https://www.cambridgetimes.ca/news/housing-affordability-is-a-human-rights-issue-wilfrid-laurier-students-exploring-housing-concerns-with-city/article_c289ca4b-507c-5777-b38d-90a1d676d692.html", label: "News Article (Interview)" },
      { url: "data/EcoVital-Final-Deliverable-1.pdf", label: "Final Deliverable (PDF)" }
    ],
    locations: [{ name: "Cambridge", coords: [43.40175, -80.32597] }]
  },
  {
    title: "Remote Sensing & GIS Assistant: Climate Change Projection (ReSEC)",
    category: "Technical",
    subcategory: "Remote Sensing",
    year: 2021,
    dateRange: "May 2021 to Sep 2021",
    summary: "Built reproducible Python pipelines with embedded QA/QC checkpoints to turn raw climate model output into analysis-ready lake ice inputs, and produced publication-quality maps.",
    description: "Led an NSERC-funded independent research project projecting lake ice phenology for Great Bear and Great Slave Lake under multiple RCP scenarios, running the CLIMoGrid thermodynamic model on MRI-CGCM3 climate outputs. Georeferenced open climate projection data into gridded spatial datasets using original model metadata. Built reproducible Python pipelines with QA/QC checkpoints and produced cartographic outputs of projected surface water and ice conditions.",
    result: "Analysis-ready hydrological inputs and publication-quality maps of projected surface water and ice conditions.",
    skills: ["Python Automation", "Georeferencing", "Reproducible Pipelines", "QA/QC Workflows", "Climate Projections", "Cartography"],
    context: ["Remote Sensing of Environmental Change (ReSEC) group", "Supported climate scenario and lake ice research", "Integrated modeled climate datasets into GIS"],
    locations: [
      { name: "Great Bear Lake",  coords: [66, -121] },
      { name: "Great Slave Lake", coords: [61, -114] }
    ]
  },
  {
    title: "Geospatial Field Assistant: Coastal & Environmental Monitoring",
    category: "Applied GIS",
    subcategory: "Field Data Collection",
    year: 2021,
    dateRange: "Jun 2021 to Oct 2021",
    summary: "Collected and validated coastal spatial data using RTK GNSS, GPS, and total stations, and integrated field observations into GIS analysis and mapping products for environmental monitoring.",
    description: "Collected coastal morphology and surface data using RTK GNSS, GPS, and total stations at three Ontario shoreline sites, supporting longitudinal erosion and water resource monitoring. Performed QA/QC validation on positional and environmental data before GIS integration. Co-prepared technical reports and map-based deliverables for an external consulting client.",
    result: "Validated field data integrated into GIS for erosion and water resource monitoring, with technical reports for a consulting client.",
    skills: ["RTK GNSS Surveying", "Total Station", "Spatial QA/QC", "Coastal Monitoring", "GIS Integration", "Technical Reporting"],
    context: ["Wilfrid Laurier University and Zuzek Inc.", "Worked across multiple Ontario coastal environments", "Supported environmental and hydrological monitoring activities"],
    locations: [
      { name: "Sauble Beach",     coords: [44.6296,  -81.26508] },
      { name: "Burlington Beach", coords: [43.31523, -79.80701] },
      { name: "Wasaga Beach",     coords: [44.52372, -80.0033] }
    ]
  },
  {
    title: "Invasive Species Monitoring: Lake Bernard Phragmites",
    category: "Applied GIS",
    subcategory: "Remote Sensing",
    year: 2021,
    dateRange: "May 2021",
    summary: "Mapped invasive Phragmites distribution using NDVI, image classification, and spatial statistics to support ecological monitoring and management decisions.",
    description: "Classified remote sensing imagery and Ontario GeoHub open data to distinguish vegetation, water, soil, and invasive Phragmites australis. Applied NDVI, kernel density estimation, buffer, and nearest-neighbour analysis to model potential spread, and produced cartographic products for stakeholder reporting.",
    result: "Spread analysis supported field management decisions; findings presented by invitation at the Students of Phrag webinar series.",
    skills: ["Image Classification", "NDVI Analysis", "Kernel Density Analysis", "Nearest-Neighbour Analysis", "UAV Imagery", "Stakeholder Reporting"],
    context: ["Great Lakes Phragmites Collaborative project", "Combined remote sensing with ecological assessment", "Presented findings through stakeholder-oriented communication"],
    links: [
      { url: "https://www.youtube.com/watch?v=5Io_79IMANw", label: "Presentation Video" }
    ],
    locations: [{ name: "Bernard Lake", coords: [45.72458, -79.3857] }]
  }
];

/* ════════════════════════════════════════════
   AWARDS DATA
════════════════════════════════════════════ */
const awards = [
  { year: 2023, title: "Barry Goodison Graduate Scholarship for Cryospheric Research", body: "University of Waterloo", note: "Presented to graduate student who has demonstrated excellence in Cryospheric research." },
  { year: 2022, title: "Lorne Russwurm Award", body: "Wilfrid Laurier University", note: "Presented to a Geography/Environmental student who produces the best BA thesis in urban geography." },
  { year: 2022, title: "Paul & Louise Puopolo Award", body: "City of Cambridge", note: "Presented to the student group whose urban planning solution was selected by the City of Cambridge." },
  { year: 2022, title: "Canadian Association of Geographers Undergraduate Award", body: "CAG", note: "Presented to outstanding graduating students with a Geography honours/major at a national level." },
  { year: 2021, title: "NSERC Undergraduate Student Research Award", body: "NSERC", note: "Received funding for undergraduate thesis research on lake ice projections based on climate projections." }
];

/* ════════════════════════════════════════════
   SKILLS DATA
   e: keywords matched against project titles (click a skill to open its project)
   Skills with no project get a dashed border and a note.
════════════════════════════════════════════ */
const skillGroups = [
  { label: "Core: used in project and job work", cls: "expert", skills: [
    { n: "ArcGIS Pro", e: ["ERA5", "Student Planner", "Phragmites"] },
    { n: "QGIS", e: ["ERA5"] },
    { n: "Remote sensing & image classification", e: ["Phragmites", "ERA5", "ReSEC"] },
    { n: "Spatial analysis", e: ["Student Planner", "Phragmites"] },
    { n: "Cartography", e: ["ERA5", "Student Planner"] },
    { n: "Python (ArcPy, pandas)", e: ["ReSEC", "ERA5"] },
    { n: "SQL", e: ["Research Analyst"] },
    { n: "QA/QC workflows", e: ["Field Assistant", "ReSEC"] },
    { n: "RTK GNSS & field data collection", e: ["Field Assistant"] },
    { n: "Spatial statistics (MBE, MAE)", e: ["ERA5"] }
  ]},
  { label: "Working knowledge", cls: "proficient", skills: [
    { n: "Geodatabase design & metadata", e: ["Student Planner"] },
    { n: "UAV imagery integration", e: ["Phragmites"] },
    { n: "Leaflet.js & GeoJSON", e: [], note: "Built into this portfolio" },
    { n: "ArcGIS Online & Enterprise", e: [] },
    { n: "Survey123", e: [], note: "Esri certificate; demo project in progress" },
    { n: "Experience Builder", e: [], note: "Esri certificate; demo project in progress" },
    { n: "FME", e: [], note: "LinkedIn Learning certificate" },
    { n: "Power BI", e: [], note: "Microsoft Press certificate" }
  ]},
  { label: "Currently building", cls: "familiar", skills: [
    { n: "Field Maps & Dashboards", e: [] },
    { n: "JavaScript", e: [] },
    { n: "GeoAI / deep learning in ArcGIS Pro", e: [], note: "Esri course completed; applying it to a project" }
  ]}
];

/* ════════════════════════════════════════════
   EMPLOYER / AUDIENCE PRESET LINKS
   Share  .../GIS_Portfolio/#field   .../#data   .../#planning   .../#water
════════════════════════════════════════════ */
const presets = {
  field:    { key: "Field Assistant", text: "Field-to-map work: RTK GNSS, GPS, and total station monitoring at three Ontario shoreline sites." },
  data:     { key: "ReSEC",           text: "Data pipelines: reproducible Python workflows with embedded QA/QC, built for analysis-ready outputs." },
  planning: { key: "Student Planner", text: "Applied GIS for municipal planning: maps and findings presented to planning staff." },
  water:    { key: "ERA5",            text: "Surface water and lake ice analysis across seven Canadian lakes over 20 years." }
};

/* ════════════════════════════════════════════
   CONSTANTS
════════════════════════════════════════════ */
const CATEGORY_COLORS = {
  "Research":    { color: "#38C6D0", fillOpacity: 0.25, weight: 1.2 },
  "Technical":   { color: "#90E2BF", fillOpacity: 0.45, weight: 1.5 },
  "Applied GIS": { color: "#F19FB4", fillOpacity: 0.35, weight: 1.2 }
};

const POLYGON_LAKES = new Set([
  "Lake Superior", "Lake Huron", "Lake Erie", "Lake Winnipeg",
  "Lake Athabasca", "Great Bear Lake", "Great Slave Lake", "Bernard Lake", "Africa"
]);

const AFRICA_COUNTRIES = [
  "Burkina Faso","Congo","Ethiopia","Gambia","Ghana","Kenya","Mali",
  "Mozambique","Niger","Nigeria","Senegal","South Africa","Uganda","Zambia","Zimbabwe","Rwanda"
];

/* ════════════════════════════════════════════
   MAP SETUP
════════════════════════════════════════════ */
const mapDiv  = document.getElementById("map");
const listDiv = document.getElementById("project-list");

var map = L.map('map').setView([52, -90], 4);
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
  attribution: '© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
  subdomains: 'abc', maxZoom: 19
}).addTo(map);

const categoryLayers = {
  "Applied GIS": L.layerGroup().addTo(map),
  "Technical":   L.layerGroup().addTo(map),
  "Research":    L.layerGroup().addTo(map)
};

const allMarkers       = [];
const polygonInstances = {};
const geojsonCache     = {};

const lakeFiles = {
  "Lake Superior":   "data/Superior.geojson",
  "Lake Huron":      "data/Huron.geojson",
  "Lake Erie":       "data/Erie.geojson",
  "Lake Winnipeg":   "data/Winnipeg.geojson",
  "Lake Athabasca":  "data/Athabasca.geojson",
  "Great Bear Lake": "data/GBL.geojson",
  "Great Slave Lake":"data/GSL.geojson",
  "Bernard Lake":    "data/Bernard.geojson",
  "Africa":          "data/afr_focus_FeaturesToJSON.geojson"
};

let loadedCount = 0;
const totalFiles = Object.keys(lakeFiles).length;

Object.entries(lakeFiles).forEach(([name, path]) => {
  fetch(path)
    .then(res => { if (!res.ok) throw new Error("Missing"); return res.json(); })
    .then(data => { geojsonCache[name] = data; })
    .catch(() => { console.warn("Skipping polygon:", name); })
    .finally(() => { loadedCount++; if (loadedCount === totalFiles) applyPolygonsFromCache(); });
});

function applyPolygonsFromCache() {
  projects.forEach(project => {
    project.locations.forEach(loc => {
      if (!POLYGON_LAKES.has(loc.name) || !geojsonCache[loc.name]) return;
      const existing = (polygonInstances[loc.name] || []).find(e => e.project === project);
      if (existing) return;
      const style = CATEGORY_COLORS[project.category];
      const poly = L.geoJSON(geojsonCache[loc.name], {
        style: { color: style.color, weight: style.weight, fillColor: style.color, fillOpacity: style.fillOpacity }
      });
      poly.addTo(categoryLayers[project.category]);
      if (project.category === "Technical") poly.bringToFront();
      poly.on("click", () => selectProject(project));
      if (!polygonInstances[loc.name]) polygonInstances[loc.name] = [];
      polygonInstances[loc.name].push({ poly, project });
      if (!project.geoLayers) project.geoLayers = [];
      project.geoLayers.push(poly);
    });
  });
  // Polygons are ready, so a preset link can now zoom to the right project
  applyPreset();
}

/* ── Build sidebar + markers ── */
projects.forEach(project => {
  project.markerLayers = [];
  project.geoLayers    = [];

  // Sidebar entry (simplified)
  const div = document.createElement("div");

  div.innerHTML = `
    <span class="project-link">${project.title}</span>
  `;

  div.querySelector(".project-link").onclick = () => selectProject(project);

  listDiv.appendChild(div);

  const ul = document.createElement("ul");
  ul.style.cssText = "font-size:11px;color:#666;margin:0 0 10px;padding-left:1em;";

  project.locations.forEach(loc => {
    if (!POLYGON_LAKES.has(loc.name)) {
      const style = CATEGORY_COLORS[project.category];
      const marker = L.circleMarker(loc.coords, {
        radius: 8, fillColor: style.color, color: "#fff",
        weight: style.weight, fillOpacity: style.fillOpacity
      }).addTo(categoryLayers[project.category]);
      marker._projectCategory = project.category;
      marker.on("click", () => selectProject(project));
      project.markerLayers.push(marker);
      allMarkers.push(marker);
    }
    const li = document.createElement("li");
    li.innerText = loc.name;
    ul.appendChild(li);
  });
  listDiv.appendChild(ul);
});

/* ════════════════════════════════════════════
   HIGHLIGHT / SELECT
════════════════════════════════════════════ */
function resetHighlight() {
  allMarkers.forEach(m => {
    const style = CATEGORY_COLORS[m._projectCategory];
    m.setStyle({ radius: 8, color: "#fff", weight: style.weight, fillColor: style.color, fillOpacity: style.fillOpacity });
  });
  projects.forEach(project => {
    (project.markerLayers || []).forEach(m => {
      const style = CATEGORY_COLORS[project.category];
      m.setStyle({ radius: 8, color: "#fff", weight: style.weight, fillColor: style.color, fillOpacity: style.fillOpacity });
    });
    (project.geoLayers || []).forEach(poly => {
      const style = CATEGORY_COLORS[project.category];
      poly.setStyle({ color: style.color, weight: style.weight, fillColor: style.color, fillOpacity: style.fillOpacity });
    });
  });
}

function selectProject(project) {
  resetHighlight();
  const groupLayers = [];

  (project.markerLayers || []).forEach(m => {
    m.setStyle({ radius: 11, color: "#FFD700", weight: 2.5, fillColor: "#FFD700", fillOpacity: 1 });
    groupLayers.push(m);
  });
  (project.geoLayers || []).forEach(poly => {
    poly.setStyle({ color: "#FFD700", weight: 3, fillColor: "#FFD700", fillOpacity: 0.45 });
    groupLayers.push(poly);
  });

  const validLayers = groupLayers.filter(l => l && typeof l.getBounds !== "undefined");
  if (validLayers.length > 0) {
    const group = L.featureGroup(validLayers);
    const bounds = group.getBounds();
    if (bounds.isValid()) map.fitBounds(bounds, { paddingTopLeft: [20, 20], paddingBottomRight: [280, 20] });
  }

  openPanel(project);

  // Keep timeline in sync
  document.querySelectorAll(".tl-item").forEach(el => {
    el.classList.toggle("selected", el.dataset.title === project.title);
  });
  showTimelineDetail(project);
}

/* ════════════════════════════════════════════
   RIGHT PANEL
════════════════════════════════════════════ */
function openPanel(project) {
  document.getElementById("infoPanel").style.display = "block";
  const color   = CATEGORY_COLORS[project.category];
  const locList = project.locations.map(l => {
    if (l.name === "Africa") return AFRICA_COUNTRIES.map(c => `<li>${c}</li>`).join("");
    return `<li>${l.name}</li>`;
  }).join("");

  const skillsHTML = (project.skills || []).map(s => `<span class="skill-tag">${s}</span>`).join(" ");

  const contextHTML = (project.context || []).length > 0
    ? `<tr><td>Context</td><td><ul style="margin:0; padding-left:1.2em;">${project.context.map(c => `<li>${c}</li>`).join("")}</ul></td></tr>`
    : "";

  const resultHTML = project.result
    ? `<tr><td>Result</td><td>${project.result}</td></tr>`
    : "";

  let linkRow = "";
  if (project.links && project.links.length > 0) {
    linkRow = project.links.map(link => {
      const safeTitle = project.title.replace(/'/g, "\\'");
      const safeLabel = link.label.replace(/'/g, "\\'");
      return `
        <div style="border-top:1px solid #ddd;">
          <div style="padding:8px 12px; font-size:12px; font-weight:bold;">${link.label}</div>
          <a class="arcgis-popup-link" href="${link.url}" target="_blank" rel="noopener">🔗 Open in New Tab →</a>
          <button class="preview-btn" onclick="openViewer('${link.url}','${safeTitle}: ${safeLabel}')">▶ Preview Below</button>
        </div>`;
    }).join("");
  } else {
    linkRow = `<p style="padding:10px 12px; font-size:12px; color:#888; margin:0;">No link available for this project.</p>`;
  }

  document.getElementById("panelContent").innerHTML = `
    <div class="arcgis-popup">
      <div class="arcgis-popup-header">
        <h3>${project.title}</h3>
        <button onclick="closePanel()">✕</button>
      </div>
      <div class="arcgis-popup-subheader" style="background:${color.color};">${project.category}${project.subcategory ? " · " + project.subcategory : ""}</div>
      ${project.summary ? `<div style="padding:10px 12px; font-size:12px; color:#444; border-bottom:1px solid #eee; line-height:1.5; font-style:italic;">${project.summary}</div>` : ""}
      <table class="arcgis-table">
        <tr><td>Period</td><td>${project.dateRange || project.year}</td></tr>
        <tr><td>Details</td><td>${project.description}</td></tr>
        ${resultHTML}
        <tr><td>Skills</td><td>${skillsHTML}</td></tr>
        ${contextHTML}
        <tr><td>Locations</td><td><ul style="margin:0; padding-left:1.2em;">${locList}</ul></td></tr>
      </table>
      ${linkRow}
    </div>`;
}

function closePanel() {
  document.getElementById("infoPanel").style.display = "none";
  resetHighlight();
}


/* ════════════════════════════════════════════
   TIMELINE
════════════════════════════════════════════ */
function buildTimeline() {
  const container = document.getElementById("tl-items");
  const sorted    = [...projects].sort((a, b) => a.year - b.year);

  sorted.forEach(project => {
    const color = CATEGORY_COLORS[project.category].color;
    const skillPills = (project.skills || []).slice(0, 3)
      .map(s => `<span class="skill-tag" style="font-size:9px;">${s}</span>`).join("");

    const item = document.createElement("div");
    item.className    = "tl-item";
    item.dataset.title = project.title;
    item.innerHTML = `
      <div class="tl-year">${project.year}</div>
      <div class="tl-dot" style="background:${color};"></div>
      <div class="tl-card">
        <div class="tl-cat" style="color:${color};">${project.category}</div>
        <div style="font-weight:bold; font-size:11px; margin-bottom:4px;">${project.title}</div>
        <div class="tl-skills">${skillPills}</div>
      </div>`;
    item.onclick = () => {
      document.querySelectorAll(".tl-item").forEach(el => {
        el.classList.remove("selected");
      });

      item.classList.add("selected");

      showTimelineDetail(project);

      selectProject(project);
    };
    container.appendChild(item);
  });
}

function showTimelineDetail(project) {
  const detail  = document.getElementById("tl-detail");
  const content = document.getElementById("tl-detail-content");
  const color   = CATEGORY_COLORS[project.category].color;
  const skillPills = (project.skills || []).map(s => `<span class="skill-tag">${s}</span>`).join(" ");
  const linkList = (project.links || []).map(l =>
    `<a href="${l.url}" target="_blank" rel="noopener" style="color:#0079c1; font-size:12px; display:block; margin-top:4px;">🔗 ${l.label}</a>`
  ).join("");
  const contextList = (project.context || []).length > 0
    ? `<ul style="margin:8px 0 0; padding-left:1.3em; font-size:11px; color:#666;">${project.context.map(c => `<li>${c}</li>`).join("")}</ul>`
    : "";

  content.innerHTML = `
    <div style="display:flex; align-items:center; gap:10px; margin-bottom:8px;">
      <span style="display:inline-block; width:12px; height:12px; border-radius:50%; background:${color}; flex-shrink:0;"></span>
      <span style="font-size:11px; font-weight:bold; text-transform:uppercase; color:${color};">${project.category}${project.subcategory ? " · " + project.subcategory : ""}</span>
      <span style="font-size:11px; color:#999; margin-left:auto;">${project.dateRange || project.year}</span>
    </div>
    <div style="font-weight:bold; font-size:14px; margin-bottom:6px;">${project.title}</div>
    ${project.summary ? `<div style="font-size:12px; color:#444; margin-bottom:8px; font-style:italic; line-height:1.5;">${project.summary}</div>` : ""}
    <div style="font-size:12px; color:#555; margin-bottom:10px;">${project.description}</div>
    ${project.result ? `<div style="font-size:12px; color:#333; margin-bottom:10px;"><b>Result:</b> ${project.result}</div>` : ""}
    <div style="margin-bottom:6px;">${skillPills}</div>
    ${contextList}
    ${linkList}`;
  detail.style.display = "block";
}

buildTimeline();

/* ════════════════════════════════════════════
   CAREER AT A GLANCE
   Figures come from the thesis and resume, so they are stated directly.
════════════════════════════════════════════ */
function buildStatsStrip() {
  const strip = document.getElementById("statsStrip");
  if (!strip) return;

  const stats = [
    { value: "7",       label: "Canadian lakes assessed",            color: "#38C6D0" },
    { value: "20 yrs",  label: "of satellite and reanalysis data",   color: "#90E2BF" },
    { value: awards.length, label: "Awards & Recognitions",         color: "#F19FB4" },
    { value: "$47K",    label: "funding secured (EGSA)",             color: "#38C6D0" }
  ];

  strip.innerHTML = stats.map(s => `
    <div style="flex:1; min-width:140px; background:${s.color}; border-radius:10px; padding:16px 18px; color:#1c1c1c;">
      <div style="font-size:26px; font-weight:bold; line-height:1;">${s.value}</div>
      <div style="font-size:12px; margin-top:6px; font-weight:600;">${s.label}</div>
    </div>`).join("");
}
buildStatsStrip();

/* ════════════════════════════════════════════
   SKILLS SECTION
════════════════════════════════════════════ */
function buildSkills() {
  const grid = document.getElementById("skillsGrid");
  if (!grid) return;
  skillGroups.forEach(g => {
    const h = document.createElement("h3");
    h.style.marginTop = "18px";
    h.textContent = g.label;
    grid.appendChild(h);
    const wrap = document.createElement("div");
    g.skills.forEach(s => {
      const pill = document.createElement("span");
      pill.className = "skill-pill " + g.cls;
      pill.textContent = s.n;
      const hits = (s.e || []).map(k => projects.find(p => p.title.includes(k))).filter(Boolean);
      if (hits.length) {
        const open = () => {
          selectProject(hits[0]);
          document.getElementById("dashboardWrap").scrollIntoView({ behavior: "smooth" });
        };
        pill.style.cursor = "pointer";
        pill.setAttribute("role", "button");
        pill.tabIndex = 0;
        pill.title = "Used in: " + hits.map(p => p.title).join("; ");
        pill.onclick = open;
        pill.onkeydown = ev => { if (ev.key === "Enter" || ev.key === " ") { ev.preventDefault(); open(); } };
      } else {
        pill.style.borderStyle = "dashed";
        pill.title = s.note || "Certificate-backed; project in progress";
      }
      wrap.appendChild(pill);
    });
    grid.appendChild(wrap);
  });
}
buildSkills();

/* ════════════════════════════════════════════
   WHERE THE ANALYSIS MADE A DIFFERENCE
   Bullets are drawn from each project's own fields above.
════════════════════════════════════════════ */
function buildImpactGrid() {
  const grid = document.getElementById("impactGrid");
  if (!grid) return;

  const highlights = [
    {
      title: "MSc Thesis: ERA5-Land Lake Ice Assessment",
      tag: "Model Evaluation",
      bullets: [
        "Quantified spatial and temporal biases using MBE and MAE across freeze-up and break-up periods",
        "Identified model limitations tied to snow cover omission and partial ice representation"
      ]
    },
    {
      title: "Invasive Species Monitoring: Lake Bernard Phragmites",
      tag: "Field & Ecological Decisions",
      bullets: [
        "Modelled potential invasive spread using kernel density, buffer, and nearest-neighbour analysis",
        "Turned classified imagery and NDVI results into stakeholder reporting; presented by invitation at the Students of Phrag webinar series"
      ]
    },
    {
      title: "Student Planner: City of Cambridge Housing Policy",
      tag: "Policy & Planning",
      bullets: [
        "Integrated GIS and census data to support housing and development planning maps",
        "Presented maps and findings to planning staff; recognized with the Paul & Louise Puopolo Award"
      ]
    }
  ];

  grid.innerHTML = highlights.map(h => `
    <div style="flex:1; min-width:260px; border:1px solid #ddd; border-left:5px solid #38C6D0; border-radius:8px; padding:16px 18px; background:#fafafa;">
      <div style="font-size:11px; font-weight:bold; text-transform:uppercase; letter-spacing:.03em; color:#38C6D0; margin-bottom:6px;">${h.tag}</div>
      <div style="font-weight:bold; font-size:13px; margin-bottom:8px;">${h.title}</div>
      <ul style="margin:0; padding-left:1.2em; font-size:12px; color:#444; line-height:1.6;">
        ${h.bullets.map(b => `<li>${b}</li>`).join("")}
      </ul>
    </div>`).join("");
}
buildImpactGrid();

/* ════════════════════════════════════════════
   PRESET LINKS (#field, #data, #planning, #water)
════════════════════════════════════════════ */
function applyPreset() {
  const p = presets[location.hash.replace("#", "")];
  if (!p) return;
  const banner = document.getElementById("presetBanner");
  banner.textContent = p.text;
  banner.style.display = "block";
  const proj = projects.find(x => x.title.includes(p.key));
  if (proj) selectProject(proj);
}
window.addEventListener("hashchange", applyPreset);

/* ════════════════════════════════════════════
   VIEW TOGGLE  (Map and Timeline)
════════════════════════════════════════════ */
window.switchView = function(view) {
  const mapRow   = document.getElementById("mapRow");
  const tlPanel  = document.getElementById("timelinePanel");
  const btnMap   = document.getElementById("btnMap");
  const btnTL    = document.getElementById("btnTimeline");

  if (view === "map") {
    mapRow.style.display  = "flex";
    tlPanel.style.display = "none";
    btnMap.classList.add("active");
    btnTL.classList.remove("active");
    map.invalidateSize();
  } else {
    mapRow.style.display  = "none";
    tlPanel.style.display = "block";
    btnMap.classList.remove("active");
    btnTL.classList.add("active");
  }
};

/* ════════════════════════════════════════════
   PDF EXPORT
════════════════════════════════════════════ */
window.exportPDF = function() {
  const rows = projects
    .slice()
    .sort((a, b) => a.year - b.year)
    .map(p => {
      const links   = (p.links || []).map(l => `<a href="${l.url}">${l.label}</a>`).join(" · ");
      const skills  = (p.skills || []).join(", ");
      const locs    = p.locations.map(l => l.name === "Africa" ? "Africa (multi-country)" : l.name).join(", ");
      const context = (p.context || []).length > 0
        ? `<ul style="margin:4px 0; padding-left:1.3em; font-size:11px; color:#666;">${p.context.map(c => `<li>${c}</li>`).join("")}</ul>`
        : "";
      return `
        <div style="border:1px solid #ddd; border-radius:8px; padding:14px 18px; margin-bottom:14px; page-break-inside:avoid;">
          <div style="font-weight:bold; font-size:13px; margin-bottom:2px;">${p.title}</div>
          <div style="font-size:11px; color:#888; margin-bottom:6px;">${p.category}${p.subcategory ? " · " + p.subcategory : ""} · ${p.dateRange || p.year}</div>
          ${p.summary ? `<div style="font-size:12px; color:#333; font-style:italic; margin-bottom:6px; line-height:1.5;">${p.summary}</div>` : ""}
          <div style="font-size:12px; color:#444; margin-bottom:6px;">${p.description}</div>
          ${p.result ? `<div style="font-size:12px; color:#333; margin-bottom:6px;"><b>Result:</b> ${p.result}</div>` : ""}
          <div style="font-size:11px; color:#666; margin-bottom:4px;"><b>Skills:</b> ${skills}</div>
          <div style="font-size:11px; color:#666; margin-bottom:4px;"><b>Locations:</b> ${locs}</div>
          ${context ? `<div style="font-size:11px; color:#666;"><b>Context:</b>${context}</div>` : ""}
          ${links ? `<div style="font-size:11px; margin-top:4px;"><b>Links:</b> ${links}</div>` : ""}
        </div>`;
    }).join("");

  const awardRows = awards.map(a => `
    <div style="padding: 6px 0; border-bottom:1px solid #eee; font-size:12px;">
      <span style="font-weight:bold;">${a.title}</span>
      <span style="color:#888; margin-left:6px;">(${a.year})</span><br>
      <span style="color:#555; font-size:11px;">${a.note}</span>
    </div>`).join("");

  const html = `<!DOCTYPE html><html><head><meta charset="UTF-8">
    <title>GIS Portfolio Summary</title>
    <style>
      body { font-family: Arial, sans-serif; padding: 32px 40px; max-width: 720px; margin: 0 auto; color: #222; }
      h1 { font-size: 20px; margin-bottom: 4px; }
      h2 { font-size: 15px; margin: 28px 0 10px; border-bottom: 2px solid #333; padding-bottom: 4px; }
      p  { font-size: 13px; color: #555; margin-top: 0; }
      a  { color: #0079c1; }
      @media print { body { padding: 16px; } }
    </style>
    </head><body>
    <h1>Ariana Mansingh: GIS & Spatial Data Portfolio</h1>
    <p>Environmental & Geospatial Analyst | Spatial Analysis | Climate Data | Environmental Systems<br>
    Pursuing Geoscientist-in-Training (GIT) registration with Professional Geoscientists Ontario (PGO)<br>
    ariana.mansingh.pro@gmail.com | linkedin.com/in/ariana-mansingh</p>
    <hr style="margin: 16px 0 20px;">
    <h2>Projects & Experience</h2>
    ${rows}
    <h2>Awards & Recognition</h2>
    ${awardRows}
    <p style="font-size:10px; color:#aaa; margin-top:24px; text-align:center;">Generated from interactive portfolio: ari-ana-m.github.io/GIS_Portfolio</p>
    </body></html>`;

  const win = window.open("", "_blank");
  win.document.write(html);
  win.document.close();
  win.focus();
  setTimeout(() => { win.print(); }, 400);
};

/* ════════════════════════════════════════════
   WEB VIEWER
════════════════════════════════════════════ */
window.openViewer = function(url, title) {
  const panel    = document.getElementById("webViewerPanel");
  const frame    = document.getElementById("webViewerFrame");
  const fallback = document.getElementById("viewerFallback");
  const label    = document.getElementById("viewerLabel");
  const openBtn  = document.getElementById("viewerOpenBtn");
  const fbLink   = document.getElementById("fallbackLink");

  panel.style.display    = "flex";
  label.textContent      = title;
  openBtn.href           = url;
  fbLink.href            = url;
  fallback.style.display = "none";
  frame.style.display    = "block";

  let embedURL = url;
  if (url.includes("youtube.com/watch")) {
    const videoId = url.split("v=")[1]?.split("&")[0];
    if (videoId) embedURL = `https://www.youtube.com/embed/${videoId}`;
  }
  if (url.includes("youtu.be/")) {
    const videoId = url.split("youtu.be/")[1]?.split("?")[0];
    if (videoId) embedURL = `https://www.youtube.com/embed/${videoId}`;
  }

  frame.src = embedURL;
  panel.scrollIntoView({ behavior: "smooth", block: "start" });

  frame.onload = function() {
    try {
      const doc = frame.contentDocument || frame.contentWindow.document;
      if (!doc || doc.body === null || doc.body.innerHTML.trim() === "") showFallback(url);
    } catch(e) { /* cross-origin */ }
  };
  frame.onerror = function() { showFallback(url); };
};

function showFallback(url) {
  document.getElementById("webViewerFrame").style.display = "none";
  document.getElementById("viewerFallback").style.display = "block";
  document.getElementById("fallbackLink").href = url;
}

window.closeViewer = function() {
  document.getElementById("webViewerPanel").style.display = "none";
  document.getElementById("webViewerFrame").src = "about:blank";
};

/* ════════════════════════════════════════════
   MISC CONTROLS
════════════════════════════════════════════ */
window.toggleLeftPanel = function() {

  const panel = document.getElementById("leftPanel");

  if (
    panel.style.width === "0px" ||
    panel.style.width === ""
  ) {
    panel.style.width = "160px";
    panel.style.padding = "10px";
    panel.style.overflow = "auto";
  } else {
    panel.style.width = "0px";
    panel.style.padding = "0px";
    panel.style.overflow = "hidden";
  }

};

window.toggleCategory = function(cat) {
  if (map.hasLayer(categoryLayers[cat])) map.removeLayer(categoryLayers[cat]);
  else map.addLayer(categoryLayers[cat]);
};

} catch(err) { console.error("App error:", err); }
});
</script>
</body>
</html>
