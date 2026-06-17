# Installation

GeoDin® Ground is distributed as a free plug-in on the **Autodesk App Store**. The installer adds a **GeoDin® Ground** ribbon tab to Civil 3D with all plug-in commands.

### Prerequisites

* **Autodesk Civil 3D 2025** or **Autodesk Civil 3D 2026** installed and licensed.
* **A GeoDin® database** containing the boreholes you want to visualise. The database can be a file-based Microsoft Access file (`.mdb` / `.accdb`) or a client/server database connection already configured in GeoDin®.
* *(Optional)* GeoDin® itself installed on the same machine - useful for editing the underlying records, but not required to run GeoDin® Ground against an existing database.

> **No database yet?** The plug-in installer ships with a **Denver** sample database you can use to explore every command. It is also downloadable directly:
>
> {% embed url="https://resources.geodin.com/downloads/autodesk/data/demo/DenverDemoDatabase.accdb" %}

### Download and install the latest version

{% embed url="https://apps.autodesk.com/CIV3D/en/Detail/Index?appLang=en&id=7392344363451764169&mode=preview&os=Win64" %}

1. Open the Autodesk App Store and search for **GeoDin® Ground** (or use the link above).
2. Download and run the installer.
3. Start or restart Civil 3D.
4. A new **GeoDin® Ground** ribbon appears in Civil 3D. If you do not see it, confirm you installed against the Civil 3D version you actually launch, then restart Civil 3D.

### Running fully offline

GeoDin® Ground can run without any network connection. If your security policy requires it, place the `.accdb` file on the local hard drive, install Civil 3D and GeoDin® Ground on the same machine, and disconnect from the network. Every command described in these docs works in that configuration.

### Next steps

Once installed, continue with [First steps](first-steps.md) to connect a database, load boreholes, and draw your first ground model.

