# User Guide — Meghalaya Historical Image Visualizer

Live viewer: <https://shivnarayanyadav1507-sys.github.io/meg-viewer/>

The Meghalaya Historical Image Visualizer runs entirely in any web browser, and its purpose is to assist in inspecting historical satellite imagery of Meghalaya (2015–2020) and visualising forest-cover change over time. The viewer enables us to load our own Cloud-Optimized GeoTIFFs (COGs), fade between years, and overlay vector boundaries. Nothing is uploaded to a server — the imagery is read directly in the browser itself.

> [!NOTE]
> New here? Read **Interface Overview**, then dip into the feature sections as you need them.

## Contents

- [Interface Overview](#interface-overview)
- [Loading Raster Imagery (COGs)](#loading-raster-imagery-cogs)
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

The viewer has three main components:

- **The Map Canvas** — the main part where all the imagery and vector layers are displayed. All changes and layer positions are visualised here, corresponding to the following components.
- **Layers panel** — the control panel for loading imagery and vectors, choosing the basemap, and adjusting display. In short, it is split into an **Imagery · COG** section and a **Vectors** section.
- **Year timeline** — this controls the historical imagery, giving the ability to fade between years. It is found along the bottom and appears once we have loaded two or more dated COGs.

<img width="1919" height="946" alt="Screenshot 2026-06-17 095127" src="https://github.com/user-attachments/assets/6005b2ca-ae01-44a9-9623-e3fd169313c5" />

You can also **drag and drop** image or vector files straight onto the map to add them.

---

## Loading Raster Imagery (COGs)

The viewer can load and display COG (Cloud-Optimized GeoTIFF) files that we add ourselves. By default, the mosaics for 2015, 2016, 2017, 2018, 2019, and 2020 are already added in the layer panel, streamed as COG files from GitHub.

To add your own data:

1. In the **Imagery · COG** section, click **Load COG files** to add your COG data.
2. For the timeline feature, select **two or more** of your 8-bit COGs to build a timeline.
3. The **year for each image is read from its filename**, so name your files consistently (e.g. include `2015`, `2016`, … in the name).

In the COG imagery panel, the eye icon turns a layer's visibility on or off on the Map Canvas. Use **Clear imagery** to remove all loaded COGs and start over.

<img width="284" height="386" alt="image" src="https://github.com/user-attachments/assets/f1827aa4-0ff1-443e-82eb-f145ec833962" />

> [!TIP]
> A single COG will display, but you need at least two dated COGs for the year timeline and the fade-between-years comparison to work.

<img width="1919" height="950" alt="Screenshot 2026-06-17 095626" src="https://github.com/user-attachments/assets/fd436937-04c8-4059-9d60-ca49f5e64abf" />

---

## RGB and NDVI Modes

The imagery section has two display modes:

- **RGB** — shows the imagery in colour (natural or false colour, depending on the band combo).
- **NDVI** — shows a vegetation index instead, colour-ramped from water and bare ground through to dense forest. This is the quickest way to read vegetation health and spot loss.

Switch between them at any time; the year timeline applies to whichever mode is active.

---

## The Year Timeline

This is the core tool for checking deforestation or any other land-use / land-cover change. As mentioned, once two or more dated COGs are loaded, a timeline appears along the bottom of the screen.

- **Drag to fade between years** — slide along the timeline to cross-fade from one year's image to the next, so changes in forest cover appear as you move.
- **Snap to year** — jump cleanly to a specific year rather than a blended view.
- **Play / speed** — animate through the years automatically; adjust the playback speed.

Fading between an earlier and a later year over the same patch of forest is the fastest way to see where cover has been lost.

---

## Basemaps

Within the imagery section there is a display-settings area, opened via the highlighted settings icon, that includes the basemap, an auto colour fix, band combinations, and brightness adjustment.

<img width="271" height="861" alt="Screenshot 2026-06-17 100325" src="https://github.com/user-attachments/assets/af1bba31-4c32-4e5e-bbce-272c63a542a0" />

As seen in the image below, we can choose the background shown beneath the imagery and vectors. Basemaps are purely for visual assistance, and they are as follows:

- **Satellite (Esri)** — provided by Esri, it helps you work out what's on the ground through real satellite photos.
- **Streets (OSM)** — a drawn map of the world by OpenStreetMap. It is free and made by volunteers. Unlike Esri it is not photos — it shows roads, rivers, the names of towns and villages, and boundaries.
- **Dark canvas** — a plain, dark, low-contrast background. Best for making your imagery, the NDVI colours, and bright vector layers stand out, since nothing in the background competes with them.
- **None** — no background at all (blank). Best used when we want only our own layers visible.

<img width="288" height="441" alt="image" src="https://github.com/user-attachments/assets/69eff1e5-8fb4-4eb8-84bf-446e53c6831d" />

---

## Image Display Adjustments

These are the sets of controls for tuning and refining the COG files. They are usually only needed if an image looks wrong (off-colour or too dark/bright).

**JPEG / WebP colour fix** — handles COGs whose colour needs converting from YCbCr to RGB.

- **Auto-detect (recommended)** — detects and fixes YCbCr JPEG/WebP COGs automatically.
- **Force on (YCbCr→RGB)** — apply the fix manually.
- **Force off (plain RGB)** — treat the data as plain RGB.

DEFLATE- or LZW-compressed COGs do not need this fix.

**Band combo** — for multi-band float mosaics, chooses which bands map to red/green/blue. For now, only **Natural · B4 B3 B2** is available.

**Brightness & 8-bit stretch** — the **Brightness** slider raises or lowers the overall brightness quickly. The **8-bit stretch** boxes set the maximum value per band (R, G, B; min 0). This is like QGIS's **Stretch to MinMax**: copy the R/G/B *Max* values from QGIS into the matching fields here. A **lower Max makes the image brighter**.

---

## NDVI Legend

When we click on the NDVI section, we can add our NDVI to visualise the calculated index. It is a very useful index, especially when applied side by side with a true-colour composite. To make the shades understandable in the viewer, the colour ramp highlights values from water to dense vegetation:

**water → bare → sparse → dense**

Low values correspond to water and bare ground; high values to sparse and then dense vegetation, shown as green shades. Best used to read vegetation health at a glance and to confirm areas flagged as loss.

---

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

The viewer also includes the ability to measure distance and area, with two buttons located at the top-right of the map. Click a button to turn that mode on (it highlights orange), then click on the map to measure distance or area. The active mode shows a prompt telling you what to do. In both modes you click to drop points and double-click on the last point to complete the measurement.

<img width="295" height="114" alt="Screenshot 2026-06-17 123145" src="https://github.com/user-attachments/assets/36f38588-3e55-40e5-a71b-077419021dd5" />

<img width="315" height="119" alt="Screenshot 2026-06-17 123046" src="https://github.com/user-attachments/assets/b9fff22e-ecc9-448a-91df-543b8accd2a3" />

**Distance** (the ruler / diagonal-line icon) — click a starting point and continue clicking along a path; the distance is shown in metres up to 1000 m and then in kilometres beyond that. You can create multiple segments along a route, then double-click to finish, giving the total length.

<img width="1191" height="760" alt="image" src="https://github.com/user-attachments/assets/e94f6a97-0a6c-4e61-b707-42e13ac45d99" />

**Area** (the polygon icon) — click 3 or more points to outline a polygon, then double-click to finish. This gives the enclosed area in hectares, and a perimeter is generated alongside it. You can also download the drawn polygon as a KML file and open it in Google Earth, QGIS, etc.

<img width="1918" height="958" alt="image" src="https://github.com/user-attachments/assets/8d9e12e2-d7d1-4330-88f0-60acf2462791" />

For example, the downloaded KML opened in Google Earth perfectly reflects the polygon's location and shape.

<img width="1919" height="1032" alt="image" src="https://github.com/user-attachments/assets/d7049b96-da74-4579-a59d-2da78c6f6035" />

---

## Labels

Within the Vector layer panel, we can either hide or show text labels such as a name or ID of the added vector layer. To turn a layer's labels on or off, click the **tag / bookmark icon** on that layer's row in the Vectors panel.

To help find the vector layer on the map, we can also **zoom to** the layer by clicking the box-like icon next to the visibility icon. Lastly, we can remove a layer either by clicking **Clear vectors** to remove all layers, or by clicking the **✕** icon to remove it individually.

<img width="274" height="127" alt="image" src="https://github.com/user-attachments/assets/354920b4-b276-4938-91cf-4fe3d4aaf704" />

---

## Tips & Troubleshooting

- **No timeline appears:** you need at least two COGs, and each must have a recognisable year in its filename.
- **Image looks off-colour:** try switching the JPEG / WebP colour fix to *Force on* or *Force off*.
- **Image too dark or washed out:** use the Brightness slider, or lower the R/G/B *Max* values in the 8-bit stretch — lower values brighten the image.
- **Shapefile won't load:** make sure you selected all its parts together (`.shp` + `.dbf` + `.prj`) or loaded it as a `.zip`.
- **Comparing the same spot across years:** use the year timeline's fade rather than reloading images.
