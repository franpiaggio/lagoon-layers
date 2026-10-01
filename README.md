# Lagoon layers

The Lagoon Nebula (M8), rebuilt in code one piece at a time.

Online: https://franpiaggio.github.io/lagoon-layers/

The page opens on the original photo. Press **Reproduce** and it goes black, then rebuilds the image from a fitted model: 6,500 Gaussian blobs, biggest first, followed by 1,744 stars, brightest first. When it finishes you are looking at code, not a photo.

## What you can do

- **Reproduce** plays the whole rebuild. Press it again to stop.
- **The slider** walks the same frames, from black to the finished image, so you can scrub back and forth and see each step. "+1 step" moves one frame.
- **Views**:
  - *Sum*: background plus every blob so far.
  - *Light added*: only the positive part of each blob, the glowing gas.
  - *Light taken away*: only the negative part, where the fit subtracts light to draw dust lanes and sharp edges. About two thirds of the blobs take light away somewhere.
  - *Final image*: every blob, the cutouts and the stars.
- **Blob outlines** draws a circle at two sigma around the latest blobs: rose for blobs that add light, teal for blobs that take it away.

## How the model was made

The photo was measured outside the browser and fitted with simple functions. Stars were found and modelled first, as a core and a halo, with diffraction spikes on the ten brightest. With the stars taken out, the remaining gas was approximated by adding Gaussian blobs one at a time where the model differed most from the photo, adjusting each one's position, size and color. Blobs may have negative color, which is how the dark dust is drawn. Small "cutouts" clean up leftover light under the brightest stars. The fitting script is not part of this repository.

The blobs are stored in the order the fit added them, which is why the rebuild goes from a blurry overall shape to fine detail.

## Running it

One HTML file plus the photo, no dependencies and no build step. Open `index.html` in a modern browser, or serve the folder:

```sh
python3 -m http.server 8000
```

The model comes from [nebulosas](https://github.com/franpiaggio/nebulosas), a playground for nebulae drawn in code. This page carries its own copy of the data.
