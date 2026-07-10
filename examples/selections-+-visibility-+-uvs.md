---
description: >-
  This page is for describing how selections and visibility affect the baking
  process
---

# Selections + visibility + UVs

The logic behind selections and visibility and how the affect the baking process is quite simple.

The rules are :

* hidden object does not participate in the bake
  * this means, if you don't want object to affect the bake at all - hide it
* currently baking only UV square of 0-1
  * everything outside of that range is not baked, but will participate in bake
  * used for creating bevels, holes etc. when using EdgeBevel
* when **using Transfer** - target is always selected as last
* when **not using** **Transfer** - order of selection does not matter
* all children in hierarchy of the selected objects are considered selected
  * this means that you may setup target and source "bake groups" instead of selecting individual objects



Which creates few scenarios that I will cover bellow. I will cover them all for completeness, but after a few you will get the idea :)

## Baking without using transfer

{% columns %}
{% column %}
<div><figure><img src="../.gitbook/assets/multiple_objects_no_transfer.png" alt=""><figcaption><p>multiple objects without using transfer</p></figcaption></figure> <figure><img src="../.gitbook/assets/selections_01.gif" alt=""><figcaption><p>selections workflow</p></figcaption></figure></div>


{% endcolumn %}

{% column %}
I will demonstrate it on an edge bevel, but the logic applies to all baking without using Transfer.

In the GIF animation I try to demonstrate what selection affect.

1. I show baking of the whole "all\_objects" group
   1. you may also notice that I use history to go back in the bake process
2. Then I show that selecting objects individually is also possible
3. Lastly I show that hiding the object inside the group makes the object "invisible" for the bake


{% endcolumn %}
{% endcolumns %}

## Baking using helper objects (without UVs / outside 0-1)

{% columns %}
{% column %}
<div><figure><img src="../.gitbook/assets/helper_object_uvs.png" alt=""><figcaption><p>helper object with UVs outside the main 0-1 UV square</p></figcaption></figure> <figure><img src="../.gitbook/assets/helper_objects_01.gif" alt=""><figcaption><p>baking using helper objects</p></figcaption></figure></div>


{% endcolumn %}

{% column %}
In this example I bake the same cube again but this time I add a detail using a helper mesh object that has it's UVs outside the 0-1 uv range. Removing the UVs works the same way.
{% endcolumn %}
{% endcolumns %}

## Transfer single highpoly onto single lowpoly

{% columns %}
{% column %}
<div><figure><img src="../.gitbook/assets/single_lowpoly.png" alt=""><figcaption><p>single lowpoly</p></figcaption></figure> <figure><img src="../.gitbook/assets/single_highpoly.png" alt=""><figcaption><p>single highpoly</p></figcaption></figure> <figure><img src="../.gitbook/assets/single_lowpoly_to_highpoly.png" alt=""><figcaption><p>single highpoly transfered onto single lowpoly</p></figcaption></figure></div>
{% endcolumn %}

{% column %}
1. select highpoly
2. select lowpoly and bake
{% endcolumn %}
{% endcolumns %}

## Transfer single highpoly object onto multiple lowpoly objects

{% columns %}
{% column %}
<div><figure><img src="../.gitbook/assets/single_highpoly_01.png" alt=""><figcaption><p>single highpoly</p></figcaption></figure> <figure><img src="../.gitbook/assets/multiple_lowpoly_01.png" alt=""><figcaption><p>multiple lowpoly</p></figcaption></figure> <figure><img src="../.gitbook/assets/single_highpoly_to_multiple_lowpoly.png" alt=""><figcaption><p>single highpoly transfered onto multiple lowpoly objects</p></figcaption></figure></div>
{% endcolumn %}

{% column %}
1. select highpoly
2. select the parent group of the lowpoly objects and bake
{% endcolumn %}
{% endcolumns %}

## Transfer multiple highpoly objects onto multiple lowpoly objects

{% columns %}
{% column %}
<div><figure><img src="../.gitbook/assets/multiple_highpoly_01.png" alt=""><figcaption><p>multiple highpoly</p></figcaption></figure> <figure><img src="../.gitbook/assets/multiple_lowpoly_02.png" alt=""><figcaption><p>multiple lowpoly</p></figcaption></figure> <figure><img src="../.gitbook/assets/multiple_lowpoly_and_highpoly_01.png" alt=""><figcaption><p>multipe highpoly transfered onto multiple lowpoly objects</p></figcaption></figure></div>
{% endcolumn %}

{% column %}
1. select either all highpoly objects individually or select the parent group of highpoly objects
2. select the parent group of the lowpoly objects and bake
{% endcolumn %}
{% endcolumns %}

