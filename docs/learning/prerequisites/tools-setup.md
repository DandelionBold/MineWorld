# Tools & Setup - Development Environment

**Navigation**: [MineWorld](../../README.md) > [Learning](../README.md) > [Prerequisites](overview.md) > [Tools & Setup](tools-setup.md)

Setting up your development environment for MineWorld game development.

## 🛠️ Required Tools

### 1. .NET 9 SDK
**Purpose**: C# runtime and development tools

**Download**: https://dotnet.microsoft.com/download/dotnet/9.0

**Verify Installation**:
```bash
dotnet --version
# Should show: 9.0.x
```

### 2. IDE (Choose One)

#### Visual Studio 2022 (Recommended)
**Download**: https://visualstudio.microsoft.com/vs/
**Required Workloads**:
- .NET desktop development
- Game development with C++ (for graphics debugging)

**Pros**: Best C# support, integrated debugging, IntelliSense
**Cons**: Windows only, large download

#### JetBrains Rider
**Download**: https://www.jetbrains.com/rider/
**Required Plugins**: None (C# support built-in)

**Pros**: Cross-platform, excellent C# support, lightweight
**Cons**: Paid (free trial available)

#### Visual Studio Code
**Download**: https://code.visualstudio.com/
**Required Extensions**:
- C# Dev Kit
- C# Extensions
- GitLens

**Pros**: Free, lightweight, cross-platform
**Cons**: Less integrated than full IDEs

### 3. Git
**Purpose**: Version control

**Download**: https://git-scm.com/

**Verify Installation**:
```bash
git --version
# Should show: git version 2.x.x
```

### 4. BlockCore Engine
**Purpose**: Game engine dependency

**Installation**: Will be added as NuGet package dependency

## 🎮 Game Development Tools

### 1. Graphics Drivers
**Purpose**: Access to latest graphics APIs

**NVIDIA**: https://www.nvidia.com/drivers/
**AMD**: https://www.amd.com/support/
**Intel**: https://www.intel.com/content/www/us/en/support/articles/000005629/graphics.html

### 2. Content Creation Tools (Optional)

#### Blender (3D Modeling)
**Purpose**: Create 3D models and textures
**Download**: https://www.blender.org/

**MineWorld Use Cases**:
- Creating block models
- Texture creation
- Asset optimization

#### GIMP (Image Editing)
**Purpose**: Texture editing and creation
**Download**: https://www.gimp.org/

**Alternative**: Adobe Photoshop, Paint.NET

#### Audacity (Audio Editing)
**Purpose**: Sound effect creation
**Download**: https://www.audacityteam.org/

## 🔧 Development Environment Setup

### 1. Project Structure
```
MineWorld/
├─ src/
│   ├─ MineWorld.Core/
│   ├─ MineWorld.Player/
│   ├─ MineWorld.World/
│   ├─ MineWorld.UI/
│   └─ MineWorld.Game/
├─ tests/
├─ docs/
└─ MineWorld.sln
```

### 2. IDE Configuration

#### Visual Studio 2022
1. **Open**: MineWorld.sln
2. **Set Startup Project**: MineWorld.Game
3. **Configure Debugging**:
   - Working Directory: `$(ProjectDir)`
   - Command Arguments: (none)

#### Rider
1. **Open**: MineWorld.sln
2. **Set Run Configuration**: MineWorld.Game
3. **Configure Debugging**: Same as Visual Studio

#### VS Code
1. **Open**: MineWorld folder
2. **Install Extensions**: C# Dev Kit
3. **Configure Launch**: `.vscode/launch.json`

### 3. Build Configuration

**Debug Build**:
```bash
dotnet build -c Debug
```

**Release Build**:
```bash
dotnet build -c Release
```

**Run Tests**:
```bash
dotnet test
```

## 🌐 Cross-Platform Considerations

### Windows Development
- **Graphics API**: DirectX 12, Vulkan
- **IDE**: Visual Studio 2022 (recommended)
- **Debugging**: Visual Studio debugger

### Linux Development
- **Graphics API**: Vulkan, OpenGL
- **IDE**: Rider or VS Code
- **Debugging**: GDB or Rider debugger

### macOS Development
- **Graphics API**: Metal, Vulkan
- **IDE**: Rider or VS Code
- **Debugging**: LLDB or Rider debugger

## 📚 Additional Tools

### 1. Git GUI (Optional)
**GitHub Desktop**: https://desktop.github.com/
**GitKraken**: https://www.gitkraken.com/
**SourceTree**: https://www.sourcetreeapp.com/

### 2. Package Managers
**NuGet**: Built into .NET SDK
**Chocolatey** (Windows): https://chocolatey.org/
**Homebrew** (macOS/Linux): https://brew.sh/

### 3. Documentation Tools
**DocFX**: Generate API documentation
**Markdown Editors**: Typora, Mark Text

## 🚀 Verification Steps

### 1. Test .NET Installation
```bash
dotnet new console -n TestApp
cd TestApp
dotnet run
# Should print: Hello, World!
```

### 2. Test BlockCore Integration
Create a simple test to verify BlockCore engine access:
```csharp
// This will be covered in v0.1 implementation
```

### 3. Test Git Integration
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## 🎯 Next Steps

1. **Install Required Tools**: .NET 9 SDK, IDE, Git
2. **Update Graphics Drivers**: Latest version for your GPU
3. **Clone Repository**: Get MineWorld source code
4. **Build Project**: Verify everything works
5. **Start Learning**: [v0.1 Learning Guide](v0.1/what-you-will-learn.md)

## 🆘 Troubleshooting

### Common Issues

**"dotnet command not found"**:
- Add .NET SDK to PATH
- Restart terminal/IDE

**"BlockCore not found"**:
- Verify BlockCore engine dependency
- Check NuGet package restore

**"Build errors"**:
- Verify .NET 9 SDK installation
- Check project dependencies

**"Performance issues"**:
- Enable hardware acceleration
- Close unnecessary applications

---

## 📖 Navigation

**Previous**: [Game Design Concepts](game-design-concepts.md)  
**Next**: [v0.1 Learning Guide](../v0.1/what-you-will-learn.md)

**Ready to start coding? Head to [v0.1 Learning Guide](../v0.1/what-you-will-learn.md)!**
