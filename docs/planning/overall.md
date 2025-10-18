# MineWorld - Overall Vision & Roadmap

**Document Version**: 1.0  
**Last Updated**: 2025-10-18  
**Status**: Living Document

---

## Executive Summary

**MineWorld** is a voxel sandbox game built on the BlockCore engine, offering players infinite procedurally generated worlds to explore, build, and survive in. It serves both as a standalone game and as a reference implementation showcasing BlockCore's capabilities. MineWorld emphasizes moddability, deterministic world generation, and a seamless blend of creative and survival gameplay.

---

## 1. Vision & Philosophy

### 1.1 Player Fantasy

**"Create and explore YOUR world—infinite possibilities from a single seed."**

Players should feel:
- **Freedom**: Build anything, anywhere, in any mode
- **Discovery**: Every world is unique but reproducible
- **Mastery**: From novice builder to expert modder
- **Community**: Share worlds, join servers, create content

### 1.2 Design Pillars

1. **Sandbox First** - No forced progression; players make their own goals
2. **Deterministic Worlds** - Same seed = same world (always)
3. **Mod-Friendly** - Every system exposable to plugins/packs
4. **Performance Matters** - Smooth 60 FPS on mid-tier hardware
5. **Content-Driven** - Data files over hardcoded logic

### 1.3 Target Audience

| Audience | Priorities | Features They Value |
|----------|-----------|-------------------|
| **Casual Builders** | Creativity, simplicity | Creative mode, easy controls, resource packs |
| **Survival Players** | Challenge, progression | Survival mode, crafting, difficulty settings |
| **Modders/Creators** | Extensibility, tools | Plugin API, SDK tools, documentation |
| **Server Admins** | Stability, control | Dedicated server, commands, whitelists |
| **Explorers** | Variety, discovery | Procedural worlds, biomes, structures |

---

## 2. Strategic Goals (2025-2030)

### 2.1 Year 1 Goals (2025)

- ✅ **v0.1-v0.3**: Foundation - Playable creative mode, basic terrain
- ✅ **v0.4-v0.6**: Systems - Resource packs, plugins, multiplayer
- 🎯 **v1.0**: First stable release with core gameplay loop

**Success Metrics**:
- 1,000+ downloads
- 10+ community-created packs/plugins
- Stable multiplayer with 10+ concurrent players

### 2.2 Year 2-3 Goals (2026-2027)

- 🎯 **v1.x**: Content expansion (mobs, advanced crafting, structures)
- 🎯 **v2.0**: Performance & polish (shaders, optimization, UI overhaul)
- 🎯 Community growth (10,000+ players, active mod scene)

**Success Metrics**:
- 50+ quality mods/packs
- Active server community (100+ public servers)
- Featured in indie game showcases

### 2.3 Year 4-5 Goals (2028-2030)

- 🎯 **v3.0**: Advanced features (quests, NPCs, automation)
- 🎯 **v4.0**: Platform expansion (console ports consideration)
- 🎯 Industry recognition (awards, partnerships)

---

## 3. Game Design Evolution

### 3.1 Core Loop (v1.0 Target)

```
Explore World → Gather Resources → Craft Tools/Blocks
      ↓                                      ↓
 Discover Biomes ←─────────────────────── Build Structures
      ↓                                      ↓
  Set Challenges ←──────────────────────── Customize Packs
      ↓                                      ↓
  Join Servers ←────────────────────────── Share Creations
```

### 3.2 Game Modes

#### Creative Mode (v0.1+)
- **Concept**: Unlimited resources, instant building, invincibility
- **Features**:
  - Infinite inventory (all blocks/items)
  - Flight enabled
  - Instant block break
  - No health/hunger
- **Use Case**: Building, planning, showcasing

#### Survival Mode (v0.3+)
- **Concept**: Gather, craft, survive
- **Features**:
  - Health and hunger systems
  - Block hardness (tools required)
  - Item durability
  - Damage sources (fall, suffocation, later: mobs)
- **Use Case**: Challenge-oriented gameplay

