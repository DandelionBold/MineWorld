# Troubleshooting - Common Issues and Solutions

Solutions to common problems encountered during MineWorld development.

## 🚨 Common Issues

### 1. Game State Issues

#### "Game state not saving"
**Symptoms**: Player progress lost on restart
**Causes**: 
- Save system not implemented
- File permissions issues
- Corrupted save data
- Memory issues during save

**Solutions**:
```csharp
// Implement proper save system
public class SaveManager {
    private string savePath;
    
    public void SaveGame(GameState state) {
        try {
            var json = JsonSerializer.Serialize(state);
            File.WriteAllText(savePath, json);
        } catch (Exception ex) {
            LogError($"Save failed: {ex.Message}");
        }
    }
    
    public GameState LoadGame() {
        if (File.Exists(savePath)) {
            var json = File.ReadAllText(savePath);
            return JsonSerializer.Deserialize<GameState>(json);
        }
        return new GameState();
    }
}
```

#### "Game crashes on startup"
**Symptoms**: Application crashes immediately
**Causes**:
- Missing dependencies
- Corrupted configuration
- Graphics driver issues
- Memory allocation failures

**Solutions**:
```csharp
// Add proper error handling
public class GameApplication {
    public void Run() {
        try {
            Initialize();
            GameLoop();
        } catch (Exception ex) {
            LogError($"Game crashed: {ex.Message}");
            ShowErrorDialog(ex.Message);
        } finally {
            Cleanup();
        }
    }
}
```

### 2. Performance Issues

#### "Low frame rate"
**Symptoms**: Game runs below 60 FPS
**Causes**:
- Too many entities rendered
- Inefficient world updates
- Memory allocation in game loop
- CPU bottleneck

**Solutions**:
```csharp
// Profile frame time
public class PerformanceProfiler {
    private Stopwatch frameTimer;
    
    public void StartFrame() {
        frameTimer.Restart();
    }
    
    public void EndFrame() {
        var frameTime = frameTimer.ElapsedMilliseconds;
        if (frameTime > 16) { // 60 FPS = 16.67ms
            LogWarning($"Slow frame: {frameTime}ms");
        }
    }
}

// Optimize rendering
public class RenderOptimizer {
    public void CullOffscreenObjects() {
        var visibleObjects = worldObjects.Where(obj => 
            IsInViewFrustum(obj.Position)).ToList();
        RenderObjects(visibleObjects);
    }
}
```

#### "Memory usage growing"
**Symptoms**: Memory usage increases over time
**Causes**:
- Memory leaks in game objects
- Objects not being disposed
- Growing collections
- Texture memory not released

**Solutions**:
```csharp
// Implement object pooling
public class ObjectPool<T> where T : new() {
    private Queue<T> pool = new Queue<T>();
    
    public T Get() {
        return pool.Count > 0 ? pool.Dequeue() : new T();
    }
    
    public void Return(T obj) {
        pool.Enqueue(obj);
    }
}

// Proper disposal
public class GameEntity : IDisposable {
    private bool disposed = false;
    
    public void Dispose() {
        if (!disposed) {
            // Cleanup resources
            texture?.Dispose();
            sound?.Dispose();
            disposed = true;
        }
    }
}
```

### 3. Input Issues

#### "Input not responding"
**Symptoms**: Keyboard/mouse input not working
**Causes**:
- Input events not being polled
- Window not focused
- Input mapping errors
- Event handler not registered

**Solutions**:
```csharp
// Proper input handling
public class InputManager {
    private Dictionary<KeyCode, Action> keyBindings;
    
    public void Update() {
        while (window.PollEvents()) {
            switch (window.Event) {
                case KeyPressedEvent keyEvent:
                    HandleKeyPress(keyEvent.Key);
                    break;
                case MouseMovedEvent mouseEvent:
                    HandleMouseMove(mouseEvent.Position);
                    break;
            }
        }
    }
    
    private void HandleKeyPress(KeyCode key) {
        if (keyBindings.ContainsKey(key)) {
            keyBindings[key]?.Invoke();
        }
    }
}
```

#### "Mouse sensitivity issues"
**Symptoms**: Mouse movement too fast/slow
**Causes**:
- Incorrect sensitivity scaling
- Delta time not applied
- Raw input not enabled
- Platform differences

