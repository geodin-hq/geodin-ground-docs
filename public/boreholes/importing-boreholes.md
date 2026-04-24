# Importing boreholes

This tutorial walks you through importing borehole data from your GeoDin database and visualizing it in Autodesk Civil 3D using our plugin.

***

## Selecting Data to Import

To start, select the borehole data you want to import and draw.

* Existing data connections are automatically discovered if GeoDin is installed.
* If you have no existing connections, click the **Manage data sources** button in the ribbon to add or configure connections.
* Click the **Select data** button in the ribbon to open the selection dialog.\
  &#xNAN;_&#x59;ou can move this dialog to a secondary screen for convenience._

**In the selection dialog:**

* Use the dropdown to choose from all discovered and manually added data connections.
* The project list updates based on the selected connection, showing all available projects.

<figure><img src="../.gitbook/assets/Picture3.png" alt=""><figcaption></figcaption></figure>

***

## Opening a Project and Selecting Boreholes

After choosing a data connection and project:

* Click the **Open project** button in the project overview to open the project in a new tab.
* The new tab displays a treeview structure listing all boreholes and drillings, showing basic drilling data.
* Use the checkboxes in the treeview to select the boreholes you want to import.
* Optionally, click the **Document** button to view related documents for each drilling.

<figure><img src="../.gitbook/assets/Picture4.png" alt=""><figcaption></figcaption></figure>

\---

## Drawing Boreholes in Civil 3D

Once you have made your selection:

* Press the **Draw boreholes** button.
* The plugin retrieves the selected borehole data from GeoDin, including ground layer descriptions. Supported ground layer description standards include:
  * EN ISO 14688 / 146789
  * ASTM D2487
  * British 5930
  * Brazilian/Portuguese ABNT\
    &#xNAN;_&#x49;f multiple description standards are present in a single borehole, the first one (alphabetically) is used._
* After processing, close the dialog to view the imported boreholes in Civil 3D.

**Visualization in Civil 3D:**

* Cogo points are drawn to represent borehole locations.
* 3D cylinders are created and styled/colored according to depth and ground unit/description.
* Each ground layer includes annotations to explain the different layers.
* All 3D objects in Civil 3D contain metadata from GeoDin, such as project, author, and other relevant information.

<figure><img src="../.gitbook/assets/Picture5.png" alt=""><figcaption></figcaption></figure>

> 💡 **Tip:** switch the Civil 3D visual style to **Shaded** to make the cylinders and layer colours easier to read. Use the **Layer Properties** panel to toggle annotations on or off, either for a single borehole or for all boreholes at once.

\---

You have now successfully imported and visualized boreholes from GeoDin in Civil 3D!

## Troubleshooting

**The boreholes don't appear, or appear in the wrong place.** Check that your Civil 3D drawing uses a coordinate reference system compatible with the one recorded against the boreholes in the GeoDin® database. A CRS mismatch can place boreholes thousands of kilometres away or at the wrong elevation. See [Troubleshooting](../support/troubleshooting.md) for the full checklist.

## Related

- [What comes across from the GeoDin® database](../documentation/what-comes-across.md) — the full list of what is and isn't rendered in Civil 3D.
- [Creating surfaces and volumes](creating-surfaces-and-volumes.md) — the natural next step once boreholes are drawn.
