# Known limitations and roadmap

A transparent summary of what GeoDin® Ground does well today, what it deliberately does not do, and what is planned. Keep this page bookmarked - it is refreshed as the plug-in evolves.

## Known limitations today

### Import is one-way

Edits made in Civil 3D - moving, deleting, or reshaping boreholes, surfaces, or solids - **do not propagate back** to the GeoDin® database. This is deliberate: Civil 3D drawings are easy to change by accident, and the GeoDin® database is protected from those changes. See [GeoDin® and GeoDin® Ground: where each fits](../documentation/geodin-vs-ground-boundary.md) for the rationale.

### Layer matching has no semantic hints

When `Draw Surfaces and Volumes` interpolates between boreholes, it matches layers by **soil type alone**. In geologically simple sites this works very well. In complex stratigraphies - where, for example, two distinct clay layers of different ages should not be bonded - the algorithm may connect them anyway.

**Workaround today:** use [virtual logs](../virtual-logs/what-are-virtual-logs.md) to constrain the interpolation, or clean up the result with Civil 3D's own solid-editing tools.

### Report-quality geological hatching lives in GeoDin®

Inside Civil 3D, soil units are communicated through **Civil 3D layer colours only**. Wrapping a cylinder with a standards-compliant hatch pattern (for example, a full USCS pattern) is not available out-of-the-box.

**Workaround today:** for a legal-quality, standards-compliant cross-section, produce it in GeoDin® itself, which supports 11 international hatching standards.

### Some data in the GeoDin® database is not yet visualised

GeoDin® Ground currently does not render samples, classification test results, CPT detail, SPT values, or groundwater readings inside Civil 3D. The full record remains available in GeoDin® and via attached documents. See [What comes across from the GeoDin® database](../documentation/what-comes-across.md) for the full list.

### No dedicated cross-section command inside the plug-in

To cut a cross-section through the ground model today, use Civil 3D's native alignment and section tools - intersect an alignment plane with the generated surfaces.

## Roadmap

The GeoDin® and Autodesk teams are collaborating on the following areas. This is a directional list; release timing and scope may change.

### Richer layer-matching input

Let users tag layers with additional information - for example, **geological age**, **genesis**, or **depositional environment** - so the plug-in can match corresponding layers more reliably instead of bonding every layer with the same soil type. This is the primary improvement queued for complex stratigraphies.

### Native cross-section command

A dedicated cross-section command inside GeoDin® Ground's ribbon - faster than the Civil 3D alignment + section workflow and tuned for geotechnical use.

### Volumetric quantity calculations

Expanded calculations that surface volumetric information directly from the ground model, to support design bills of quantities and carbon/cost modelling.

### Better merges of geophysics data

Improved ability to combine geophysical datasets with borehole-derived ground models, to help plan site investigations and reduce drilling while maintaining design confidence.

---

For current release notes, see [Release Notes](release-notes.md). If there is a limitation that blocks your work, [let us know](get-support.md) - the team uses customer input directly to prioritise the roadmap.
