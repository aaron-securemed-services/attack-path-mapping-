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

### Features
- **Add, rename, and delete** any node; **draw or delete paths** between them (Connect tool).
- **Drag** to arrange, scroll to zoom, drag empty space to pan, **⤢** to fit.
- **Find root paths** — enumerates every complete Entry Vector → Consequence chain and lists them; click one to highlight it on the canvas.
- **Zoom into a chain** — focus a single node to isolate its full upstream + downstream attack path.
- **Disable / enable a node** — model a mitigation and instantly see which paths break.
- **Live analysis panel**: consequences reachable from an entry vector, total complete attack paths available, and nodes disabled.
- **Save / Load** the model as JSON and **Export** the diagram as SVG.

Color palette: navy, white, green, and gray.