#### Adventure Mode (v2.0+) *(Future)*
- **Concept**: Custom maps, quests, restrictions
- **Features**:
  - Can't break/place blocks (unless allowed)
  - Custom objectives
  - Locked inventories
- **Use Case**: Mini-games, adventure maps

---

## 4. Feature Roadmap

### v0.1 - Foundation (3-4 months)

**Focus**: Prove the game loop; get players in-world

#### Features
- [ ] Title screen with main menu
- [ ] World creation screen (name, seed input)
- [ ] Single-player creative mode
- [ ] Flat world generation (superflat for testing)
- [ ] Place/break blocks (no collision yet)
- [ ] Basic HUD (crosshair, selected block)
- [ ] Save/load world
- [ ] Exit to menu

**Milestone**: "Hello World" - Player can create, modify, and save a simple world

---

### v0.2 - World & Biomes (2-3 months)

**Focus**: Infinite terrain; exploration

#### Features
- [ ] Heightmap-based terrain generation
- [ ] 3-5 biomes (Plains, Forest, Desert, Mountains, Ocean)
- [ ] Chunk loading/unloading by player distance
- [ ] Tree generation (simple oak trees)
- [ ] Ore generation (stone, coal, iron)
- [ ] Skylight propagation (basic lighting)
- [ ] Render distance setting
- [ ] World backup/restore UI

**Milestone**: "Exploration" - Player can explore diverse, infinite worlds

---

### v0.3 - Survival (2-3 months)

**Focus**: Challenge and progression

#### Features
- [ ] Survival game mode toggle
- [ ] Health system (10 hearts)
- [ ] Fall damage
- [ ] Block hardness (tools affect break speed)
- [ ] Simple tool crafting (wooden pickaxe, stone tools)
- [ ] Inventory system (hotbar + 27 slots)
- [ ] Hunger system (basic, optional)
- [ ] Death & respawn

**Milestone**: "Survival" - Player can survive, gather, and progress

---

### v0.4 - Content & Packs (3-4 months)

**Focus**: Customization and polish

#### Features
- [ ] Resource pack support (textures, models, sounds)
- [ ] Resource pack selector UI
- [ ] Hot-reload packs (no restart required)
- [ ] Shader profile system (Classic, Cinematic, Toon)
- [ ] Localization support (English + community translations)
- [ ] In-game commands (accessible via chat)
- [ ] Command permissions (player, op)
- [ ] Settings menu (video, controls, audio, gameplay)

**Milestone**: "Customization" - Player can personalize their experience

---

### v0.5 - Plugins (3-4 months)

**Focus**: Mod support and extensibility

#### Features
- [ ] Plugin loading system (Lua scripts)
- [ ] Plugin manifest format
- [ ] Sample plugins (Home/Teleport, Keep Inventory, Minimap)
- [ ] Plugin API docs
- [ ] Plugin folder UI (enable/disable)
- [ ] Event hooks for modders
- [ ] Storage API for plugins (key-value)

**Milestone**: "Extensibility" - Modders can create gameplay extensions

---

### v0.6 - Multiplayer (4-6 months)

**Focus**: Online play

#### Features
- [ ] Dedicated server build (headless)
- [ ] Multiplayer menu (server browser)
- [ ] LAN discovery
- [ ] Join via IP
- [ ] Server configuration (server.toml)
- [ ] Player list & kick/ban commands
- [ ] Chat system (global, team planned later)
- [ ] Whitelist & operator system
- [ ] Content hash validation (client must match server packs)

**Milestone**: "Together" - Players can host and join servers

---

### v1.0 - Stable Release (Polishing phase)

**Focus**: Complete gameplay loop; production-ready

#### Features
- [ ] Crafting system (shaped/shapeless recipes)
- [ ] Recipe book UI
- [ ] Loot tables (block drops, chest loot)
- [ ] Simple structure generation (villages, ruins)
- [ ] Achievement system (optional)
- [ ] Complete sound design
- [ ] Tutorial/help system
- [ ] Performance optimization (60 FPS target met)
- [ ] Comprehensive documentation
- [ ] API freeze (v1.x backward compatible)

