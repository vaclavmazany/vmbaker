---
description: An overview of the VmBaker plugin interface and workflow.
---

# Introduction to VmBaker

Welcome to the **VmBaker** documentation!

The goal of VmBaker is to be a fast, GPU-accelerated texture baking tool built for any DCC software capable of running Python. Currently, Maya (2024+) and Blender (4.2+) are supported, with others planned. It leverages NVIDIA OptiX and CUDA, so you must have an NVIDIA RTX graphics card to use this plugin.

{% hint style="warning" %}
Currently supporting **Windows** and **Nvidia RTX** cards only.
{% endhint %}

Because it is designed to support multiple DCC applications, there are some limitations to what it can bake. The main limitation is that it does not support built-in shader graphs or materials; it is strictly a mesh-based renderer.

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
