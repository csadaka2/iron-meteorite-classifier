# Iron Meteorite Classifier

A browser-based tool to classify iron meteorites by comparing elemental compositions against a reference database of 649 meteorites across 13 groups.

**Live app → https://csadaka2.github.io/iron-meteorite-classifier/**

Based on code by Clara Maurel.

---

## What it does

Upload your sample's XRF data as an `.xlsx` file and the app overlays it on 11 log–log scatter plots, each showing a different pair of trace elements. Your sample appears as a gold square with error bars; the reference groups are shown as coloured circles.

Plots are interactive — hover over any point to see the meteorite name and exact values. Use the Plotly toolbar (top-right of each plot) to zoom, pan, or download the figure as an SVG.

### Reference groups

IC, IIAB, IIC, IID, IIE, IIF, IIG, IIIAB, IIIE, IIIF, IVA, IVB, IAB-MG

### Plots generated

| X axis | Y axis |
|--------|--------|
| Ni (wt%) | Ge (ppm) |
| Ni (wt%) | Ir (ppm) |
| As (ppm) | Ge (ppm) |
| As (ppm) | Ga (ppm) |
| As (ppm) | Co (wt%) |
| As (ppm) | Ni (wt%) |
| As (ppm) | Ir (ppm) |
| Au (ppm) | Ge (ppm) |
| Au (ppm) | Ga (ppm) |
| Au (ppm) | Ni (wt%) |
| Au (ppm) | Co (wt%) |

---

## Sample file format

Your `.xlsx` file must contain a sheet named **`Feuil1`** (French template) or **`Sheet1`** (English template) with the following layout:

| Row | Content |
|-----|---------|
| 1 | Column headers (see below) |
| 2 | Measured values |
| 3 *(optional)* | 1σ uncertainties |

### Accepted column headers

| Header | Element | Unit |
|--------|---------|------|
| `Ni (wt%)` | Ni | wt% |
| `Co (wt%)` | Co | wt% |
| `Ga (ppm)` | Ga | ppm |
| `Ge (ppm)` | Ge | ppm |
| `As (ppm)` | As | ppm |
| `Ir (ppm)` | Ir | ppm |
| `Au (ppm)` | Au | ppm |
| `Cr (ppm)` | Cr | ppm *(read but not plotted)* |
| `Cu (ppm)` | Cu | ppm *(read but not plotted)* |
| `Mo (ppm)` | Mo | ppm *(read but not plotted)* |
| `Pd (ppm)` | Pd | ppm *(read but not plotted)* |
| `Sb (ppm)` | Sb | ppm *(read but not plotted)* |
| `W (ppm)`  | W  | ppm *(read but not plotted)* |

Columns not listed above are ignored. Missing or blank cells are treated as absent (no point plotted for that element pair).

---

## How error bars are displayed

- **X axis** — 1σ (the value in row 3)
- **Y axis** — 2σ (2 × the value in row 3)

Error bars are only shown when the uncertainty is present and non-zero.

---

## Technical notes

- Runs entirely in the browser — no server, no installation
- Reference database embedded in the HTML at build time
- Uses [Plotly.js](https://plotly.com/javascript/) for interactive charts and [SheetJS](https://sheetjs.com/) for Excel parsing
