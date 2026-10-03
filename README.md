# Tokyo CBD · 1.00 sq mi · interactive 3D

One square mile of downtown Tokyo (Shimbashi / Suklan / Shijo-in) as a fully interactive 3D model, in a **single HTML file**.

Live: https://oherna25.github.io/tokyo-1sqmi/

## What it is

Real geometry, not a procedural mock-up. Building footprints, street network, parks, trees and the elevated metropolitan expressway were pulled from OpenStreetMap (Overpass API) for a 1.609 km × 1.609 km bounding box centred on Shimbashi, then encoded as a compact quantised blob embedded in the page. Heights come from `height` / `building:levels` tags, with a district heuristic where OSM is untagged.

- 4423 buildings, 1464 road polylines, 336 named structures
- bbox `35.68887–35.70333, 139.73140–139.74920`
- tallest 134 m, mean 13.0 m
- file size ~495 KB, one dependency: three.js r169 from a CDN

## Controls

| Input | Action |
|---|---|
| drag | look / orbit |
| wheel | zoom |
| WASD | move |
| space / v | up, down |
| shift | fast |
| click | select building (info card) |
| hover | name tooltip |
| F / G / M | fly / street-level / map camera |
| T | auto time-of-day cycle |

Panel: time-of-day slider, day/night cycle, minimum-floor filter, six category toggles, camera mode, reset view, screenshot, landmark list with `go to landmark` and `focus selected`.

Selection is GPU id-picking (an offscreen id pass), so hover/click work against the merged building mesh rather than thousands of separate objects.

## Local use

Open `index.html` directly, or serve the directory:

```
python -m http.server 8000
```

Needs network only for the three.js CDN import; the city data is embedded.

## Data attribution

Map data © OpenStreetMap contributors, https://www.openstreetmap.org — [OSM terms of use](https://www.openstreetmap.org/copyright). Generated from an Overpass API extract; untagged building heights are estimated, so individual structures are approximate.
