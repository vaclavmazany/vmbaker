---
description: Continue the step-by-step tutorial to render and refine your normal map.
cover: ../../.gitbook/assets/bullet_example_cover.png
coverY: 0
---

# Baking - Normal map

{% stepper %}
{% step %}
#### Check Paths

Please check that the paths are correctly set up before you start baking. At the bottom of the VmBaker UI, you will see the final path that will be used for the baked texture.

At this stage, we want to bake into the normal map so the path should point to the small PNG image that was included in the example scene.

If you are working on a custom model or the paths do not match, adjust the paths accordingly.

{% hint style="info" %}
VmBaker does not change or update materials, it works solely on the texture files. So if the paths are incorrect you may encounter issues with the viewport updates. **It is up to the user to make sure it bakes to the proper texture file.**
{% endhint %}
{% endstep %}

{% step %}
#### First Bake

Now let's start finally baking!

Let's set up the resolution to use **512x512**, make sure you are in the **Normals Edge Bevel** tab and set the **Radius** to about 0,2cm (adjust to your liking).

Select the **shell** model and hit **RENDER**

You should see immediately something similar to the first screenshot.

{% tabs %}
{% tab title="Maya" %}
<div><figure><img src="../../.gitbook/assets/maya_first_bake.png" alt="Maya first bake result"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_first_bake_radius_0_5.png" alt="Bake result with radius 0.5"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/clean_edges.png" alt="Clean beveled edges preview 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/clean_edges1.png" alt="Clean beveled edges preview 2"><figcaption></figcaption></figure></div>


{% endtab %}

{% tab title="Blender" %}
<div><figure><img src="../../.gitbook/assets/blender_first_bake.png" alt="Blender first bake result"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_first_bake_radius_0_5.png" alt="Blender bake result with radius 0.5"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_clean_edges.png" alt="Blender clean beveled edges preview 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_clead_edges1.png" alt="Blender clean beveled edges preview 2"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

If you don't like it - experiment with the settings. Try to increase the Radius or Samples.

Notice that the baked edge bevel is well connected even when viewed from very close. This is often where other bakers have serious problems.

{% hint style="info" %}
If you use right mouse click on any of the UI settings, you will have option to open **Online Manual**
{% endhint %}
{% endstep %}

{% step %}
#### Baking using helper meshes

The first bake was quite simple, let's continue with additional stuff.

Unhide the **modifiers** group and examine its contents. It contains simple cutters and intersections—meshes designed to modify the resulting bake.

{% hint style="info" %}
Notice that the models have no UVs - this is important.

* all selected models that have UVs inside the 0-1 UV tile are considered for baking
* this UV logic is similar to what users of Blender's ZEN BBQ might be used to
{% endhint %}

The color of those models is only for convenience.

Now if you select the group called **modifiers** together with the **shell** model and just simply hit **RENDER**.

{% tabs %}
{% tab title="Maya" %}
<div><figure><img src="../../.gitbook/assets/maya_modifiers_unhidden.png" alt="Modifiers group unhidden in viewport"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_modifiers_after_bake.png" alt="Bake result with modifiers"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_modifiers_after_bake_solo.png" alt="Bake result with modifiers isolated"><figcaption></figcaption></figure></div>


{% endtab %}

{% tab title="Blender" %}
<div><figure><img src="../../.gitbook/assets/blender_modifiers_unhidden.png" alt="Blender modifiers group unhidden"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_modifiers_after_bake.png" alt="Blender bake result with modifiers"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_modifiers_after_bake_solo.png" alt="Blender bake result with modifiers isolated"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

Based on the settings you have entered you should see something similar to the 2nd and 3rd screenshot.

{% hint style="info" %}
I'm using **Isolate selection** to show only portions of the scene.
{% endhint %}
{% endstep %}

{% step %}
#### History traversal

Perhaps you don't like what you see, and want to get back the previous bake. You can, open the History tab. If you select any of the labels in the history, it will load that previous baked texture.

{% tabs %}
{% tab title="Maya" %}
<div><figure><img src="../../.gitbook/assets/maya_history_0.png" alt="History tab item 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_history_1.png" alt="History tab item 2"><figcaption></figcaption></figure></div>


{% endtab %}

{% tab title="Blender" %}
<div><figure><img src="../../.gitbook/assets/blender_history_0.png" alt="Blender history tab item 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_history_1.png" alt="Blender history tab item 2"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Large files may take some time to reload. Please be patient if traversing the history of large textures.
{% endhint %}

The process is as follows - when selecting in the history tab it will replace the texture, it does not change texture paths, it rather replaces the textures. So you may return in history and continue from that point onward.
{% endstep %}

{% step %}
#### Baking additional details / overlaying bakes using Transfer

