# Render Settings

Control the quality and size of your final baked maps.

* **Resolution (Width / Height):** The output texture width and height in pixels.
* **SSAA:** Supersampling factor. Renders the map at a higher internal resolution and downscales it to reduce aliasing (jagged edges). _Note: Higher values will increase render times._
* **UV Tolerance:** The distance threshold for UV seam detection.
  * Increasing this value helps greatly with UV border edges, that are in an angle so that it mitigates the UV seams
  * Increasing it too much may introduce some artifacts
  * Decrease if you see some weird artifacts or UV padding being unpredictable
  * Default value works for majority of scenarios

![Screenshot of Render Settings](../../.gitbook/assets/render_settings.png)
