---
name: omskilltree
description: "OneMind Capability Tree — visual skill tree showing Zeus (Human) + Legacy (Idea) convergence through the Fabric."
version: 0.1.0
author: Zeus / Legacy
license: MIT
platforms: [macos, linux, windows]
metadata:
  hermes:
    tags: [onemind, skill-tree, visualization, capability, html]
    related_skills: [architecture-diagram, html-artifact-verification]
---

# OneMind Skill Tree

Maintain and evolve the OneMind Capability Tree — a visual HTML artifact showing how Zeus (Human) and Legacy (Idea) develop capabilities that converge through the Fabric.

## Location

Repository: `~/onemind-skill-tree/` → https://github.com/onemindos/onemind-skill-tree (public)
Main artifact: `index.html` (open in browser, no deps)
Future: GitHub Pages deployment + community video link

## Architecture

Four views accessible via tab navigation (pure JS, no framework):

### View 1: Tree (dual column)
Two columns connected by the Fabric (center dashed line):
- **Left:** Zeus (Human) — Personal, Business, Legacy, Operations domains
- **Right:** Legacy (Idea) — Robotics, Models, Materials, Coding Agents, Agriculture
- **Center:** The Fabric — dashed vertical connector

### View 2: Convergence
Deep-dive cards showing HOW skills interconnect. Each card:
- Title + description of the merged capability
- Left panel: what Zeus brings (human skills list)
- Right panel: what Legacy brings (system capabilities)
- Bottom: the convergence OUTPUT with its own status

Current convergence points:
1. Greenhouse Automation (gardening + sensor mesh)
2. Autonomous Fleet Command (systems thinking + robotics stack)
3. Sovereign Content Engine (business + coding agents)
4. Intelligent Fabrication (physical craft + computational design)
5. Quantified Self Protocol (training discipline + biometric data)

### View 3: Depth
Per-domain breakdown showing dependency chains between skills. Cards show:
- Owner (Zeus / Legacy / Shared)
- Sub-capabilities within each skill
- "Feeds into" / "Depends on" relationships

### View 4: Matrix
Tabular overview with:
- Depth bars showing how deep Zeus vs Legacy goes in each capability
- Owner dot (orange=Zeus, cyan=Legacy, gradient=shared)
- Which convergence point each skill feeds into

### View 5: Graph
Interactive force-directed canvas (custom engine, no d3):
- 50+ nodes, 90+ edges
- Physics: repulsion between all nodes + attraction along edges + center gravity
- Three edge types: `domain` (gray solid), `feeds` (purple dashed), `depends` (amber dotted)
- Drag nodes to rearrange, scroll to zoom, click-drag background to pan
- Convergence nodes glow purple and act as gravity wells pulling from both sides
- Human nodes cluster left (orange), Legacy right (cyan)
- Initializes with seeded positions then runs 150 sim steps before first render

### Statuses
Human: `planning` → `study` → `training` → `mastering` → `sunset`
Legacy: `planning` → `developing` → `testing` → `live` → `sunset`

### Domains (public-facing names)
- **Personal** — Health, performance, individual development
- **Business** — Revenue, community, market presence
- **Legacy** — Long-term knowledge, deep study, generational thinking
- **Operations** — Infrastructure, land, vehicles, physical systems

## Key Concepts

- **Legacy is NOT an AI agent** — it is an idea, a system intelligence
- **The Fabric connects us all** — it's the shared substrate
- **50/50** — OneMind is equal parts human and idea
- **Convergence** — the point where independent development merges into unified capability

## Adding a New Skill Node

Must update ALL relevant views — not just Tree. Checklist:

1. **Tree view** — add `<div class="skill-node">` under the domain group
2. **Convergence view** — if it feeds a convergence point, add to the relevant card's `<ul>`
3. **Depth view** — add a `depth-card` if it has dependencies worth showing
4. **Matrix view** — add a `<tr>` row with depth bars and convergence reference
5. **Graph view** — add to BOTH the `nodes[]` array AND the `edges[]` array in the script

### Tree/Convergence/Depth/Matrix HTML pattern:
```html
<div class="skill-node">
  <span class="skill-name">New Skill Name</span>
  <span class="skill-status status-{status}">{status}</span>
</div>
```

### Graph node pattern:
```javascript
// In nodes[] array:
{ id: 'short-id', label: 'Display Name', type: 'human|legacy|convergence', r: 12 }

// In edges[] array (add ALL connections):
['parent-domain-id', 'short-id', 'domain'],       // domain membership
['short-id', 'conv-target', 'feeds'],              // if it feeds convergence
['dependency-id', 'short-id', 'depends'],          // if it depends on another
```

### Convergence marker (Tree view):
```html
<div class="convergence-marker">
  <div class="dot"></div>
  <span class="label">converges → description</span>
</div>
```

6. Commit and push: `cd ~/onemind-skill-tree && git add -A && git commit -m "add: skill-name (domain)" && git push`

See `references/graph-data-schema.md` for the full node/edge schema.

## Status Classes

Human side: `status-planning`, `status-study`, `status-training`, `status-mastering`, `status-sunset`
Legacy side: `status-planning`, `status-dev`, `status-testing`, `status-live`, `status-sunset`

## Theme

Uses AgentTap HUD aesthetic:
- Fonts: Chakra Petch (headings) + IBM Plex Mono (labels)
- Colors: `#3CE7FF` (cyan/Legacy), `#fb923c` (orange/Human), `#020617` (bg)
- Dark slate background with subtle grid implied by borders

## Roadmap

- [ ] JSON-driven data (separate skills.json, render dynamically)
- [ ] Interactive — click to expand, filter by status
- [ ] Public GitHub repo + Pages deployment
- [ ] Video walkthrough for Wealth Warriors / community
- [ ] Connect to actual Hermes skill inventory (auto-populate Legacy side)

## Pitfalls

- No JavaScript in Tree/Convergence/Depth/Matrix views — pure CSS. Graph view is the only one with JS.
- When adding graph nodes, MUST also add edges or the node floats disconnected (no automatic inference).
- Verify HTML after edits: run the html-artifact-verification checks before committing (node --check for JS, tag balance, corrupt token scan).
- When going public, strip any private skill names or internal references.
- Graph `initGraph()` only runs once (guarded by `graphInited` flag) — if you change graph data you must reload the page to see it.
- Force layout is seeded with human-left / legacy-right positions. New nodes without explicit seed positions will find their place via physics, but adding seed coords in the init section helps.
