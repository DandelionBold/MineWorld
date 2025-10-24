# MineWorld Planning Documentation

**Navigation**: [MineWorld](../README.md) > [Planning](README.md)

This directory contains comprehensive planning and architectural documentation for the MineWorld game.

## 📑 Documentation Index

### Strategic Planning

- **[Overall Vision & Roadmap](overall.md)** - Long-term game vision and multi-year roadmap
  - Game design philosophy
  - Feature roadmap (v0.1 → v1.0 → v2.0+)
  - Integration with BlockCore engine
  - Content and community strategy

### Version Plans

- **[v0.1 Plan](v0.1.md)** - Foundation milestone (Current)
  - Discovery Phase & goals
  - Game design & architecture
  - Implementation checklist
  - Acceptance criteria

### Future Versions

- v0.2 Plan *(Coming after v0.1 completion)*
- v0.3 Plan *(Planned)*
- v0.4 Plan *(Planned)*

---

## 🗺️ Quick Navigation

| Version | Status | Focus Area | Key Deliverables |
|---------|--------|------------|------------------|
| v0.1 | 🚧 In Planning | Foundation | Title screen, world creation, flat world, creative mode |
| v0.2 | ⏳ Planned | World & Biomes | Terrain generation, biomes, trees, ores |
| v0.3 | ⏳ Planned | Survival | Health, damage, block hardness, basic tools |
| v0.4 | ⏳ Planned | Content & Packs | Resource packs, shader profiles, commands |
| v0.5 | ⏳ Planned | Plugins | Plugin system, example plugins |
| v0.6 | ⏳ Planned | Multiplayer | Dedicated server, networking |
| v1.0 | ⏳ Future | Stable Release | Crafting, inventory, complete gameplay loop |

---

## 📋 Documentation Standards

All planning documents follow this structure:

1. **Discovery Phase** - Player goals, success criteria, design pillars
2. **Initiation & Planning** - Repo governance, content pipeline, risks
3. **Project Definition** - Feature scope, deliverables, boundaries
4. **Preliminary Design** - Game systems, UI/UX, integration with BlockCore
5. **Implementation Checklist** - Tracked with `[ ]` / `🚧` / `[x]`
6. **Acceptance Criteria** - Playability and quality gates

---

## 🔄 How to Use These Plans

1. **Before Starting Work**: Read the relevant version plan completely
2. **During Development**: Update checklists with 🚧 for in-progress, [x] for completed
3. **After Milestones**: Playtest against acceptance criteria, gather feedback
4. **Planning Next Version**: Reference overall.md for long-term direction

---

## 🎮 Client vs Server

**Important**: MineWorld produces **both** client and server from the same codebase:

- **Client Build**: Full game with rendering, UI, audio
- **Server Build**: Headless dedicated server (no rendering)

Both are built from this repository and share:
- Game logic (blocks, items, worldgen, rules)
- Commands implementation
- Plugin loading
- Save format

---

## 📖 Navigation

**Previous**: [Learning Documentation](../learning/README.md)  
**Next**: [Overall Vision & Roadmap](overall.md)

Last Updated: 2025-10-18

