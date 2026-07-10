---
description: >-
  This example showcases the traditional workflow on how to bake details from a
  highpoly model onto a lowpoly model. With addition of baking into LODs as
  well.
---

# Highpoly to Lowpoly transfer Normal+AO

This example consists of two groups - lowpoly model group and highpoly model group. Both groups have multiple objects inside.

I will showcase this on a model of a vehicle tire.

<div><figure><img src="../.gitbook/assets/tireLOD0.png" alt=""><figcaption><p>lowpoly LOD0 example</p></figcaption></figure> <figure><img src="../.gitbook/assets/tireLOD1.png" alt=""><figcaption><p>lowpoly LOD1 example</p></figcaption></figure> <figure><img src="../.gitbook/assets/tireHP.png" alt=""><figcaption><p>highpoly model example</p></figcaption></figure></div>

Because we want to use ordinary details transfer from highpoly to lowpoly - we will use the Normals Transfer tab and later on the AO tab.

## Baking Normal

{% columns %}
{% column %}
<div><figure><img src="../.gitbook/assets/tire_normal_01.gif" alt=""><figcaption><p>Normal transfer bake setup</p></figcaption></figure> <figure><img src="../.gitbook/assets/tire_LODs_normal.png" alt=""><figcaption><p>example of LOD0 and LOD1 with baked normalmap</p></figcaption></figure></div>


{% endcolumn %}

{% column %}
Notice that you can bake one group of objects into another group of objects. Of course you may select individual objects if you wish.

For transfer the selection works like this :

1. select the source - highpoly model
2. select the target - lowpoly model
3. use Normals Transfer tab (or enable Transfer in other tabs)
4. bake

Second image shows both LOD0 and LOD1 models baked from the same highpoly source.
{% endcolumn %}
{% endcolumns %}

{% hint style="info" %}
I'm using Isolate selection to show only the lowpoly model of the tire - this is just so that it's visible what is baked.
{% endhint %}

## Baking AO

{% columns %}
{% column %}
<div><figure><img src="../.gitbook/assets/tire_ao_01.gif" alt=""><figcaption><p>AO transfer bake setup</p></figcaption></figure> <figure><img src="../.gitbook/assets/tire_LODs_ao.png" alt=""><figcaption><p>example of LOD0 and LOD1 with baked AO</p></figcaption></figure></div>
{% endcolumn %}

{% column %}
The process with AO is similar.

Select first the source, then target, enable Transfer and hit bake.

The end of the animation is just me showing the preview of the texture.
{% endcolumn %}
{% endcolumns %}

{% hint style="warning" %}
I'm skipping the materials setup in this example and concentrating on the baking only.

The VmBaker only renders the textures, you have to link it to your materials yourself.

Keep in mind that you can bake into textures without the materials.
{% endhint %}
