---
theme: seriph
background: /assets/cover.svg
title: GeoLibre - GIS in your browser
info: |
  ## GeoLibre: GIS in your browser
  A one-hour online workshop from Temple University Libraries.
  GeoLibre is a free, open-source GIS that runs in a web browser.
class: text-center
colorSchema: light
drawings:
  persist: false
transition: slide-left
mdc: true
duration: 60min
---

# GeoLibre

GIS in your browser, with nothing to install\
<br>
Felipe Valdez\
felipe.valdez@temple.edu\
<br>
October 2026

<div class="abs-br m-6 text-xl">
  <a href="https://charlesstudy.temple.edu/calendar/workshops?&t=g&d=0000-00-00&cal%5B%5D=6197&ct%5B%5D=69157" title="More workshops" target="_blank" class="slidev-icon-btn">
    <carbon:information />
  </a>
</div>

<!--
WELCOME (5 min, together with the next three slides)

- Start the recording. Slides, recording and sample data go out by email afterwards.
- Who is in the room: anyone who came to last week's QGIS session? Anyone who has never opened a GIS?
- This session is hands-on. Everything happens in a browser tab.
-->

---
layout: default
---

# Workshop contents

- 🌍 **What GeoLibre is** and why a browser GIS is worth a look
- 🧭 **The workspace**: panels, menus, moving around the map
- 📂 **Add your files**: drag and drop, plus points from a spreadsheet
- 🎨 **Style and inspect**: colors, choropleths, the attribute table
- 🔗 **Remote layers**: load data straight from a URL
- ✏️ **Edit features**: attributes and geometry
- 📤 **Save and share**: a project you can send as a link
- 🏁 **Wrap-up**: desktop, mobile, Jupyter, and where to go next

<!--
One line each. Do not dwell here: the goal is to have everyone on the map within five minutes.

Rough timing:
- Welcome and framing: 5
- Workspace tour: 5
- Step 1 Add your files: 8
- Step 2 Style: 7
- Step 3 Inspect: 6
- Step 4 Layer by URL: 8
- Step 5 Edit: 8
- Step 6 Save and share: 7
- Same project everywhere: 4
- Wrap-up and questions: 2
-->

---
layout: two-cols
layoutClass: gap-12
---

# Get set up

Open GeoLibre in a new tab:

<div class="text-3xl font-bold my-6">
  <a href="https://web.geolibre.app" target="_blank">web.geolibre.app</a>
</div>

Any modern browser works. There is no sign-up and no download.

::right::

<div class="mt-22">

Then download the sample data:

<div class="flex flex-col items-start gap-3 mt-6">
  <DataFile file="philadelphia-neighborhoods.geojson" />
  <DataFile file="philadelphia-neighborhoods.zip" />
  <DataFile file="philly_landmarks.csv" />
</div>

<p class="fine mt-6">
The .zip is a zipped Shapefile. Leave it zipped.
</p>

</div>

<!--
Paste both links into the chat:
- https://web.geolibre.app
- the link to this slide deck, so people can click the three download buttons

Give people a full minute here. Ask for a thumbs-up when the map is on screen.

The three files:
- philadelphia-neighborhoods.geojson: 159 neighborhood polygons (OpenDataPhilly, CC BY 4.0)
- philadelphia-neighborhoods.zip: the same data as a zipped Shapefile
- philly_landmarks.csv: 19 landmarks with longitude and latitude columns (approximate, made for this workshop)
-->

---
layout: image-right
image: https://assets.geolibre.app/images/GeoLibre-demo.webp
backgroundSize: contain
---

# What is GeoLibre?

A free, open-source GIS for visualizing, exploring, and analyzing geospatial data.

