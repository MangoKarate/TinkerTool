# TinkerTool

A single-file wiring visualizer for hobby electronics. Lay out microcontrollers,
SBCs, and components, define each part's connection points, and wire them
point-to-point with color-coded jumper wires. Everything lives in one HTML file —
no install, no build step, no server.

**Current version:** v2.5 · **Live:** https://mangokarate.github.io/TinkerTool/

---

## Run it

Double-click `index.html` — it opens in any modern browser and runs entirely on
your machine. Once published to GitHub Pages (steps below), you can also open it
from any device at your Pages URL.

## What it does

- **Parts library** — starts empty on purpose. Build it up with `+ New part…`:
  name the part, pick a shape, size and colour, then enter the pinout — one pin
  at a time, a block of rows at once, or pasted straight from a datasheet. A live
  preview draws the part as you type, so a wrong side or a missing number is
  obvious before you save. Parts are stored in this browser and can be edited or
  removed later. Saved layouts carry their own definitions, so they open whether
  or not the library has the part.
- **Shapes** — `+ Component` draws parts as silhouettes rather than boxes: DIP
  IC, module, display, screw terminal block, resistor, electrolytic seen from
  above or from the side, diode, LED with dome and flange, TO-220 with its tab,
  TO-92, push button, potentiometer, servo with flanges, speaker, barrel jack —
  plus plain rectangle, rounded, circle and a splice marker. Pins follow the
  real outline, so an LED's pins sit on its flange and a TO-92's on its curved
  back. The outline is all there is: the inside of a block stays empty so pin
  names and numbers own that space.
- **Components** — adding one asks how many pins it has, unless the package
  fixes that already (a resistor has two leads and always will). Pins space
  themselves evenly and the block grows to hold them, so a 30-pin breakout is
  readable the moment it lands. `Arrange…` re-lays them in IC order, in two
  plain columns, or in one; `+ Pin` fills whichever column is shorter.
- **Pin kinds** — every pin is power, ground, GPIO or signal, guessed from its
  name and overridable. Power pads draw red and ground grey, so the two that
  matter are findable on a dense board. `Group by kind` gathers them.
- **Editing** — double-click a pin to change its number, name, side or kind
  without hunting for its row; double-click a component to rename it.
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
  Grab a wire anywhere and drag: that point becomes a waypoint you can move in
  any direction, and a wire can carry as many as you need. Double-click a
  waypoint to remove it, or double-click elsewhere on the wire to drop them all.
- **Wire numbers** — each wire carries its schedule number in a small badge on
  the run itself, repeated about every 300px up to five times, so a long wire
  can be identified anywhere along its length and matched to the printed table.
- **Optimize** — replaces Tidy, and shuffles rather than settles. Choose
  Routing, Placement or Both; each press offers a different arrangement — four
  board placements (nudge in place, columns, rows, columns ordered by how many
  wires a board carries) and four routing styles (channel position, which edge
  wires escape around, lane order). Routing also clears hand-placed waypoints.
- **Colors** — pick from the classic jumper-wire palette (or a custom color);
  every wire's color is editable afterward. Components take a color too, from a
  preset row or a picker; labels flip between light and dark ink automatically
  so they stay readable on any background.
- **Names** — component names sit on a plate above each block by default, clear
  of the pin text, and show in full rather than being clipped. Switch to
  `Name: inside` for the older look.
- **Right-click** — right-click a board, wire or note for rename, colour, save to
  library and delete, without going to the side panel. On a tablet, long-press
  does the same.
- **Grid** — the canvas grid can work in millimetres (1, 2.54, 5 or 10 mm) as
  well as the default screen spacing, and Snap follows whichever is set.
- **Canvas** — drag to move, drag empty space to pan, scroll to zoom, Fit to
  frame everything. Shift-click a wire to delete it fast. Boards follow the
  pointer while you drag and land on the grid when you let go; untick **Snap**
  for free positioning. Select a board, wire or note and press **Delete** (or
  Backspace) to remove it — deleting a board takes its wires with it.
- **Undo / redo** — `⌘Z` and `⇧⌘Z`, or the two arrows in the toolbar. Every
  edit is undoable, sixty deep, so a mistaken Delete costs one keystroke.
- **Notes** — the `✎ Note` button drops a callout bubble you can drag anywhere
  and type into. Each carries a number badge that matches its line in the printed
  schedule, so a bubble on the drawing and a note on the sheet refer to each
  other. Paper colour, font and text size are per note.
- **Report** — the `Report` button opens a landscape blueprint sheet: the drawing
  recolored for paper, a title block, a numbered wire schedule with colors, and
  your notes. Print it or save it as a PDF.
