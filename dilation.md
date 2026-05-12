---
description: Apply post-process dilation to an external texture map.
---

# Dilation

Unlike the other baking modes, the **Dilation** tab does not perform any 3D rendering or raycasting. It is a dedicated 2D image processing mode used strictly to apply dilation (edge padding) to an already existing external texture file.

Dilation expands the solid pixels of a texture outward into the transparent/empty space, which prevents black backgrounds from bleeding into the image when viewed at lower mip-map levels.

## Settings

- **Input file:** Click the `...` button to open a file browser and select the `.png` image file you want to apply dilation to.
- **Dilation:** The pixel count used to expand the map edges. (e.g., `64px`).

![Screenshot of Dilation tab](https://placehold.co/800x400?text=Screenshot+of+Dilation+tab)
