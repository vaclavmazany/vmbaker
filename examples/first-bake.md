---
description: A step-by-step guide to rendering your first texture with VmBaker.
---

# First Bake - Bullet

Now let's get straight to it. For the purpose of the first example, I will demonstrate the workflow in both Maya and Blender. Following examples will be done only in one of the DCC applications, but the workflow still applies to all the supported softwares.

## In General

If you haven't already, please unpack the Examples.zip (you will find it on the downloads page of the addon).

After unzipping you should see contents similar to this (this may be subject to change, if I add more examples in the future) :&#x20;

<figure><img src="../.gitbook/assets/Examples.png" alt=""><figcaption></figcaption></figure>

For this example we will concentrate on the "bullet" folder. You will find these files in there :

* bullet.fbx
* bullet\_ao.png
* bullet\_normal.png

{% hint style="info" %}
The FBX file is already setup with the links to the textures. If you are working on your custom model, you have to create materials and texture links manually.
{% endhint %}

## Maya

#### Initial scene setup

<details>

<summary><strong>Initial scene setup -</strong> you may skip this if you are only interested in the baking process</summary>

First let's open fresh empty scene. And import the **bullet.fbx** file using the File -> Import and locate the unziped **bullet.fbx**.

After importing, you should see something similar to this.

<figure><img src="../.gitbook/assets/bullet_maya_import.png" alt="" width="188"><figcaption></figcaption></figure>

Now please save the scene in the same directory as the FBX file. So your directory should look similar to this.

<figure><img src="../.gitbook/assets/bullet_maya_savedScene.png" alt=""><figcaption></figcaption></figure>

This is for the convenience so that the VmBaker can automatically guess the output paths for rendering.

Now for an optional step, but for better preview of the model. This will basically just load the HDRI and use it as a cubemap reflections in the viewport.



1. Please add a sky dome light using Arnold -> Lights -> Skydome Light
2. In the attributes editor of the newly created aiSkyDomeLight1 please assign the included HDRI image from the examples to the Color slot as shown in the screenshots.
3. Enable all lights in the viewport settings.
4. If you wish, disable the preview of the HDRI in the background by disabling **Show -> Viewport -> Lighting, Shading & Rendering -> Lights.** I will keep it disabled.

<div><figure><img src="../.gitbook/assets/add_dome_light.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/add_new_node.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/add_file_node.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/set_hdri_path.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/set_all_lights.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure></div>

Now have a look at the outliner's content. Specifically the "modifiers", "transfer\_details", "transfer\_details\_variations" - all of these are there to show you the baking process.

For now you may hide these, if they distract you. We'll unhide them one by one once we will be baking them into the texture.

Open the VmBaker window from the main menu using **VmBaker -> Open VmBaker** and you should see the interface, with the texture output paths already filled in.

</details>

#### Baking process

{% stepper %}
{% step %}
### Check Paths

Please check that the paths are correctly setup before you start baking. At the bottom you will see the final path that will be used for the baked texture.

At this stage, we want to bake into the normal map so the path should point to the small PNG image that was included in the example scene.

If you are working on a custom model or the paths do not match, adjust the paths accordingly.

{% hint style="info" %}
VmBaker does not change or update materials, it works solely on the texture files. So if the paths are incorrect you may encounter issues with the viewport updates. **It is up to the user to make sure it bakes to the proper texture file.**
{% endhint %}
{% endstep %}

{% step %}
### First Bake

<div><figure><img src="../.gitbook/assets/maya_first_bake.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_first_bake_radius_0_5.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/clean_edges.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/clean_edges1.png" alt=""><figcaption></figcaption></figure></div>

Now let's start finally baking!

Let's setup the resolution to use **512x512**, make sure you are in the **Normals Edge Bevel** tab and set the **Radius** to about 0,2cm (adjust to your liking).

Select the **shell** model and hit **RENDER**

You should see immediately something similar to the first screenshot.

If you don't like it - experiment with the settings. Try to increase the Radius or Samples.

Notice that the baked edge bevel is well connected even when viewed from very close. This is often where other bakers have serious problems.

{% hint style="info" %}
If you use right mouse click on any of the UI settings, you will have option to open **Online Manual**
{% endhint %}
{% endstep %}

{% step %}
### Baking using helper meshes

<div><figure><img src="../.gitbook/assets/maya_modifiers_unhidden.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_modifiers_after_bake.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_modifiers_after_bake_solo.png" alt=""><figcaption></figcaption></figure></div>

The first bake was quite simple, let's continue with additional stuff.

Unhide the **modifiers** group and have a look what is in there. It's just a bunch of simple cutters, intersections - just some meshes that are supposed to modify the resulting bake.

{% hint style="info" %}
Notice that the models have no UVs - this is important.

* all selected models that have UVs inside the 0-1 UV tile are considered for baking
* this UV logic is similar to what users of Blender's ZEN BBQ might be used to
{% endhint %}

The color of those models is only for convenience.

