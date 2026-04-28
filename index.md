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
<div style="position:relative; height:700px; margin-top:40px; border:2px solid #333; border-radius:10px; overflow:hidden; display:flex;">

  <!-- SIDEBAR (POP-OUT) -->
  <div id="sidebar" style="width:300px; background:#fafafa; border-right:1px solid #ccc; padding:15px; overflow-y:auto; transition:0.3s;">
    
    <button onclick="toggleSidebar()" style="margin-bottom:10px;">☰</button>

    <h3>Projects</h3>
    <div id="project-list"></div>

  </div>

  <!-- MAP -->
  <div id="map" style="flex:1;"></div>

  <!-- INFO PANEL -->
  <div id="info-panel" style="width:350px; background:#fff; border-left:1px solid #ccc; padding:15px; overflow-y:auto;">
    <h3>Select a project</h3>
  </div>

</div>

<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css"/>
<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

<link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster/dist/MarkerCluster.css"/>
<script src="https://unpkg.com/leaflet.markercluster/dist/leaflet.markercluster.js"></script>

<script>

// INIT MAP
var map = L.map('map').setView([50, -90], 4);

// BASEMAP
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
  attribution: '© OpenStreetMap'
}).addTo(map);

// COLORS
function getColor(category) {
  if (category === "Applied GIS") return "#44BFC7";
  if (category === "Technical") return "#97D8CD";
  return "#F5E8AD";
}

// MARKER CLUSTERS
const categoryLayers = {
  "Applied GIS": L.markerClusterGroup().addTo(map),
  "Technical": L.markerClusterGroup().addTo(map),
  "Research": L.markerClusterGroup().addTo(map)
};

// HIGHLIGHT LAYER
let highlightLayer = L.layerGroup().addTo(map);

// LAKES (GeoJSON)
let lakeLayers = {};

const lakeFiles = {
  "Great Bear Lake": "data/GBL.geojson",
  "Great Slave Lake": "data/GSL.geojson",
  "Lake Athabasca": "data/Athabasca.geojson",
  "Lake Winnipeg": "data/Winnipeg.geojson",
  "Lake Superior": "data/Superior.geojson",
  "Lake Huron": "data/Huron.geojson",
  "Lake Erie": "data/Erie.geojson",
  "Bernard Lake": "data/Bernard.geojson"
};

Object.entries(lakeFiles).forEach(([name, path]) => {
  fetch(path)
    .then(res => res.json())
    .then(data => {
      let layer = L.geoJSON(data, {
        style: {
          color: "#333",
          weight: 1,
          fillColor: "#999",
          fillOpacity: 0.2
        }
      }).addTo(map);

      lakeLayers[name] = layer;
    });
});

