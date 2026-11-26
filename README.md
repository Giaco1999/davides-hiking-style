# Davide's Hiking Style — a MapLibre map style

A hiking map style for the Dolomites and north-east Italy, written directly in the
[MapLibre style specification](https://maplibre.org/maplibre-style-spec/) on
MapTiler data. Live demo: `https://giaco1999.github.io/davides-hiking-style/`

## Data

| Source | MapTiler tileset | Used for |
| --- | --- | --- |
| `omt` | Planet v3 (OpenMapTiles schema) | land cover, water, roads, paths, peaks, places |
| `contours` | Contours v2 | contour lines and index labels |
| `outdoor` | Outdoor | marked trails, difficulty, trail numbers, huts, bivouacs, viewpoints, caves |
| `v4` | Planet v4 | buildings (from z12), lake label points |
| `dem` | Terrain RGB v2 | hillshade and 3D terrain |

## Design choices

- **The trail network is the subject.** Roads stay pale and narrow; marked
  trails are the only red lines on the map, as on Italian CAI maps.
- **Difficulty is read from the dash, not the colour.** Easy, mountain and
  alpine trails (from OSM `sac_scale`) share one red and differ in dash length,
  so the map still works in greyscale and for colour-blind users.
- **Unmarked paths are secondary.** All footpaths come from the base map in a thin
  brown dash; marked trails from the outdoor tileset sit on top with a white halo.
- **Zoom-level hierarchy.** Contours thin out at low zoom (every 5th/10th line
  below z13); peaks are filtered by rank until z13; saddles, hut names and trail
  numbers appear only from z13, where they have room.
- **Huts win label conflicts.** On a mountain map huts are destinations, so they
  get bold names and beat peak and place names when labels collide. Huts,
  bivouacs, viewpoints and caves use a small custom sprite (`icons/`, built into
  `sprite.png` / `sprite@2x.png`).
- **Labels avoid trails.** An invisible symbol layer along the marked trails
  takes up collision space; hut, bivouac and peak names pick a free position.
- **Lakes are landmarks.** One straight, horizontal name per lake at its label
  point (Planet v4 `water_centroid`), sized by area and placed above every
  other label; lakes are drawn over rivers.
- **Relief.** A warm, north-west-lit hillshade blends with the paper colour;
  glacier contours are blue, following printed alpine maps.

## Area

The style is designed and checked for north-east Italy. The view is limited
to the Alps and their surroundings, from z6.

## Run it

1. Get a MapTiler API key and restrict it to your domain.
2. Put it in `config.js`.
3. Serve the folder (GitHub Pages, or `python3 -m http.server`).

The work was significantly sped up by using Claude (Anthropic) to write the style
code. The cartographic choices, and the review of every result, are mine.

Data © MapTiler © OpenStreetMap contributors.
