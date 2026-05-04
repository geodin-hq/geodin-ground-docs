# Overlaying your design on the ground model

Because GeoDin® Ground generates **native Civil 3D surfaces and 3D solids**, you can combine the ground model with any Civil 3D design object using the tools you already use every day. There is no separate "GeoDin view" — once the ground model is drawn, it is part of the drawing.

This page walks through how to overlay a design on the ground model and what kinds of queries become possible once both are in the same space.

## Typical workflow

1. **Import your boreholes** for the area of interest ([Importing boreholes](../boreholes/importing-boreholes.md)).
2. **Generate surfaces and volumes** across those boreholes ([Creating surfaces and volumes](../boreholes/creating-surfaces-and-volumes.md)).
3. Bring your design into the same drawing — a tunnel alignment, a road corridor, a bridge foundation, a pipeline route, a dam profile, or any other Civil 3D design object.
4. Use Civil 3D's standard tools to inspect the combined geometry:
   - Section the ground model along your alignment.
   - Measure cover above a tunnel.
   - Clip the ground solids to a design envelope.
5. Run Civil 3D's volume-calculation commands against the ground solids to extract quantities for the design.

## Querying quantities by soil or rock unit

Because `Draw Surfaces and Volumes` produces **one 3D solid per soil layer** — not a single lumped surface — you can ask more precise questions than a traditional surface model allows:

- How much clay will the excavation remove?
- What volume of a specific rock unit will a tunnel bore intersect?
- What is the thickness profile of a single layer along a planned corridor?

Each solid carries the ground-unit classification from the GeoDin® database, so the quantity you compute is directly tied to the geological meaning of the material, not just to elevation.

> **Tip:** For large sites, generate surfaces and volumes only for the cluster of boreholes that covers your current design area. That keeps the drawing light and the Civil 3D volume calculations fast. You can regenerate over a different cluster any time.

## Where this leaves "two worlds" behind

Traditionally, designers worked from PDF borehole logs while the ground model lived in a specialist tool. Overlaying the design on the ground model inside Civil 3D removes that gap:

- The design team and the geotechnical team look at the same 3D representation.
- Design iteration is faster because ground insights are immediately visible against the proposed geometry.
- There is no re-keying of ground data into the design environment.

If you need the full geotechnical record behind any borehole — samples, laboratory tests, CPT detail — open the attached documents directly from Civil 3D (see [Get support](../support/get-support.md) if documents are missing), or go back to GeoDin® for the full record. For a crisp breakdown of what Ground does and does not visualise, see [What comes across from the GeoDin database](what-comes-across.md).
