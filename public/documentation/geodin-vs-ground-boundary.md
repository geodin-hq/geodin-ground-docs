# GeoDin® and GeoDin® Ground: where each fits

GeoDin® Ground is intentionally scoped. It handles **ground visualisation and interaction inside Civil 3D** — nothing more. The rest of the geotechnical workflow stays in GeoDin®, where the reporting engine, templates, scripting surface, and data-entry UI live.

Knowing where the boundary sits helps you answer the question "which tool do I use for this?" quickly.

## A simple rule of thumb

- Use **GeoDin®** for anything that touches the **geotechnical record itself**.
- Use **GeoDin® Ground** for anything that combines that record with a **Civil 3D design**.

## What stays in GeoDin®

The following are **not** exposed inside the Civil 3D plug-in:

- **Report generation** — borehole logs, cross-section reports, and bulk PDF output. The reporting engine and templates live in GeoDin®.
- **Standards-compliant geological hatching** — GeoDin® supports 11 international hatching standards. Inside Civil 3D, soil units are communicated through Civil 3D layer colours only. For report-quality, standards-compliant hatching, produce the cross-section in GeoDin®.
- **Python scripting** — the scripting surface available in GeoDin® is not available inside GeoDin® Ground.
- **Data entry and editing of the underlying records** — add, edit, or reorganise boreholes, samples, and test results in GeoDin®. Changes made in Civil 3D to drawn boreholes or solids stay in the drawing and **do not propagate back** to the database.

## What stays in GeoDin® Ground

- Connecting the Civil 3D drawing to a GeoDin® database.
- Drawing boreholes as 3D sticks with metadata and layer annotations.
- Interpolating surfaces and 3D solids between boreholes.
- Creating virtual logs to refine the ground model.
- Opening attached borehole documents from Civil 3D.
- Handing the combined design + ground model off to BIM via IFC 4.3 (see [BIM handoff](bim-ifc-handoff.md)).

## Why the boundary is drawn here

Two reasons:

1. **Data integrity.** Civil 3D drawings are easy to change by accident. Treating the GeoDin® database as read-only from the Civil 3D side protects the geotechnical record from unintended edits.
2. **Avoiding duplication.** Civil 3D already has strong tools for editing surfaces, computing volumes, running alignments, and generating sections. GeoDin® Ground deliberately does not duplicate them — instead, the ground model is exposed as **native Civil 3D objects**, so Civil 3D's own tools work on them out of the box.

## Frequently asked "where does this happen?"

| Task | Where |
|---|---|
| Add a new borehole to the record | GeoDin® |
| Correct a typo in a borehole name | GeoDin® (then reload in Civil 3D) |
| Draw a standards-compliant borehole log | GeoDin® |
| Draw a legal-quality cross-section with hatching | GeoDin® |
| Model the ground under a Civil 3D design | GeoDin® Ground |
| Compute volumes of each soil unit under a road corridor | GeoDin® Ground + Civil 3D tools |
| Run a Python script against the geotechnical record | GeoDin® |
| Push a borehole to ArcGIS Online | ArcGIS for AutoCAD, alongside GeoDin® Ground (see [ArcGIS integration](arcgis-integration.md)) |
