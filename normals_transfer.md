---
description: Project high-poly surface normals onto a low-poly mesh.
---

# Normals Transfer

Unlike the Edge Bevel tab, the **Normals Transfer** mode is strictly dedicated to standard projection baking. It captures the surface details of a complex high-poly source mesh and bakes them into a tangent-space normal map for a low-poly target.

## General Settings

- **Suffix:** The filename suffix appended to the output file (default is `_normal`).
- **Average normal filter:** Blends the baked normals with their neighbors to smooth out high-frequency details, pushing minor deviations back towards flat normal blue (RGB `128, 128, 255`).

![Screenshot of Normals Transfer tab](https://placehold.co/800x400?text=Screenshot+of+Normals+Transfer+tab)

## Use Transfer (Always Enabled)

Because this mode relies entirely on projection, the Transfer settings are always enabled.

- **In ray distance:** The distance rays are cast *inward* from the target surface to find the source mesh.
- **Out ray distance:** The distance rays are cast *outward* from the target surface to map geometry that protrudes past the low-poly shell.
- **Use Smooth Normals:** Calculates the initial ray direction using interpolated vertex normals instead of flat face normals.
- **Use Vertex Color Mask:** Restricts the projection baking only to areas painted white in the vertex color layer.
