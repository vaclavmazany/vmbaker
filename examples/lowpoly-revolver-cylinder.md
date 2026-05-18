---
description: In this example we will cover an example of baking a lowpoly revolver cylinder
cover: ../.gitbook/assets/revolver_cylinder.png
coverY: 13.992985971943888
---

# Lowpoly revolver cylinder

Now let's try to bake details to a very lowpoly model, literally just a simple cylinder so that it resembles a revolver cylinder.

This example is to showcase some non-ordinary features of VmBaker - such as baking "fake" booleans using the Edge Bevel with Transfer options.

Please find the **revolver\_cylinder** folder inside the examples.

{% hint style="info" %}
I will not cover the basic scene setup here, you may find it in the [first-bake.md](first-bake/first-bake.md "mention")of the [first-bake](first-bake/ "mention")example.
{% endhint %}

{% hint style="info" %}
In this example I will use just the Blender for showcase, but the logic stays the same inside any other supported DCC.
{% endhint %}

## Baking

{% stepper %}
{% step %}
### FBX Scene contents

As in the [first-bake](first-bake/ "mention") example, you will find groups called **modifiers**, **transfer\_hard\_normals**, **transfer\_smooth\_normals**.

These are there just to make it straight forward to follow the baking steps. But please try your own models or modify the examples ones - just so that you try anything that comes to your mind.

I like to keep these objects semi transparent so that I can see the bake beneath.
{% endstep %}

{% step %}
### Baking the base

Start of by just selecting the **revolver\_cylinder** mesh and baking it using the settings in the screenshot - or try anything you like the most.

What I found that works well for me was radius of 0,1cm

<div><figure><img src="../.gitbook/assets/blender_revolver_base_0.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/blender_revolver_base_1.png" alt=""><figcaption></figcaption></figure></div>

Now try to include the **modifiers** group, and have a look what it does.&#x20;

<div><figure><img src="../.gitbook/assets/blender_revolver_base_2.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/blender_revolver_base_3.png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
You may select just the root of the selection that you want to be used for baking. When the root is selected it automatically includes all the children inside that group.
{% endhint %}
{% endstep %}

{% step %}
### Adding additional details

Start of by baking the group **transfer\_hard\_normals**.

The settings are simple, just use **transfer** and make sure you have smooth normals disabled. Just like in the screenshots.

{% hint style="info" %}
Keep in mind that when using **Transfer** the order of selection matters. Always select the target object last.
{% endhint %}

<div><figure><img src="../.gitbook/assets/blender_revolver_transfer_hard_0.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/blender_revolver_transfer_hard_1.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/blender_revolver_transfer_hard_2.png" alt=""><figcaption></figcaption></figure></div>

Now include the group **transfer\_smooth\_normals** - again follow the settings in the screenshots. This time change the **Radius** to 0,3 and **In ray distance** to 2 and **Out ray distance** to 0.

<div><figure><img src="../.gitbook/assets/blender_revolver_transfer_smooth_0.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/blender_revolver_transfer_smooth_1.png" alt=""><figcaption></figcaption></figure></div>

Perhaps experiment with the radius settings.

{% hint style="info" %}
As this type of baking is overlaying the bakes on top of each other, use **History** to get back if you do not like the current bake.
{% endhint %}

<div><figure><img src="../.gitbook/assets/blender_revolver_boolean_0.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/blender_revolver_boolean_1.png" alt=""><figcaption></figcaption></figure></div>

Inspect the objects, that are inside that group - move them and try to bake them individually so that you also get the intuition for the In / Out ray distances.

Or try using completely different objects.
{% endstep %}

{% step %}
### Conclusion

But in the end, you should have something similar to this.

<figure><img src="../.gitbook/assets/revolver_cylinder.png" alt=""><figcaption></figcaption></figure>


{% endstep %}
{% endstepper %}
