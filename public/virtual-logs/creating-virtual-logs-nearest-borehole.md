# Creating a virtual log from the nearest borehole

The **Nearest Borehole** option is the fastest way to place a virtual log in a location where you expect the stratigraphy to resemble a nearby real borehole. Instead of typing every layer by hand, GeoDin® Ground copies the layer sequence from the closest real borehole and lets you refine it.

Use this when:

- You want to extend the data density in an area that is geologically similar to a nearby borehole.
- A real borehole is just outside the design corridor and you need a virtual log inside it.
- You are starting from a known good stratigraphy and only want to tweak one or two layers.

## Before you start

- You have imported at least one real borehole into the drawing. Nearest Borehole needs a real borehole to copy from.
- If the new virtual log should constrain the ground model, make sure the real borehole you expect it to copy from is the closest to your chosen location.

## Steps

1. On the **GeoDin® Ground** ribbon, click **Virtual Log**.
2. From the submenu, select **Nearest Borehole**.
3. Place the virtual log:
   - Type the coordinates in the command line, or
   - Click directly in the drawing where you want the virtual log to sit.
4. The plug-in identifies the nearest real borehole and **copies its layer sequence** — soil or rock types, layer depths, and descriptions — into the Virtual Log Designer dialog.
5. Adjust the copied stratigraphy as needed:
   - Update individual layer properties (soil/rock type, depth).
   - Add new layers between existing ones, or remove layers that you know are not present at the new location.
   - Reorder layers if local knowledge indicates a different sequence.
6. Set a unique **Name** and confirm the **Elevation** of the ground surface at the virtual log location.
7. Click **Save to drawing** (or **Add and refresh layer generation** to save and immediately regenerate surfaces and volumes).

The virtual log is drawn in the same style as real boreholes — a 3D cylinder with annotations — but remains distinguishable by its name.

## After creating the virtual log

- Re-run **Draw Surfaces and Volumes** — or use **Add and refresh layer generation** when saving — to rebuild the 3D ground model with the new log included. See [Updating the ground model](updating-surfaces.md).
- Virtual logs, including those created from the nearest borehole, are **not persisted to the GeoDin® database**. They exist only in the current Civil 3D drawing.

## When not to use Nearest Borehole

If the area where you want to add a virtual log is geologically different from every nearby real borehole, Nearest Borehole will copy a misleading starting point. In that case, either:

- Use the [**Empty**](creating-virtual-logs.md) option and enter the stratigraphy by hand, or
- Use the [**Surface Interpolation**](creating-virtual-logs-surface-interpolation.md) option to sample the stratigraphy predicted by the current ground model at that location.
