# Troubleshooting

Short answers to the issues most commonly raised by new users. If you run into something not covered here, [open a support ticket](get-support.md).

## My boreholes don't appear where I expect them

Check the **coordinate reference system (CRS)** on both sides:

- The boreholes carry the CRS recorded against them in the GeoDin® database.
- Your Civil 3D drawing carries its own CRS.

If the two do not match, boreholes can land thousands of kilometres away, on the wrong side of a projection, or at the wrong elevation. Set the Civil 3D drawing CRS to match the data - or transform the data - before drawing.

If the boreholes appear in the right place but at the wrong height, check that the **top elevation** on the GeoDin® side uses the same vertical datum as your drawing.

## Some of my layer colours look wrong

Layer colour is mapped from the **ground-unit configuration** in your GeoDin® database into Civil 3D layer colours. Some of those mappings are currently hard-coded. If a particular unit is not picking up your preferred colour, adjust it directly on the Civil 3D layer after drawing. The mapping will be respected in subsequent regenerations in the same drawing.

## My drawing feels heavy when I load many boreholes

GeoDin® Ground deliberately does not pull the full geotechnical record into the drawing, to keep drawings workable. If Civil 3D still slows down:

- **Reduce the number of boreholes you draw at once.** Load only those relevant to the area you are designing in right now.
- **Generate surfaces and volumes on that subset.** Surface interpolation across many boreholes adds geometric complexity; interpolating across the cluster you actually need is faster and easier to review.
- If you need a site-wide view, generate a coarse ground model from a representative subset first, then refine locally where design work is happening.

## I edited a borehole in Civil 3D - why is the database unchanged?

This is by design. Edits made in Civil 3D - moving, deleting, reshaping boreholes, surfaces, or solids - stay in the drawing and **never write back** to the GeoDin® database.

If you need to change the underlying record, edit the borehole in GeoDin®, then redraw it in Civil 3D. See [GeoDin® and GeoDin® Ground: where each fits](../documentation/geodin-vs-ground-boundary.md) for the rationale.

## I want a legal-quality cross-section

Produce it in GeoDin®, not in Civil 3D. The Civil 3D view is useful for combining ground and design, but **standards-compliant geological hatching** (11 international standards) and the full reporting toolkit live in GeoDin®. Inside Civil 3D, soil units are communicated through Civil 3D layer colours only.

## Can I put the database on Autodesk Docs?

This has not been validated by GeoDin®. Run the database from a local drive or a network share for now.

## The GeoDin® Ground ribbon doesn't show up in Civil 3D

- Confirm you installed GeoDin® Ground against the Civil 3D version you actually launch (2025 or 2026). Installing against a different Civil 3D version does not register the ribbon.
- Restart Civil 3D after installation.
- Open the Autodesk App Store and check that the plug-in is listed as installed for this machine.

## I regenerated the ground model but my changes are gone

When you re-run **Draw Surfaces and Volumes** or **Regenerate Ground Model**, the current surfaces and solids are removed and rebuilt from the boreholes (including any virtual logs). Hand-edits you made with Civil 3D tools on the previous solids are not preserved.

If you want a change to survive regeneration, encode it as a **virtual log** instead - see [Creating a virtual log](../virtual-logs/creating-virtual-logs.md).
