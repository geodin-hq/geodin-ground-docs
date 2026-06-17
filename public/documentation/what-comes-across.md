# What comes across from the GeoDin® database

GeoDin® Ground is a **visualisation layer** on top of your GeoDin® database. It deliberately pulls across only what is needed to draw a working 3D ground model inside Civil 3D. Everything else stays in GeoDin®, where the full geotechnical record lives.

This page is the quick reference for what you will and will not find in Civil 3D after importing boreholes.

## What is rendered in Civil 3D

For each imported borehole, GeoDin® Ground brings across:

- **Borehole identifier** - name or code as stored in the GeoDin® database.
- **Coordinates** - X, Y, and the coordinate reference system (CRS) recorded against the borehole.
- **Top elevation** - the ground-surface elevation at the borehole.
- **Total depth** - how deep the borehole was drilled.
- **Layered ground description** - each layer's top, bottom, soil unit, and description text, according to the standard used in the database (EN ISO 14688 / 14689, ASTM D2487, British 5930, Brazilian/Portuguese ABNT).
- **Attached documents** - PDF logs, photos, and other files stored against the borehole in GeoDin®. You can open them from the ribbon without leaving Civil 3D.

From these inputs, GeoDin® Ground draws:

- The borehole as a 3D cylinder, segmented and coloured by soil unit.
- Annotations on the left (borehole metadata) and the right (per-layer ground description).
- On request, interpolated surfaces and 3D solids between boreholes (see [Creating surfaces and volumes](../boreholes/creating-surfaces-and-volumes.md)).

## What is **not** rendered in Civil 3D today

The following **are stored** in the GeoDin® database but are **not** visualised or made queryable inside Civil 3D by GeoDin® Ground:

- **Sample and specimen records** - which samples were taken, at what depth, for what test programme.
- **Classification and index test results** - particle size distribution, water content, Atterberg limits, and similar laboratory results.
- **CPT detail** - full depth-indexed cone-penetration sequences.
- **SPT values.**
- **Groundwater level readings.**
- **Borehole log reports** generated in GeoDin® (see below).

If you need any of the above while working in Civil 3D, open the borehole's attached documents from the ribbon - the full PDF log and any test reports are usually attached there. For anything not attached, go back to GeoDin® for the full record.

## Where these live

| Data type | Lives in |
|---|---|
| Geotechnical record (samples, tests, CPT, SPT, groundwater) | GeoDin® |
| Standards-compliant borehole log reports and cross-sections | GeoDin® |
| 3D ground model on top of the design | GeoDin® Ground (Civil 3D) |
| Design objects (alignments, corridors, structures) | Civil 3D |

For a deeper view of where GeoDin® Ground ends and GeoDin® begins, see [GeoDin® and GeoDin® Ground: where each fits](geodin-vs-ground-boundary.md).
