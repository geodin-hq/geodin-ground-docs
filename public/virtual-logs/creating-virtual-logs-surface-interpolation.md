# Creating a virtual log from surface interpolation

The **Surface Interpolation** option creates a virtual log by sampling the **currently generated ground model** at your chosen location. Instead of copying from the nearest real borehole, the plug-in reads the interpolated top and bottom of every layer where the virtual log is placed - as if the borehole were drilling through the existing 3D solids.

Use this when:

- You already have a ground model generated, and you want to **lock in** what the model currently predicts at a specific location as a constraint for future regenerations.
- You want to add an intermediate control point between existing boreholes to stabilise the interpolation during iteration.
- You want to refine the ground model at a known point where you have a prediction but no real drilling.

## Before you start

- You have imported at least two real boreholes.
- You have run **Draw Surfaces and Volumes** at least once - Surface Interpolation needs an existing 3D model to sample from.

## Steps

1. On the **GeoDin® Ground** ribbon, click **Virtual Log**.
2. From the submenu, select **Surface Interpolation**.
3. Place the virtual log:
   - Type the coordinates in the command line, or
   - Click directly in the drawing where you want the virtual log to sit.
4. The plug-in intersects the current surfaces and volumes at that location and **copies the resulting stratigraphy** - layer tops, bottoms, and soil units - into the Virtual Log Designer dialog.
5. Adjust the sampled stratigraphy as needed:
   - Update layer properties if you have better information than the interpolation.
   - Add, remove, or reorder layers to encode local knowledge.
6. Set a unique **Name** and confirm the **Elevation** of the ground surface at the virtual log location.
7. Click **Save to drawing** (or **Add and refresh layer generation** to save and immediately regenerate surfaces and volumes).

After saving, the virtual log appears in the drawing alongside the real boreholes. From this point on, any regeneration of the ground model will treat it as an additional control point.

## After creating the virtual log

- Re-run **Draw Surfaces and Volumes** - or use **Add and refresh layer generation** when saving - to rebuild the 3D ground model with the new log included. See [Updating the ground model](updating-surfaces.md).
- Virtual logs, including those created from surface interpolation, are **not persisted to the GeoDin® database**. They exist only in the current Civil 3D drawing.

## Why this mode matters

`Draw Surfaces and Volumes` rebuilds the ground model from scratch each time it runs. Without constraints, a small change - adding a new real borehole, for example - can shift the interpolation in areas you were happy with.

Dropping in a Surface Interpolation virtual log at a point you trust turns that interpolation into a **fixed reference** that future regenerations will respect, which makes the ground model stable to iterate on.

## When not to use Surface Interpolation

- Before you have run `Draw Surfaces and Volumes` at least once. There is no model to sample from yet.
- In an area where the current interpolation is known to be wrong - sampling it would lock in the wrong values. Use [**Empty**](creating-virtual-logs.md) or [**Nearest Borehole**](creating-virtual-logs-nearest-borehole.md) and enter the correct stratigraphy manually.