**Success Criteria**:
- ✅ 10+ hours of engaging gameplay
- ✅ Stable for 6+ months without critical bugs
- ✅ Active community (1,000+ players)
- ✅ 20+ quality community mods/packs

---

### v2.0+ - Advanced Features (Future)

#### Planned Features
- [ ] Mobs (passive & hostile)
- [ ] Redstone-like automation system
- [ ] Advanced structures (temples, dungeons)
- [ ] Enchanting & potions
- [ ] The Nether (alternate dimension)
- [ ] Advanced shader packs (PBR, raytracing)
- [ ] Spectator mode
- [ ] Replays/demos
- [ ] Mod API v2 (more hooks)

---

## 5. Technical Architecture

### 5.1 Game Layer on BlockCore

```
┌─────────────────────────────────────────────────────┐
│              MineWorld (Game Layer)                 │
│  ┌──────────────────────────────────────────────┐  │
│  │  Client                 Server                │  │
│  │  - UI/Menus             - Headless            │  │
│  │  - Rendering            - Authoritative logic │  │
│  │  - Input handling       - World management    │  │
│  │  - Audio                - Player state        │  │
│  └──────────────┬───────────────┬────────────────┘  │
│  ┌──────────────┴───────────────┴────────────────┐  │
│  │         Shared Game Logic                     │  │
│  │  - Blocks/Items (content catalogs)            │  │
│  │  - Game rules (creative/survival)             │  │
│  │  - Worldgen configs (biomes, ores)            │  │
│  │  - Commands (tp, gamemode, give, etc.)        │  │
│  │  - Crafting/recipes                           │  │
│  └───────────────────────────────────────────────┘  │
└──────────────────────┬──────────────────────────────┘
                       │ Uses BlockCore APIs
┌──────────────────────┴──────────────────────────────┐
│            BlockCore Engine (v0.x → v1.0)           │
│  - Rendering, Physics, Voxels, WorldGen            │
│  - Networking, Plugins, Resources, Commands        │
└─────────────────────────────────────────────────────┘
```

### 5.2 Repository Structure

```
MineWorld/
  ├─ src/
  │   ├─ MineWorld.Core/           # Shared game logic (client & server)
  │   │   ├─ Content/              # Blocks, items, recipes
  │   │   ├─ WorldGen/             # Biome configs, feature placement
  │   │   ├─ GameModes/            # Creative, survival rule sets
  │   │   ├─ Commands/             # Game-specific commands
  │   │   └─ Systems/              # Damage, hunger, crafting logic
  │   ├─ MineWorld.Client/         # Client-only (UI, rendering config)
  │   │   ├─ UI/                   # Menus, HUD, inventory screens
  │   │   ├─ Audio/                # Sound management
  │   │   └─ Program.cs            # Client entry point
  │   └─ MineWorld.Server/         # Server-only (headless entry)
  │       ├─ Program.cs            # Server entry point
  │       └─ ServerConfig.cs       # Server-specific settings
  ├─ content/
  │   ├─ packs/
  │   │   └─ Default/              # Default resource pack
  │   │       ├─ manifest.json
  │   │       ├─ textures/
  │   │       ├─ models/
  │   │       ├─ sounds/
  │   │       └─ lang/
  │   └─ data/
  │       ├─ blocks.json           # Block definitions
  │       ├─ items.json            # Item definitions
  │       └─ recipes.json          # Crafting recipes
  ├─ plugins/                      # User-installed plugins
  ├─ worlds/                       # Saved worlds (gitignored)
  ├─ docs/
  │   └─ planning/
  └─ tests/
```

### 5.3 Build Outputs

| Target | Command | Output | Purpose |
|--------|---------|--------|---------|
| **Client** | `dotnet build src/MineWorld.Client` | `MineWorld.exe` | Player's game |
| **Server** | `dotnet build src/MineWorld.Server` | `MineWorld-Server.exe` | Dedicated server |

---

## 6. Content Pipeline

### 6.1 Block Definition (Data-Driven)

