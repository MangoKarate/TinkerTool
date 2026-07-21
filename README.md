# TinkerTool

A single-file wiring visualizer for hobby electronics. Lay out microcontrollers,
SBCs, and components, define each part's connection points, and wire them
point-to-point with color-coded jumper wires. Everything lives in one HTML file —
no install, no build step, no server.

**Current version:** v1.5 · **Live:** https://mangokarate.github.io/TinkerTool/

---

## Run it

Double-click `index.html` — it opens in any modern browser and runs entirely on
your machine. Once published to GitHub Pages (steps below), you can also open it
from any device at your Pages URL.

## What it does

- **Parts library** — the `⊞ Parts` button drops in ready-made boards (Arduino
  Uno / Nano, ESP32, ESP8266, Raspberry Pi 40-pin) and components (LED, resistor,
  button, pot, servo, HC-SR04, DHT11, buzzer) with correct pin names and sides.
- **Components** — or add a blank block and set label, size, colour, and any
  number of named pins (top / right / bottom / left); pins auto-space along
  their side and can be reordered or moved to another side.
- **Pin numbers** — a pin's number is separate from where it sits, so a board
  can keep a readable layout — power down one side, GPIO down the other — while
  still telling you which physical pin to count to. The number draws outside the
  block and the function name inside, the way an IC schematic is normally drawn.
- **Your own parts** — edit any board on the canvas, then `Save to library` to
  keep it under "My parts". Built-ins are read-only, so forking one never costs
  you the original.
- **Autosave** — the layout is kept in the browser and restored when you come
  back, so a closed tab no longer loses your work.
- **Wiring** — click a pin, then another to connect, or use the "connect to…"
  dropdown under any pin. Wires stay attached when you drag boards around.
- **Routing** — `Route: Tidy` runs wires as straight segments with rounded
  corners and steps them clear of a board when a pin faces the wrong way, so
  nothing cuts across a part. `Curved` and `Direct` are there if you prefer them.
  Wires that would share a route are fanned into parallel lanes so none is
  hidden underneath another, which also makes a bus read as a deliberate bundle.
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

> Autosave keeps the current layout in this browser only. Export the `.json`
> if you want to keep a diagram, move it to another machine, or version it.

## Shelley Skelley

`shelley-skelley-v30.json` is the finished wiring diagram for that build — 15
parts, 47 wires, and the manifest's cautions as notes on the canvas. Open
TinkerTool, click **Load**, and pick that file.

All 40 connections are checked against *Shelley Skelley Verified Wire Labels
v30*, including the radar's UART crossover (radar TX to GP01, radar RX to GP00).
The extra seven wires are the five unflagged Eye 2 legs into the Y-splices and
the two leads of the 470uF decoupling cap. H1 position 6 is drawn and left
deliberately unwired.

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

### v1.5
- Pin numbers are now separate from pin position, drawn outside the block with
  the function name inside. The Pico 2 W / Treedix carries its real DIP numbers
  and the LD2410C its H1 harness positions.
- Pins can be reordered within a side from the editor.
- Added capacitors (ceramic and electrolytic), diode, SPST switch and fuse, plus
  the 470uF 16V the Shelley build calls for.
- Added an editable parts library: save any board under "My parts", stored in
  the browser. Built-ins stay read-only.
- Added autosave and restore of the working layout.
- Added `shelley-skelley-v30.json`, the complete pre-wired Shelley diagram.

### v1.4
- Wires that want the same channel are now assigned parallel lanes instead of
  stacking on identical paths. A wire's horizontal run and vertical run are
  laned independently, so two wires heading for the same board no longer share
  a drop. On a seven-wire test layout the worst-buried wire went from 89%
  hidden to 11%.
- Tidy routing is now strictly right-angled. Offsets move a whole channel line
  rather than a single corner, and a corner too tight to round keeps its hard
  right angle instead of being dropped — that omission was joining its two
  neighbours with a diagonal.

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
