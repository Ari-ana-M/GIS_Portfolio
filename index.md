<div style="display:flex; gap:40px; align-items:center; border:2px solid #333; padding:30px; border-radius:10px; margin-top:20px;">

<!-- LEFT TEXT CONTENT -->
<div style="flex:1; min-width:280px;">

<h1 style="margin-bottom:5px;">GIS & Spatial Data Portfolio</h1>

<p style="margin-top:0;"><b>Geospatial Analyst | Data-Driven Workflows | Environmental Systems</b></p>

<style>
  ul.top-level {
    list-style-type: disc; /* solid bullet */
    padding-left: 0;
  }

  ul.top-level ul {
    list-style-type: circle; /* hollow bullet */
    margin-top: 5px;
    margin-bottom: 10px;
    padding-left: 20px;
  }
</style>

<h3>Education</h3>

<ul class="top-level">

  <li>
    <b>Honors BA Environmental Studies</b> – Wilfrid Laurier University
    <ul>
      <li>Option in Geomatics and Minor in Sociology</li>
      <li>GPA: 3.8</li>
    </ul>
  </li>

  <li>
    <b>MSc Geography</b> – University of Waterloo
    <ul>
      <li>Focus: Climate data & lake ice systems</li>
      <li>GPA: 3.8</li>
    </ul>
  </li>

</ul>

<h3>Approach</h3>
<p>
Workflow-oriented GIS: focusing on how data is acquired, processed, and transformed into usable insight.
</p>

<h3>Tools & Technologies</h3>

<p>
<span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">ArcGIS Pro</span>
<span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">QGIS</span>
<span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">Python</span>
<span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">SQL</span>
<span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">Remote Sensing</span>
<span style="background:#eee; padding:6px 10px; border-radius:8px; margin:3px; display:inline-block;">Spatial Analysis</span>
</p>

</div>

<!-- RIGHT SVG -->

<div style="flex:1; display:flex; justify-content:center;">

<svg width="520" height="475" viewBox="0 0 520 440">
<rect x="10" y="60" width="500" height="395" 
      fill="none" 
      stroke="#333" 
      stroke-width="1" 
      rx="10"/>

  <!-- TOP TITLE -->
  <text x="260" y="25" text-anchor="middle" font-size="18" font-weight="bold">
    Communication & Translation
  </text>

  <text x="260" y="45" text-anchor="middle" font-size="12">
    Presenting to stakeholders • Interdisciplinary collaboration • Reporting
  </text>

  <!-- CIRCLES -->
  <circle cx="170" cy="210" r="110" fill="#44BFC7" fill-opacity="0.8"/>
  <circle cx="350" cy="210" r="110" fill="#97D8CD" fill-opacity="0.6"/>
  <circle cx="260" cy="320" r="110" fill="#F5E8AD" fill-opacity="0.8"/>

  <!-- TITLES -->
  <text x="150" y="95" text-anchor="middle" font-size="14" font-weight="bold">
    Data Acquisition
  </text>

  <text x="370" y="95" text-anchor="middle" font-size="14" font-weight="bold">
    Geospatial Analysis & Modeling
  </text>

  <text x="260" y="445" text-anchor="middle" font-size="14" font-weight="bold">
    Applied Systems
  </text>

  <!-- LEFT TEXT -->
  <text x="170" y="160" text-anchor="middle" font-size="13">
    <tspan x="170" dy="0">Field Surveying</tspan>
    <tspan x="170" dy="16">Remote Sensing</tspan>
    <tspan x="170" dy="16">Data Sourcing</tspan>
  </text>

  <!-- RIGHT TEXT (RAISED) -->
  <text x="350" y="150" text-anchor="middle" font-size="13">
    <tspan x="350" dy="0">GIS (ArcGIS, QGIS)</tspan>
    <tspan x="350" dy="16">Python</tspan>
    <tspan x="350" dy="16">Spatial Analysis</tspan>
    <tspan x="350" dy="16">Climate modelling</tspan>
    <tspan x="350" dy="16">workflows</tspan>
  </text>

  <!-- BOTTOM TEXT -->
  <text x="260" y="315" text-anchor="middle" font-size="13">
    <tspan x="260" dy="0">Policy</tspan>
    <tspan x="260" dy="16">Planning</tspan>
    <tspan x="260" dy="16">Environmental Systems</tspan>
    <tspan x="260" dy="16">Infrastructure Applications</tspan>
  </text>

  <!-- CENTER LABEL (FIXED) -->
  <rect x="210" y="230" width="100" height="45" rx="8" fill="white" opacity="0.40"/>
  <text x="260" y="245" text-anchor="middle" font-size="11" font-weight="bold">
    <tspan x="260" dy="0">End-to-End</tspan>
    <tspan x="260" dy="13">Geospatial</tspan>
    <tspan x="260" dy="13">Workflows</tspan>
  </text>

