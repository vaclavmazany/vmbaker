---
description: How to install and activate VmBaker.
---

# Installation & Activation

VmBaker is deployed via a unified Windows executable installer that automatically handles setting up the plugin for both Autodesk Maya and Blender. 

## Running the Installer

1. Run the `VmBaker_X.X.X.exe` installer.
2. The core Python and application files are installed centrally to `C:\Program Files\VmBaker`.
3. The installer will automatically detect your host applications and create the necessary deployment links (`.mod` files for Maya, and Extension symlinks for Blender).

![Screenshot of the Installer Window](https://placehold.co/800x400?text=Screenshot+of+the+Installer+Window)

---

## Activating in Autodesk Maya

The installer automatically places a `.mod` file into your `%DOCUMENTS%\maya\modules` directory. This makes the plugin available to all installed versions of Autodesk Maya instantly.

**To open VmBaker:**
1. Launch Autodesk Maya.
2. Look at the top menu bar.
3. Click the newly generated **VmBaker** menu item to open the user interface.

![Screenshot of the Maya Top Menu](https://placehold.co/800x400?text=Screenshot+of+the+Maya+Top+Menu)

---

## Activating in Blender (4.2+)

The installer creates a local extension symlink directly into your `%APPDATA%` Blender extensions cache for all compatible installed versions.

**To enable VmBaker:**
1. Launch Blender.
2. Navigate to **Edit > Preferences**.
3. Select the **Add-ons** tab on the left side.
   *(Note: While you can check the 'Get Extensions' tab to verify the files were copied, the actual enabling/disabling of the tool must be done in the Add-ons tab).*
4. Search for "VmBaker" in the search bar.
5. Check the box to enable the add-on.
6. The VmBaker UI will now be available in your 3D Viewport sidebar (N-panel).

![Screenshot of the Blender Preferences Add-ons Tab](https://placehold.co/800x400?text=Screenshot+of+the+Blender+Preferences+Add-ons+Tab)