// PROJECT DATA (FULL)
const projects = [

{
  category:"Applied GIS",
  title:"Field Research Assistant — Coastal & Environmental Monitoring",
  locations:[
    {name:"Sauble Beach", coords:[44.6296,-81.26508]},
    {name:"Burlington Beach", coords:[43.31523,-79.80701]},
    {name:"Wasaga Beach", coords:[44.52372,-80.0033]}
  ],
  lakes:[],
  short:"Field data collection & QA/QC",
  long:"Collected RTK GNSS data, validated datasets, and integrated field observations into GIS workflows."
},

{
  category:"Applied GIS",
  title:"Research Presenter — Invasive Species Monitoring",
  locations:[
    {name:"Bernard Lake", coords:[45.72458,-79.3857], link:"https://www.youtube.com/watch?v=5Io_79IMANw"}
  ],
  lakes:["Bernard Lake"],
  short:"Phragmites monitoring",
  long:"Analyzed invasive vegetation using GIS, remote sensing, and UAV data to support management strategies."
},

{
  category:"Applied GIS",
  title:"Student Planner — Municipality Housing Policies",
  locations:[
    {name:"Cambridge", coords:[43.40175,-80.32597]}
  ],
  lakes:[],
  short:"Housing policy analysis",
  long:"Analyzed missing middle housing strategies and policy impacts using GIS and census data."
},

{
  category:"Technical",
  title:"Environmental & Climate Data Analysis",
  locations:[
    {name:"Africa", coords:[0,20], link:"https://ecologyandsociety.org/vol29/iss3/art22/"}
  ],
  lakes:[],
  short:"Climate resilience research",
  long:"Conducted spatial and literature-based analysis supporting climate resilience research."
},

{
  category:"Technical",
  title:"Remote Sensing of Environmental Change (ReSEC)",
  locations:[
    {name:"Great Bear Lake", coords:[66,-121]},
    {name:"Great Slave Lake", coords:[61,-114]}
  ],
  lakes:["Great Bear Lake","Great Slave Lake"],
  short:"Climate change & lake ice",
  long:"Used satellite data and Python workflows to analyze climate-driven lake ice changes."
},

{
  category:"Research",
  title:"ERA5-Land Thesis",
  locations:[
    {name:"Great Bear Lake", coords:[66,-121]},
    {name:"Great Slave Lake", coords:[61,-114]},
    {name:"Lake Athabasca", coords:[59,-109]},
    {name:"Lake Winnipeg", coords:[52,-97]},
    {name:"Lake Superior", coords:[47.7,-87.5]},
    {name:"Lake Huron", coords:[45,-82.4]},
    {name:"Lake Erie", coords:[42.2,-81.2]}
  ],
  lakes:["Great Bear Lake","Great Slave Lake","Lake Athabasca","Lake Winnipeg","Lake Superior","Lake Huron","Lake Erie"],
  short:"ERA5-Land validation",
  long:"Evaluated biases in lake ice fraction, timing, and temperature across 7 lakes.",
  link:"https://uwspace.uwaterloo.ca/items/b983d97f-d2ec-4c1a-a6d0-82be963c476a"
}

];

// ADD MARKERS
projects.forEach(project => {
  project.locations.forEach(loc => {

    let marker = L.circleMarker(loc.coords, {
      radius:7,
      fillColor:getColor(project.category),
      color:"#000",
      weight:1,
      fillOpacity:0.8
    });

    let popup = `<b>${project.title}</b><br>${loc.name}`;
    if(loc.link) popup += `<br><a href="${loc.link}" target="_blank">View</a>`;

    marker.bindPopup(popup);

    categoryLayers[project.category].addLayer(marker);

  });
});

// BUILD SIDEBAR
const list = document.getElementById("project-list");

projects.forEach(project => {

  let div = document.createElement("div");
  div.innerHTML = `<b style="cursor:pointer; text-decoration:underline;">${project.title}</b>`;
  div.style.marginBottom="10px";

  div.onclick = () => selectProject(project);

  list.appendChild(div);

});

// SELECT PROJECT
function selectProject(project){

  highlightLayer.clearLayers();

  project.lakes.forEach(name => {
    let lake = lakeLayers[name];
    if(lake){
      lake.eachLayer(l => {
        let highlight = L.geoJSON(l.toGeoJSON(), {
          style:{color:"yellow", weight:3, fillOpacity:0}
        });
        highlightLayer.addLayer(highlight);
      });
    }
  });

  if(highlightLayer.getLayers().length > 0){
    map.fitBounds(highlightLayer.getBounds());
  }

  document.getElementById("info-panel").innerHTML = `
    <h3>${project.title}</h3>

    <div style="background:#eee; padding:8px; margin-bottom:10px;">
      ${project.locations.map(l=>l.name).join("<br>")}
    </div>

    <table style="width:100%;">
      <tr><td><b>Type</b></td><td>${project.category}</td></tr>
      <tr><td><b>Summary</b></td><td>${project.short}</td></tr>
      <tr><td><b>Details</b></td><td>${project.long}</td></tr>
      ${project.link ? `<tr><td><b>Link</b></td><td><a href="${project.link}" target="_blank">View</a></td></tr>`:""}
    </table>
  `;
}

// SIDEBAR TOGGLE
function toggleSidebar(){
  let sb = document.getElementById("sidebar");
  sb.style.width = sb.style.width === "0px" ? "300px" : "0px";
}

</script>
