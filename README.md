---
description: An overview of the VmBaker plugin interface and workflow.
cover: .gitbook/assets/Gitbook header.png
coverY: 0
layout:
  width: default
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Introduction to VmBaker

Welcome to the **VmBaker** documentation!

VmBaker is a hardware-accelerated texture baking tool built to integrate into any DCC software capable of running Python. By leveraging NVIDIA OptiX and CUDA, VmBaker processes mesh-based texture generation efficiently using your local GPU.

The plugin is designed with a unified user interface. This ensures that the workflow, settings, and behavior remain identical regardless of which host application you are currently using.

{% hint style="warning" %}
Currently supporting **Windows** and **Nvidia RTX** cards only.
{% endhint %}

## Key Features

* **GPU Rendering:** Utilizes NVIDIA OptiX and CUDA for hardware-accelerated baking.
* **Unified UI:** Provides the exact same interface and workflow across all supported DCC applications.
* **History Management:** Includes a built-in history panel to store, view, and reload settings from previous baking sessions.
* **Post-Processing:** Features automated edge dilation (padding) and Gaussian blur options to process the final output texture.
* **Non-Destructive Workflows:** Supports incremental saving and appending baked results onto existing textures.

## Baking Modes

VmBaker is a strictly mesh-based renderer. It does not evaluate host-application shader graphs or materials. Instead, it focuses on geometry-driven baking via dedicated modes:

* **Normals Edge Bevel:** Generates a normal map that simulates smoothed, rounded edges on hard-surface geometry.
* **Normals Transfer:** Projects high-poly surface normals and details onto a low-poly target mesh.
* **Ambient Occlusion (AO):** Calculates geometric self-shadowing based on ray distance and spread parameters.
* **Utility Masks:** Generates flat-color, vertex-color, or ID masks based on mesh properties.

## System Requirements

* **OS:** Windows x64
* **Hardware:** NVIDIA RTX Graphics Card (with up-to-date drivers)
* **Supported Host Applications:**
  * Autodesk Maya (2024 and newer)
  * Blender (4.2 and newer)
  * _(The underlying architecture is designed to support additional Python-capable DCCs in future updates.)_

{% hint style="info" %}
#### Licensing <a href="#user-content-licensing-1" id="user-content-licensing-1"></a>

To keep the user experience as frictionless as possible, VmBaker contains absolutely no DRM, license keys, or online authorization checks. It relies entirely on the honor system. If this tool saves you time and improves your workflow, please consider purchasing it from our [Gumroad Store](https://vaclavmazany.gumroad.com/l/VmBaker) to support future updates.
{% endhint %}

## Interface Breakdown

The interface is divided into three main sections:

1. **Global Settings:** Controls for output directories, rendering resolution, and post-processing effects.
2. **History:** A quick-access panel to view and load your previous bakes.
3. **Baking Modes (Tabs):** The core rendering modes, each with its own specific settings and transfer options.

Use the sidebar navigation to explore the specific settings for each tab and feature.

## Where to buy

### Gumroad

* [https://vaclavmazany.gumroad.com/l/VmBaker](https://vaclavmazany.gumroad.com/l/VmBaker)

### Superhivemarket

* ...
