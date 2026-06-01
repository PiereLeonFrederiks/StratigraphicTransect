# Stratigraphic Transect Viewer
### Core Logger Addon



A single-file, browser-based tool for visualising multiple sediment core or borehole profiles as a georeferenced stratigraphic transect. Designed as a companion to the **Geoarchaeological Core Logger**, it imports JSON or TXT exports directly and renders a publication-ready cross-section.
*by PLF*
---

## Features

### Profile Import
- Import **Core Logger JSON** (full session profiles) or **TXT / TSV / CSV** exports
- Drag-and-drop or file picker; **multiple files at once** are supported
- Each loaded profile appears in the sidebar borehole list and can be individually toggled

### Transect Visualisation
- Renders all boreholes as a side-by-side stratigraphic cross-section on an HTML5 canvas
- Borehole positions are ordered spatially by **perspective direction** (N / S / W / E) based on their GPS coordinates — left-to-right order reflects real-world geometry along the chosen axis
- **Absolute elevation alignment** (m a.s.l.) when surface elevation data is present, so stratigraphic contacts can be visually correlated across uneven terrain
- Soil layers rendered in their logged colours with Munsell-mapped tones; layer classification codes shown as labels

### 3D Offset Rendering
- Adjustable **3D offset depth** gives each borehole column a pseudo-3D extruded appearance for improved readability in printed figures

### Overlays (all toggleable)
- Manual correlation lines
- Markers and horizon indicators
- Compaction zones
- Layer classification labels
- Depth axis and scale bar
- Horizontal grid lines
- Absolute elevation alignment

### Correlation Mode
- Click-to-connect **manual layer correlation** across boreholes
- Select 2–6 layers across different cores to draw a colour-coded correlation band
- Connections listed in the sidebar with individual delete controls
- Clear all connections in one click

### Scale & Layout Controls
- **Vertical scale multiplier** (0.25× – 8×): stretch or compress the depth axis
- **Horizontal scale multiplier** (0.25× – 8×): adjust spacing between boreholes
- **Borehole column width** (20 – 140 px)
- **3D offset depth** (0 – 60 px)
- **Paper format**: A4 or A3, landscape or portrait — canvas sized to match at 96 dpi

### Export
- **PNG** — raster image at paper dimensions
- **JPG** — compressed raster
- **SVG** — scalable vector for further editing in Inkscape, Illustrator, etc.

---

## Usage

1. Open `index.html` in any modern browser — no installation required
2. Import one or more Core Logger profile files via the **Import Profiles** panel (drag-and-drop or click)
3. Select a **Perspective Direction** to order boreholes spatially
4. Adjust scale, column width, and paper format as needed
5. Toggle overlays on or off
6. Optionally enter **Correlation Mode** to draw stratigraphic connections between cores
7. Export the finished transect as PNG, JPG, or SVG

---

## Input File Formats

| Format | Source |
|---|---|
| `.json` | Core Logger "Save Profile (JSON)" export |
| `.txt` / `.tsv` / `.csv` | Core Logger "Download TXT" or "Copy as TSV" export |

Coordinates (longitude/latitude/elevation) embedded in the profile are used to position boreholes spatially. Profiles without coordinates are placed at the origin and spaced evenly.

---

## Companion Tool

This viewer is an addon to the **Geoarchaeological Core Logger** (`index.html`), which handles field data entry, soil classification, and initial profile export. Use the Core Logger in the field to capture layers, markers, and GPS coordinates, then import the exports here to build the cross-section.

---

## Browser Compatibility

| Browser | Support |
|---|---|
| Chrome / Edge (desktop) | ✅ Full |
| Firefox (desktop) | ✅ Full |
| Safari (macOS) | ✅ Full |
| Mobile browsers | ⚠ Functional; optimised for desktop use |

---

## License

See repository or contact the author for licensing information.
