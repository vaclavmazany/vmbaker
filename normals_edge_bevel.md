---
description: Bake simulated beveled edges on hard-surface geometry.
---

# Normals Edge Bevel

This baking mode generates a normal map that simulates smoothed, rounded edges on hard-surface geometry without adding extra polygons to the mesh.

## General Settings

- **Suffix:** The filename suffix appended to the output file (default is `_normal`).
- **Falloff:** Controls how the sample weight decreases with distance from the edge center. 
- **Radius:** The maximum distance from each surface point that samples are gathered within. This dictates how "wide" the bevel effect appears.
- **Samples:** The number of rays cast per texel. Higher sample counts will significantly reduce noise, but will increase the bake time.
- **Average normal filter:** Blends the baked normals with their neighbors to smooth out high-frequency details. This filters out small nuances back to the default flat normal color (RGB `128, 128, 255`).

![Screenshot of Normals Edge Bevel tab]()

## Use Transfer

Toggle this section to enable projection baking, which transfers details from a high-poly source mesh onto your low-poly target.

- **In ray distance:** The distance rays are cast *inward* from the target surface to find the source mesh.
- **Out ray distance:** The distance rays are cast *outward* from the target surface to map geometry that protrudes past the low-poly shell.
- **Use Smooth Normals:** Calculates the initial ray direction using interpolated vertex normals instead of flat face normals.
  > [!NOTE]
  > The smooth normals approach requires supporting edges on the geometry. Disabling this may result in disconnections on hard, un-beveled edges.
- **Use Vertex Color Mask:** Restricts the projection baking only to areas painted white in the vertex color layer.

![Screenshot of Transfer settings]()
