# BIM handoff via IFC 4.3

When you export your Civil 3D design to IFC for a BIM handoff, the GeoDin® Ground model travels with it under **IFC 4.3**. Downstream BIM consumers receive the structure together with the ground it sits in, rather than a design object floating in space.

This matters for projects where the ground model is contractually part of the deliverable, for coordination with structural and architectural disciplines, and for owners who maintain a federated BIM of their asset.

## Before you export

Civil 3D itself does not ship an IFC classification taxonomy for geotechnical units. A one-time setup is needed so that your ground solids export with meaningful classification, not just geometry:

1. Decide which Civil 3D layers represent which soil or rock units in your project.
2. Map those layers to your preferred **IFC classification** (for example, an internal code or a publicly maintained geotechnical classification).
3. Save this mapping as part of your project template so every export is consistent.

Without that mapping, the ground solids still export geometrically - the BIM file will contain the correct shapes - but classification metadata will be generic and downstream consumers will not be able to filter or query by ground unit.

## What the IFC export contains

The IFC 4.3 export includes:

- The geometry of every generated surface and volume from GeoDin® Ground.
- The Civil 3D design objects in the same drawing.
- The layer and property mapping you configured (see above).

The export is driven by Civil 3D's own IFC exporter - GeoDin® Ground does not add a separate command. You export the whole drawing as you normally would.

> **Note:** IFC 4.3 is the current target. Earlier IFC schemas do not include geotechnical entities in a first-class way.

## When to use this handoff

- You are delivering a **federated BIM** to an owner or main contractor.
- The ground model needs to be **auditable** alongside the design - for example, on infrastructure programmes where ground risk is a contractual concern.
- Disciplines that do not use Civil 3D (structures, MEP, architecture) need visibility of the ground in their authoring tool.

If the receiving side only needs a GIS view of the boreholes, see [ArcGIS integration](arcgis-integration.md) instead.
