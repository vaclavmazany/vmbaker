---
description: Follow this step-by-step tutorial to bake a normal map in Maya using VmBaker.
cover: ../../.gitbook/assets/bullet_example_cover.png
coverY: 0
---

# Initial scene setup

#### Initial scene setup

{% tabs %}
{% tab title="Maya" %}
First, let's open a fresh, empty scene. Import the **bullet.fbx** file using File -> Import and locate the unzipped **bullet.fbx**.

After importing, you should see something similar to this.

<figure><img src="../../.gitbook/assets/bullet_maya_import.png" alt="Imported bullet.fbx in Maya viewport" width="188"><figcaption></figcaption></figure>

Now please save the scene in the same directory as the FBX file. So your directory should look similar to this.

<figure><img src="../../.gitbook/assets/bullet_maya_savedScene.png" alt="Maya scene saved next to the FBX file"><figcaption></figcaption></figure>

This is for convenience so that VmBaker can automatically guess the output paths for rendering.

This is an optional step to get a better preview of the model. It will load the HDRI and use it as cubemap reflections in the viewport.

1. Please add a sky dome light using Arnold -> Lights -> Skydome Light
2. In the attributes editor of the newly created aiSkyDomeLight1 please assign some HDRI image to the Color slot as shown in the screenshots.
   1. You may find free HDRI here [https://polyhaven.com/](https://polyhaven.com/)
3. Enable all lights in the viewport settings.
4. If you wish, disable the preview of the HDRI in the background by disabling **Show -> Viewport -> Lighting, Shading & Rendering -> Lights.** I will keep it disabled.

<div><figure><img src="../../.gitbook/assets/add_dome_light.png" alt="Adding a Skydome Light"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/add_new_node.png" alt="Adding a new node to color slot"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/add_file_node.png" alt="Adding a file node"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/set_hdri_path.png" alt="Setting HDRI image path"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/set_all_lights.png" alt="Enabling all lights in viewport"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image.png" alt="HDRI environment preview"><figcaption></figcaption></figure></div>

Now have a look at the outliner's content. Specifically, the "modifiers", "transfer\_details", and "transfer\_details\_variations" groups. All of these are provided to demonstrate the baking process.

For now you may hide these, if they distract you. We'll unhide them one by one once we will be baking them into the texture.

Open the VmBaker window from the main menu using **VmBaker -> Open VmBaker** and you should see the interface, with the texture output paths already filled in.
{% endtab %}

{% tab title="Blender" %}
Create a new scene and remove the default cube.

Import the example file using **File -> Import -> FBX** and load the **bullet.fbx** file.

<figure><img src="../../.gitbook/assets/blender_after_import.png" alt="Imported bullet.fbx in Blender viewport" width="188"><figcaption><p>After import in Blender</p></figcaption></figure>

Change the renderer to Cycles -> GPU Compute and switch to **Viewport shading**.

<figure><img src="../../.gitbook/assets/image (1).png" alt="Viewport shading enabled in Blender" width="188"><figcaption><p>Viewport shading on</p></figcaption></figure>

There are some groups like **modifiers**, **transfer\_details**, and **transfer\_details\_variations**—you may hide these or use Local View so they don't get in the way.

Now, please save the scene in the same directory as the FBX file so your directory looks similar to this.

<figure><img src="../../.gitbook/assets/blender_scene_setup.png" alt="Blender scene saved next to the FBX file"><figcaption></figcaption></figure>

If the add-on is activated properly, you should see a new panel called **VmBaker** in the Blender N-Panel (sidebar). Please open it.
{% endtab %}
{% endtabs %}