**Example**: `content/data/blocks.json`
```json
{
  "mineworld:grass_block": {
    "displayName": "Grass Block",
    "model": "cube_all",
    "textures": {
      "top": "mineworld:blocks/grass_top",
      "bottom": "mineworld:blocks/dirt",
      "sides": "mineworld:blocks/grass_side"
    },
    "hardness": 0.6,
    "toolRequired": false,
    "drops": {
      "default": "mineworld:dirt"
    },
    "tags": ["ground", "natural"]
  }
}
```

### 6.2 WorldGen Pipeline (v0.2+)

```
Seed → Noise Generation → Heightmap → Biome Assignment
  ↓
Terrain Fill (stone, dirt, grass layers)
  ↓
Feature Placement (trees, ores, lakes)
  ↓
Structure Placement (villages, ruins - later)
  ↓
Final Chunk Data → BlockCore for rendering
```

### 6.3 Recipe System (v1.0)

**Example**: Crafting Table recipe
```json
{
  "mineworld:crafting_table": {
    "type": "shaped",
    "pattern": [
      "PP",
      "PP"
    ],
    "key": {
      "P": "mineworld:planks"
    },
    "result": {
      "item": "mineworld:crafting_table",
      "count": 1
    }
  }
}
```

---

## 7. Integration with Ecosystem

### 7.1 Dependency on BlockCore

```
MineWorld (NuGet) → BlockCore v0.x
```

**Version Compatibility Matrix**:
| MineWorld | Requires BlockCore | Notes |
|-----------|-------------------|-------|
| v0.1 | ^0.1 | Foundation |
| v0.2 | ^0.2 | World generation |
| v0.3 | ^0.3 | Physics required |
| v0.6 | ^0.6 | Networking required |
| v1.0 | ^1.0 | Stable API freeze |

### 7.2 SDK Tools

**MineWorld-SDK** provides:
- `mwtool` CLI for creating mods, packs, plugins
- Schemas for MineWorld-specific content (blocks, items, recipes)
- Templates for common mods (teleport, home, custom blocks)
- Validation against MineWorld + BlockCore versions

**Workflow**:
```bash
# Create a plugin using MineWorld-SDK
mwtool new plugin MyPlugin --lang lua

# Validate plugin
mwtool validate ./MyPlugin --game MineWorld:^0.4

# Package for distribution
mwtool pack ./MyPlugin --out MyPlugin-1.0.0.zip

# Install locally for testing
mwtool install MyPlugin-1.0.0.zip --game-path ~/MineWorld
```

---

## 8. Performance & Quality Targets

### 8.1 Performance Budgets

| Metric | Target | Measurement |
|--------|--------|-------------|
| **Frame Rate** | 60 FPS @ 10 chunks render distance | Average on GTX 1060 |
| **Startup Time** | ≤ 5 seconds to menu | Cold start |
| **World Load** | ≤ 10 seconds to spawn | New world creation |
| **Chunk Gen** | ≤ 100ms per chunk | P95 worldgen time |
| **Save Time** | ≤ 2 seconds | Blocking UI time |
| **Memory** | ≤ 2 GB RAM | 16 chunks loaded |

### 8.2 Quality Metrics

| Category | Target | How Measured |
|----------|--------|--------------|
| **Stability** | 0 crashes in 4-hour session | Soak testing |
| **Determinism** | 100% chunk hash match | Same seed tests |
| **Mod Compat** | 50+ plugins work v1.0 | Community testing |
| **Localization** | 5+ languages at v1.0 | Community contributions |

---

## 9. Community & Content Strategy

### 9.1 Community Growth Plan

**Phase 1 (v0.1-v0.3)**: Early adopters
- Dev blog/progress videos
- Open-source repository
- Discord/community hub launch

**Phase 2 (v0.4-v0.6)**: Content creators
- SDK tools release
- Modding documentation
- Plugin showcase/marketplace

**Phase 3 (v1.0+)**: Mainstream
- Steam/Itch.io release
- Content creator partnerships (YouTube/Twitch)
- Mod competition/showcase events

