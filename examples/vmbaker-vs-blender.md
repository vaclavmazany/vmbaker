---
description: >-
  This demonstration is supposed to be only a comparison of the advantages that
  VmBaker has over native Blender baking.
---

# VmBaker vs Blender

## Precision in general

The simplest demonstration I can show you the difference in precision is how blender handles baking normal maps when using edge beveling. Let's demonstrate it on a simple cube as it is the most obvious example.

### The differences

<figure><img src="../.gitbook/assets/vmbaker_vs_blender128.png" alt=""><figcaption><p>VmBaker vs Blender at the same sample count</p></figcaption></figure>

* Notice the disconnection with the native Blender on the corner and the edge of the cube and the well connected VmBaker baked normals



### The setup

<div><figure><img src="../.gitbook/assets/simple cube.png" alt="" width="375"><figcaption><p>Cube edge bake example</p></figcaption></figure> <figure><img src="../.gitbook/assets/simple_cube_uvs.png" alt="" width="375"><figcaption><p>UVs</p></figcaption></figure></div>

There is nothing special about the setup really, it is just a single cube with size of 5x5x5cm and UVs unpacked for baking normalmaps - UVs split on hard edges.

### Bake settings

{% tabs %}
{% tab title="VmBaker" %}
<figure><img src="../.gitbook/assets/vmbaker_vs_blender_01.png" alt="" width="95"><figcaption></figcaption></figure>

Simple setup using VmBaker with radius of 2mm and 128 samples for comparable results.
{% endtab %}

{% tab title="Blender native" %}
<div><figure><img src="../.gitbook/assets/vmbaker_vs_blender_02.png" alt="" width="327"><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/vmbaker_vs_blender_03.png" alt="" width="103"><figcaption></figcaption></figure></div>

Simple setup using Bevel node in shader editor with 128 samples, radius of 2mm and using Cycles with GPU support for the bake.
{% endtab %}
{% endtabs %}



## Precision vs samples

<figure><img src="../.gitbook/assets/vmbaker_vs_blender_32.png" alt=""><figcaption><p>VmBaker vs Blender EdgeBevel</p></figcaption></figure>

* Notice that the VmBaker still holds well even with a lot less samples (this results with faster baking speeds)

### Separated objects

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Baking separate objects</p></figcaption></figure>

* With VmBaker may render as many objects as you like, you do not have to merge the objects as you do with native Blender baking. Still notice the disconnected edges on the native Blender bake.
