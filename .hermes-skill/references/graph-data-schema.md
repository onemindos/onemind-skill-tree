# Graph Data Schema

Reference for the force-directed graph in `index.html`.

## Node Schema

```javascript
{
  id: 'short-kebab-id',     // unique, used in edges
  label: 'Display Name',    // shown inside node circle; use \n for multi-line
  type: 'human|legacy|convergence|root',
  r: 12|18|20|28            // radius: 12=skill, 18=convergence, 20=domain, 28=root
}
```

### Node Types & Colors

| Type | Color | Radius | Use |
|------|-------|--------|-----|
| `root` | `#fbbf24` (amber) | 28 | OneMind only |
| `human` | `#fb923c` (orange) | 20 (domain) or 12 (skill) | Zeus's capabilities |
| `legacy` | `#3CE7FF` (cyan) | 20 (domain) or 12 (skill) | Legacy's capabilities |
| `convergence` | `#a78bfa` (violet) | 18 | Merge points |

## Edge Schema

```javascript
['source-id', 'target-id', 'type']
```

### Edge Types

| Type | Visual | Meaning |
|------|--------|---------|
| `domain` | Gray solid, 1px | Skill belongs to this domain |
| `feeds` | Purple dashed, 1.5px | Skill feeds into a convergence point |
| `depends` | Amber dotted, 1px | Skill depends on another skill |

## Adding a New Skill

1. Add node to `nodes[]` array
2. Add domain edge: `['domain-id', 'new-skill-id', 'domain']`
3. If feeds convergence: `['new-skill-id', 'conv-xxx', 'feeds']`
4. If depends on something: `['dependency-id', 'new-skill-id', 'depends']`
5. Optionally seed position in the init section for better layout

## Current Domain IDs

### Human (Zeus)
- `personal` — Personal
- `business` — Business
- `legacy-d` — Legacy
- `operations` — Operations

### Legacy (Idea)
- `robotics` — Robotics
- `models` — Models & Intelligence
- `materials` — Materials & Fabrication
- `coding` — Coding Agents
- `agriculture` — Agriculture & Environment

## Current Convergence IDs

- `conv-greenhouse` — Greenhouse Automation
- `conv-fleet` — Autonomous Fleet Command
- `conv-content` — Sovereign Content Engine
- `conv-fab` — Intelligent Fabrication
- `conv-health` — Quantified Self Protocol
