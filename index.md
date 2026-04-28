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

<!-- MAP + SIDEBAR CONTAINER -->
<!-- MAP + SIDEBAR + INFO PANEL -->
<div style="display:flex; height:650px; margin-top:40px; border:2px solid #333; border-radius:10px; overflow:hidden;">

  <!-- SIDEBAR -->
  <div style="width:320px; padding:15px; overflow-y:auto; background:#fafafa; border-right:1px solid #ccc;">

    <h3>Filter</h3>
    <label><input type="checkbox" checked onchange="toggleCategory('Applied GIS')"> 🟢 Applied GIS</label><br>
    <label><input type="checkbox" checked onchange="toggleCategory('Technical')"> 🟣 Technical</label><br>
    <label><input type="checkbox" checked onchange="toggleCategory('Research')"> 🔵 Research</label>

    <hr>

    <h3>Projects</h3>
    <div id="project-list"></div>

  </div>

  <!-- MAP -->
  <div id="map" style="flex:1;"></div>

  <!-- INFO PANEL -->
  <div id="info-panel" style="width:340px; padding:15px; background:#fff; border-left:1px solid #ccc; overflow-y:auto;">
    <h3>Select a project</h3>
    <p>Click a project to view details</p>
  </div>

</div>

<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css"/>
<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

<link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster/dist/MarkerCluster.css"/>
<link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster/dist/MarkerCluster.Default.css"/>
<script src="https://unpkg.com/leaflet.markercluster/dist/leaflet.markercluster.js"></script>

<script>

// INIT MAP
var map = L.map('map').setView([50, -90], 4);

// BASEMAP
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
  attribution: '© OpenStreetMap'
}).addTo(map);

// COLOR FUNCTION (match your Venn palette)
function getColor(category) {
  if (category === "Applied GIS") return "#44BFC7";
  if (category === "Technical") return "#97D8CD";
  return "#F5E8AD";
}

// CATEGORY LAYERS
const categoryLayers = {
  "Applied GIS": L.markerClusterGroup(),
  "Technical": L.markerClusterGroup(),
  "Research": L.markerClusterGroup()
};

// HIGHLIGHT LAYER (ArcGIS-style)
let highlightLayer = L.layerGroup().addTo(map);

// STORE LAKES
let lakeLayers = {};

// LOAD GEOJSON LAKES
const lakeFiles = {
  "Lake Athabasca": "data/Athabasca.geojson",
  "Bernard Lake": "data/Bernard.geojson",
  "Lake Erie": "data/Erie.geojson",
  "Great Bear Lake": "data/GBL.geojson",
  "Great Slave Lake": "data/GSL.geojson",
  "Lake Huron": "data/Huron.geojson",
  "Lake Superior": "data/Superior.geojson",
  "Lake Winnipeg": "data/Winnipeg.geojson"
};

Object.entries(lakeFiles).forEach(([name, path]) => {

  fetch(path)
    .then(res => res.json())
    .then(data => {

      let layer = L.geoJSON(data, {
        style: {
          color: "#333",
          weight: 1,
          fillColor: "#888",
          fillOpacity: 0.2
        }
      }).addTo(map);

      lakeLayers[name] = layer;

    });

});

// PROJECT DATA
const projects = [
  {
    category: "Research",
    title: "ERA5-Land Thesis",
    locations: [
      "Great Bear Lake","Great Slave Lake","Lake Athabasca","Lake Winnipeg",
      "Lake Superior","Lake Huron","Lake Erie"
    ],
    start: "2004",
    end: "2023",
    short: "ERA5-Land validation against satellite observations",
    long: "Evaluates biases in lake ice fraction, timing, and temperature across 7 lakes.",
    link: "https://uwspace.uwaterloo.ca/items/b983d97f-d2ec-4c1a-a6d0-82be963c476a"
  }
];

// BUILD SIDEBAR
const list = document.getElementById("project-list");

projects.forEach(project => {

  let div = document.createElement("div");
  div.innerHTML = `<b style="cursor:pointer; text-decoration:underline;">${project.title}</b>`;
  div.style.marginBottom = "10px";

  div.onclick = () => selectProject(project);

  list.appendChild(div);

});

// SELECT PROJECT FUNCTION 🔥
function selectProject(project) {

  highlightLayer.clearLayers();

  let bounds = [];

  project.locations.forEach(loc => {

    let lake = lakeLayers[loc];

    if (lake) {

      lake.eachLayer(l => {

        let highlight = L.geoJSON(l.toGeoJSON(), {
          style: {
            color: "yellow",
            weight: 3,
            fillOpacity: 0
          }
        });

        highlightLayer.addLayer(highlight);

        bounds.push(...l.getBounds().getSouthWest(), ...l.getBounds().getNorthEast());

      });

    }

  });

  if (bounds.length > 0) {
    map.fitBounds(highlightLayer.getBounds());
  }

  // INFO PANEL
  document.getElementById("info-panel").innerHTML = `

    <h3>${project.title}</h3>

    <div style="background:#f5f5f5; padding:10px; margin-bottom:10px;">
      ${project.locations.map(l => `<div>${l}</div>`).join("")}
    </div>

    <table style="width:100%; border-collapse:collapse;">
      <tr><td><b>Project Type</b></td><td>${project.category}</td></tr>
      <tr><td><b>Start</b></td><td>${project.start}</td></tr>
      <tr><td><b>End</b></td><td>${project.end}</td></tr>
      <tr><td><b>Short</b></td><td>${project.short}</td></tr>
      <tr><td><b>Details</b></td><td>${project.long}</td></tr>
      <tr><td><b>Link</b></td><td><a href="${project.link}" target="_blank">View</a></td></tr>
    </table>

  `;

}

// FILTER
function toggleCategory(category) {
  if (map.hasLayer(categoryLayers[category])) {
    map.removeLayer(categoryLayers[category]);
  } else {
    map.addLayer(categoryLayers[category]);
  }
}

</script>