- **Save / Load** — export the whole layout to JSON and re-import it later.

> Autosave keeps the current layout in this browser only. Export the `.json`
> if you want to keep a diagram, move it to another machine, or version it.

## Shelley Skelley

`shelley-skelley-v31.json` is the finished wiring diagram for that build — 20
parts, 52 wires, and the manifest's cautions as notes on the canvas. Open
TinkerTool, click **Load**, and pick that file. Parts are drawn as silhouettes:
the Pico and breakouts as modules, the eyes as displays, the distribution rails
as terminal blocks, the servos, speaker, barrel jack and electrolytic as
themselves.

The five eye signals meet at real three-legged splices rather than terminating
on Eye 1's connector: roughly 6in from each eye joins at a soldered junction,
and a single pigtail carries the signal on to the Treedix. Only that pigtail
carries a wire flag, which is why the flag count stays at 40 while the drawing
holds 52 wires — the ten eye legs and the two capacitor leads are real but
unflagged.

`shelley-skelley-v30.json` is the earlier version, kept for reference.

All 40 connections are checked against *Shelley Skelley Verified Wire Labels
v30*, including the radar's UART crossover (radar TX to GP01, radar RX to GP00).
H1 position 6 is drawn and left deliberately unwired — a structural check
confirms it is the only unconnected pin of 103.

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

### v2.6
- **Saving a part to the library works again.** The save helper never returned
  its result, so every save reported that the browser was blocking local storage
  and stopped — after having already written the part. The library never
  refreshed and the builder never closed, so it looked like nothing happened.
- **Adding a component asks how many pins it has**, and lays them out evenly.
  Parts whose lead count is fixed by the package — a resistor, an LED, a TO-220,
  a servo — skip the question and arrive with their datasheet lead names.
- **Pins no longer pile up on one side of a block that never grew.** Eleven pins
  on an 80px body sat 6.7px apart with 11px pads, so they overlapped and their
  labels stacked. Blocks now grow to hold their pins at a 24px pitch, and `+ Pin`
  fills whichever column is shorter instead of always the right.
- **Pins have a kind — power, ground, GPIO or signal** — guessed from the name
  (`VSYS`, `3V3`, `GND2`, `GP15`) and overridable per pin. Power pads draw red
  and ground grey, the bench convention, so the two that matter are findable on
  a crowded board.
- **Arrange…** re-lays a part's pins: two columns in IC order (pin 1 top left,
  numbering counter-clockwise), two columns reading top to bottom, or one column.
  **Group by kind** brings power and ground together. Grouping is opt-in — pin
  order is a property of the real part, not ours to change silently.
- **Double-click a pin to edit it** where it sits: number, name, side, kind, or
  delete. Double-click a component to rename it.
- **Nothing is drawn inside a block any more.** Cone rings, mounting holes,
  bezels, screw heads and polarity bands competed with the pin names and numbers
  for the same space. The outline identifies the part; what the marks encoded —
  which end is the cathode, where pin 1 sits — the lead names now say outright.

### v2.5
- The printed drawing keeps its title block on the same page. The page break
  came immediately after the drawing, so page one carried no project, date,
  revision or wire count — the one sheet most likely to reach a bench was the
  one that could not identify itself.

### v2.4
- Loading is atomic. A file that is not a layout, or was saved by a newer
  version, is refused rather than partly applied; unreadable records need
  confirmation before import; and the board you had stays one Undo away.
- Note paper, font and size now survive Load and session restore — the
  validator had been silently discarding them since v2.2.
- Optimize leaves the routing it actually drew in state, so the picture no
  longer changes on the next redraw.
- Undo covers name position, grid, and both Optimize variants.
- Clicking a wire only selects it. A waypoint is created on movement, so a
  click leaves nothing behind and a drag is a single undo step.
- Same-component wires ring the correct pair of edges — a top-to-bottom
  connection no longer runs through the body. All sixteen side pairs verified.
- Pins sharing an edge are laned apart at the stub, so a fan-out off one side
  no longer buries itself.
- Colours are restricted to six-digit hex and the report swatch is built as a
  node, closing a CSS-injection path through a saved colour.
- The pinout paste accepts single-spaced lines, the format its own help shows.

### v2.3
- Wires are hand-routed with waypoints instead of a single-axis nudge. Grab a
  wire anywhere and it becomes a point you can move in any direction; add as
  many as a run needs. Double-click removes one, or clears the wire.
- Fixed the elbow rule that made a hand-routed wire climb to a waypoint and come
  straight back down the line it had just travelled.
