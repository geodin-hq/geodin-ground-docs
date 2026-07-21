# ArcGIS integration

GeoDin® Ground and Esri's **ArcGIS for AutoCAD** plug-in can coexist inside the same Civil 3D session. Together they let you overlay GIS context onto your boreholes, and share selected boreholes outward to stakeholders who work in ArcGIS rather than CAD.

There is no special wiring between the two plug-ins. Each is installed independently; once both are present in Civil 3D, their commands simply coexist on the ribbon.

## Install requirements

- GeoDin® Ground installed (see [Installation](../getting-started/installation.md)).
- Esri **ArcGIS for AutoCAD** plug-in installed. This is Esri's free plug-in for AutoCAD and Civil 3D.
- The two plug-ins are installed against the same Civil 3D version.

## What this unlocks

### Overlay GIS layers over your boreholes

Once both plug-ins are loaded, you can pull layers from Esri's **Living Atlas** - or from your organisation's ArcGIS Online - into the Civil 3D drawing as reference:

- Satellite imagery
- Topography and hillshade
- Land use and zoning
- Hydrology and floodplain layers
- Any shared layer your organisation publishes to ArcGIS Online

With these layers underneath your borehole sticks, the geotechnical data is instantly placed in its real-world context - next to roads, rivers, protected areas, existing infrastructure.

### Push a borehole (or the full set) to ArcGIS Online

You can share the selected features outward so non-CAD stakeholders can see them on a web map:

- Individual boreholes or the full set as point features.
- Attribute data carried along (name, elevation, depth, and any attributes exposed through the GeoDin® database).

This is useful for steering committee reviews, public consultations, and cross-team alignment with a GIS team that does not open Civil 3D files.

## When to use which tool

| Goal | Tool |
|---|---|
| 3D visualisation and design integration of ground data | GeoDin® Ground |
| GIS-style 2D overlays behind the boreholes | ArcGIS for AutoCAD |
| Sharing boreholes as a web map to non-CAD stakeholders | ArcGIS for AutoCAD (push to ArcGIS Online) |
| Editing the underlying borehole record | GeoDin® (the desktop application) |
<!-- src: loom/arcgis-3d-C -->
| Bringing the full 3D ground model (not just points) into ArcGIS Pro | Open the Civil 3D drawing directly in an ArcGIS Pro Local Scene |

The two plug-ins are complementary. You do not have to pick one: a typical workflow brings both into the same drawing, uses GeoDin® Ground for the 3D ground model, and uses ArcGIS for AutoCAD for 2D GIS context and outward sharing.

## Georeferencing the drawing

<!-- src: loom/arcgis-3d-B -->
Before overlaying GIS layers or exporting the drawing to other tools, make sure the drawing itself carries the correct coordinate system:

- On the **ArcGIS** ribbon in Civil 3D (ArcGIS for AutoCAD), choose **Coordinate System > Assign**.
- Enter the drawing's coordinate system.
- Save the drawing to persist the setting.

This prevents CRS-mismatch issues when overlaying GIS layers or exporting the drawing later.

## Taking the model further in ArcGIS Pro

<!-- src: loom/arcgis-3d-C -->
Beyond the two plug-ins above, there is a third integration path: open the saved Civil 3D drawing directly in ArcGIS Pro to work with the **full 3D ground model** — and take it all the way to a browser-based web scene. This is covered as a step-by-step tutorial series, from bringing the model in to sharing it with stakeholders:

1. [Bringing the ground model into ArcGIS Pro](arcgis-pro-ground-model.md) — open the drawing in a Local Scene, navigate underground, and turn the raw annotation data into readable borehole labels.
2. [Extracting boreholes, the model, and soil types](arcgis-pro-extract-features.md) — split the MultiPatch into separate feature classes per dataset using definition queries.
3. [Attaching geotechnical reports to borehole annotations](arcgis-pro-attach-reports.md) — wire each borehole's PDF report to its document annotation with a matching key.
4. [Publishing and reviewing the model as a web scene](arcgis-web-scene.md) — convert units, set the coordinate system, publish to ArcGIS Online, and review the model (including the Slice tool) in Scene Viewer.

A public demo scene produced with this series is available at [arcg.is/0rD1OL3](https://arcg.is/0rD1OL3).
