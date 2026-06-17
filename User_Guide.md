# User Guide — Meghalaya Historical Image Visualizer (https://shivnarayanyadav1507-sys.github.io/meg-viewer/)
The Meghalaya Historical Image Visualizer runs entirely in any web browser and it's purpose is its assitance in inspecting historical satellite imagery of Meghalaya (2015–2020),  visualising the forest-cover change over time. The viwers enalbles us to load our own Cloud Optimized GeoTIFFs (COGs), had the capability to fade between years, and for overlaying vector boundaries. Nothing is uploaded to a server, the imageries are read directly in the browser itself.

> [!NOTE]
> New here? Read **Interface Overview**, then dip into the feature sections as you need them.

## Contents

- [Interface Overview](#interface-overview)
- [Loading Imagery (COGs)](#loading-imagery-cogs)
- [RGB and NDVI Modes](#rgb-and-ndvi-modes)
- [The Year Timeline](#the-year-timeline)
- [Basemaps](#basemaps)
- [Image Display Adjustments](#image-display-adjustments)
- [NDVI Legend](#ndvi-legend)
- [Vector Layers](#vector-layers)
- [Measuring](#measuring)
- [Labels](#labels)
- [Tips & Troubleshooting](#tips--troubleshooting)

---
## Interface Overview

The viewer has basically three main components:

- **The Map Canvas** — the main part where all the imageries and vector layers are displayed. All the changes and location of layers are visualised here, corresponding to the following components. 
- **Layers panel** — It is the control panel for loading imagery and vectors, choosing the basemap, and adjusting display. In short, it is split into an **Imagery · COG** section and a **Vectors** section.
- **Year timeline** — This controls the historical imagery , basically giving the ability to fade between years. It is found along the bottom and appears once we have loaded two or more dated COGs for moving between years.
<img width="1919" height="946" alt="Screenshot 2026-06-17 095127" src="https://github.com/user-attachments/assets/6005b2ca-ae01-44a9-9623-e3fd169313c5" />
You can also **drag and drop** image or vector files straight onto the map to add them.

---

## Loading Raster Imagery

The viewer has to capability of loading and displaying COG (Cloud-Optimized GeoTIFFs) files that we add ourselves. However, by default the viewer , the mosaics of 2015, 2016, 2017, 2018, 2019 and 2020 are added in the layer panel, which is done through streaming their COG files from GitHub.
Therefore, the steps are as follows:
1. In the **Imagery · COG** section, click **Load COG files** to added your COG data.
2. For the timeline feature, select **two or more** of your 8-bit COGs to build a timeline.
3. The **year for each image is read from its filename**, so name your files consistently (e.g. include `2015`, `2016`, … in the name).

In the COG imagery panel, the eye icon represents the ability to turn off or turn on the layers visibility on the Map Canvas. Additionally, use **Clear imagery** to remove all loaded COGs and start over.
<img width="284" height="386" alt="image" src="https://github.com/user-attachments/assets/f1827aa4-0ff1-443e-82eb-f145ec833962" />
> [!KEYNOTE]
> A single COG will display, but you need at least two dated COGs for the year timeline and the fade-between-years comparison to work.
<img width="1919" height="950" alt="Screenshot 2026-06-17 095626" src="https://github.com/user-attachments/assets/fd436937-04c8-4059-9d60-ca49f5e64abf" />


---

## Display Settings and NDVI 

Within the imagery section, the following features are found within it:

# Display Settings — Includes the basemap, an auto correct colour fix and band combinations and brightness adjustment. 
<img width="271" height="861" alt="Screenshot 2026-06-17 100325" src="https://github.com/user-attachments/assets/af1bba31-4c32-4e5e-bbce-272c63a542a0" />
The highlight settings icon is where we can access the display settings.

# Basemaps


As per seen in the image below, we can choose the backgrounds shown beneath the imagery and vectors. Basemaps are purely for visual assistance and they are as follows:

Satellite (Esri) — Provided by ESRI, it helps you work out what's on the ground through satellite. 
Streets (OSM) — A drawn map of the world by OpenStreetMap. It is free and made by volunteers. Unlike ESRI, it is not photos ,it shows roads, rivers, the names of towns and villages, and boundaries. 
Dark canvas — A plain, dark, low-contrast background. Best for making your imagery, the NDVI colours, and bright vector layers stand out, since nothing in the background competes with them.
None — Basically no background at all (blank). Best use when we want only owr own layers visible. 
<img width="288" height="441" alt="image" src="https://github.com/user-attachments/assets/69eff1e5-8fb4-4eb8-84bf-446e53c6831d" />


## Image Display Adjustments

The are the sets of controls for tuning and refining the COG files. However. this would be usually only needed if an image looks wrong (off-colour or too dark/bright).

**JPEG / WebP colour fix** — This handles COGs whose colour needs converting from YCbCr to RGB .

- **Auto-detect (recommended)** — It detects and fixes YCbCr JPEG/WebP COGs automatically.
DEFLATE- or LZW-compressed COGs do not need this fix.

**Band combo** — It is for multi-band float mosaics, chooses which bands map to red/green/blue:

- However, for now only **Natural · B4 B3 B2** is avaialble. 

**Brightness (8-bit stretch · Max per band, Min 0)** — This is for adjusting and setting the maximum value for the R, G, and B bands. This is like  QGIS's **Stretch to MinMax**: copy the R/G/B *Max* values from QGIS into the matching fields here. A **lower max makes the image brighter**.

---

## NDVI Legend

When we click on the  NDVI section, we can add our NDVI to visualize the calcuated NDVI. It is a very useful indice especially when applied side by side with a true colour composite. To make the shades understandable in the viewer, the colour ramp basically highlights the shades from water to dense. 
Basically-
**water → bare → sparse → dense**
Low values correspond to water and bare ground; high values to sparse and then dense vegetation visualised as green shades. Best to use it to read vegetation health at a glance and to confirm areas flagged as loss.

---
## The Year Timeline

This is the core tool for checking deforestation or any other land use land cover changes. As mentioned, once two or more dated COGs are loaded, a timeline appears along the bottom of the screen.

- **Drag to fade between years** — slide along the timeline to cross-fade from one year's image to the next, so changes in forest cover appear as you move.
- **Snap to year** — jump cleanly to a specific year rather than a blended view.
- **Play / speed** — animate through the years automatically; adjust the playback speed.

Fading between an earlier and a later year over the same patch of forest is the fastest way to see where cover has been lost.
- **NDVI** — shows a vegetation index instead, colour-ramped from water and bare ground through to dense forest. This is the quickest way to read vegetation health and spot loss.

Switch between them at any time; the year timeline applies to whichever mode is active.

---

---

#
## Vector Layers

You can add vector layers and overlay boundaries and other vector data on top of the imagery.
<img width="290" height="309" alt="Screenshot 2026-06-17 095942" src="https://github.com/user-attachments/assets/8b5e5d31-4fbd-4dda-9bab-145667c2952f" />

1. In the **Vectors** section, click **Add vector** (or drag the files onto the map).
2. Supported formats:
   - **KML**
   - **GeoJSON**
   - **Shapefile** — select the `.shp`, `.dbf`, and `.prj` parts together, or load a single `.zip`.
   - **GeoPackage** (`.gpkg`)

Use **Clear vectors** to remove all vector layers.

> [!IMPORTANT]
> For shapefiles, the `.shp` on its own is not enough — include at least the `.dbf` and `.prj` (or zip the whole set), or the layer won't load correctly.

---

## Measuring


The viewer has a measure tool with two buttons, top-right of the map. Click a button to turn that mode on (it highlights orange), then click on the map to measure. The active mode shows a prompt telling you what to do.

Distance (the ruler / diagonal-line icon) — click points along a path, then double-click to finish. Gives you the total length.
Area (the polygon icon) — click 3 or more points to outline a shape, then double-click to finish. Gives you the enclosed area. You can also download the polygon you drew, so a measured shape can be saved and reused as a vector layer (for example, brought into QGIS or back into this viewer).


In both modes you click to drop points and double-click on the last point to complete the measurement.

<img width="295" height="114" alt="Screenshot 2026-06-17 123145" src="https://github.com/user-attachments/assets/36f38588-3e55-40e5-a71b-077419021dd5" />
<img width="315" height="119" alt="Screenshot 2026-06-17 123046" src="https://github.com/user-attachments/assets/b9fff22e-ecc9-448a-91df-543b8accd2a3" />


---

## Labels

Vector layers can show text labels (for example, parcel names or IDs) drawn from their attributes. Toggle labels on or off as needed.

<!-- TODO: confirm where the label toggle lives and which attribute drives the label text. -->

---

## Tips & Troubleshooting

- **No timeline appears:** you need at least two COGs, and each must have a recognisable year in its filename.
- **Image looks off-colour:** try switching the JPEG / WebP colour fix to *Force on* or *Force off*.
- **Image too dark or washed out:** adjust the R/G/B *Max* values under Brightness — lower values brighten the image.
- **Shapefile won't load:** make sure you selected all its parts together (`.shp` + `.dbf` + `.prj`) or loaded it as a `.zip`.
- **Comparing the same spot across years:** use the year timeline's fade rather than reloading images.
