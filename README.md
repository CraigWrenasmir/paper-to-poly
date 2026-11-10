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