Now if you select the group called **modifiers** together with the **shell** model and just simply hit **RENDER**.

Based on the settings you have entered you should see something similar to the 2nd and 3rd screenshot.&#x20;

{% hint style="info" %}
I'm using **Isolate selection** to show only portions of the scene.
{% endhint %}
{% endstep %}

{% step %}
### History traversal

Perhaps you don't like what you see, and want to get back the previous bake. You can, open the History tab. If you select any of the labels in the history, it will load that previous baked texture.

<div><figure><img src="../.gitbook/assets/maya_history_0.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_history_1.png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
Large files may take some time to reload. Please be patient if traversing the history of large textures.
{% endhint %}

The process is as follows - when selecting in the history tab it will replace the texture, it does not change texture paths, it rather replaces the textures. So you may return in history and continue from that point onward.
{% endstep %}

{% step %}
### Baking additional details / overlaying bakes using Transfer

In this step we try how to append the bakes on top of each other.

Unhide the **transfer\_details** group and inspect it's contents. There's just a simple hole-like mesh. This will be used to add this detail on top of existing bake.

This time select the group **transfer\_details FIRST** and the **shell** model **SECOND**. The order is important.

{% hint style="info" %}
**When using Transfer the order of selection matters.** All except the last selection is considered as SOURCE and the last selection is considered as the TARGET of the bake.
{% endhint %}

Setup the bake so that you still use the **Normals Edge Bevel** tab, but you enable the **Transfer** checkbox. Also please use settings similar to what you seen on the screenshots. Then hit Render - you should see similar results as on the screenshots.

<div><figure><img src="../.gitbook/assets/maya_overlay_0.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_overlay_1.png" alt=""><figcaption></figcaption></figure></div>

As always experiment, this time perhaps try to bake it multiple times, with different offset or scale. Or perhaps delete the inned face - so that it creates a "ring".

<div><figure><img src="../.gitbook/assets/maya_overlay_2.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_overlay_3.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_overlay_4.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_overlay_5.png" alt=""><figcaption></figcaption></figure></div>

Notice how the detail keeps on adding. And again - if you wish, go back few steps in the history.
{% endstep %}

{% step %}
### Baking additional details

Unhide the **transfer\_details\_variations** group and start experimenting with baking these. You will see, that there's a ring around the main cylinder - this is if you are not satisfied with how the **modifiers** group baked into the texture, you may replace it with custom made model or add additional details to the model.

No need to bake the whole **transfer\_details\_variations** group, this time - select any of the individual objects in that group and the **shell** model as last.

<div><figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure></div>

Add the details as many times as you wish. Just try to get the hang of it.

<div><figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
There are additional settings such as **Use smooth normals** or **Use vertex color mask** and ray distance settings which will be covered in other examples.
{% endhint %}
{% endstep %}

{% step %}
### Conclusion

So this is the basic working of the VmBaker.

At this point you should be able to bake beveled edges on lowpoly geometry and also use transfer to add additional details on top of that. All these features aren't mutually exclusive, you may combine these to get the desired results.

{% hint style="info" %}
The **Append to texture** option in the Global settings allows you to work on multiple meshes that share the same texture - try it.
{% endhint %}
{% endstep %}

{% step %}
### Check Paths

Please check that the paths are correctly setup before you start baking. At the bottom you will see the final path that will be used for the baked texture.

At this stage, we want to bake into the normal map so the path should point to the small PNG image that was included in the example scene.

If you are working on a custom model or the paths do not match, adjust the paths accordingly.

{% hint style="info" %}
VmBaker does not change or update materials, it works solely on the texture files. So if the paths are incorrect you may encounter issues with the viewport updates. **It is up to the user to make sure it bakes to the proper texture file.**
{% endhint %}
{% endstep %}
{% endstepper %}



## Blender WIP

#### Initial scene setup

<details>

<summary><strong>Initial scene setup -</strong> you may skip this if you are only interested in the baking process</summary>

Create a new scene, remove the default cube.

Import the example file using **File -> Import -> FBX** and load the **bullet.fbx** file

<figure><img src="../.gitbook/assets/blender_after_import.png" alt="" width="188"><figcaption><p>After import in Blender</p></figcaption></figure>

Change renderer to Cycles -> GPU Compute and switch to **Viewport shading**

<figure><img src="../.gitbook/assets/image (7).png" alt="" width="188"><figcaption><p>Viewport shading on</p></figcaption></figure>

There are some groups like **modifiers,** transfer\_details and transfer\_details\_variations - you may hide these or use Local view so that they don't get in the way.

</details>

#### Baking process

{% stepper %}
{% step %}
### Check Paths

Please check that the paths are correctly setup before you start baking. At the bottom you will see the final path that will be used for the baked texture.

At this stage, we want to bake into the normal map so the path should point to the small PNG image that was included in the example scene.

If you are working on a custom model or the paths do not match, adjust the paths accordingly.

