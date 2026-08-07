---
description: >-
  Export a Civil 3D drawing containing a GeoDin Ground model to IFC 4.3, and
  understand how ground units are identified inside the resulting BIM file.
---

# BIM handoff via IFC 4.3

When you export your Civil 3D design to IFC for a BIM handoff, the GeoDin® Ground model travels with it under **IFC 4.3**. Downstream BIM consumers receive the structure together with the ground it sits in, rather than a design object floating in space.

This matters for projects where the ground model is contractually part of the deliverable, for coordination with structural and architectural disciplines, and for owners who maintain a federated BIM of their asset.

## Before you export

Civil 3D itself does not ship an IFC classification taxonomy for geotechnical units. A one-time setup is needed so that your ground solids export with meaningful classification, not just geometry:

1. Decide which Civil 3D layers represent which soil or rock units in your project.
2. Map those layers to your preferred **IFC classification** (for example, an internal code or a publicly maintained geotechnical classification).
3. Save this mapping as part of your project template so every export is consistent.

Without that mapping, the ground solids still export geometrically - the BIM file will contain the correct shapes - but classification metadata will be generic and downstream consumers will not be able to filter or query by ground unit. See [How ground units are identified](#how-ground-units-are-identified) for what that generic case looks like in the file, and how a consumer can still work with it.

### Setting the base point

Before the first export, set the drawing's IFC base point with **Set IFC Base Point** on the **Add-ins** tab's **IFC Infrastructure** panel, next to the export command (see [Running the export](#running-the-export)). The export writes the model against projected real-world coordinates, so a base point that matches your project's survey control keeps the ground model aligned with the rest of the federated model. <!-- src: loom/ifc-export#georeferencing -->

## Running the export

The export is driven by Civil 3D's own IFC exporter, on the **Add-ins** ribbon tab: open the **IFC Infrastructure** panel and choose **Export to IFC**, then pick a location and file name. GeoDin® Ground does not add a separate export command of its own - you export the whole drawing as you normally would, and the ground model travels with it. <!-- src: loom/ifc-export#export-command -->

<figure><img src="../.gitbook/assets/ifc-export-ribbon.png" alt="Civil 3D Add-ins ribbon tab showing the IFC Infrastructure panel with Set IFC Base Point, Export to IFC, and Import from IFC commands"><figcaption><p>The <strong>IFC Infrastructure</strong> panel on the <strong>Add-ins</strong> tab. <strong>Export to IFC</strong> writes the whole drawing, ground model included; <strong>Set IFC Base Point</strong> sits alongside it. Note that the <strong>GeoDin® Ground</strong> tab is separate - these are Civil 3D's own IFC commands, not the plug-in's.</p></figcaption></figure>

## What the IFC export contains

The IFC 4.3 export includes:

- The geometry of every generated surface and volume from GeoDin® Ground.
- The Civil 3D design objects in the same drawing.
- The layer and property mapping you configured (see above).
- A record of the GeoDin® Ground settings the model was generated with (see [Model settings recorded in the file](#model-settings-recorded-in-the-file)).

{% hint style="info" %}
**Note:** IFC 4.3 is the current target. Earlier IFC schemas do not include geotechnical entities in a first-class way. GeoDin® Ground does not yet write those dedicated entities, however - ground units export as generic terrain elements, described under [How ground units are identified](#how-ground-units-are-identified).
{% endhint %}

## When to use this handoff

- You are delivering a **federated BIM** to an owner or main contractor.
- The ground model needs to be **auditable** alongside the design - for example, on infrastructure programs where ground risk is a contractual concern.
- Disciplines that do not use Civil 3D (structures, MEP, architecture) need visibility of the ground in their authoring tool.

If the receiving side only needs a GIS view of the boreholes, see [ArcGIS integration](arcgis-integration.md) instead.

***

## Reference: inside the exported file

This section is for BIM coordinators and anyone writing a downstream consumer of the file. You do not need it to produce a valid handoff.

### File schema and geometry

The exporter writes the `IFC4X3_ADD2` schema. Lengths are meters, areas square meters, volumes cubic meters, and angles radians.

Surfaces and volumes arrive as **triangulated meshes**, not parametric solids: each element carries a tessellated body representation built from a point list and a triangulated face set. Meshes are a faithful copy of what you see in Civil 3D, and they render reliably in any IFC viewer, but they cannot be edited parametrically downstream. The whole model is placed under a single site, against projected real-world coordinates taken from the drawing's IFC base point. <!-- src: loom/ifc-export#schema-and-geometry -->

### How ground units are identified

Unless you have configured the classification mapping described in [Before you export](#before-you-export), ground units are identified in the file by **presentation layer name** and color, carried over from the Civil 3D layers that GeoDin® Ground drew them on. Each element also carries its unit name, for example `GRP1-1 (Sand) TOP`.

This means the layer naming convention is what a downstream consumer filters on. Surfaces carry an `SRFC` prefix, volumes a `VOL` prefix, and boreholes a `LOC` prefix; the full convention, including how the soil type and borehole name are appended, is documented in [Creating surfaces and volumes](../boreholes/creating-surfaces-and-volumes.md).

A consumer that cannot read a formal classification can therefore still separate surfaces from volumes from boreholes, and pick out individual ground units, by matching on these prefixes. <!-- src: loom/ifc-export#layer-naming -->

{% hint style="info" %}
Ground units currently export as generic terrain elements rather than IFC 4.3's dedicated geotechnical entities. See [Known limitations and roadmap](../support/known-limitations-and-roadmap.md) for what that means for a downstream consumer.
{% endhint %}

### Model settings recorded in the file

The export attaches a property set named `Custom_Properties` to the IFC project, recording the settings the ground model was generated with. This travels with the deliverable, so a reviewer can tell how the model was built without access to the original drawing:

| Property | What it records |
|---|---|
| `UUID` | A unique id for this export |
| `GEODIN_SELETED_DATABASE` | Name of the source GeoDin® database |
| `GEODIN_BOREHOLE_DIAMETER` | Borehole display diameter |
| `GEODIN_BOREHOLE_HEIGHT_MULTIPLIER` | Vertical exaggeration applied to boreholes |
| `GEODIN_SURFACE_POINT_SPREAD_SIZE` | Surface interpolation point spread |
| `GEODIN_SURFACE_POINT_SPREAD_NUM_POINTS` | Number of points used in the spread |

{% hint style="warning" %}
**Property name spelling:** `GEODIN_SELETED_DATABASE` is not a docs typo - the property name is misspelled in the file itself. A parser reading these properties must match the name as written.
{% endhint %}

This is the record that makes the handoff **auditable**: two exports of the same site can be compared on the settings that produced them, not just on their geometry. <!-- src: loom/ifc-export#geodin-property-set -->

### Before you send the file on

Two things to check when the recipient is outside your organization:

- IFC records an owner history for the file, which includes the **user name and organization** of whoever ran the export. An `.ifc` file is plain text, so you can check this in any text editor before sending. Review it if that attribution should not leave your team.
- Each export writes a log file alongside the `.ifc`, named after the drawing. The log is a diagnostic aid for the export itself and is not part of the deliverable - send the `.ifc` on its own. <!-- src: loom/ifc-export#owner-history -->
