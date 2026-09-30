# Floor Plan Designer

A browser-based tool for interior floor planning and fitout design. Place furniture on a 2D plan, add or remove walls, take measurements, then switch to a live Three.js 3D scene in one click. Orbit for a bird's-eye view or walk through the space in first person. The whole app is a single `index.html` with no build step: open it and it runs.

## Project context

This repository is the final-year project deliverable of **Bideri Alec** at the Adventist University of Central Africa (AUCA). The project scope was reviewed and accepted by **Nexus Vision Partners**, a construction and interior fitout company, as the student's final-year project work.

It builds on the open-source project [`wy51ai/floorplan-3d`](https://github.com/wy51ai/floorplan-3d). This is the English-first edition: English is the default interface, the source comments and documentation are in English, and the original Chinese / English toggle is kept, so the UI can still switch to Chinese at any time.

## Features

**2D planning**

- Shown at the original plan's 1:60 / 1:100 scale, dimensions in mm
- Drag 60+ furniture and appliance types in from the left library (bedroom, living room, dining and kitchen, bathroom, appliances, study and leisure)
- Drag to move, rotate (hold Shift for free angles), resize; items snap flush to walls
- Measure tool (snaps near walls, hold Shift to lock horizontal / vertical)
- Remove non-load-bearing walls; load-bearing walls are marked separately
- Layer toggles: dimensions, room names, furniture, grid, load-bearing walls

**3D scene**

- Bird's-eye, angled and top-down views; click a room in the list to fly to it
- Walk mode: WASD + mouse on desktop, a virtual joystick on touch devices, tap doors to open and close them
- Full-height / cut-wall toggle, sunlight-time slider, night lighting
- Detailed furniture models: cabinet door seams and handles, upholstered headboards, metal and ceramic materials with environment reflections
- Select and drag furniture in 3D too, synced live with the 2D plan

**Plans and statistics**

- Automatic room area and net floor area totals
- Set the flooring per room (oak, walnut, tile, marble, terrazzo, carpet and more) with cost estimated from area plus 5% waste
- Undo / redo, plans saved in the browser
- English / Chinese interface toggle (top-right button; English by default, the choice is remembered)
- Export a PNG image, export / import the plan as JSON

## Quick start

```bash
git clone https://github.com/alecbideri/floorplan-3d-en.git
cd floorplan-3d-en
```

Then open `index.html` in a browser. Or serve it locally:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

> Three.js loads from the jsDelivr CDN, so the 3D scene needs an internet connection the first time it opens.

## Keyboard shortcuts

| Key | Action |
| --- | --- |
| `T` | Switch 2D / 3D |
| `V` / `M` / `X` | Select / Measure / Demolish wall |
| `R` / `Shift+R` | Rotate selected furniture 90° clockwise / counter-clockwise |
| `Delete` / `Backspace` | Delete selected furniture |
| `Ctrl/⌘ + D` | Duplicate selected furniture |
| `Ctrl/⌘ + Z`, `Ctrl/⌘ + Shift + Z` | Undo, redo |
| `F` | Fit to window |
| `+` / `-` | Zoom in / out |
| `[` / `]` | Show / hide the furniture library, show / hide the right panel |
| `Shift + F` | Fullscreen |
| `Esc` | Cancel the current action |
| Walk: `WASD` / arrow keys, `Shift`, `E` | Move, run, open and close doors |

## Tech stack

- Plain HTML / CSS / JavaScript, no framework, no build step
- 2D plan drawn with SVG
- 3D scene with [Three.js](https://threejs.org/) r160 (OrbitControls, PointerLockControls, RoundedBoxGeometry, RoomEnvironment, CSS2DRenderer)
- Data stored in `localStorage`

## Customising the floor plan

The plan data lives in `index.html`:

- `ROOMS`: room polygons, names, default flooring
- `WALLS` / `WINS`: walls and window openings
- `MATS`: flooring names and unit prices
- `LIB`: furniture library (type, name, default size, colour)
- `buildFurniture()`: the 3D model for each furniture type

Edit these to swap in your own floor plan.

## Credits and attribution

- Upstream open-source project: [wy51ai/floorplan-3d](https://github.com/wy51ai/floorplan-3d)
- English edition and final-year project work: Bideri Alec, Adventist University of Central Africa (AUCA). Project scope reviewed and accepted by Nexus Vision Partners.

The upstream repository does not ship a licence file. This edition keeps the original attribution. Confirm licensing with the upstream author before reuse.
