# attack-path-mapping-

An interactive, single-file tool for mapping the attack paths of a system or device and turning lab work into a documented assessment. Built for teaching: students link entry vectors, findings, capabilities and consequences into a visual chain, then rate, test and report on it. Inspired by MITRE ATT&CK and the Cyber Kill Chain.

## Usage

Open **`attack-path-mapper.html`** in any modern browser. No install, no server, no network — everything runs locally in one file, so it works offline in an isolated lab. Nothing you enter leaves the browser.

Open **✨ Examples** to load a finished model (a simulated infusion pump, or a clinic IT network), and **❔ Guide** for the assessment workflow and shortcuts.

## The model

An attack is a directed graph of four node shapes joined by **paths** that begin at an entry vector:

| Shape | Node type | Meaning |
|-------|-----------|---------|
| Hexagon (navy) | **Entry Vector** | how the attacker first reaches the system |
| Rectangle (gray) | **Finding** | a specific weakness you found |
| Diamond (green) | **Artifact / Capability** | what that gives the attacker |
| Octagon (navy/green) | **Consequence** | the resulting impact |

A node is reached when **any** incoming path works (OR). Set a node to **AND** when the attacker needs several things at once — e.g. a modified firmware image *and* a device that skips signature checks.

## Build & explore

- **Add nodes** (buttons or keys `1`–`4`), **drag** to arrange, **Auto-arrange** to lay the graph out left to right.
- **Draw paths** by dragging the green **+** on a selected node (drop on empty space to create the next node already connected), by `Shift`+drag, or with Connect mode (`C`).
- **Click a path** to label it ("port 23", "dump flash"), reverse it or delete it.
- **Undo / redo** everything (`Ctrl+Z` / `Ctrl+Y`), duplicate nodes (`Ctrl+D`), **search** across labels, techniques, CWEs and notes.
- **Focus a node's chain** to isolate everything upstream and downstream of it.

## Assess

Each node has a details panel:

- **Findings** — status (suspected → confirmed → exploited, or ruled out), severity, ease of exploitation (1–5), CWE, a **CVSS v3.1 calculator** that produces the vector, score and severity, plus **evidence** and **remediation** fields.
- **Consequences** — impact (1–5) and category (patient safety, confidentiality, integrity, availability).
- **Any node** — MITRE ATT&CK technique (searchable built-in subset, tactic filled in automatically), notes, and a **Mitigated** switch with a description of the control.
- **Assessment record** (nothing selected) — target, assessor, date, scope and rules of engagement, conclusions.

Status, severity, impact, AND gates and mitigations are all drawn on the nodes, so the map reads at a glance.

## Analyse

- **Paths tab** — every complete entry → consequence chain, **ranked by risk**. Path risk = ease of exploitation of the hardest finding on the path × impact of the consequence (1–25).
- **Walkthrough** — click a path to step through it node by node (`←` / `→`), with the technique, evidence and notes shown for each step.
- **Analysis tab** — reachable consequences, path counts, a 5×5 risk matrix, **choke points** (nodes whose removal makes a consequence unreachable), a ranking of the **best mitigations to try**, and ATT&CK tactic coverage.
- **What-if mitigation** — mark a node mitigated and see immediately how many paths and consequences it removes.
- **Review tab** — a checklist of gaps before you report: findings without evidence, missing ratings, unverified findings, dead ends, orphan nodes, an incomplete assessment record.

## Save, export, report

- **Save / load** a `.json` file, plus continuous **autosave** in the browser. Files from the earlier version still load.
- **Export** the diagram as PNG or SVG; a **findings register**, attack paths and node inventory as CSV; a Markdown report; raw JSON.
- **Publish Report** builds a self-contained, print-ready HTML report: scope, key figures, the attack map, risk-ranked paths, risk matrix, a findings register with evidence and remediation, mitigation priorities and observations. Print it to PDF or download it.

## Notes

- The built-in ATT&CK technique and CWE lists are a reference subset for quick mapping; any ID or free text can be typed. Check attack.mitre.org and cwe.mitre.org for the full catalogues.
- The risk score is a simple teaching model, not a substitute for a formal risk-management process.
- Use it only for systems you are authorised to test.
