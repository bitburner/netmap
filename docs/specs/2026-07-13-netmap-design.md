# NetMap — Network Diagram App (Design)

Date: 2026-07-13 · Status: Approved by user

## Goal
A single self-contained `netmap.html` the user opens in a browser to turn an
Advanced IP Scanner XML export into an editable, printable network diagram.

## Data model
- Device node: `{ id, type, name, ip, mac, manufacturer, status, notes, x, y }`
- Connector edge: `{ id, from, to, label }`
- Project: `{ version, title, nodes, edges }` saved as `.netmap.json`

## Import (Advanced IP Scanner XML)
- Parse `<row>` attributes: `status`, `name`, `ip`, `mac`, `manufacturer`, service flags.
- Default filter: keep rows that are alive OR have a name/manufacturer/non-zero MAC
  ("real devices"). Import dialog offers "import all rows" as alternative.
- Auto-guess icon type from manufacturer/name/IP (SonicWall→firewall, TP-Link→router,
  Google→media/IoT, Oculus→IoT, ASUS→PC, `.1`/`.254` gateway→router, has_rdp→PC…).
- Merge by IP on re-import (update metadata, keep position); new nodes laid out in a grid.

## UI
- Top toolbar: title, Import XML, Save/Open JSON, Export PNG, Print/PDF, undo/redo, zoom/fit.
- Left palette: built-in SVG stencils (router, switch, firewall, wifi AP, PC, laptop,
  server, phone, tablet, printer, camera, IoT, NAS, media, cloud, generic) — drag onto
  canvas or click to add.
- Canvas: SVG world with pan (drag background), wheel zoom, dot grid, snap-to-grid drag.
  Nodes are cards: colored icon chip, name, IP, status dot (green alive / red dead).
- Connectors: drag from a port handle on a hovered/selected node to another node.
  Click to select, Delete to remove, label editable in panel.
- Right properties panel: edit name, IP, MAC, manufacturer, type, notes; delete button.
- Keyboard: Delete, Ctrl+Z/Y undo/redo, Ctrl+S save, Esc deselect, arrows nudge.
- Autosave to localStorage; restored on reopen.

## Export
- PNG at 2× via SVG serialization → canvas.
- Print/PDF: print stylesheet renders only the fitted diagram + title; user prints
  to PDF from the browser dialog.

## Non-goals
Live scanning, SNMP/topology discovery, multi-page documents, collaboration.