### 9.2 Content Creator Support

- **SDK Tools**: Easy-to-use CLI for creating packs/mods
- **Documentation**: Comprehensive tutorials and examples
- **Licensing**: CC-BY-4.0 for community content
- **Showcase**: Featured mods page on website
- **Support**: Discord channels for modders

---

## 10. Monetization & Sustainability

### 10.1 Revenue Model

**v1.0 Launch Strategy**:
- ✅ **Free & Open Source** (MIT license for code)
- ✅ **Donations** (Patreon, Ko-fi, GitHub Sponsors)
- ❓ **Optional Premium Packs** (official high-quality texture/shader packs)
- ❓ **Merchandise** (if community grows large enough)

**No Pay-to-Win**: All gameplay features free; only cosmetic/convenience paid content

### 10.2 Long-Term Sustainability

- Community-driven development (contributions)
- Modding ecosystem generates content
- Server hosting (official hosted servers as premium service?)
- Educational use (partnerships with schools/coding camps)

---

## 11. Risk Management

### 11.1 Technical Risks

| Risk | Impact | Mitigation |
|------|--------|-----------|
| **BlockCore API changes** | High | Pin versions; test compatibility matrix |
| **Save corruption** | Critical | Backups; versioned format; migration tools |
| **Multiplayer desync** | High | Deterministic worldgen; thorough net testing |
| **Mod conflicts** | Medium | Plugin sandbox; capability checks |
| **Performance regressions** | Medium | Continuous profiling; benchmark suite |

### 11.2 Project Risks

| Risk | Impact | Mitigation |
|------|--------|-----------|
| **Scope creep** | High | Lock feature set per version; say no often |
| **Community toxicity** | Medium | Clear code of conduct; moderation |
| **Burnout** | Medium | Realistic timelines; community co-development |
| **Legal issues** | Low | Original assets; clear licensing |

---

## 12. Success Metrics

### v1.0 Success Criteria

**Quantitative**:
- ✅ 1,000+ downloads in first month
- ✅ 50+ community mods/plugins
- ✅ 10+ active public servers
- ✅ 60 FPS on mid-tier hardware
- ✅ 0 critical bugs in 6 months post-release

**Qualitative**:
- ✅ Positive reviews (4+/5 average)
- ✅ Active community (daily Discord activity)
- ✅ Content creator coverage (YouTube videos, streams)
- ✅ "It feels good to play" - playtest feedback

---

## 13. Open Questions & Decisions

### To Be Decided

- [ ] **Mobs**: Simple AI or complex behavior? (Decision by v1.5)
- [ ] **Redstone**: Implement or leave for mods? (Decision by v2.0)
- [ ] **Dimensions**: Nether/End equivalents? (Decision by v2.5)
- [ ] **Console Ports**: Feasible with C#/.NET? (Decision by v3.0)
- [ ] **VR Support**: Worth investigating? (Decision by v3.0)

### Research Needed

- [ ] Best practices for voxel multiplayer at scale
- [ ] Procedural structure generation (villages, dungeons)
- [ ] Advanced shader techniques for voxel rendering
- [ ] Cloud save integration options

---

## 14. Conclusion

MineWorld is a **multi-year journey** to create a polished, moddable voxel sandbox game. Success comes from:

1. **Player Focus**: Fun, performant gameplay first
2. **Community Building**: Empower content creators
3. **Technical Excellence**: Built on solid BlockCore foundation
4. **Sustainable Development**: Realistic scope, incremental delivery

**The journey from v0.1 to v1.0 builds the game. Everything after is polish and community growth.**

---

## Appendix: Related Documents

- [v0.1 Plan](v0.1.md) - Detailed implementation plan for first milestone
- [BlockCore Overall](https://github.com/DandelionBold/BlockCore/blob/main/docs/planning/overall.md)
- [MineWorld-SDK Overall](https://github.com/DandelionBold/MineWorld-SDK/blob/main/docs/planning/overall.md)

---

**Last Reviewed**: 2025-10-18  
**Next Review**: After v0.1 completion