In this step we try how to append the bakes on top of each other.

Unhide the **transfer\_details** group and inspect its contents. It contains a simple hole-like mesh. This will be used to add this detail on top of existing bake.

This time select the group **transfer\_details FIRST** and the **shell** model **SECOND**. The order is important.

{% hint style="info" %}
**When using Transfer the order of selection matters.** All except the last selection is considered as SOURCE and the last selection is considered as the TARGET of the bake.
{% endhint %}

Set up the bake so that you still use the **Normals Edge Bevel** tab, but you enable the **Transfer** checkbox. Also, please use settings similar to what you see in the screenshots. Then hit Render - you should see similar results as on the screenshots.

{% tabs %}
{% tab title="Maya" %}
<div><figure><img src="../../.gitbook/assets/maya_overlay_0.png" alt="Transfer details overlay bake 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_overlay_1.png" alt="Transfer details overlay bake 2"><figcaption></figcaption></figure></div>


{% endtab %}

{% tab title="Blender" %}
<div><figure><img src="../../.gitbook/assets/blender_overlay_0.png" alt="Blender transfer details overlay bake 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_overlay_1.png" alt="Blender transfer details overlay bake 2"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

As always experiment, this time perhaps try to bake it multiple times, with different offset or scale. Or perhaps delete the inner face - so that it creates a "ring".

{% tabs %}
{% tab title="Maya" %}
<div><figure><img src="../../.gitbook/assets/maya_overlay_2.png" alt="Additional overlay detail 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_overlay_3.png" alt="Additional overlay detail 2"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_overlay_4.png" alt="Additional overlay detail 3"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_overlay_5.png" alt="Additional overlay detail 4"><figcaption></figcaption></figure></div>


{% endtab %}

{% tab title="Blender" %}
<div><figure><img src="../../.gitbook/assets/blender_overlay_2.png" alt="Blender additional overlay detail 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_overlay_3.png" alt="Blender additional overlay detail 2"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_overlay_4.png" alt="Blender additional overlay detail 3"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_overlay_5.png" alt="Blender additional overlay detail 4"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

Notice how the detail keeps on adding. And again - if you wish, go back few steps in the history.
{% endstep %}

{% step %}
#### Baking additional details

Unhide the **transfer\_details\_variations** group and start experimenting with baking these. You will see, that there's a ring around the main cylinder - this is if you are not satisfied with how the **modifiers** group baked into the texture, you may replace it with custom made model or add additional details to the model.

No need to bake the whole **transfer\_details\_variations** group, this time - select any of the individual objects in that group and the **shell** model as last.

{% tabs %}
{% tab title="Maya" %}
<div><figure><img src="../../.gitbook/assets/maya_additional_details_0.png" alt="Additional details variation 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_additional_details_1.png" alt="Additional details variation 2"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_additional_details_2.png" alt="Additional details variation 3"><figcaption></figcaption></figure></div>


{% endtab %}

{% tab title="Blender" %}
<div><figure><img src="../../.gitbook/assets/blender_additional_details_0.png" alt="Blender additional details variation 1"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_additional_details_1.png" alt="Blender additional details variation 2"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_additional_details_2.png" alt="Blender additional details variation 3"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

Add the details as many times as you wish. Just try to get the hang of it.

{% tabs %}
{% tab title="Maya" %}
<div><figure><img src="../../.gitbook/assets/maya_additional_details_3.png" alt="Additional details variation 4"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_additional_details_4.png" alt="Additional details variation 5"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/maya_additional_details_5.png" alt="Additional details variation 6"><figcaption></figcaption></figure></div>


{% endtab %}

{% tab title="Blender" %}
<div><figure><img src="../../.gitbook/assets/blender_additional_details_3.png" alt="Blender additional details variation 4"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_additional_details_4.png" alt="Blender additional details variation 5"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/blender_additional_details_5.png" alt="Blender additional details variation 6"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

{% hint style="info" %}
There are additional settings such as **Use smooth normals** or **Use vertex color mask** and ray distance settings which will be covered in other examples.
{% endhint %}
{% endstep %}

{% step %}
#### Conclusion

So this is the basic working of the VmBaker.

At this point you should be able to bake beveled edges on lowpoly geometry and also use transfer to add additional details on top of that. All these features aren't mutually exclusive, you may combine these to get the desired results.

{% hint style="info" %}
The **Append to texture** option in the Global settings allows you to work on multiple meshes that share the same texture - try it.
{% endhint %}
{% endstep %}
{% endstepper %}

<figure><img src="../../.gitbook/assets/bullet_example.png" alt="Bullet Normal Map bake example"><figcaption><p>Bullet Normal Map bake example</p></figcaption></figure>