{% hint style="info" %}
VmBaker does not change or update materials, it works solely on the texture files. So if the paths are incorrect you may encounter issues with the viewport updates. **It is up to the user to make sure it bakes to the proper texture file.**
{% endhint %}
{% endstep %}

{% step %}
### First Bake

<div><figure><img src="../.gitbook/assets/maya_first_bake.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_first_bake_radius_0_5.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/clean_edges.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/clean_edges1.png" alt=""><figcaption></figcaption></figure></div>

Now let's start finally baking!

Let's setup the resolution to use **512x512**, make sure you are in the **Normals Edge Bevel** tab and set the **Radius** to about 0,2cm (adjust to your liking).

Select the **shell** model and hit **RENDER**

You should see immediately something similar to the first screenshot.

If you don't like it - experiment with the settings. Try to increase the Radius or Samples.

Notice that the baked edge bevel is well connected even when viewed from very close. This is often where other bakers have serious problems.

{% hint style="info" %}
If you use right mouse click on any of the UI settings, you will have option to open **Online Manual**
{% endhint %}
{% endstep %}

{% step %}
### Baking using helper meshes

<div><figure><img src="../.gitbook/assets/maya_modifiers_unhidden.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_modifiers_after_bake.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_modifiers_after_bake_solo.png" alt=""><figcaption></figcaption></figure></div>

The first bake was quite simple, let's continue with additional stuff.

Unhide the **modifiers** group and have a look what is in there. It's just a bunch of simple cutters, intersections - just some meshes that are supposed to modify the resulting bake.

{% hint style="info" %}
Notice that the models have no UVs - this is important.

* all selected models that have UVs inside the 0-1 UV tile are considered for baking
* this UV logic is similar to what users of Blender's ZEN BBQ might be used to
{% endhint %}

The color of those models is only for convenience.

Now if you select the group called **modifiers** together with the **shell** model and just simply hit **RENDER**.

Based on the settings you have entered you should see something similar to the 2nd and 3rd screenshot.&#x20;

{% hint style="info" %}
I'm using **Isolate selection** to show only portions of the scene.
{% endhint %}


{% endstep %}

{% step %}
### History traversal

Perhaps you don't like what you see, and want to get back the previous bake. You can, open the History tab. If you select any of the labels in the history, it will load that previous baked texture.

<div><figure><img src="../.gitbook/assets/maya_history_0.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_history_1.png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
Large files may take some time to reload. Please be patient if traversing the history of large textures.
{% endhint %}

The process is as follows - when selecting in the history tab it will replace the texture, it does not change texture paths, it rather replaces the textures. So you may return in history and continue from that point onward.
{% endstep %}

{% step %}
### Baking additional details / overlaying bakes using Transfer

In this step we try how to append the bakes on top of each other.

Unhide the **transfer\_details** group and inspect it's contents. There's just a simple hole-like mesh. This will be used to add this detail on top of existing bake.

This time select the group **transfer\_details FIRST** and the **shell** model **SECOND**. The order is important.

{% hint style="info" %}
**When using Transfer the order of selection matters.** All except the last selection is considered as SOURCE and the last selection is considered as the TARGET of the bake.
{% endhint %}

Setup the bake so that you still use the **Normals Edge Bevel** tab, but you enable the **Transfer** checkbox. Also please use settings similar to what you seen on the screenshots. Then hit Render - you should see similar results as on the screenshots.

<div><figure><img src="../.gitbook/assets/maya_overlay_0.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_overlay_1.png" alt=""><figcaption></figcaption></figure></div>

As always experiment, this time perhaps try to bake it multiple times, with different offset or scale. Or perhaps delete the inned face - so that it creates a "ring".

<div><figure><img src="../.gitbook/assets/maya_overlay_2.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_overlay_3.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_overlay_4.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/maya_overlay_5.png" alt=""><figcaption></figcaption></figure></div>

Notice how the detail keeps on adding. And again - if you wish, go back few steps in the history.
{% endstep %}

{% step %}
### Baking additional details

Unhide the **transfer\_details\_variations** group and start experimenting with baking these. You will see, that there's a ring around the main cylinder - this is if you are not satisfied with how the **modifiers** group baked into the texture, you may replace it with custom made model or add additional details to the model.

No need to bake the whole **transfer\_details\_variations** group, this time - select any of the individual objects in that group and the **shell** model as last.

<div><figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure></div>

Add the details as many times as you wish. Just try to get the hang of it.

<div><figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
There are additional settings such as **Use smooth normals** or **Use vertex color mask** and ray distance settings which will be covered in other examples.
{% endhint %}
{% endstep %}

{% step %}
### Conclusion

So this is the basic working of the VmBaker.

At this point you should be able to bake beveled edges on lowpoly geometry and also use transfer to add additional details on top of that. All these features aren't mutually exclusive, you may combine these to get the desired results.

{% hint style="info" %}
The **Append to texture** option in the Global settings allows you to work on multiple meshes that share the same texture - try it.
{% endhint %}
{% endstep %}
{% endstepper %}