- Runs in a **web browser**
- Also a **desktop** app, a **mobile** app, and a **Jupyter** widget
- One project file works in all four
- MIT licensed, developed in the open at [opengeos/GeoLibre](https://github.com/opengeos/GeoLibre)

<p class="fine mt-8">Screenshot: geolibre.app</p>

<!--
GIS in one sentence: software for working with data that has a location attached.

The usual barrier is installation: a large download, admin rights, a managed laptop that will not allow it. GeoLibre removes that step.

If people ask how it compares to QGIS: QGIS is the full desktop workhorse from last week. GeoLibre covers the everyday loop (load, style, inspect, edit, share) with nothing to install. They are complementary, and near the end we will see that GeoLibre can import a QGIS project.
-->

---
layout: default
---

# Why try a browser GIS?

<div class="pillars grid-cols-3">
<div v-click>

### Nothing to install

Open a tab and start. It works on a library computer, a Chromebook, or a locked-down work laptop.

</div>
<div v-click>

### No account to make a map

Loading, styling, inspecting, and editing data all work without signing in.

</div>
<div v-click>

### Your files stay with you

Files you add are processed inside your browser. They are not uploaded to a server.

</div>
</div>

<div v-click class="heads-up">

Data leaves your browser in two cases only: when **you add a layer from a URL**, and when **you choose to share a project**. Sharing a link is also the one step that asks you to sign in.

</div>

<!--
Be precise here, because privacy is a selling point and people will repeat what you say.

- The hosted site is a static site on GitHub Pages. There is no server-side account.
- Files you drop on the map are read by code running in your own browser.
- Adding a remote URL makes your browser request that URL, as any web page would.
- Project → Share uploads the project file to share.geolibre.app. We will look at exactly what that includes in step 6.
- The hosted site counts page visits with Google Analytics. It does not see the data you load.
-->

---
layout: section
transition: slide-up
---

# Hands on

<div class="text-2xl mt-6">
  <a href="https://web.geolibre.app" target="_blank">web.geolibre.app</a>
</div>

<!--
Switch to the browser now and stay there for most of the session. Come back to the slides at the start of each step so people can see the menu names.
-->

---
layout: image-right
image: https://assets.geolibre.app/images/geolibre-interface-overview.webp
backgroundSize: contain
---

# The workspace

- **Layers** panel on the left
- **Map** in the center
- **Style** panel on the right
- **Attribute table** along the bottom
- **Status bar** with coordinates and zoom

Nine menus across the top. Today we use five:

[Project]{.menu} [Edit]{.menu} [Add Data]{.menu} [Plugins]{.menu} [Help]{.menu}

<p class="fine mt-6">Screenshot: geolibre.app</p>

<!--
WORKSPACE TOUR (5 min, with the next slide)

Point at each part on the live app:
- Left edge: Browser and Layers tabs. Click a tab to expand the panel.
- Right edge: Comments and Style tabs.
- Bottom: status bar. Click "Attribute table" to expand it.
- Top right: light/dark toggle and the project name, which is editable.

The other four menus are View, Processing, Controls and Settings. Mention they exist and move on.

Ctrl/Cmd + K opens a command palette that searches every action. Good to know if someone gets lost in the menus.
-->

---
layout: default
---

# Moving around the map

| To do this | Do this |
| --- | --- |
| Pan | Drag the map |
| Zoom | Scroll wheel, or the zoom buttons on the map |
| Rotate | Hold the right mouse button and drag |
| Tilt | Hold <kbd>Ctrl</kbd> / <kbd>Cmd</kbd> and drag |
| Back to north-up, top-down | Press <kbd>R</kbd>, or click the compass button |
| Find a place | Search box at the bottom of the Layers panel |
| Change the basemap | Double-click **Background** at the bottom of the Layers panel |

<!--
Have everyone search for "Philadelphia" in the Layers panel search box and zoom in.

Then have them tilt and rotate once, and press R to reset. People enjoy this, and it shows the map is 3D-capable.

Change the basemap once (Positron is a good quiet background for the choropleth later).

On a trackpad, rotate and tilt gestures vary. If someone is stuck, the on-map compass button resets north.
-->

---
layout: two-cols
layoutClass: gap-10
---

<StepTag :n="1" :min="8" />

# Add your files

1. Drag **philadelphia-neighborhoods.geojson** from your downloads folder onto the map
2. Do the same with **philadelphia-neighborhoods.zip**
3. Find both in the **Layers** panel

::right::

<div class="mt-20">

In the Layers panel you can:

- Show or hide a layer
- Change its opacity
- Drag to reorder
- Zoom to the layer

<div class="heads-up">

Same data, two formats. GeoLibre reads the coordinate system from the file and reprojects it for you.

</div>

</div>

<!--
STEP 1 (8 min, with the next slide)

Demo: drag the GeoJSON onto the map. 159 Philadelphia neighborhoods appear. Then drag the zip.

Talking points:
- A Shapefile is really several files (.shp, .dbf, .shx, .prj). Zipped, it travels as one.
- The two layers sit exactly on top of each other. Toggle one off, lower the opacity of the other.
- For last week's QGIS attendees: GeoLibre reprojects vector files to EPSG:4326 on load, reading the source CRS from the file itself (here the .prj inside the zip).

Remove the Shapefile copy before moving on, so there is one neighborhoods layer.

Other formats that can be dropped: KMZ, GPX. Keep rasters out of the hands-on part: local raster files may need the desktop app.
-->

---
layout: two-cols
layoutClass: gap-10
---

<StepTag :n="1" :min="8" />

# Points from a CSV

A spreadsheet with coordinate columns becomes a point layer.

1. [Add Data → Delimited Text Layer]{.menu}
2. Choose **philly_landmarks.csv**
3. Set the **longitude** and **latitude** columns
4. Add the layer

::right::

<div class="mt-20">

```csv
name,category,longitude,latitude
Philadelphia City Hall,Civic,-75.1636,39.9524
Independence Hall,Historic site,-75.1500,39.9489
Reading Terminal Market,Market,-75.1592,39.9533
30th Street Station,Transit,-75.1820,39.9558
```

<p class="fine mt-4">
Longitude is the x value (east–west). Latitude is the y value (north–south). Swapping them is the most common mistake.
</p>

</div>

<!--
Demo: Add Data → Delimited Text Layer, pick the CSV, confirm the two coordinate columns.

19 points land on the neighborhoods. If they land in the ocean off Antarctica, longitude and latitude are swapped.

Worth saying: this is how most people's first map starts, with a spreadsheet of addresses or coordinates. This dialog can also geocode address columns, which is beyond today.

The coordinates in this file are approximate and made for teaching.
-->

---
layout: image-right
image: https://assets.geolibre.app/images/geolibre-style-panel.webp
backgroundSize: contain
---

<StepTag :n="2" :min="7" />

# Style the layers

Select a layer, then open the **Style** panel.

**One look for everything**

- Fill color, outline color, fill opacity

**Color by a value**

1. Set **Style type** to **Graduated**
2. Pick a numeric **Attribute**
3. Choose **Classes**, a **Scheme**, and a **Colormap**
4. Click **Apply style type**

<!--
STEP 2 (7 min)

Demo on the neighborhoods layer:
1. Simple: a pale fill, a darker outline, fill opacity around 0.5 so the basemap shows through.
2. Graduated: Attribute = Shape_Area, 5 classes, any sequential colormap. This colors neighborhoods by size. It is not a deep insight, but it shows the mechanics of a choropleth.

Then the landmarks layer: bigger circles in a contrasting color. If time allows, try Categorized on the "category" field so museums, parks and stadiums get different colors.

Say out loud: a graduated map needs a numeric field; a categorized map needs a text field with a small number of distinct values.

TEST BEFORE THE SESSION: the exact label for categorized styling in the Style type list.
-->

---
layout: image-right
image: https://assets.geolibre.app/images/geolibre-attribute-table.webp
backgroundSize: contain
---

<StepTag :n="3" :min="6" />

# Inspect the data

Every feature on the map is a row in a table.

1. Click **Attribute table** on the status bar and pick the layer
2. Click a column header to **sort**
3. Type in **Search attributes** to filter rows
4. Click a row: the feature lights up on the map
5. Click **Explore** to profile every field

On the map: turn on **Identify features** for a layer, then click a feature.

<!--
STEP 3 (6 min)

Demo on the neighborhoods layer:
- Open the table. 159 rows, one per neighborhood.
- Sort by Shape_Area. Which neighborhood is largest?
- Search for "Fishtown" or the neighborhood you live in. Click the row and watch the map.
- Explore: shows each field's type, how many values are missing, and the distribution. Use it to answer "what is actually in this data?" before styling.

Then Identify: turn it on for the landmarks layer and click a point to see its popup.

The table and the map share one selection. That link between rows and shapes is the core idea of GIS, so say it explicitly.
-->

---
layout: default
---

<StepTag :n="4" :min="8" />

# Add a layer from a URL

Data does not have to be on your computer. If a file is on the web, GeoLibre can read it in place.

1. [Add Data → Vector Layer]{.menu}
2. Paste a URL
3. Click **Load**

<div class="wrap-code">

World countries, as GeoParquet:

```text
https://data.source.coop/giswqs/opengeos/countries.parquet
```

Philadelphia neighborhoods again, this time straight from GitHub:

```text
https://raw.githubusercontent.com/opendataphilly/open-geo-data/master/philadelphia-neighborhoods/philadelphia-neighborhoods.parquet
```

</div>

<!--
STEP 4 (8 min)

Paste both URLs into the chat so people can copy them.

Demo:
1. Add Data → Vector Layer, paste the countries URL, Load. Zoom out to see the world.
2. Style it as a real choropleth: Graduated on POP_EST or GDP_MD_EST. This is the meaningful version of what we did in step 2.

Talking points:
- GeoParquet is a compact, cloud-friendly format. Large remote files can be streamed in pieces rather than downloaded whole.
- Web services work the same way from the Add Data menu: XYZ tiles, WMS, WFS, ArcGIS services. Show one only if there is time.
- Limitation to name: in a browser, the remote server has to allow cross-origin requests (CORS). If a URL will not load here, it may still load in the desktop app.

This is one of the two moments when something leaves your browser: a request to that URL.

TEST BEFORE THE SESSION: both URLs load on the network you will present from.
-->

---
layout: two-cols
layoutClass: gap-10
---

<StepTag :n="5" :min="8" />

# Edit features

<div>

**Attributes**, in the attribute table:

</div>

1. Click **Edit**, change a cell, click **Save**
2. **Add field** creates a new column
3. **Calculate** fills a field from an expression

```text
round($area("square-kilometers"), 2)
```

Undo with <kbd>Ctrl</kbd> / <kbd>Cmd</kbd> + <kbd>Z</kbd>.

::right::

<div class="mt-20">

**Shapes**, on the map:

1. [Plugins → GeoEditor]{.menu}
2. Draw a new feature, or move the vertices of an existing one

**Take your edits with you**

Click **Export** in the attribute table: GeoJSON, GeoParquet, GeoPackage, KML, zipped Shapefile, or CSV.

</div>

<!--
STEP 5 (8 min)

Do this on the dragged-in neighborhoods GeoJSON layer, not on a layer added by URL (those can be read-only in the table).

Demo:
1. Open the neighborhoods table, click Calculate. Target: Create field "area_km2", Output type Number. Expression: round($area("square-kilometers"), 2). Check the preview, then Calculate.
2. Re-style: Graduated on area_km2. A field made a minute ago now drives the map.
3. Click Edit, fix or change one name, Save.
4. Plugins → GeoEditor. Draw one polygon (your own "neighborhood") or drag one vertex.
5. Export the layer as GeoJSON. That file is now on your computer, with your edits.

Key message: edits live in the browser tab until you export. Export is how you keep them.

TEST BEFORE THE SESSION: that Edit and Calculate are enabled on the dragged-in layer, and the GeoEditor draw flow.
-->

---
layout: two-cols
layoutClass: gap-10
---

<StepTag :n="6" :min="7" />

# Save and share

A project is one small file, **.geolibre.json**. It records the map view, the basemap, and every layer with its source and style.

**In the browser**

- Your work is autosaved in this browser
- [Project → History]{.menu} restores an earlier snapshot
- [Project → Export as HTML]{.menu} writes a standalone page

::right::

<div class="mt-20">

**Share it as a link**

1. [Project → Share]{.menu}
2. Sign in to share.geolibre.app
3. Confirm the title and upload
4. Copy the public link

Anyone can open the link. They do not need an account.

<div class="heads-up">

Saving a project file to disk needs the desktop app.

</div>

</div>

<!--
STEP 6 (7 min, with the next slide)

Sharing needs a share.geolibre.app sign-in. Decide in advance:
- Option A: you share live as a demo and paste the link in the chat. Attendees open it. Nobody else needs an account.
- Option B: attendees who want to can sign in and share their own map.

Option A keeps the "no account" promise of the session intact. Recommended.

Demo:
1. Rename the project (top right).
2. Project → Share. Read the dialog out loud, especially any "layers will be missing" warning.
3. Share, copy the link, paste it in the chat, and open it in a new private window to prove it works without an account.

Autosave lives in this browser on this device only. It is a safety net, not a backup.

TEST BEFORE THE SESSION: sign in to share.geolibre.app once, and check Export as HTML in the browser you will use.
-->

---
layout: default
---

<StepTag :n="6" :min="7" />

# What a shared link carries

The share service stores the project file. It does not store your data files.

| Where the layer came from | Does the other person see it? |
| --- | --- |
| A URL: GeoParquet, tiles, WMS, and so on | Yes. Their browser fetches it from the same URL |
| A small local vector file added with [Add Data → Vector Layer]{.menu} | Yes. It is embedded in the upload |
| Other files on your computer, such as a GeoTIFF | No. The layer is missing for them |

<div class="heads-up">

The Share dialog lists every layer that will be missing <span v-mark.underline.orange>before</span> you upload. Read it. This is the moment data leaves your machine, and it is your choice.

</div>

<!--
This is the honest version of "your data never leaves your machine".

- Nothing is uploaded until you press Share.
- Layers added by URL travel as a reference, so they always work for the recipient (as long as the URL is public).
- Small local vector layers added through Add Data → Vector Layer are embedded in the project file, which means that data does go to share.geolibre.app.
- If the dialog shows "N layers will be missing from the shared map", the button reads "Share anyway".

For a map that always works for others: host the data somewhere public and add it by URL.

For data that must not go anywhere: do not share. Export as HTML, or use the desktop app and send files your usual way.

TEST BEFORE THE SESSION: what the dialog says about the dragged-in neighborhoods layer and the CSV layer, so there are no surprises live.
-->

---
layout: default
---

# The same project, everywhere

<div class="pillars grid-cols-4">
<div>

### Browser

Open a shared link, or [Project → Open From → URL]{.menu}

</div>
<div>

### Desktop

Windows, macOS, Linux. Adds saving to disk and local raster files

</div>
<div>

### Mobile

Open the link on a phone, or use the Android or iOS app

</div>
<div>

### Jupyter

The whole app inside a notebook cell

</div>
</div>

<div class="mt-8">

```python
# pip install geolibre
from geolibre import Map

m = Map()
m.load_project("my-map.geolibre.json")
m
```

</div>

<!--
SAME PROJECT EVERYWHERE (4 min, instructor demo)

Use the link you shared in step 6:
1. Desktop app: Project → Open From → URL, paste the link. Same layers, same styles.
2. Phone: open the link in the phone's browser and hold it up to the camera. The layout adapts to touch. There are also Android and iOS apps.
3. Jupyter or Google Colab: run the cell on the slide. The full GeoLibre interface appears in the output, and Python can read and change the map.

Point: nothing built today is trapped in a browser tab.

Downloads: https://geolibre.app/downloads/

TEST BEFORE THE SESSION: have the desktop app installed, the phone ready, and a notebook already open with geolibre installed. Installing live will eat the four minutes.
-->

---
layout: default
---

# Coming from QGIS?

Last week's concepts carry straight over: layers, the attribute table, coordinate systems, styling by attribute.

- [Project → Import → Import QGIS Project]{.menu} reads a **.qgs** or **.qgz** file and rebuilds its layers, groups, layer order, styling, and saved map view
- Layer styles can be imported from QGIS **QML** files
- GeoLibre reports what it could not bring across and why

<div class="heads-up">

In the browser, layers that point to files on your disk are skipped, because a web page cannot reopen those paths. Open the same project in GeoLibre Desktop to load them.

</div>

<!--
Skip this slide if nobody attended the QGIS session.

Do not demo the import live unless you have tested it with last week's project. The import handles file-based vector layers and rasters the app can open; other providers are listed as skipped.

Framing: QGIS and GeoLibre are not competitors for your attention. Build in whichever suits the task, and use GeoLibre when you need to put a map in front of someone quickly.
-->

---
layout: two-cols
layoutClass: gap-10
---

# Workflow

1. Open [web.geolibre.app](https://web.geolibre.app)
2. Add your files
3. Style the layers
4. Inspect the attributes
5. Add layers from a URL
6. Edit, then export
7. Share a link

::right::

# Keep going

- [User Guide](https://geolibre.app/user-guide/interface/)
- [Tutorial: Your First Map](https://geolibre.app/tutorials/first-map/)
- [Tutorial: Cloud-Native Data](https://geolibre.app/tutorials/cloud-native-data/)
- [Tutorial: Vector Analysis](https://geolibre.app/tutorials/vector-analysis/)
- [Download the desktop app](https://geolibre.app/downloads/)

**Data to practice with**

- [OpenDataPhilly](https://opendataphilly.org/)
- [Temple Open Data](https://temple.maps.arcgis.com/home/index.html)

<!--
WRAP-UP (2 min)

Recap the loop in one breath: add, style, inspect, edit, share.

Tip for beginners exploring on their own: Help → Simplify Interface hides the advanced menus. Switch back to Advanced at any time.

Things we did not touch and people may ask about: 1,000+ processing tools, a SQL workspace, story maps, print layouts. All in the User Guide.

Ask for questions. Remind people the slides, recording and data are on their way by email.
-->

---
layout: default
---

# Credits

<div>

**Software**\
[GeoLibre](https://geolibre.app) by Qiusheng Wu and contributors, MIT license. Screenshots on these slides are from the GeoLibre documentation.

**Sample data**\
Philadelphia neighborhood boundaries from the OpenDataPhilly [open-geo-data](https://github.com/opendataphilly/open-geo-data) repository, attributed to Abaca Labs, [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).\
World countries from the GeoLibre tutorials, hosted on Source Cooperative.\
Landmark coordinates are approximate and were prepared for this workshop.

**Slides**\
Built with [Slidev](https://sli.dev).

</div>

---
layout: end
---

Contact us at:\
felipe.valdez@temple.edu \
<br>
Visit our guides:\
https://guides.temple.edu/gis-mapping