</svg>

</div>

</div>

<!-- =========================
FULL GIS DASHBOARD LAYOUT
========================= -->
<div style="
  display:flex;
  height:780px;
  margin-top:40px;
  border:2px solid #333;
  border-radius:10px;
  overflow:hidden;
">

  <!-- LEFT PANEL -->
  <div id="leftPanel" style="
    width:160px;
    background:#fafafa;
    border-right:1px solid #ccc;
    padding:10px;
    overflow-y:auto;
  ">

    <button onclick="toggleLeftPanel()" style="margin-bottom:10px;">☰</button>

    <h4>Filter</h4>

    <label><input type="checkbox" checked onchange="toggleCategory('Applied GIS')"> 🟢 Applied GIS</label><br>
    <label><input type="checkbox" checked onchange="toggleCategory('Technical')"> 🟣 Technical</label><br>
    <label><input type="checkbox" checked onchange="toggleCategory('Research')"> 🔵 Research</label>

    <hr>

    <h4>Projects</h4>
    <div id="project-list"></div>

  </div>

  <!-- MAP -->
  <div id="map" style="flex:1; min-width:0;"></div>

  <!-- RIGHT PANEL -->
  <div id="infoPanel" style="
    width:260px;
    background:white;
    border-left:2px solid #333;
    padding:16px;
    overflow-y:auto;
    display:none;
  ">
    <button onclick="closePanel()">Close</button>
    <div id="panelContent"></div>
  </div>

</div>

<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css"/>
<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

<style>
.project-link{
  cursor:pointer;
  font-weight:600;
  color:#44BFC7;
  text-decoration:underline;
  display:inline-block;
  margin-bottom:6px;
}
.project-link:hover{
  color:#DE879D;
}
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

