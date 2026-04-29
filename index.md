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

<div style="display:flex; height:780px; margin-top:40px; border:2px solid #333; border-radius:10px; overflow:hidden;">

  <!-- LEFT PANEL -->
  <div id="leftPanel" style="width:160px; background:#fafafa; border-right:1px solid #ccc; padding:10px; overflow-y:auto;">
    <button onclick="toggleLeftPanel()">☰</button>

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
  <div id="infoPanel" style="width:260px; background:white; border-left:2px solid #333; padding:16px; overflow-y:auto; display:none;">
    <button onclick="closePanel()">Close</button>
    <div id="panelContent"></div>
  </div>

</div>

<style>
.project-link{
  cursor:pointer;
  font-weight:600;
  color:#44BFC7;
  text-decoration:underline;
  display:inline-block;
  margin-bottom:6px;
}
.project-link:hover{ color:#DE879D; }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

/* =========================
COLOR SCHEME (YOUR EXACT REQUEST)
========================= */
const colors = {
  "Research": "#38C6D0",
  "Technical": "#90E2BF",
  "Applied GIS": "#F19FB4"
};

/* =========================
BLACK & WHITE BASEMAP (FIX)
========================= */
const map = L.map('map').setView([52, -90], 4);

L.tileLayer(
  "https://{s}.basemaps.cartocdn.com/light_nolabels/{z}/{x}/{y}{r}.png",
  { attribution: "© CARTO (B&W)" }
).addTo(map);

/* =========================
LAYERS
========================= */
const categoryLayers = {
  "Applied GIS": L.layerGroup().addTo(map),
  "Technical": L.layerGroup().addTo(map),
  "Research": L.layerGroup().addTo(map)
};

const allMarkers = [];
const allPolygons = {};

/* =========================
YOUR EXACT GEOJSON FILES (UNCHANGED)
========================= */
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

/* =========================
LOAD POLYGONS (TRANSLUCENT OVERLAP SAFE)
========================= */
Object.entries(lakeFiles).forEach(([name, path]) => {

  fetch(path)
    .then(r => r.json())
    .then(data => {

      const poly = L.geoJSON(data, {
        style: {
          color: colors["Research"],
          weight: 1.5,
          fillColor: colors["Research"],
          fillOpacity: 0.25   // <-- overlap blending effect
        }
      }).addTo(map);

      allPolygons[name] = poly;
    })
    .catch(err => {
      console.warn("Missing polygon:", name);
    });

});

/* =========================
RESET STYLE
========================= */
function resetHighlight() {

  allMarkers.forEach(m => {
    m.setStyle({
      radius: 7,
      color: "#000",
      fillColor: m.options.baseColor
    });
  });

  Object.values(allPolygons).forEach(p => {
    p.setStyle({
      color: colors["Research"],
      weight: 1.5,
      fillColor: colors["Research"],
      fillOpacity: 0.25
    });
  });
}

/* =========================
PROJECT CLICK
========================= */
function selectProject(project) {

  resetHighlight();

  const boundsItems = [];

  // highlight markers
  project.layers.forEach(m => {
    m.setStyle({
      radius: 10,
      color: "#000",
      fillColor: "#FFD700"
    });
    boundsItems.push(m);
  });

  // highlight polygons
  project.locations.forEach(loc => {
    const poly = allPolygons[loc.name];
    if (poly) {
      poly.setStyle({
        color: "#FFD700",
        weight: 3,
        fillOpacity: 0.35
      });
      boundsItems.push(poly);
    }
  });

  if (boundsItems.length) {
    map.fitBounds(L.featureGroup(boundsItems).getBounds());
  }

  openPanel(project);
}

/* =========================
PANEL
========================= */
function openPanel(project) {

  document.getElementById("infoPanel").style.display = "block";

  const locs = project.locations.map(l => `<li>${l.name}</li>`).join("");

  document.getElementById("panelContent").innerHTML = `
    <h2>${project.title}</h2>
    <ul>${locs}</ul>
    <p><b>Category:</b> ${project.category}</p>
    <p>${project.description}</p>
    ${project.link ? `<a href="${project.link}" target="_blank">Open Project →</a>` : ""}
  `;
}

function closePanel(){
  document.getElementById("infoPanel").style.display = "none";
}

/* =========================
UI HELPERS
========================= */
window.toggleLeftPanel = function(){
  const p = document.getElementById("leftPanel");
  p.style.width = (p.style.width === "0px") ? "160px" : "0px";
};

window.toggleCategory = function(cat){
  map.hasLayer(categoryLayers[cat])
    ? map.removeLayer(categoryLayers[cat])
    : map.addLayer(categoryLayers[cat]);
};

/* =========================
PROJECT RENDER (FIXED RULE APPLIED)
NO POLYGON → SHOW POINT
POLYGON EXISTS → HIDE POINT
========================= */
const listDiv = document.getElementById("project-list");

const projects = [ /* YOUR FULL ORIGINAL LIST (UNCHANGED) */ ];

projects.forEach(project => {

  project.layers = [];

  const div = document.createElement("div");
  div.innerHTML = `<span class="project-link">${project.title}</span>`;
  div.onclick = () => selectProject(project);
  listDiv.appendChild(div);

  const ul = document.createElement("ul");

  project.locations.forEach(loc => {

    const polygonExists = allPolygons[loc.name];

    // ONLY CREATE POINT IF NO POLYGON EXISTS
    if (!polygonExists) {

      const color = colors[project.category];

      const marker = L.circleMarker(loc.coords, {
        radius: 7,
        color: "#000",
        fillColor: color,
        fillOpacity: 0.9
      }).addTo(categoryLayers[project.category]);

      marker.options.baseColor = color;

      marker.on("click", () => selectProject(project));

      project.layers.push(marker);
      allMarkers.push(marker);
    }

    const li = document.createElement("li");
    li.textContent = loc.name;
    ul.appendChild(li);

  });

  listDiv.appendChild(ul);
});

});
</script>