- Each wire carries its schedule number in a badge on the run, repeated about
  every 300px up to five times, so the drawing and the printed table can be read
  against each other anywhere along a wire.
- Roomier geometry: longer pin stubs, a larger corner radius and more board
  clearance, so turns near pins are less pinched.
- Renamed Tidy to Optimize, with Routing, Placement and Both.

### v2.2
- Notes are numbered, and the badge on a bubble matches its number in the
  printed schedule so the two can be cross-referenced.
- Notes take a paper colour, a font and a text size of their own.
- Component names moved to a plate above the block by default, which ends the
  collision with pin names and lets a long name show in full. `Name: inside`
  keeps the old behaviour.
- Added a right-click menu on boards, wires and notes — rename, recolour, save
  to library, straighten, delete — writing to the same state the side panel and
  toolbar use. Long-press is the tablet equivalent.
- The canvas grid can be set in millimetres (1, 2.54, 5, 10) and Snap follows
  it, so spacing can match a real board.
- Touch: pinch to zoom, two-finger pan, larger pin targets and controls on
  coarse-pointer devices.

### v2.1
- Emptied the built-in parts library. Pinouts are being re-entered one at a
  time and checked against datasheets; the earlier definitions remain in git
  history, and saved layouts are unaffected because they carry their own.
- Added a part builder: `+ New part…` in the library. Name, category, shape,
  width, height and colour, plus a pin table that grows one row at a time, by a
  block of rows, or by pasting a pinout. Each pin takes a number, a name and a
  side, and rows can be reordered. A live preview renders the part with the same
  geometry the canvas uses, so what you see is what you get. User parts can be
  reopened and edited.
- Fixed pin rows wrapping onto two lines — the grid still assumed three columns
  per row after number and reorder controls were added in v1.5.
- Escaped library category text, which was the injection sink left over from the
  earlier pass (that fix had landed on the shape picker instead).

### v2.0
- Added undo and redo (⌘Z / ⇧⌘Z), sixty steps deep.
- Selection is now mutually exclusive, so Delete can no longer remove a stale
  wire or note while a different object looks selected. Deletion is suppressed
  behind the report and both modals.
- Autosave covers every edit rather than only those that repainted everything,
  persists the routing variants, and flushes when the page is hidden. A blank
  board is a valid saved state.
- Loaded files are validated and normalised before being applied: duplicate
  ids, wires pointing at missing pins and out-of-range values are dropped, and
  ids are derived from the file rather than a trusted counter.
- The printed sheet recolours silhouette marks, gives every wire a dark casing
  so pale ones stay visible, prints pin numbers alongside names, and breaks
  cleanly across pages.
- Escape routing understands top and bottom pins; both ends of a wire take
  their own lane; pins follow rounded corners; the top-view electrolytic is
  round; two pins on the same board loop around it rather than through it.
- Editing a field no longer loses focus when the panel repaints.
- Added a LICENSE (MIT).

### v1.9
- Replaced the flowchart shape set with component silhouettes, which is what a
  wiring diagram actually needs: twenty shapes grouped into basic, chips and
  boards, passives, and semiconductors and I/O.
- A shape is now an outline plus a few marks — a notch, a polarity band,
  mounting holes, a cathode stripe — because the outline alone is not enough to
  recognise a part. Marks take the block's readable ink colour, so they work on
  any component colour.

### v1.8
- Extended the shape set to eleven flowchart shapes: added parallelogram,
  hexagon, cylinder, document, trapezoid, triangle and chevron alongside the
  existing rectangle, rounded, circle and diamond.
- Shapes are defined as normalised outlines and pins are placed by intersecting
  that outline, so every shape gets correct pin positions from one routine
  rather than a special case each. Shapes with a narrow apex centre their label
  instead of colliding with it.

### v1.7
- Tidy now shuffles through options instead of applying one fixed result:
  four board layouts and four routing styles, cycling on each press, with the
  current one named on screen.
- Delete / Backspace removes the selected board, wire or note. Wires can now be
  selected, and are highlighted when they are. Keystrokes are ignored while
  typing in a field.
- `+ Component` offers rectangle, rounded, circle and diamond, and the shape of
  an existing board can be changed from the editor. Pin positions follow the
  outline of the shape.

### v1.6
- Boards and notes now follow the pointer while dragging and snap to the grid
  on release. Previously they snapped on every move, so a drag shorter than
  half a grid step produced no movement at all and felt broken.
- A right-angle wire can only slide along its own channel. The cursor now says
  which way, and a drag across the grain no longer records a bend that does
  nothing but still counts as hand-routed.
- Tidy reports what it did, instead of appearing broken when the board was
  already tidy and there was nothing to change.

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