try {

<script>
document.addEventListener("DOMContentLoaded", function () {
try {

// =========================
// SAFETY CHECKS
// =========================
const mapDiv = document.getElementById("map");
const listDiv = document.getElementById("project-list");

if (!mapDiv || !listDiv) {
  console.error("Missing required DOM elements");
  return;
}

// =========================
// COLOR SCHEME
// =========================
const CATEGORY_COLORS = {
  "Research": "#38C6D0",
  "Technical": "#90E2BF",
  "Applied GIS": "#F19FB4"
};

// =========================
// MAP INIT
// =========================
var map = L.map('map').setView([52, -90], 4);

// Black-and-white basemap
L.tileLayer('https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png', {
  attribution: '© OpenStreetMap © CARTO'
}).addTo(map);

// =========================
// LAYERS
// =========================
const categoryLayers = {
  "Applied GIS": L.layerGroup().addTo(map),
  "Technical": L.layerGroup().addTo(map),
  "Research": L.layerGroup().addTo(map)
};

const allMarkers = [];
const allPolygons = {};

// =========================
// GEOJSON FILES
// =========================
const lakeFiles = {
  "Lake Superior": "data/Superior.geojson",
  "Lake Huron": "data/Huron.geojson",
  "Lake Erie": "data/Erie.geojson",
  "Lake Winnipeg": "data/Winnipeg.geojson",
  "Lake Athabasca": "data/Athabasca.geojson",
  "Great Bear Lake": "data/GBL.geojson",
  "Great Slave Lake": "data/GSL.geojson",
  "Bernard Lake": "data/Bernard.geojson"
};

const POLYGON_NAMES = new Set(Object.keys(lakeFiles));

Object.entries(lakeFiles).forEach(([name, path]) => {
  fetch(path)
    .then(res => {
      if (!res.ok) throw new Error("Missing file");
      return res.json();
    })
    .then(data => {
      const poly = L.geoJSON(data, {
        style: {
          color: CATEGORY_COLORS["Research"],
          weight: 1.2,
          fillColor: CATEGORY_COLORS["Research"],
          fillOpacity: 0.18
        }
      }).addTo(map);

      allPolygons[name] = poly;
    })
    .catch(() => {
      console.warn("Skipping polygon:", name);
    });
});

// =========================
// RESET
// =========================
function resetHighlight() {
  allMarkers.forEach(m => {
    const cat = m.options.category;
    m.setStyle({
      radius: 7,
      color: "#111",
      fillColor: CATEGORY_COLORS[cat] || "#999",
      fillOpacity: 0.9
    });
  });

  Object.values(allPolygons).forEach(p => {
    p.setStyle({
      color: "#444",
      weight: 1.2,
      fillColor: CATEGORY_COLORS["Research"],
      fillOpacity: 0.18
    });
  });
}

// =========================
// SELECT PROJECT
// =========================
function selectProject(project) {
  resetHighlight();

  const groupLayers = [...project.layers];

  // Highlight markers
  project.layers.forEach(m => {
    m.setStyle({
      radius: 10,
      color: "#000",
      fillColor: "#FFD700",
      fillOpacity: 1
    });
  });

  // Highlight polygons
  project.locations.forEach(loc => {
    const poly = allPolygons[loc.name];
    if (poly) {
      poly.setStyle({
        color: "#FFD700",
        weight: 3,
        fillColor: "#FFD700",
        fillOpacity: 0.28
      });
      groupLayers.push(poly);
    }
  });

  if (groupLayers.length > 0) {
    const group = L.featureGroup(groupLayers);
    map.fitBounds(group.getBounds(), {
      paddingTopLeft: [160, 20],
      paddingBottomRight: [260, 20]
    });
  }

  openPanel(project);
}

// =========================
// PANEL
// =========================
function openPanel(project) {
  document.getElementById("infoPanel").style.display = "block";

  const locs = project.locations.map(l => `<li>${l.name}</li>`).join("");

  document.getElementById("panelContent").innerHTML = `
    <h2>${project.title}</h2>
    <ul>${locs}</ul>

    <table style="width:100%; margin-top:10px;">
      <tr><td><b>Category</b></td><td>${project.category}</td></tr>
      <tr><td><b>Description</b></td><td>${project.description}</td></tr>
      <tr><td><b>Link</b></td><td>
        ${project.link ? `<a href="${project.link}" target="_blank">Open Project →</a>` : "-"}
      </td></tr>
    </table>
  `;
}

function closePanel() {
  document.getElementById("infoPanel").style.display = "none";
}

// =========================
// LEFT PANEL TOGGLE
// =========================
window.toggleLeftPanel = function () {
  const panel = document.getElementById("leftPanel");
  panel.style.width = panel.style.width === "0px" ? "160px" : "0px";
};

// =========================
// FILTER
// =========================
window.toggleCategory = function (cat) {
  if (map.hasLayer(categoryLayers[cat])) {
    map.removeLayer(categoryLayers[cat]);
  } else {
    map.addLayer(categoryLayers[cat]);
  }
};

// =========================
// PROJECT DATA
// Keep your existing full project list here unchanged
// =========================
const projects = [
  {
    title: "Field Research Assistant — Coastal & Environmental Monitoring",
    category: "Applied GIS",
    description: "Field-based GPS and RTK GNSS coastal data collection, QA/QC, and spatial integration workflows.",
    locations: [
      { name: "Sauble Beach", coords: [44.6296, -81.26508] },
      { name: "Burlington Beach", coords: [43.31523, -79.80701] },
      { name: "Wasaga Beach", coords: [44.52372, -80.0033] }
    ]
  },
  {
    title: "Research Presenter — Invasive Species Monitoring",
    category: "Applied GIS",
    description: "Spatial + NDVI analysis of Phragmites spread in Lake Bernard.",
    link: "https://www.youtube.com/watch?v=5Io_79IMANw",
    locations: [
      { name: "Bernard Lake", coords: [45.72458, -79.3857] }
    ]
  },
  {
    title: "Student Planner — Municipal Housing Policy",
    category: "Applied GIS",
    description: "Missing middle housing analysis using GIS and census data.",
    link: "https://www.cambridgetimes.ca/news/housing-affordability-is-a-human-rights-issue-wilfrid-laurier-students-exploring-housing-concerns-with-city/article_c289ca4b-507c-5777-b38d-90a1d676d692.html",
    locations: [
      { name: "Cambridge", coords: [43.40175, -80.32597] }
    ]
  },
  {
    title: "Research Assistant — Environmental & Climate Data Analysis",
    category: "Technical",
    description: "Scoping review + spatial climate synthesis workflows.",
    link: "https://ecologyandsociety.org/vol29/iss3/art22/",
    locations: [
      { name: "Africa", coords: [0, 20] }
    ]
  },
  {
    title: "ReSEC Research Assistant — Remote Sensing of Climate Change",
    category: "Technical",
    description: "Python + GIS analysis of lake ice variability using satellite data.",
    locations: [
      { name: "Great Bear Lake", coords: [66, -121] },
      { name: "Great Slave Lake", coords: [61, -114] }
    ]
  },
  {
    title: "ERA5-Land Lake Ice Thesis",
    category: "Research",
    description: "20-year lake ice bias evaluation across 7 Canadian lakes.",
    link: "https://uwspace.uwaterloo.ca/items/b983d97f-d2ec-4c1a-a6d0-82be963c476a",
    locations: [
      { name: "Great Bear Lake", coords: [66, -121] },
      { name: "Great Slave Lake", coords: [61, -114] },
      { name: "Lake Athabasca", coords: [59, -109] },
      { name: "Lake Winnipeg", coords: [52, -97] },
      { name: "Lake Superior", coords: [47.7, -87.5] },
      { name: "Lake Huron", coords: [45, -82.4] },
      { name: "Lake Erie", coords: [42.2, -81.2] }
    ]
  }
];

// =========================
// RENDER
// =========================
projects.forEach(project => {
  project.layers = [];

  const div = document.createElement("div");
  div.innerHTML = `<span class="project-link">${project.title}</span>`;
  div.onclick = () => selectProject(project);
  listDiv.appendChild(div);

  const ul = document.createElement("ul");

  project.locations.forEach(loc => {
    // Do not create a point if a polygon exists for that location
    if (POLYGON_NAMES.has(loc.name)) return;

    const marker = L.circleMarker(loc.coords, {
      radius: 7,
      fillColor: CATEGORY_COLORS[project.category] || "#999",
      color: "#111",
      weight: 1,
      fillOpacity: 0.9
    }).addTo(categoryLayers[project.category]);

    marker.options.category = project.category;
    marker.on("click", () => selectProject(project));

    project.layers.push(marker);
    allMarkers.push(marker);

    const li = document.createElement("li");
    li.innerText = loc.name;
    ul.appendChild(li);
  });

  listDiv.appendChild(ul);
});

} catch (err) {
  console.error("App crashed:", err);
}
});
</script>
