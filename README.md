# Paper to Poly

Photograph a character drawn on paper and it becomes a low-poly 3D model you can spin, make dance, and save.

Single file (`index.html`), no server and no API keys. Everything runs in the browser.

## How it works

1. **Find the paper.** A smooth surface is fitted through the paper-coloured parts of the photo, so uneven lighting and soft shadows are divided out.
2. **Cut out the drawing.** Anything darker or more colourful than the paper is ink. Closed outlines are filled in. Bits touching the photo edge (table, shadows) are dropped.
3. **Scatter points.** Along the outline, down the middle of thin limbs, along pen lines and colour edges, then a loose fill.
4. **Triangulate.** Delaunay triangulation, keeping the triangles inside the cut-out. Each triangle takes the average colour underneath it.
5. **Inflate.** Points further from the edge are pushed out further, front and back, giving a puffy solid.

## Controls

- Chunky / Detailed: triangle size
- Flat / Puffy: depth
- Look: flat-colour facets, or the original drawing wrapped on the model
- Fix cut-out: pick up more or less, and rub out stray bits
- Save picture (PNG), Save 3D model (GLB), and on iPad/iPhone, Put it in my room (AR Quick Look)

## Testing without a camera

`index.html?sample` loads a built-in sample drawing. Extra options: `&detail=0-100`, `&look=drawing`, `&still`, `&turn=45`, `&fix`.

Libraries (three.js, delaunator) load from jsDelivr, so the page needs to be online.

## Make Me Low Poly (`me.html`)

Take a photo of someone in a room. The person is rebuilt from shaded triangles and the room is left as it was.

- The person is found on the device with MediaPipe's selfie segmentation model (hair, face, skin, clothes). No photo leaves the device.
- Points follow the outline and the strong edges in the photo, with finer triangles on the face.
- Each triangle takes the average colour underneath it, then is lit as a facet of a puffed-up body shape.
- Controls: Chunky / Detailed, Smooth / Bumpy, Lines, Room too (low-poly everything), hold to see the real photo, Save picture.

The first photo downloads the model (about 16 MB), so it takes a little longer.

Testing: `me.html?test=<image url>` (the image host must allow cross-origin loading), plus `&detail=`, `&bump=`, `&lines`, `&room`.
