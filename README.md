# NetMap

A single-file network diagram editor. Open **`netmap.html`** in any modern browser
(just double-click it) — no install, no server, works offline.

## What it does

- **Import Scan** — load an Advanced IP Scanner export in **XML or CSV** format (the
  file type is detected automatically; CSV handles both comma- and semicolon-delimited
  exports, and the Comments column is kept as device notes). Each endpoint becomes a
  device card with its name, IP, MAC, manufacturer, and online status. Empty "unknown"
  rows are skipped by default (a dialog lets you import everything instead). Device
  icons are guessed from the manufacturer (SonicWall → firewall, ASUS → PC,
  Oculus → IoT, …) and can be changed at any time.
- **Draw the map** — drag devices anywhere (snaps to grid). Hover a device and drag one
  of the blue **ports** to another device to draw a connector. Click a connector to
  label it (VLAN, port, link speed) or delete it.
- **Add / edit / delete** — drag any of the 16 stencils from the left palette onto the
  canvas (or double-click empty canvas). Click a device to edit its name, IP, MAC,
  manufacturer, type, status, and notes in the right panel. `Delete` removes the
  selected item.
- **Save / Open** — projects are saved as `.netmap.json` files. Work is also autosaved
  to the browser so it survives closing the tab.
- **Export** — PNG image, or **Print / PDF** (uses the browser print dialog →
  "Save as PDF"; landscape layout with title and device count).
- **Light / dark theme** — toggle with the sun/moon button in the toolbar. Follows
  your system preference on first launch and remembers your choice. Printed and
  exported diagrams always use the light palette so they stay document-friendly.

## Shortcuts

| Key | Action |
|---|---|
| `Ctrl+Z` / `Ctrl+Y` | Undo / redo |
| `Ctrl+S` | Save project |
| `Delete` | Delete selected device/connection |
| Arrow keys | Nudge selected device (`Shift` = fine) |
| Mouse wheel | Zoom · drag background = pan · double-click = add device |

## Files

- `netmap.html` — the whole app
- `docs/specs/` — design notes
