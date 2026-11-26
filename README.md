# Davide's Hiking Style

Hiking map style for north-east Italy, written in the
[MapLibre style specification](https://maplibre.org/maplibre-style-spec/) on
MapTiler data.

Live map: https://giaco1999.github.io/davides-hiking-style/
(the design choices are explained in the map's legend panel).

## Data

| Source | MapTiler tileset | Used for |
| --- | --- | --- |
| `omt` | Planet v3 | land cover, water, roads, paths, peaks, places, huts |
| `v4` | Planet v4 | buildings, lake labels |
| `outdoor` | Outdoor | marked trails, difficulty, trail numbers, viewpoints, caves |
| `contours` | Contours | contour lines |
| `dem` | Terrain RGB | hillshade and 3D terrain |

## Files

- `style.json`: the style
- `sprite.*`, `sprite@2x.*`, `icons/`: custom icons
- `index.html`, `config.js`: the demo page

The work was greatly sped up by using Claude (Anthropic) to write both the style
code and the HTML page. The cartographic choices, and the review of every result,
are mine.

Data © MapTiler © OpenStreetMap contributors.
