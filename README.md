# Stratigraphic Transect Viewer

### Core Logger Addon

**v0.2.0 · Pre-release**

A single-file, browser-based tool for visualising multiple sediment core or borehole profiles as a georeferenced stratigraphic transect. Designed as a companion to the **Geoarchaeological Core Logger**, it imports JSON or TXT exports directly and renders a publication-ready cross-section.

To the application: https://piereleonfrederiks.github.io/StratigraphicTransect/

⚠ Early Access — This project is under active development. Features, exports, and data formats may change between versions. If you use this tool, I'd love to hear what works, what doesn't, and what's missing.

DOI: <https://doi.org/10.5281/zenodo.21983560>

---
 
## Features
 
### Import & Profiles
 
- Drag-and-drop or click-to-browse import, multiple files at once
- Reads Core Logger JSON exports (v2 schema) and TXT/TSV/CSV exports
- Duplicate filenames are replaced automatically on re-import
- Per-profile summary (coordinates, elevation, layer count) with one-click removal
- Click a core's colour strip in the sidebar to open a per-layer colour editor
### Layout & Perspective
 
- Four look directions (N/S/E/W) — orders boreholes left→right along the corresponding real-world axis
- Auto-fit or manual vertical/horizontal scale multipliers, with the resulting px/m always shown
- Adjustable borehole column width and an optional 3D "core" perspective effect (off by default — a flat 2D view unless turned on)
- Optional alignment to absolute elevation (m a.s.l.) instead of raw depth, when survey elevation is present
### Paper & Canvas
 
- A4, A3, or fully custom paper size (mm) in landscape or portrait
- Independently adjustable page margins
- Custom canvas background colour, with an optional transparent background for PNG/SVG export
- Toggleable decorative paper-grid texture and horizontal reference grid lines, independent of each other
### Stratigraphic Rendering
 
- Standard flat-colour columns, or a **grain-size / weathering profile** style where each layer's column width tapers to reflect its grain-size fraction (mirrors the Core Logger's own convention), including gradational (sloped) boundaries
- Boundary line style reflects recorded contact character — dashed for gradual/diffuse, a small wave for irregular, solid for sharp
- Disturbed/reworked layers get a hatch fill, togglable independently of the flat colour
- "Missing core" intervals get a distinct dashed/void treatment
- Optional per-layer depth labels (cm from the top of that specific core) beside each boundary, and an optional total logged depth per core
- Optional borehole outline box, anchored to each core's own depth range — useful as a reference frame, especially with the grain-size column style
- Markers, horizon tags, and observation/find-texture overlays are three independently toggleable layers (tick/leader-line, text label, and texture ornament)
- Automatic collision avoidance for the various right-hand-side text annotations (depth ticks, disturbance tags, marker labels) — nothing overlaps illegibly; a short leader line marks anything nudged from its true depth
- Independent font-size scaling for four text categories: header block, axis text, in-column classification labels, and annotations
- Depth-axis and elevation-axis tick spacing are automatic by default, or can be fixed to any interval
### Correlation Between Cores
 
- Correlation mode: click one or more layers in each core, then connect them into a shaded band
- **Pinch-out / uncertain-continuation wedges**: anchor either side of a connection at the layer's full span, or collapse it to just its top or bottom edge, to show a horizon that may not be documented at one core but could continue between them
- In grain-size column mode, correlation bands attach to the actual tapered edge of the connected layer, not a fixed column width
- Disturbed/heterogeneous correlated units carry the same hatch pattern as the layer they connect
- Per-connection colour, label, and free-text note; existing connections are editable afterward — including cycling their anchor type — without deleting and re-creating them
### Legend
 
- Auto-detects which lithology codes and correlation bands are actually present and lists them, so you don't have to type them in twice
- Two independently toggleable sections: core descriptions and correlation bands — show either, both, or neither
- Adjustable size (swatch/font/spacing scale)
- Either appended below the plot automatically, or dragged to any position directly on the canvas
- Editable directly on the canvas — click any legend row, in either position mode, to edit its note (and label, for correlation bands) right there, in addition to the sidebar panel
### View Navigation
 
