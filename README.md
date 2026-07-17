# business-card

My business card, laid out in HTML + CSS. One file — `index.html` — is both the
on-screen preview and the print-ready source. Print it to a PDF and upload straight
to a printer (I used Staples same-day).

The card is a mock editor's markup: a WordArt-style name, a hand-drawn blue-pencil
frame, curly "let's keep in touch!" note, and bracket annotations labelling the
website / email / handle. Everything is vector (SVG + CSS), so it scales to any DPI.

## Quick start

```bash
npm install     # once — pulls in lite-server
npm run dev     # serves at http://localhost:3000 with live reload
```

`npm run dev` opens the card in your browser and reloads on every save to
`index.html` — edit, watch it update, no manual refresh.

No Node? Just open `index.html` in a browser directly. You lose live reload but
everything else works, including printing.

## Two views, one file

On screen the page loads showing the **finished card** (trimmed, no guides).
The button top-left toggles the **bleed + guides** view:

- **red dashed** = trim line (where the card is cut)
- **blue dashed** = safe area (keep text inside)
- the cream extends past the trim on all sides = the 0.125" bleed

Toggling is screen-only — neither view affects the printed output.

## Printing (Staples-ready PDF)

Specs baked into the file:

| | size |
|---|---|
| Trim (final card) | 3.5 × 2 in |
| File (with bleed) | 3.75 × 2.25 in (0.125" bleed all sides) |
| Safe area | 0.125" inside the trim |

To export:

1. Open `index.html`, **Print** (Cmd/Ctrl-P).
2. Destination: **Save as PDF**.
3. Paper size: **3.75 × 2.25 in**.
4. Margins: **None**.
5. **Background graphics: ON** (or the cream and gold drop out).
6. No crop marks — Staples adds its own.

Upload the resulting PDF to the printer. Done.

## Notes

- The name is a self-contained SVG (gradient face + stacked 3D extrusion). An
  earlier CSS `background-clip` version desynced in print RIPs — the Staples proof
  came back doubled — so it's baked into SVG geometry now.
- Fonts (Anton, Caveat, IBM Plex Mono) load from Google Fonts, so the browser
  needs a network connection when you print.
