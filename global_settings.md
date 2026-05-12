---
description: Configure output paths, render resolutions, and post-processing.
---

# Global Settings

These settings are applied globally, regardless of which baking mode you currently have selected.

## File Output

Configure where and how your baked textures are saved.

- **Output Path:** The base folder where textures are saved.
- **Output Filename:** The core name of the file without suffix or extension. VmBaker manages the file format (e.g., `.png`) and mode-specific suffixes (e.g., `_normal`) automatically.
- **Save to history:** When enabled, VmBaker saves each bake result to a numbered history folder based on the texture name, preventing accidental data loss.
- **Append to texture:** Instead of overwriting the entire image, this overlays the newly baked UV islands on top of the existing texture.

![Screenshot of File Output settings]()

## Render Settings

Control the quality and size of your final baked maps.

- **Resolution (Width / Height):** The output texture width and height in pixels.
- **SSAA:** Supersampling factor. Renders the map at a higher internal resolution and downscales it to reduce aliasing (jagged edges). *Note: Higher values will increase render times.*
- **UV Tolerance:** The distance threshold for UV seam detection. Increase this value if you see seams or artifacts appearing along the edges of your baked texture.

![Screenshot of Render Settings]()

## PostProcess

Effects applied after the initial render is complete.

- **Dilation:** Expands the texture edges into empty UV space. This is crucial for preventing dark background pixels from bleeding into your texture when the model is viewed from a distance (mip-mapping).
- **Blur:** Applies a Gaussian blur to the final baked texture, softening the overall result.

![Screenshot of PostProcess settings]()
