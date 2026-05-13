---
description: An overview of the VmBaker plugin interface and workflow.
---

# Introduction to VmBaker

Welcome to the **VmBaker** documentation!

The goal of VmBaker is to be a fast, GPU-accelerated texture baking tool built for any DCC software that is capable of running python, currently Maya (from 2024 and up) and Blender (from 4.2 and up) are supported, others are planned. It leverages NVIDIA OptiX and CUDA so in order to use this plugin you must have Nvidia RTX graphics card.

{% hint style="warning" %}
Currently supporting **Windows** and **Nvidia RTX** cards only.
{% endhint %}

Due to the fact that it's designed to support all possible DCC applications there are some limitations to what it might bake. Main limitation is that it will not support the built in shader graphs or materials. Currently it is strictly mesh based renderer.

This documentation serves as an overview of the user interface, explaining what each setting controls during a bake.

## Requirements

* Windows x64
* Nvidia RTX GPU with updated drivers
* any DCC application of your choice
  * Maya (2024 and up)
  * Blender (4.2 and up)
  * stay tuned for more

## Interface Breakdown

The interface is divided into three main sections:

1. **Global Settings:** Controls for output directories, rendering resolution, and post-processing effects.
2. **History:** A quick-access panel to view and load your previous bakes.
3. **Baking Modes (Tabs):** The core rendering modes, each with its own specific settings and transfer options.

Use the sidebar navigation to explore the specific settings for each tab and feature.

> \[!TIP] If you are upgrading from an older version, note that VmBaker now automatically handles filename extensions and suffixes based on the active tab!
