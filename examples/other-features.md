---
description: >-
  Purpose of this page is to demonstrate some outstanding or useful functions of
  VmBaker.
---

# Other Features

For the purpose of demonstration I will be using just a simple geometry.

### Normals Transfer vs Normals EdgeBevel + Transfer

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/transfer_vs_edgebevel_transfer.png" alt=""><figcaption><p>Bake types differences</p></figcaption></figure>

<div><figure><img src="../.gitbook/assets/normals_transfer_settings.png" alt=""><figcaption><p>Normals Transfer settings used</p></figcaption></figure> <figure><img src="../.gitbook/assets/edgebevel_settings.png" alt=""><figcaption><p>EdgeBevel settings used</p></figcaption></figure></div>


{% endcolumn %}

{% column %}
You may use both **Normals Transfer** and **Normals EdgeBevel** with **Transfer** enabled to transfer details from any geometry. It is very useful when used on floating geometry.

* Objects on the left are baked using ordinary **Normals Transfer**
* Objects on the right are baked using **Normals Edgebevel + Transfer**
* Both green circles are using vertex colors with alpha transparency
* Both hexagonal cylinders have hard edges
* Notice that you may use **EdgeBevel + Transfer** to capture even details that are perfectly parallel to the target surface


{% endcolumn %}
{% endcolumns %}

### Vertex color alpha mask

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/vertex_color_alpha_mask.png" alt=""><figcaption><p>Usage of vertex color mask</p></figcaption></figure>

<figure><img src="../.gitbook/assets/vertex_color_mask_layering.png" alt=""><figcaption><p>Layering effect</p></figcaption></figure>
{% endcolumn %}

{% column %}
Top object didn't use the **Use Vertex Color Mask** feature, bottom one did.

You may see the difference in the blending.

This example was done using Normals Transfer, but it also works when using EdgeBevel with enabled Transfer.

Also notice that you may use this feature to layer details on top of each other. Just bake the details in sequence.
{% endcolumn %}
{% endcolumns %}

### Adding details when baking using EdgeBevel

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/edgeBevel_details.png" alt=""><figcaption><p>EdgeBevel geometry details</p></figcaption></figure>

<figure><img src="../.gitbook/assets/edgeBevel_details_settings.png" alt=""><figcaption><p>Settings used for this example</p></figcaption></figure>
{% endcolumn %}

{% column %}
The EdgeBevel feature may be used to add all sorts of additional details when baking.

You may add holes, or protrusions by using geometry with removed UVs (this makes sure that the object itself is not baked in the texture, but it is used to modify the resulting normals)

* RED faces are back facing faces
* GREEN are forward facing faces

{% hint style="info" %}
This example does NOT use the Transfer feature. It bakes all that is selected and has UVs in the main 0..1 UV square.
{% endhint %}


{% endcolumn %}
{% endcolumns %}

### Baking in steps

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/baking_in_steps.png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
There is no need to bake everyhing in a single step.

It's possible to keep on adding details after initial bake was done.

In this example I first baked EdgeBevel and then transfered details on top of it.
{% endcolumn %}
{% endcolumns %}