**Solutions**:
```csharp
// Apply sensitivity and delta time
public class MouseController {
    private float sensitivity = 0.1f;
    
    public void HandleMouseMove(Vector2 delta, float deltaTime) {
        var adjustedDelta = delta * sensitivity * deltaTime;
        camera.Rotate(adjustedDelta);
    }
}
```

### 4. World System Issues

#### "Blocks not rendering"
**Symptoms**: World appears empty
**Causes**:
- Chunk loading failed
- Mesh generation failed
- Rendering system not initialized
- Shader compilation errors

**Solutions**:
```csharp
// Check chunk loading
public class ChunkManager {
    public void LoadChunk(ChunkCoord coord) {
        if (!IsChunkLoaded(coord)) {
            var chunk = GenerateChunk(coord);
            if (chunk != null) {
                loadedChunks[coord] = chunk;
                GenerateMesh(chunk);
            }
        }
    }
    
    private void GenerateMesh(Chunk chunk) {
        var mesh = meshGenerator.Generate(chunk);
        if (mesh != null) {
            chunk.SetMesh(mesh);
        }
    }
}
```

#### "World generation issues"
**Symptoms**: Terrain looks wrong or crashes
**Causes**:
- Invalid seed values
- Algorithm errors
- Memory allocation failures
- Threading issues

**Solutions**:
```csharp
// Safe world generation
public class WorldGenerator {
    public Chunk GenerateChunk(ChunkCoord coord, int seed) {
        try {
            var noise = new PerlinNoise(seed);
            var chunk = new Chunk(coord);
            
            for (int x = 0; x < Chunk.SIZE; x++) {
                for (int z = 0; z < Chunk.SIZE; z++) {
                    var height = noise.GetHeight(x, z);
                    GenerateColumn(chunk, x, z, height);
                }
            }
            
            return chunk;
        } catch (Exception ex) {
            LogError($"Chunk generation failed: {ex.Message}");
            return null;
        }
    }
}
```

### 5. UI Issues

#### "UI not displaying"
**Symptoms**: Menus and HUD not visible
**Causes**:
- UI system not initialized
- Rendering order issues
- Font loading failures
- Layout calculation errors

**Solutions**:
```csharp
// Proper UI initialization
public class UIManager {
    public void Initialize() {
        LoadFonts();
        CreateMainMenu();
        CreateHUD();
        SetRenderingOrder();
    }
    
    public void Render() {
        // Render UI elements in correct order
        RenderBackground();
        RenderMenus();
        RenderHUD();
        RenderTooltips();
    }
}
```

#### "UI elements overlapping"
**Symptoms**: UI elements appear on top of each other
**Causes**:
- Incorrect z-order
- Layout calculation errors
- Responsive design issues
- Event handling conflicts

**Solutions**:
```csharp
// Proper UI layering
public class UIElement {
    public int ZOrder { get; set; }
    public Rectangle Bounds { get; set; }
    
    public bool Contains(Vector2 point) {
        return Bounds.Contains(point);
    }
}

public class UILayoutManager {
    public void ArrangeElements(List<UIElement> elements) {
        elements.Sort((a, b) => a.ZOrder.CompareTo(b.ZOrder));
        
        foreach (var element in elements) {
            element.Bounds = CalculateBounds(element);
        }
    }
}
```

## 🔧 Debugging Techniques

### 1. Game State Debugging

#### State Logging
```csharp
public class GameStateLogger {
    private List<string> stateLog = new List<string>();
    
    public void LogState(string state) {
        stateLog.Add($"{DateTime.Now:HH:mm:ss.fff}: {state}");
        
        // Keep only last 100 entries
        if (stateLog.Count > 100) {
            stateLog.RemoveAt(0);
        }
    }
    
    public void PrintStateLog() {
        foreach (var entry in stateLog) {
            Console.WriteLine(entry);
        }
    }
}
```

#### Save State Validation
```csharp
public class SaveValidator {
    public bool ValidateSave(GameState state) {
        if (state == null) return false;
        if (state.Player == null) return false;
        if (state.World == null) return false;
        
        // Validate player data
        if (state.Player.Health < 0 || state.Player.Health > 100) {
            LogError("Invalid player health");
            return false;
        }
        
        return true;
    }
}
```

