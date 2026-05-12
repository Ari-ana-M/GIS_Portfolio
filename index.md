<html lang="en"> 
<head><meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0"><title>GIS & Spatial Data Portfolio</title>
<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css"/>
<style>
/* ── Base ── */
body { margin: 0; padding: 16px; font-family: Arial, sans-serif; box-sizing: border-box; }

/* ── Skill tags ── */
.skill-tag {
  display: inline-block;
  font-size: 12px;
  padding: 6px 10px;
  border-radius: 12px;
  margin: 3px 4px 0 0;
  background: #e8f8fa;
  color: #1a7a85;
  border: 1px solid #b2e4ea;
  white-space: nowrap;
}

/* ── TOOL TAGS (ADD THIS RIGHT BELOW) ── */
.tool-tag {
  display: inline-block;
  font-size: 12px;
  padding: 6px 10px;
  border-radius: 8px;
  margin: 3px 4px 0 0;
  background: #f2f2f2;
  color: #333;
  border: 1px solid #ddd;
  white-space: nowrap;
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
        Environmental & Geospatial Analyst specializing in climate data,
        remote sensing, and applied GIS workflows
      </b>
    </p>

    <p style="font-size:13px; color:#444; line-height:1.6;">
      Environmental and geospatial analyst with experience in environmental
      modelling, spatial analysis, and climate data interpretation.
      Skilled in evaluating model outputs, analyzing variability and
      uncertainty, and integrating spatial and field data to support
      environmental system understanding.
      Eligible for registration as a
      <b>Geoscientist-in-Training (GIT)</b>
      with Engineers and Geoscientists British Columbia.
    </p>

    <h3>Education</h3>

    <ul style="list-style-type: disc; padding-left: 20px; line-height:1.6;">

      <li>
        <b>MSc Geography</b> – University of Waterloo
        <span style="color:#888; font-size:12px;">
          (Sep 2022 – Dec 2025)
        </span>

        <ul style="margin-top:5px;">
          <li>Focus: Climate data, lake ice systems & remote sensing</li>
          <li>GPA: 3.93 / 4.0</li>
        </ul>
      </li>

      <li>
        <b>Honours BA Environmental Studies</b> –
        Wilfrid Laurier University

        <span style="color:#888; font-size:12px;">
          (Sep 2018 – Apr 2022)
        </span>

        <ul style="margin-top:5px;">
          <li>Option in Geomatics; Minor in Sociology</li>
          <li>GPA: 3.8 / 4.0 · Dean's List 2018–2022</li>
        </ul>
      </li>

    </ul>

  </div>

  <!-- RIGHT SIDE SVG -->
  <div style="flex:1; display:flex; justify-content:center; align-items:flex-start;">

    <svg width="520" height="475" viewBox="0 0 520 480">

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
        <tspan x="260" dy="16">Infrastructure Applications</tspan>
    
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

<!-- ═══════════════════════════════════════════════
     SKILLS / TOOLS / AWARDS PANEL
════════════════════════════════════════════════ -->
<div style="border:2px solid #333; border-radius:10px; padding:30px; margin-top:24px;">

  <h2 style="margin-top:0;">Professional Skills & Tools</h2>

  <!-- EXPANDABLE SKILLS -->
  <details open style="margin-bottom:14px;">
    <summary style="cursor:pointer; font-weight:bold; font-size:15px;">
      GIS & Spatial Analysis
    </summary>

    <div style="margin-top:10px;">
      <span class="skill-tag">ArcGIS Pro</span>
      <span class="skill-tag">QGIS</span>
      <span class="skill-tag">Spatial Analysis</span>
      <span class="skill-tag">Cartography</span>
      <span class="skill-tag">Remote Sensing</span>
      <span class="skill-tag">NDVI Analysis</span>
      <span class="skill-tag">Image Classification</span>
      <span class="skill-tag">Spatial Statistics</span>
      <span class="skill-tag">GIS Integration</span>
    </div>
  </details>

  <details style="margin-bottom:14px;">
    <summary style="cursor:pointer; font-weight:bold; font-size:15px;">
      Environmental & Climate Analysis
    </summary>

    <div style="margin-top:10px;">
      <span class="skill-tag">Climate Data Analysis</span>
      <span class="skill-tag">Environmental Modeling</span>
      <span class="skill-tag">Temporal Analysis</span>
      <span class="skill-tag">Environmental Monitoring</span>
      <span class="skill-tag">Cryosphere Research</span>
      <span class="skill-tag">Lake Ice Systems</span>
      <span class="skill-tag">Climate Projections</span>
    </div>
  </details>

  <details style="margin-bottom:14px;">
    <summary style="cursor:pointer; font-weight:bold; font-size:15px;">
      Programming & Data Workflows
    </summary>

    <div style="margin-top:10px;">
      <span class="skill-tag">Python</span>
      <span class="skill-tag">ArcPy</span>
      <span class="skill-tag">SQL</span>
      <span class="skill-tag">QA/QC</span>
      <span class="skill-tag">Data Validation</span>
      <span class="skill-tag">Automation</span>
      <span class="skill-tag">Reproducible Pipelines</span>
      <span class="skill-tag">Workflow Design</span>
    </div>
  </details>

  <details style="margin-bottom:24px;">
    <summary style="cursor:pointer; font-weight:bold; font-size:15px;">
      Field & Applied Skills
    </summary>

    <div style="margin-top:10px;">
      <span class="skill-tag">RTK GNSS</span>
      <span class="skill-tag">GPS Surveying</span>
      <span class="skill-tag">Field Data Collection</span>
      <span class="skill-tag">Stakeholder Communication</span>
      <span class="skill-tag">Planning Analysis</span>
      <span class="skill-tag">Technical Reporting</span>
    </div>
  </details>

  <!-- TOOLS -->
  <h3>Tools & Technologies</h3>

  <p>
    <span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">ArcGIS Pro</span>

    <span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">ArcGIS Online</span>

    <span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">QGIS</span>

    <span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">Python</span>

    <span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">ArcPy</span>

    <span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">SQL</span>

    <span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">Leaflet</span>

    <span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">RTK GNSS</span>
  </p>


  <!-- AWARDS -->
  <h3>Awards</h3>

  <ul style="font-size:13px; padding-left:1.2em; color:#333; line-height:1.7;">

    <li>
      <b>Barry Goodison Graduate Scholarship</b>
      – Cryospheric Research Excellence (2023)
    </li>

    <li>
      <b>Lorne Russwurm Award</b>
      – Best BA Thesis in Urban Geography (2022)
    </li>

    <li>
      <b>Paul & Louise Puopolo Award</b>
      – Urban Planning Solution selected by City of Cambridge (2022)
    </li>

    <li>
      <b>CAG Undergraduate Award</b>
      – Canadian Association of Geographers (2022)
    </li>

    <li>
      <b>NSERC Undergraduate Student Research Award</b>
      – Lake ice thesis funding (2021)
    </li>

  </ul>

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
      <a id="viewerOpenBtn" href="#" target="_blank" style="color:#90E2BF; text-decoration:none; white-space:nowrap; font-size:12px;">↗ Open in new tab</a>
      <button onclick="closeViewer()" style="background:none; border:none; color:white; font-size:16px; cursor:pointer; padding:0; line-height:1;">✕</button>
    </div>
    <div id="viewerFallback" style="display:none; padding:24px; font-family:Arial,sans-serif; font-size:13px; color:#555; text-align:center; background:#f9f9f9; border-bottom:1px solid #ddd;">
      <div style="font-size:28px; margin-bottom:10px;">🔒</div>
      <p style="margin:0 0 6px;"><b>This site can't be previewed here.</b></p>
      <p style="margin:0 0 14px; font-size:12px; color:#888;">Many sites block iframe embedding for security reasons.</p>
      <a id="fallbackLink" href="#" target="_blank"
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

<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
<script>
document.addEventListener("DOMContentLoaded", function () {
try {

/* ════════════════════════════════════════════
   PROJECT DATA  — sourced from CV + project briefs
════════════════════════════════════════════ */
const projects = [
  {
    title: "Assessment of ERA5-Land Lake Ice Variables (MSc Thesis)",
    category: "Research",
    subcategory: "Climate & Cryosphere Analysis",
    year: 2025,
    dateRange: "Sep 2022 – Dec 2025",
    summary: "Evaluated ERA5-Land lake ice variables against satellite observations across seven Canadian lakes using spatial and statistical analysis workflows. Assessed freeze-up, break-up, ice fraction, and surface temperature variability to identify environmental model biases and climate system trends.",
    description: "Evaluated ERA5-Land lake ice fraction, timing, and surface temperature against satellite observations across seven Canadian lakes (2004–2023). Quantified spatial and temporal biases using MBE and MAE during freeze-up and break-up periods. Identified key model limitations related to snow cover omission and partial ice representation, with implications for climate modelling accuracy.",
    skills: ["Climate Data Analysis", "Spatial Statistics (MBE, MAE)", "Environmental Model Validation", "ArcGIS Pro", "QGIS", "Python", "Satellite Remote Sensing", "Temporal Analysis", "Data Integration & QA/QC", "Cartographic Visualization", "Technical Reporting"],
    context: ["MSc Geography thesis project", "Multi-year environmental dataset analysis (2004–2023)", "Combined ERA5-Land + IMS satellite observations", "Focused on cryosphere and environmental systems interpretation"],
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
    title: "Research Analyst — Environmental & Climate Data Analysis",
    category: "Technical",
    subcategory: "Research Analytics",
    year: 2023,
    dateRange: "Jan 2023 – Apr 2023",
    summary: "Conducted structured climate resilience and environmental data analysis using spatial, statistical, and SQL-based workflows. Produced publication-quality visualizations and synthesized findings into interdisciplinary research outputs.",
    description: "Conducted structured scoping review of climate resilience literature. Extracted and analyzed data using SQL-based querying and systematic workflows. Produced graphs, statistical summaries, and workflow diagrams for interdisciplinary research reporting. Applied data validation to ensure accuracy and consistency.",
    skills: ["SQL Querying", "Data Organization", "Climate Data Analysis", "GIS Workflows", "Statistical Summaries", "Data Validation & QA/QC", "Workflow Reproducibility", "Research Synthesis", "Scientific Visualization", "Technical Communication"],
    context: ["University of Waterloo research role", "Supported interdisciplinary environmental research", "Focused on structured analytical workflows and reporting"],
    links: [
      { url: "https://ecologyandsociety.org/vol29/iss3/art22/", label: "Published Article (Ecology & Society)" }
    ],
    locations: [{ name: "Africa" }]
  },
  {
    title: "Lake Ice Projections under Climate Scenarios (Undergraduate Thesis)",
    category: "Research",
    subcategory: "Remote Sensing / Climate Projection",
    year: 2022,
    dateRange: "Sep 2021 – Apr 2022",
    summary: "Processed and analyzed environmental and climate datasets using Python, GIS, and remote sensing workflows to assess lake ice variability and climate-driven environmental change.",
    description: "Analyzed projected lake ice thickness and phenology for Great Bear and Great Slave Lakes under multiple RCP climate scenarios. Processed and integrated climate model outputs to force the CLIMoGrid thermodynamic lake ice model. Conducted trend and scenario analysis to assess climate-driven changes in ice duration and thickness.",
    skills: ["Python Automation", "SQL Workflows", "Remote Sensing", "Climate Projections", "GIS Analysis", "Spatial Data Processing", "Environmental Modeling", "QA/QC Workflows", "Reproducible Pipelines", "Data Visualization"],
    context: ["Remote Sensing of Environmental Change (ReSEC) group", "Supported climate scenario and lake ice research", "Integrated satellite and modeled environmental datasets"],
    locations: [
      { name: "Great Bear Lake",  coords: [66, -121] },
      { name: "Great Slave Lake", coords: [61, -114] }
    ]
  },
  {
    title: "Student Planner — Housing Policy & GIS Analysis",
    category: "Applied GIS",
    subcategory: "Planning",
    year: 2022,
    dateRange: "Sep 2021 – Sep 2022",
    summary: "Supported municipal housing and planning analysis through GIS-based spatial workflows, census integration, and cartographic visualization. Produced stakeholder-focused planning outputs supporting housing and development assessment.",
    description: "Analyzed and integrated GIS and census datasets to support planning maps and spatial insights for the City of Cambridge. Produced cartographic outputs and visualizations for housing and development analysis. Collaborated with staff and stakeholders to support evidence-based planning decisions. Recognized with the Paul & Louise Puopolo Award.",
    skills: ["GIS Spatial Analysis", "Census Data Integration", "Cartography", "ArcGIS Pro", "Planning Analysis", "Stakeholder Communication", "Data Organization", "Policy Research", "Spatial Visualization", "Workflow Improvement"],
    context: ["Collaboration with City of Cambridge", "Applied GIS within municipal planning context", "Contributed to award-recognized planning project"],
    links: [
      { url: "https://www.cambridgetimes.ca/news/housing-affordability-is-a-human-rights-issue-wilfrid-laurier-students-exploring-housing-concerns-with-city/article_c289ca4b-507c-5777-b38d-90a1d676d692.html", label: "News Article (Interview)" },
      { url: "data/EcoVital-Final-Deliverable-1.pdf", label: "Final Deliverable (PDF)" }
    ],
    locations: [{ name: "Cambridge", coords: [43.40175, -80.32597] }]
  },
  {
    title: "Remote Sensing & GIS Assistant — Climate Change Projection (ReSEC)",
    category: "Technical",
    subcategory: "Remote Sensing",
    year: 2021,
    dateRange: "May 2021 – Sep 2021",
    summary: "Processed and analyzed environmental and climate datasets using Python, GIS, and remote sensing workflows to assess lake ice variability and climate-driven environmental change.",
    description: "Extracted and processed large geospatial datasets using Python and SQL workflows. Applied GIS and remote sensing techniques to generate spatial products supporting environmental analysis of lake ice variability. Built reproducible data pipelines with integrated QA/QC checks. Visualized spatial patterns through interpretable map outputs.",
    skills: ["Python Automation", "SQL Workflows", "Remote Sensing", "Climate Projections", "GIS Analysis", "Spatial Data Processing", "Environmental Modeling", "QA/QC Workflows", "Reproducible Pipelines", "Data Visualization"],
    context: ["Remote Sensing of Environmental Change (ReSEC) group", "Supported climate scenario and lake ice research", "Integrated satellite and modeled environmental datasets"],
    locations: [
      { name: "Great Bear Lake",  coords: [66, -121] },
      { name: "Great Slave Lake", coords: [61, -114] }
    ]
  },
  {
    title: "Geospatial Field Assistant — Coastal & Environmental Monitoring",
    category: "Applied GIS",
    subcategory: "Field Data Collection",
    year: 2021,
    dateRange: "Jun 2021 – Oct 2021",
    summary: "Collected and validated coastal and environmental spatial datasets using RTK GNSS, GPS, and surveying workflows. Integrated field observations into GIS analysis and mapping products supporting environmental monitoring initiatives.",
    description: "Collected spatial data using RTK GNSS, GPS, and surveying tools for environmental monitoring at three Ontario shoreline sites. Performed QA/QC validation to ensure positional accuracy. Integrated field data into GIS workflows for downstream analysis and mapping. Supported preparation of technical reports and map-based deliverables.",
    skills: ["RTK GNSS Surveying", "GPS Field Collection", "Spatial QA/QC", "Environmental Monitoring", "GIS Integration", "Field Data Validation", "Coastal Data Collection", "Mapping Workflows", "Technical Reporting", "Data Accuracy Assessment"],
    context: ["Combined field surveying with GIS analysis", "Worked across multiple Ontario coastal environments", "Supported environmental and hydrological monitoring activities"],
    locations: [
      { name: "Sauble Beach",     coords: [44.6296,  -81.26508] },
      { name: "Burlington Beach", coords: [43.31523, -79.80701] },
      { name: "Wasaga Beach",     coords: [44.52372, -80.0033] }
    ]
  },
  {
    title: "Invasive Species Monitoring — Lake Bernard Phragmites",
    category: "Applied GIS",
    subcategory: "Remote Sensing",
    year: 2020,
    dateRange: "Jan 2020 – Apr 2020",
    summary: "Conducted GIS and remote sensing analysis of invasive Phragmites distribution using NDVI, image classification, and spatial statistics to support ecological monitoring and environmental management.",
    description: "Conducted spatial analysis of Phragmites distribution using ArcGIS to assess ecological impacts. Applied NDVI analysis and image classification to evaluate vegetation health and invasive spread. Performed kernel density estimation, buffer analysis, and nearest neighbor analysis to model potential spread. Integrated UAV imagery and monitoring reports for stakeholder-focused summaries.",
    skills: ["ArcGIS Spatial Analysis", "NDVI Analysis", "Image Classification", "UAV Imagery Integration", "Kernel Density Analysis", "Buffer Analysis", "Nearest Neighbor Analysis", "Ecological GIS Workflows", "Remote Sensing Interpretation", "Scientific Presentation"],
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
L.tileLayer('https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png', {
  attribution: '© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> © <a href="https://carto.com/">CARTO</a>',
  subdomains: 'abcd', maxZoom: 19
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

  let linkRow = "";
  if (project.links && project.links.length > 0) {
    linkRow = project.links.map(link => {
      const safeTitle = project.title.replace(/'/g, "\\'");
      const safeLabel = link.label.replace(/'/g, "\\'");
      return `
        <div style="border-top:1px solid #ddd;">
          <div style="padding:8px 12px; font-size:12px; font-weight:bold;">${link.label}</div>
          <a class="arcgis-popup-link" href="${link.url}" target="_blank">🔗 Open in New Tab →</a>
          <button class="preview-btn" onclick="openViewer('${link.url}','${safeTitle} — ${safeLabel}')">▶ Preview Below</button>
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
   TIMELINE  (Feature 2)
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
    `<a href="${l.url}" target="_blank" style="color:#0079c1; font-size:12px; display:block; margin-top:4px;">🔗 ${l.label}</a>`
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
    <div style="margin-bottom:6px;">${skillPills}</div>
    ${contextList}
    ${linkList}`;
  detail.style.display = "block";
}

buildTimeline();

/* ════════════════════════════════════════════
   VIEW TOGGLE  (Map ↔ Timeline)
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
   PDF EXPORT  (Feature 3)
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
    <h1>GIS & Spatial Data Portfolio</h1>
    <p>Environmental & Geospatial Analyst | Spatial Analysis | Climate Data | Environmental Systems<br>
    Eligible for registration as Geoscientist-in-Training (GIT) — Engineers and Geoscientists BC</p>
    <hr style="margin: 16px 0 20px;">
    <h2>Projects & Experience</h2>
    ${rows}
    <h2>Awards & Recognition</h2>
    ${awardRows}
    <p style="font-size:10px; color:#aaa; margin-top:24px; text-align:center;">Generated from interactive portfolio</p>
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
