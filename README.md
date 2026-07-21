# attack-path-mapping-

An interactive, single-file tool to manually map the attack paths of a system or device — for use in labs and assessments. Inspired by the MITRE ATT&CK framework and the Cyber Kill Chain.

## Usage

Open **`attack-path-mapper.html`** in any modern browser. No install, no server, no network — everything runs locally and self-contained, so it works offline in an isolated lab.

Click **✨ Sample** to load an example model and see how it fits together.

## What it does

Model an attack as a directed graph of four distinct node shapes, all connected by directed **paths** that begin at an entry vector:

| Shape | Node type | Meaning |
|-------|-----------|---------|
| Hexagon (navy) | **Entry Vector** | how the attacker first reaches the system |
| Rectangle (gray) | **Finding** | a specific weakness / misconfiguration |
| Diamond (green) | **Artifact / Capability** | something the attacker gains or can now do |
| Octagon (navy/green) | **Consequence** | the impact / objective |

### Build & explore
- **Add, rename, and delete** any node; **draw or delete paths** between them (Connect tool).
- **Drag** to arrange, scroll to zoom, drag empty space to pan, **⤢** to fit.
- **Find root paths** — enumerates every complete Entry Vector → Consequence chain and lists them; click one to highlight it on the canvas.
- **Zoom into a chain** — focus a single node to isolate its full upstream + downstream attack path.
- **Disable / enable a node** — model a mitigation and instantly see which paths break.
- **Highlight choke points** — flags nodes that appear on *every* path to a consequence (single points of failure / top mitigation priorities).

### Analysis panel
Live metrics that update as you edit:
- Consequences reachable from an entry vector, and total complete attack paths available.
- Node breakdown (entry vectors / findings / capabilities / consequences) and edge count.
- Longest and average chain length.
- Choke points, nodes disabled (mitigated), unreachable consequences, dead-end entry vectors, and orphan nodes.

### Save
- **Save / Load to a file** (`.json`).
- **Save / Restore in the browser** — plus continuous **autosave** to `localStorage`, so your model survives a page reload.

### Export
- **PNG** raster image and **SVG** vector of the diagram.
- **Attack paths (CSV)** and **Node inventory (CSV)** for spreadsheets.
- **Markdown report** (`.md`) and **raw data (JSON)**.

### Publish Report
One click generates a self-contained, print-ready **HTML report** (open in a new tab; print to PDF or download). It summarizes everything: the model name, a stat dashboard, an embedded snapshot of the attack map, every enumerated attack path, the full node inventory with MITRE notes, choke points as mitigation priorities, and observations (unreachable consequences, dead-end entries, orphans, and active mitigations).

Give the model a name in the top bar — it titles the report and every exported file.

Color palette: navy, white, green, and gray.
