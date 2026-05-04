# Creating Geological Surfaces and Volumes from Borehole Data in Civil 3D

{% embed url="https://www.youtube.com/watch?v=62K8ztaJl1c" %}

This tutorial guides you through the process of generating accurate geological surfaces and volumes in Civil 3D based on previously imported borehole data. You'll learn how to transform your borehole information into comprehensive 3D ground models.

> **Note:** If you notice anything unusual or inaccurate with the 3D representation of surfaces and volumes, we'd appreciate your feedback to improve the experience. Please contact support@geodin.com, and our team will work with you to address any issues.

## Preparing your drawing

Before beginning, ensure that you have successfully imported your borehole data into Civil 3D. The plugin uses this data to:

1. Connect ground layers based on similar soil groups
2. Create relationships between different boreholes
3. Construct a detailed 3D ground model

During this process, the plugin employs "lensing" - a geological concept where soil or rock layers form lens-shaped bodies that thin out toward their edges. This natural phenomenon occurs when sedimentary deposits vary in thickness or are interrupted across an area. Our algorithm optimizes the 3D model to accurately represent these geological lenses, resulting in more realistic ground representations.

<figure><img src="../.gitbook/assets/Picture5.png" alt=""><figcaption></figcaption></figure>


## Selecting boreholes for surface/volume creation

To begin creating surfaces and volumes:

1. Locate the **Draw surfaces and volumes** button in the ribbon interface
2. Note that this button is only enabled when you have imported or created 2 or more boreholes
3. Click the button to initiate the surface generation process
4. Select two or more imported boreholes using any selection method (window selection, individual clicks, etc.)

The plugin intelligently identifies which 3D objects belong to each borehole, regardless of your selection method, and determines which boreholes will contribute to the surface generation.

<figure><img src="../.gitbook/assets/Picture6.png" alt=""><figcaption></figcaption></figure>

## Generation of surfaces and volumes

After confirming your selection (press Enter), the plugin's algorithm performs several sophisticated operations:

1. Groups ground layers based on geological properties (medium type, classification)
2. Combines contiguous layers within each group while respecting geological boundaries
3. Builds initial volumes by sorting layers by depth and constructing 3D representations
4. Extends volumes by connecting to additional relevant boreholes based on spatial visibility
5. Validates connections using geometric intersection tests and probability calculations

The algorithm carefully handles edge cases and ensures that the resulting surfaces accurately represent the geological conditions suggested by your borehole data.

<figure><img src="../.gitbook/assets/ground-model.png" alt=""><figcaption></figcaption></figure>

## Reviewing your result

Once processing completes, you'll see the resulting surfaces and volumes displayed in your Civil 3D environment. These 3D representations provide valuable insights into:

- Soil distribution and layer thickness variations
- Potential geological anomalies or features
- Volume calculations for different soil types

Take time to review the model from different angles to ensure it meets your project requirements.

> ℹ️ **Native Civil 3D entities.** The generated surfaces and 3D solids are native Civil 3D objects. You can edit them with Civil 3D's own tools — cut, move, reshape, trim — without needing any GeoDin®-specific commands. Because there is **one 3D solid per soil layer**, Civil 3D's volume-calculation tools can give you quantities **by soil or rock unit**, not just against a single lumped surface.

## Refining the result

If the auto-interpolated model does not match what you know about the site, use [virtual logs](../virtual-logs/what-are-virtual-logs.md) rather than editing the solids by hand. Virtual logs re-feed your knowledge into the interpolator so that any future regeneration respects it. Hand-edits made with Civil 3D tools on the previous solids are lost when the ground model is regenerated; virtual logs survive.

## Next Steps

With your geological surfaces and volumes created, you can now:

- [Overlay your design on the ground model](../documentation/overlaying-design-on-ground-model.md) — tunnel alignments, road corridors, bridges, pipelines.
- [Hand the combined model off to BIM via IFC 4.3](../documentation/bim-ifc-handoff.md).
- [Refine the model with virtual logs](../virtual-logs/what-are-virtual-logs.md).
- Make adjustments to the model as needed.

For additional assistance or to provide feedback on the surface generation process, please contact our support team.