# MineWorld

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![.NET](https://img.shields.io/badge/.NET-9.0-purple.svg)](https://dotnet.microsoft.com/)
[![Engine](https://img.shields.io/badge/Engine-BlockCore-green.svg)](https://github.com/DandelionBold/BlockCore)
[![Status](https://img.shields.io/badge/Status-In%20Development-yellow.svg)]()

**A voxel sandbox game built on the BlockCore engine.**

MineWorld is an infinite-world sandbox game where players can explore, build, and survive in procedurally generated voxel worlds. Built entirely on [BlockCore](https://github.com/DandelionBold/BlockCore), it showcases the engine's capabilities while providing a fun, moddable gaming experience.

---

## 🎮 Features

- **🌍 Infinite Procedural Worlds**: Explore endless terrain generated from seeds with diverse biomes
- **🎨 Creative & Survival Modes**: Build freely or survive against the elements
- **📦 Resource Packs**: Customize textures, sounds, and UI with community packs
- **🔌 Plugin System**: Extend gameplay with Lua plugins (teleport, home, custom commands)
- **💾 World Management**: Create, backup, import, and export worlds
- **🎨 Shader Profiles**: Choose visual styles (Classic, Cinematic, Toon)
- **🌐 Multiplayer**: Host or join servers with synchronized gameplay
- **⚙️ Fully Configurable**: Customize controls, graphics, and gameplay settings

---

## 📸 Screenshots

> **Note**: Screenshots coming after v0.1 release!

---

## 🚀 Getting Started

> **Note**: MineWorld is currently in early development (v0.1). Features are limited.

### Download

- **Windows**: [Download MineWorld-v0.1-Windows.zip](#) *(Coming Soon)*
- **Linux**: [Download MineWorld-v0.1-Linux.tar.gz](#) *(Coming Soon)*
- **macOS**: [Download MineWorld-v0.1-macOS.dmg](#) *(Coming Soon)*

### System Requirements

**Minimum**:
- OS: Windows 10, Ubuntu 20.04, macOS 11.0
- CPU: Dual-core 2.5 GHz
- RAM: 4 GB
- GPU: Integrated graphics with Vulkan/DX12/Metal support
- Storage: 500 MB

**Recommended**:
- OS: Windows 11, Ubuntu 22.04, macOS 13.0
- CPU: Quad-core 3.0 GHz or better
- RAM: 8 GB
- GPU: GTX 1060 / RX 580 or better
- Storage: 2 GB

---

## 🎮 How to Play

### First Launch

1. Launch MineWorld
2. Click **Create New World**
3. Enter a world name and seed (optional)
4. Click **Create** and start playing!

### Controls

| Action | Key/Button |
|--------|-----------|
| Move Forward | W |
| Move Backward | S |
| Move Left | A |
| Move Right | D |
| Jump | Space |
| Place Block | Right Click |
| Break Block | Left Click |
| Open Inventory | E |
| Open Chat/Commands | T |
| Toggle Gamemode | F3 + G |
| Screenshot | F2 |

### Commands

- `/seed` - Display world seed
- `/gamemode <creative|survival>` - Switch game mode
- `/tp <x> <y> <z>` - Teleport to coordinates
- `/time set <day|night>` - Set time of day
- `/give <block> [count]` - Give items (creative mode)

---

## 🛠️ Building from Source

### Prerequisites

- [.NET 9 SDK](https://dotnet.microsoft.com/download/dotnet/9.0)
- [BlockCore](https://github.com/DandelionBold/BlockCore) (automatically fetched via NuGet)

### Build Steps

```bash
# Clone the repository
git clone https://github.com/DandelionBold/MineWorld.git
cd MineWorld

# Restore dependencies
dotnet restore

# Build client
dotnet build -c Release

# Build dedicated server (headless)
dotnet build -c Release -p:ServerMode=true

# Run client
dotnet run --project src/MineWorld.Client

# Run server
dotnet run --project src/MineWorld.Server
```

---

## 🌍 Worlds & Content

### Creating Worlds

Worlds are generated from **seeds** (text or numbers). Same seed = same world!

**Example seeds**:
- `12345` - Classic terrain with varied biomes
- `Mountains` - Highland terrain with peaks
- `Flat` - Superflat world (creative mode)

### Resource Packs

1. Download `.zip` pack from community
2. Place in `MineWorld/packs/` folder
3. Select in **Options → Resource Packs**
4. Reload game

### Plugin Installation

1. Download `.zip` plugin
2. Place in `MineWorld/plugins/` folder
3. Restart game or reload plugins

---

## 🖥️ Running a Server

### Quick Start

```bash
# Run dedicated server
./MineWorld-Server --world "MyServer" --port 25565

# Or with config file
./MineWorld-Server --config server.toml
```

### Server Configuration (`server.toml`)

```toml
[server]
world_name = "MyServer"
port = 25565
max_players = 10
difficulty = "normal"
gamemode = "survival"

[world]
seed = "MyServerSeed"
generate_structures = true
```

### Joining a Server

1. Launch MineWorld
2. Click **Multiplayer**
3. Click **Add Server**
4. Enter server IP and port
5. Click **Join**

---

## 📚 Documentation

- **🎓 Learning Path**: [Comprehensive guides](docs/learning/README.md) for developers transitioning from enterprise development to game development
- [Planning & Roadmap](docs/planning/overall.md) - Long-term vision
- [v0.1 Development Plan](docs/planning/v0.1.md) - Current milestone
- [Modding Guide](#) *(Coming Soon)*
- [Server Administration](#) *(Coming Soon)*

---

## 🎨 Modding & Content Creation

Create your own content using the official SDK tools:

- [**MineWorld-SDK**](https://github.com/DandelionBold/MineWorld-SDK) - Toolkit for creating mods, packs, and plugins
- [**BlockCore-SDK**](https://github.com/DandelionBold/BlockCore-SDK) - Advanced engine extensions

### Popular Mods

- Home Teleport Plugin *(Coming Soon)*
- Minimap Mod *(Coming Soon)*
- High-Res Texture Pack *(Coming Soon)*

---

## 🗺️ Roadmap

- **v0.1** - Title screen, world creation, flat world, creative mode
- **v0.2** - Terrain generation, biomes, trees, basic ores
- **v0.3** - Survival mode, health, damage, block hardness
- **v0.4** - Resource packs, shader profiles, commands
- **v0.5** - Plugin support, example plugins
- **v0.6** - Multiplayer, dedicated server
- **v1.0** - Stable release, crafting, advanced gameplay

---

## 🤝 Contributing

We welcome contributions! Whether you're fixing bugs, adding features, or creating content:

1. Check [open issues](https://github.com/DandelionBold/MineWorld/issues)
2. Read CONTRIBUTING.md *(Coming Soon)*
3. Submit pull requests

### Development Guidelines

- **C# Conventions**:
  - Constants: `SCREAMING_SNAKE_CASE`
  - Variables/Functions: `camelCase`
  - Classes: `PascalCase`
- **Branching**: `MAJOR.MINOR.PATCH/feature/<short-slug>`
- **Commits**: Reference task plan files

---

## 📄 License

MineWorld is dual-licensed:
- Code: [MIT License](LICENSE)
- Default Asset Pack: [CC BY 4.0](LICENSE-CC-BY-4.0)

---

## 🌟 Related Projects

- [**BlockCore**](https://github.com/DandelionBold/BlockCore) - The voxel engine powering MineWorld
- [**BlockCore-SDK**](https://github.com/DandelionBold/BlockCore-SDK) - Engine extension toolkit
- [**MineWorld-SDK**](https://github.com/DandelionBold/MineWorld-SDK) - Game modding toolkit

---

## 💬 Community

- GitHub Issues: Bug reports and feature requests
- Discussions: Questions and community chat *(Coming Soon)*
- Discord: *(Coming Soon)*

---

## ❤️ Acknowledgments

MineWorld is inspired by the sandbox genre and built with love by the community.

Special thanks to:
- BlockCore engine developers
- All contributors and testers
- The voxel game community

---

**Explore. Build. Survive. Welcome to MineWorld.**

