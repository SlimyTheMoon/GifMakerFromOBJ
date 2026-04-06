# GifMakerFromOBJ

## Overview

This project is a single-page website that loads a 3D model from an `.obj` file, renders it in a stylized wireframe scanner view, and generates an animated GIF of the rotating scene.

The page is built entirely in `index.html` using:
- `three.js` for 3D rendering
- `OBJLoader` to parse `.obj` mesh files
- `gif.js.optimized` to capture frames and encode a GIF
- Tailwind CSS for the interface styling

## How It Works

1. User uploads an `.obj` file using the `UPLOAD .OBJ` button.
2. The app reads the file contents as text and parses it with `THREE.OBJLoader()`.
3. The model is centered, scaled, and converted into a wireframe mesh.
4. A live preview canvas renders the scene with:
   - rotating 3D geometry
   - glow and scanline effects
   - grid overlay and vignette
   - dynamic HUD text labels and random hexadecimal telemetry values
5. When the user clicks `Generate Modernized GIF`, the app records frame-by-frame output from the preview canvas.
6. The captured frames are encoded into a GIF using `gif.js.optimized`.
7. A download link appears when rendering is complete.

## User Interface

The right panel controls the scan effect and GIF output:
- Text labels (`LABEL 1`, `VALUE 1`, `LABEL 2`, `VALUE 2`)
- Theme color and background color
- GIF duration
- Model scale
- Glow intensity
- Grid opacity
- Scanline opacity

The left panel shows the live preview and upload button.

## Usage

1. Open `index.html` in a modern browser.
2. Upload a valid `.obj` file.
3. Adjust the visual settings as desired.
4. Click `Generate Modernized GIF`.
5. Download the resulting GIF from the link that appears.

> For best results, serve the page via a local web server (for example, VS Code Live Server). Direct `file://` opening may produce worker or resource loading issues.

## Default Behavior

- If no `.obj` is uploaded, the app renders a default procedural torus knot.
- The GIF is created at 20 FPS and uses the configured duration.
- The output filename defaults to `3D_Tech_Analysis.gif`.

## Customization

You can edit the built-in configuration values inside `index.html` near the top of the script:
- `GIF_DURATION_SECONDS`
- `THEME_COLOR_HEX`
- `BG_COLOR_HEX`
- `LABEL_TRGT`
- `TEXT_TRGT`
- `LABEL_STAT`
- `TEXT_STAT`
- `MODEL_SCALE`
- `GLOW_INTENSITY`
- `GRID_OPACITY`
- `SCANLINE_OPACITY`

These values control the default appearance and behavior of the rendered scanner scene.

## Notes

- The page depends on external CDN-hosted libraries. Internet access is required unless resources are hosted locally.
- The GIF worker script is loaded dynamically from CDN during GIF generation.
- If parsing fails, the app will show an error message and preserve the current preview state.

## Project Files

- `index.html` — entire app, layout, styling, and JavaScript logic
- `README.md` — this explanation

