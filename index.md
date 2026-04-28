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

    <h4>Projects</h4>
    <div id="project-list"></div>

  </div>

  <!-- MAP -->
  <div id="map" style="flex:1; min-width:0;"></div>

  <!-- RIGHT PANEL -->
  <div id="infoPanel" style="
    width:360px;
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
}
.project-link:hover{ color:#DE879D; }
</style>

<script>

// =========================
// MAP
// =========================
var map = L.map('map').setView([52,-90],4);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',{
  attribution:'© OpenStreetMap'
}).addTo(map);

// =========================
// PANELS WIDTH (CRITICAL FIX FOR ZOOM)
// =========================
const LEFT_PANEL_WIDTH = 160;
const RIGHT_PANEL_WIDTH = 360;

// convert to approximate pixel offset correction
function getHorizontalPadding(){
  return [
    LEFT_PANEL_WIDTH / 2,
    RIGHT_PANEL_WIDTH / 2
  ];
}

// =========================
// LAYERS
// =========================
const categoryLayers = {
  "Applied GIS": L.layerGroup().addTo(map),
  "Technical": L.layerGroup().addTo(map),
  "Research": L.layerGroup().addTo(map)
};

const allMarkers = [];
const lakeLayers = {}; // IMPORTANT: preserve polygons separately

// =========================
// RESET STYLE
// =========================
function resetHighlight(){

  // markers
  allMarkers.forEach(m=>{
    m.setStyle({radius:8,color:"#000"});
  });

  // lakes (CRITICAL RESTORE)
  Object.values(lakeLayers).forEach(l=>{
    l.setStyle({
      color:"#333",
      weight:1,
      fillOpacity:0.3
    });
  });
}

// =========================
// SELECT PROJECT (FIXED ZOOM LOGIC)
// =========================
function selectProject(project){

  resetHighlight();

  let group = L.featureGroup();

  project.layers.forEach(l=>{

    group.addLayer(l);

    if(l.setStyle){

      l.setStyle({
        color:"yellow",
        weight:4,
        fillOpacity:0.25
      });

    } else if(l.getLatLng){

      l.setStyle({
        radius:12,
        color:"yellow",
        weight:3
      });

    }
  });

  // 🔥 FIX: padding accounts for panels
  map.fitBounds(group.getBounds(),{
    paddingTopLeft: [LEFT_PANEL_WIDTH + 40, 40],
    paddingBottomRight: [RIGHT_PANEL_WIDTH + 40, 40]
  });

  openPanel(project);
}

// =========================
// PANEL
// =========================
function openPanel(project){

  document.getElementById("infoPanel").style.display="block";

  let locs = project.locations.map(l=>`<li>${l.name}</li>`).join("");

  document.getElementById("panelContent").innerHTML=`
    <h2>${project.title}</h2>
    <ul>${locs}</ul>
    <p>${project.description}</p>
    <a href="${project.link||'#'}" target="_blank">Open Link</a>
  `;
}

function closePanel(){
  document.getElementById("infoPanel").style.display="none";
}

function toggleLeftPanel(){
  const p=document.getElementById("leftPanel");
  p.style.width = p.style.width==="0px"?"160px":"0px";
}

// =========================
// PROJECT DATA (UNCHANGED STRUCTURE)
// =========================
const projects=[

{
title:"ERA5-Land Lake Ice Thesis",
category:"Research",
description:"Lake ice evaluation across 7 Canadian lakes.",
link:"https://uwspace.uwaterloo.ca/items/b983d97f-d2ec-4c1a-a6d0-82be963c476a",
locations:[
{name:"Great Bear Lake",coords:[66,-121]},
{name:"Great Slave Lake",coords:[61,-114]},
{name:"Lake Athabasca",coords:[59,-109]},
{name:"Lake Winnipeg",coords:[52,-97]},
{name:"Lake Superior",coords:[47.7,-87.5]},
{name:"Lake Huron",coords:[45,-82.4]},
{name:"Lake Erie",coords:[42.2,-81.2]}
]
}

];

// =========================
// GEOJSON LAKES (RESTORED + PROTECTED)
// =========================
const lakes={
  "Great Bear Lake":"data/GBL.geojson",
  "Great Slave Lake":"data/GSL.geojson",
  "Lake Athabasca":"data/Athabasca.geojson",
  "Lake Winnipeg":"data/Winnipeg.geojson",
  "Lake Superior":"data/Superior.geojson",
  "Lake Huron":"data/Huron.geojson",
  "Lake Erie":"data/Erie.geojson"
};

Object.entries(lakes).forEach(([name,path])=>{
  fetch(path).then(r=>r.json()).then(data=>{

    const layer=L.geoJSON(data,{
      style:{
        color:"#333",
        weight:1,
        fillOpacity:0.3
      }
    }).addTo(map);

    lakeLayers[name]=layer;
  });
});

// =========================
// RENDER PROJECTS
// =========================
const list=document.getElementById("project-list");

projects.forEach(project=>{

  project.layers=[];

  let div=document.createElement("div");
  div.innerHTML=`<span class="project-link">${project.title}</span>`;
  div.onclick=()=>selectProject(project);
  list.appendChild(div);

  let ul=document.createElement("ul");

  project.locations.forEach(loc=>{

    let marker=L.circleMarker(loc.coords,{
      radius:8,
      fillColor:"blue",
      color:"#000",
      weight:1,
      fillOpacity:0.8
    }).addTo(categoryLayers[project.category||"Research"]);

    project.layers.push(marker);
    allMarkers.push(marker);

    let li=document.createElement("li");
    li.innerText=loc.name;
    ul.appendChild(li);

  });

  list.appendChild(ul);

});

</script>
