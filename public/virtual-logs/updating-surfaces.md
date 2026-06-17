# Updating the ground model

When working with geotechnical data in Civil3D, you may need to update your ground model after adding virtual logs or importing new boreholes. This tutorial walks you through the process of updating surfaces and volumes to reflect these changes in your geotechnical design.

## When to update surfaces and volumes

Given a ground model of boreholes, you have the ability to import additional boreholes or create artificial ones by making virtual logs. While the action to update the surface/volumes is relatively simple, it's important to note that many different scenarios might require you to update them. Some examples are:

- Deleting a borehole(s)
- (Re)importing additional borehole(s)
- Creating virtual log(s)
- Changing settings or parameters

However, in this tutorial we will showcase the example of creating virtual logs. The principle is the same where the underlying data or boreholes have changed, and there we need to update the surface/volumes to get the correct insights and calculations in your geotechnical design.

<figure><img src="../.gitbook/assets/regenerate-ground-model-ribbon.png" alt=""><figcaption></figcaption></figure>

## Before regeneration

To get started, we assume you have done all previous steps of creating a drawing with boreholes. You have imported boreholes and generated the surface/volumes previously. Below you will find two examples. In example A, we have a previous model, where we have added a virtual log to correct the edges of the ground model. In example B, we have extended the original ground model with additional boreholes outside the original area.

| Example A: Edge Correction | Example B: Extending Area |
|---------|--------------|
| <figure><img src="../.gitbook/assets/virtual-log-result.png" alt=""><figcaption></figcaption></figure> | <figure><img src="../.gitbook/assets/example-b-begin.png" alt=""><figcaption></figcaption></figure> |

## Regenerating the ground model

Given these new boreholes next to the existing model, we simple have to press the _Regenerate ground model_ button in the ribbon to redraw the surfaces and volumes. All current created surfaces and volumes are removed, and the plugin restarts the original process of creating the 3D representation. But, this time it accounts with the newly created boreholes and includes them into the consideration of the algorithm.


| Example A: Edge Correction (result) | Example B: Extending Area |
|---------|--------------|
| <figure><img src="../.gitbook/assets/example-a-result.png" alt=""><figcaption></figcaption></figure> | <figure><img src="../.gitbook/assets/example-b-result.png" alt=""><figcaption></figcaption></figure> |

## Save and regenerate in one step

When creating a new virtual log, you can skip the separate regeneration step: in the Virtual Log Designer dialog, click **Add and refresh layer generation** instead of **Save to drawing**. The virtual log is saved and the ground model is rebuilt immediately, taking the new log into account. This is the fastest way to iterate when you are placing several virtual logs to refine a particular area.

## What survives regeneration

- **Boreholes and virtual logs** - these are the inputs and are preserved across every regeneration.
- **Hand-edits made on the previous solids with Civil 3D tools** - these are **not** preserved. `Regenerate Ground Model` rebuilds the surfaces and volumes from scratch each time.

If you want a change to survive regeneration, encode it as a [virtual log](what-are-virtual-logs.md) rather than editing the generated solid directly.