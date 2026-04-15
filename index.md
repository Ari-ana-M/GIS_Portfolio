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
<div style="display:flex; height:600px; margin-top:40px; border:2px solid #333; border-radius:10px; overflow:hidden;">

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

</div>

<!-- LEAFLET -->
<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css"/>
<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

<!-- CLUSTER -->
<link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster/dist/MarkerCluster.css"/>
<link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster/dist/MarkerCluster.Default.css"/>
<script src="https://unpkg.com/leaflet.markercluster/dist/leaflet.markercluster.js"></script>

<script>

// INIT MAP
var map = L.map('map').setView([45, -80], 5);

// BASEMAP
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
  attribution: '© OpenStreetMap'
}).addTo(map);

// COLOR FUNCTION
function getColor(category) {
  if (category === "Applied GIS") return "green";
  if (category === "Technical") return "purple";
  return "blue";
}

// CATEGORY LAYERS (for filtering)
const categoryLayers = {
  "Applied GIS": L.markerClusterGroup(),
  "Technical": L.markerClusterGroup(),
  "Research": L.markerClusterGroup()
};

// GROUPED PROJECT DATA
const projects = [

  {
    category: "Applied GIS",
    title: "Field Research Assistant — Coastal Monitoring",
    locations: [
      { name: "Sauble Beach", coords: [44.6296, -81.26508] },
      { name: "Burlington Beach", coords: [43.31523, -79.80701] },
      { name: "Wasaga Beach", coords: [44.52372, -80.0033] }
    ]
  },

  {
    category: "Applied GIS",
    title: "Invasive Species Monitoring",
    locations: [
      { name: "Bernard Lake", coords: [45.72458, -79.3857], link: "https://www.youtube.com/watch?v=5Io_79IMANw" }
    ]
  },

  {
    category: "Applied GIS",
    title: "Municipal Housing Planning",
    locations: [
      { name: "Cambridge", coords: [43.40175, -80.32597] }
    ]
  },

  {
    category: "Technical",
    title: "Climate Data Analysis",
    locations: [
      { name: "Africa", coords: [0, 20], link: "https://ecologyandsociety.org/vol29/iss3/art22/" }
    ]
  },

  {
    category: "Technical",
    title: "ReSEC Lake Ice Research",
    locations: [
      { name: "Great Bear Lake", coords: [66, -121] },
      { name: "Great Slave Lake", coords: [61, -114] }
    ]
  },

  {
    category: "Research",
    title: "ERA5-Land Thesis",
    locations: [
      { name: "Great Bear Lake", coords: [66, -121] },
      { name: "Great Slave Lake", coords: [61, -114] },
      { name: "Lake Athabasca", coords: [59, -109] },
      { name: "Lake Winnipeg", coords: [52, -97] },
      { name: "Lake Superior", coords: [47.7, -87.5] },
      { name: "Lake Huron", coords: [45, -82.4] },
      { name: "Lake Erie", coords: [42.2, -81.2], link: "https://uwspace.uwaterloo.ca/items/b983d97f-d2ec-4c1a-a6d0-82be963c476a" }
    ]
  }

];

// STORE MARKERS
const markerRefs = [];

// ADD MARKERS
projects.forEach(project => {

  project.locations.forEach(loc => {

    let marker = L.circleMarker(loc.coords, {
      radius: 8,
      fillColor: getColor(project.category),
      color: "#000",
      weight: 1,
      fillOpacity: 0.8
    });

    let popup = `<b>${project.title}</b><br>${loc.name}`;
    if (loc.link) popup += `<br><a href="${loc.link}" target="_blank">View Project</a>`;

    marker.bindPopup(popup);

    categoryLayers[project.category].addLayer(marker);

    markerRefs.push({ marker, coords: loc.coords });

  });

});

// ADD ALL LAYERS
Object.values(categoryLayers).forEach(layer => map.addLayer(layer));

// FILTER FUNCTION
function toggleCategory(category) {
  if (map.hasLayer(categoryLayers[category])) {
    map.removeLayer(categoryLayers[category]);
  } else {
    map.addLayer(categoryLayers[category]);
  }
}

// BUILD SIDEBAR
const list = document.getElementById("project-list");

projects.forEach(project => {

  let title = document.createElement("div");
  title.innerHTML = `<b>${project.title}</b>`;
  title.style.marginTop = "10px";
  list.appendChild(title);

  let ul = document.createElement("ul");

  project.locations.forEach(loc => {

    let li = document.createElement("li");
    li.innerText = loc.name;
    li.style.cursor = "pointer";

    li.onclick = () => {
      map.setView(loc.coords, 7);
    };

    ul.appendChild(li);

  });

  list.appendChild(ul);

});

</script>