### 2. Performance Debugging

#### Frame Time Profiling
```csharp
public class FrameProfiler {
    private Dictionary<string, float> timers = new Dictionary<string, float>();
    
    public void StartTimer(string name) {
        timers[name] = GetCurrentTime();
    }
    
    public void EndTimer(string name) {
        if (timers.ContainsKey(name)) {
            var elapsed = GetCurrentTime() - timers[name];
            LogPerformance(name, elapsed);
            timers.Remove(name);
        }
    }
}
```

#### Memory Profiling
```csharp
public class MemoryProfiler {
    public static void LogMemoryUsage(string context) {
        var process = Process.GetCurrentProcess();
        var memoryMB = process.WorkingSet64 / (1024 * 1024);
        Console.WriteLine($"{context}: {memoryMB}MB");
    }
    
    public static void ForceGC() {
        GC.Collect();
        GC.WaitForPendingFinalizers();
        GC.Collect();
    }
}
```

### 3. Input Debugging

#### Input Event Logging
```csharp
public class InputDebugger {
    private List<string> inputLog = new List<string>();
    
    public void LogInput(string input) {
        inputLog.Add($"{DateTime.Now:HH:mm:ss.fff}: {input}");
    }
    
    public void PrintInputLog() {
        foreach (var entry in inputLog) {
            Console.WriteLine(entry);
        }
    }
}
```

## 🚀 Performance Optimization

### 1. Rendering Optimization

#### Object Culling
```csharp
public class RenderCuller {
    public List<GameObject> CullObjects(List<GameObject> objects, Camera camera) {
        return objects.Where(obj => {
            var distance = Vector3.Distance(obj.Position, camera.Position);
            return distance < camera.FarPlane && IsInFrustum(obj, camera);
        }).ToList();
    }
}
```

#### Level of Detail
```csharp
public class LODManager {
    public void UpdateLOD(GameObject obj, Camera camera) {
        var distance = Vector3.Distance(obj.Position, camera.Position);
        
        if (distance < 50) {
            obj.SetLOD(LOD.High);
        } else if (distance < 100) {
            obj.SetLOD(LOD.Medium);
        } else {
            obj.SetLOD(LOD.Low);
        }
    }
}
```

### 2. Memory Optimization

#### Object Pooling
```csharp
public class GameObjectPool {
    private Queue<GameObject> pool = new Queue<GameObject>();
    private int maxSize = 100;
    
    public GameObject Get() {
        if (pool.Count > 0) {
            var obj = pool.Dequeue();
            obj.Reset();
            return obj;
        }
        return new GameObject();
    }
    
    public void Return(GameObject obj) {
        if (pool.Count < maxSize) {
            pool.Enqueue(obj);
        }
    }
}
```

#### Resource Streaming
```csharp
public class ResourceStreamer {
    private Dictionary<string, Resource> loadedResources = new Dictionary<string, Resource>();
    
    public Resource Load(string path) {
        if (loadedResources.ContainsKey(path)) {
            return loadedResources[path];
        }
        
        var resource = LoadFromDisk(path);
        loadedResources[path] = resource;
        return resource;
    }
    
    public void Unload(string path) {
        if (loadedResources.ContainsKey(path)) {
            loadedResources[path].Dispose();
            loadedResources.Remove(path);
        }
    }
}
```

## 🎯 Best Practices

### 1. Error Handling
- Always wrap game logic in try-catch blocks
- Log errors with context information
- Provide graceful degradation
- Use assertions for debugging

### 2. Performance Monitoring
- Profile regularly, not just when problems occur
- Set performance budgets
- Monitor memory usage
- Track frame time consistency

### 3. Debugging Tools
- Use debug overlays for real-time information
- Implement console commands for testing
- Log important events
- Use breakpoints strategically

### 4. Code Organization
- Separate game logic from rendering
- Use consistent naming conventions
- Document complex algorithms
- Keep functions small and focused

---

**Still having issues? Check the [Game Design Patterns](game-design-patterns.md) for architectural solutions!**
