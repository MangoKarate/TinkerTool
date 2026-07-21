# TinkerTool

A single-file wiring visualizer for hobby electronics. Lay out microcontrollers,
SBCs, and components, define each part's connection points, and wire them
point-to-point with color-coded jumper wires. Everything lives in one HTML file —
no install, no build step, no server.

**Current version:** v1.3 · **Live:** https://mangokarate.github.io/TinkerTool/

---

## Run it

Double-click `index.html` — it opens in any modern browser and runs entirely on
your machine. Once published to GitHub Pages (steps below), you can also open it
from any device at your Pages URL.

## What it does

- **Parts library** — the `⊞ Parts` button drops in ready-made boards (Arduino
  Uno / Nano, ESP32, ESP8266, Raspberry Pi 40-pin) and components (LED, resistor,
  button, pot, servo, HC-SR04, DHT11, buzzer) with correct pin names and sides.
- **Components** — or add a blank block and set label, size, and any number of
  named pins (top / right / bottom / left); pins auto-space along their side.
- **Wiring** — click a pin, then another to connect, or use the "connect to…"
  dropdown under any pin. Wires stay attached when you drag boards around.
- **Routing** — `Route: Tidy` runs wires as straight segments with rounded
  corners and steps them clear of a board when a pin faces the wrong way, so
  nothing cuts across a part. `Curved` and `Direct` are there if you prefer them.
  Drag any wire to reroute it by hand; double-click it to straighten it again.
- **Tidy** — one action to snap boards to the grid and push apart anything
  overlapping, reset hand-routed wires, or both.
- **Colors** — pick from the classic jumper-wire palette (or a custom color);
  every wire's color is editable afterward. Components take a color too, from a
  preset row or a picker; labels flip between light and dark ink automatically
  so they stay readable on any background.
- **Canvas** — drag to move, drag empty space to pan, scroll to zoom, Fit to
  frame everything, Snap to align. Shift-click a wire to delete it fast.
- **Notes** — the `✎ Note` button drops a callout bubble you can drag anywhere
  and type into; use them to flag the details that bite you later. Notes travel
  with the saved layout and appear on the printed report.
- **Report** — the `Report` button opens a landscape blueprint sheet: the drawing
  recolored for paper, a title block, a numbered wire schedule with colors, and
  your notes. Print it or save it as a PDF.
- **Save / Load** — export the whole layout to JSON and re-import it later.

> Layouts save as downloaded JSON files, not in the browser — keep the exported
> `.json` if you want to return to a diagram.

## Icon

`TinkerTool.ico` is a multi-size icon (16–256 px) for a desktop/taskbar shortcut,
and serves as the browser tab icon on the hosted site.

## Publishing (GitHub Desktop → public + Pages)

1. **GitHub Desktop → File → Add Local Repository…** and point at this folder.
   It already has an initial commit, so it's recognized immediately.
2. Click **Publish repository**. **Uncheck "Keep this code private"** — Pages
   needs a public repo on the free tier.
3. On github.com, open the repo → **Settings → Pages → Source: Deploy from a
   branch → Branch: `main` / `root` → Save.** Wait ~60 seconds for the live URL.
4. Paste that URL into the "Live" line above and commit.

Never let the live site be your only copy — with GitHub Desktop the files live
both on your machine and on GitHub, so neither side alone is a single point of
failure.

## Versioning

The version shows in the toolbar and travels with each commit message
(e.g. `Update TinkerTool to v1.2 — <feature>`). Keep the same repo across
iterations so history stays in one place — no file renaming needed.

## Changelog

### v1.3
- Component labels moved to the top of each block with a divider rule, and now
  shrink or clip to fit, so they no longer collide with pin names.
- Rewrote wire routing: straight runs with rounded corners, and wires step
  around a board when a pin points away from its target. Added Curved and
  Direct styles, drag-to-reroute, and double-click to straighten.
- Added Tidy: snap boards to the grid and separate overlaps, reset wire
  routing, or both.
- Added per-component colors with a preset palette and automatic label contrast.

### v1.2
- Added note bubbles (`✎ Note`): draggable, auto-sizing callouts, saved with
  the layout and included on the report.
- Added the blueprint report (`Report`): landscape print sheet with title block,
  wire schedule, and notes.
- Added a Shelley Skelley parts category: 14 components matching Verified Wire
  Labels v30, including the Pico 2 W / Treedix pin map and the three power
  distribution junctions.

### v1.1
- Added Parts library (`⊞ Parts`): 5 boards + 8 common components with correct
  pin maps. Added tab/desktop icon and favicon link.

### v1.0
- Initial release: components with configurable pins, point-to-point + dropdown
  wiring, jumper-color palette, drag/pan/zoom canvas, snap-to-grid, JSON
  save/load, seeded Arduino→LED example.
