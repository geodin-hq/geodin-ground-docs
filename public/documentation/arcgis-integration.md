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

## Bringing the 3D ground model into ArcGIS Pro

<!-- src: loom/arcgis-3d-C -->
Besides overlaying GIS layers inside Civil 3D, there is a third integration path: open the saved Civil 3D drawing directly in an ArcGIS Pro **Local Scene** to bring the full 3D ground model - not just point features - into ArcGIS Pro.

- Start a **Local Scene** project and connect the project geodatabase.
- In the **Catalog** pane, use **Add Folder Connection** to connect the folder where the Civil 3D drawing is saved.
- From the drawing's feature classes, add the **MultiPatch** (the 3D ground model plus boreholes) to the map.
- For elevation, keep the default **WorldElevation3D** surface, or replace **Ground** with your own DEM (for example, a 1 m resolution dataset) for accurate alignment.
- Enable **Navigate Underground** on the **Ground** elevation surface to view the subsurface.
- The borehole text lives in a separate **TextPoint** feature class. Add it to the map, then use **Export Features** to save it into the project geodatabase (for example, as `BH_Annotation`), and remove the raw **TextPoint** layer before styling.
- Style the annotation layer with a single symbol (for example, a thin line marker rotated 90°, in a distinct color) and label it using the **RefName** field.
- Refine label placement as needed.

To publish the result as a browser-viewable web scene, see [Publishing to ArcGIS Online](https://docs.geodin.com/integrations-and-plug-ins/overview/publish-to-arcgis-online) in the GeoDin® documentation.

## Attaching geotechnical reports to borehole annotations

<!-- src: loom/arcgis-3d-D -->
Once the drawing's annotations are in ArcGIS Pro (see the previous section), the exported PDF reports can be attached directly to the document annotations. The full generic recipe lives in the GeoDin® documentation - this is the short version for the Civil 3D-sourced annotation layer:

- Filter the annotation records with **Select By Attributes** (`RefName` contains `document`).
- Add a text field (for example, `AttachKey`) and use **Calculate Field** (Python) to derive the borehole name from the `Layer` value - stripping the `LOC_BASE-` prefix and `-BASIC` suffix, and appending `" -"` so the key prefix-matches exactly one report filename:

```python
def extract_bh(layer):
    layer = layer.upper()

    # Define known prefix and suffix
    prefix = "LOC_BASE-"
    suffix = "-BASIC"

    if layer.startswith(prefix) and layer.endswith(suffix):
        return layer[len(prefix):-len(suffix)] + " -"

    return None
```

- Enable **Attachments** on the feature class (**Properties > Manage**).
- Run **Generate Attachments Match Table** (Key Field = `AttachKey`, Match Pattern = **Prefix**, filtered to `*.pdf`).
- Run **Add Attachments** (Input Join Field = `OBJECTID`, Match Join Field = `MatchID`).
- Verify the attachment via the feature's pop-up.

For the same workflow starting from GeoDin®-exported point layers, see [Attach reports](https://docs.geodin.com/integrations-and-plug-ins/overview/attach-reports).

## Reviewing the model in a web scene

<!-- src: loom/arcgis-3d-F -->
The published model - soil-type volume layers (for example, clay, sand, chalk, limestone) plus boreholes - can be reviewed in **ArcGIS Online Scene Viewer** in the browser. Use the **Slice** tool (under **Scene tools**; hold **Shift** for a vertical slice) to cut into the model and inspect subsurface structure and borehole relationships. Slices can be captured as slides for reporting.

Set the borehole point layer's elevation placement to **On the ground** so location markers sit on the surface instead of inside the model.

> 🌐 **Try it live:** a public demo scene produced with this workflow is available at [arcg.is/0rD1OL3](https://arcg.is/0rD1OL3) — open it in Scene Viewer to explore the soil-type volumes, borehole annotations, and the Slice tool without setting anything up. <!-- src: loom/arcgis-3d-F -->

Esri's Scene Viewer documentation covers general navigation, styling, and slide capture.
