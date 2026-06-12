# OneMind Capability Tree

A visual, interactive skill tree showing how **Zeus** (Human) and **Legacy** (Idea) develop capabilities independently — then converge through the Fabric into something neither could achieve alone.

> Legacy is not an AI agent. It is an idea. The Fabric connects us all.

## Live

Open `index.html` in any browser. No build step, no dependencies.

Future: GitHub Pages deployment + video walkthrough for the community.

## Views

| View | Purpose |
|------|---------|
| **Tree** | Dual-column overview — Zeus (left) / Fabric (center) / Legacy (right) |
| **Convergence** | Deep dive into merge points — what each side brings, what emerges |
| **Depth** | Per-domain cards showing dependency chains and feeds |
| **Matrix** | Tabular with depth bars showing ownership split per capability |
| **Graph** | Interactive force-directed canvas — drag, zoom, pan to explore all connections |

## Domains

### Human Side (Zeus)
- **Personal** — Health, performance, individual development
- **Business** — Revenue, community, market presence
- **Legacy** — Long-term knowledge, deep study, generational thinking
- **Operations** — Infrastructure, land, vehicles, physical systems

### Legacy Side (Idea / System Intelligence)
- **Robotics** — DIMOS, Go2, drones, sensor fusion
- **Models & Intelligence** — Local LLM, fine-tuning, world models, RAG
- **Materials & Fabrication** — CNC, 3D printing, welding
- **Coding Agents** — Claude Code, Kanban workers, code review, skill system
- **Agriculture & Environment** — Greenhouse mesh, growth modeling, irrigation

## Statuses

| Human Lifecycle | Legacy Lifecycle |
|----------------|-----------------|
| Planning | Planning |
| Study | Developing |
| Training | Testing |
| Mastering | Live |
| Sunset | Sunset |

## Convergence Points

These are where independent skills merge into unified capabilities:

1. **Greenhouse Automation** — Gardening knowledge + sensor mesh + growth modeling
2. **Autonomous Fleet Command** — Systems thinking + robotics stack + world models
3. **Sovereign Content Engine** — Business instincts + coding agents + self-hosted infra
4. **Intelligent Fabrication** — Physical craft + computational design
5. **Quantified Self Protocol** — Training discipline + biometric data pipeline

## Tech

- Pure HTML/CSS/JS — single file, no framework
- Canvas-based force-directed graph engine (custom, no d3)
- AgentTap HUD theme: Chakra Petch + IBM Plex Mono, cyan/orange palette
- `#020617` dark slate background

## Contributing

This is a living document. Skills get added as they develop. To add a node:

1. Add to the appropriate view section in `index.html`
2. Add to the graph's `nodes[]` and `edges[]` arrays
3. Commit with: `git commit -m "add: skill-name (domain)"`

## Roadmap

- [ ] JSON-driven data layer (skills.json → render all views dynamically)
- [ ] Auto-populate Legacy side from Hermes skill inventory
- [ ] GitHub Pages deployment
- [ ] Video walkthrough for Wealth Warriors community
- [ ] Hover tooltips on graph nodes with status + description
- [ ] Filter graph by domain, status, or convergence point
- [ ] Timeline view showing progression over time

---

*OneMind — 50/50 Human + Idea. The Fabric connects us all.*