- Drag to pan, scroll wheel to zoom the on-screen view — purely a display transform; the underlying canvas resolution, and therefore every export, is completely unaffected by how it's currently zoomed or panned
- One-click "Reset View" back to exactly what the paper format settings produce
### Save & Resume
 
- **Save Project** writes one JSON file containing every loaded profile, every correlation (with anchors, colours, labels, notes), every legend note, and the complete display-settings state
- **Load Project** restores all of it exactly, syncing every control in the sidebar — pick up exactly where you left off, or hand the file to someone else to continue
---
 
## Export Formats
 
| Format                  | Description                                                                 |
| ------------------------ | ----------------------------------------------------------------------------- |
| **PNG**                  | Raster image of the transect, any DPI from screen resolution to 600 DPI, optional transparent background |
| **JPG**                  | Raster image, flattened onto the chosen canvas background colour (no alpha channel) |
| **SVG**                  | Vector export — a hi-DPI raster layer for fills/textures, with a crisp vector layer on top for text and outlines; optional transparent background |
| **Save Project (JSON)**  | Full session state — profiles, correlations (with anchors/colours/notes), legend notes, and every display setting |
| **Load Project (JSON)**  | Re-import a previously saved project file                                    |
 
There's no lossy step anywhere in this pipeline: Save Project round-trips every setting exactly, and raster/vector exports always render from the same underlying draw pass shown on screen — panning or zooming the view never affects what gets exported.
 
---
 
## Usage
 
1. Open the `.html` file in any modern browser — no installation, no internet required
2. Import two or more Core Logger exports using the **Import Profiles** panel
3. Pick a look direction and paper size, then adjust layout/canvas/typography to taste
4. Switch on correlation mode and connect matching horizons between adjacent cores
5. Turn on the legend — it auto-detects what's present — and add any descriptions you want, editing directly on the canvas or from the sidebar
6. Export at your target DPI, or save the project to keep working on it later
---
 
## Companion Tool — Core Logger
 
This viewer is designed to consume the JSON/TXT export from the **Geoarchaeological Core Logger**. Any core logged there — including gradational shifts, banded soils, Munsell-aware colours, and find textures — can be dropped straight in and will render with its full classification intact.
 
---
 
## Desktop-Oriented
 
Unlike the Core Logger, this viewer is built for the desk, not the field: laying out and correlating a multi-core transect benefits from a larger screen and a mouse (drag-to-pan, scroll-to-zoom, click-and-drag legend placement). It will load in a mobile browser, but the control panel and canvas interactions are not optimised for touch.
 
---
 
## Paper & Export Reference
 
| Setting          | Range                                                             |
| ----------------- | -------------------------------------------------------------------- |
| Paper size         | A4, A3, or custom (mm), landscape or portrait                        |
| Export DPI         | 96 (screen) – 600 (poster), selectable per export                    |
| Background         | Any colour, or transparent (PNG/SVG only — JPG always flattens)      |
| Legend position    | Auto (below the plot) or manual (dragged anywhere on the canvas)     |
 
---
 
## File Structure
 
The entire application is a single self-contained `.html` file. All styles, logic, and rendering code are inlined — no external dependencies, no build step.
 
---
 
## Browser Compatibility
 
| Browser                | Support   |
| ------------------------ | ----------- |
| Chrome / Edge (desktop)  | ✅ Full     |
| Firefox (desktop)        | ✅ Full     |
| Safari (macOS)           | ✅ Full     |
| Mobile browsers          | ⚠️ Loads and functions, but the interface is not touch-optimised |
 
Built and tested against current Chrome/Chromium; only uses standard Canvas 2D, File, and Blob APIs, so any modern evergreen browser should work.
 
---
 
## Known Limitations (Pre-release)
 
- Single-file, single-session tool — there's no server, no accounts, and no auto-save; use **Save Project** before closing the tab if you want to keep your work
- Designed around the Core Logger's JSON schema; hand-edited or third-party files that deviate from that schema may not import cleanly
- Very large transects (dozens of cores, or very high export DPI) will be slower to render — this is a client-side canvas renderer with no pagination
---
 
## License
 
See repository or contact the author for licensing information.
 
## Credits
 
Developed by Pière Leon Frederiks. AI-assisted development — Claude (Anthropic) was used during parts of the scripting process.
 
