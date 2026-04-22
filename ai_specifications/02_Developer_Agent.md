# 02. Developer Agent Specification

**Role:** Developer Agent
**Objective:** Architect and implement the 3D game using Electron, Vite, TypeScript, and Three.js. Ensure high performance, clean code, and faithful implementation of the Game Design specs.

## 1. Project Architecture
- **Environment:** Electron wraps a Vite dev server for local development and packages a static Vite build for production.
- **Frontend Framework:** Vanilla TypeScript (No React/Vue needed for the core loop, though HTML/CSS can be overlaid for the HUD).
- **3D Rendering Engine:** Three.js.
- **Physics/Collision:** Implement a custom grid-based 2D physics engine running under the hood, mapped to 3D coordinates. Do not use heavy physics engines (like Cannon.js) unless absolutely necessary for destructible wall debris.

## 2. Directory Structure Recommendation
```text
src/
├── main/              # Electron Main Process code (main.ts, window management)
├── preload/           # Electron Preload scripts (IPC bridges)
├── renderer/          # Frontend Web code (Three.js, UI)
│   ├── assets/        # Models (.glb), Sounds (.mp3/.wav), Textures
│   ├── core/          # Game Loop, Game State Management
│   ├── entities/      # Classes for Player, Ghosts, Pellets
│   ├── level/         # Maze generation, Grid Logic
│   ├── systems/       # Input handling, Camera controllers, Audio manager
│   ├── ui/            # HTML/CSS HUD overlay logic
│   └── index.ts       # Renderer entry point
```

## 3. Camera Controllers
Implement two distinct Three.js camera systems:
1.  **FPS Camera (`PerspectiveCamera`):**
    -   Attached to the Player entity's position.
    -   Y-axis locked (no looking up/down required, strict horizontal rotation).
    -   Smooth rotation (LERP) when turning corners to prevent motion sickness.
2.  **Top-Down Camera (`OrthographicCamera` or high-altitude `PerspectiveCamera`):**
    -   Positioned high above the maze center, looking straight down.
    -   Requires a smooth transition animation (e.g., pulling up from FPS to Top-down) when toggled.

## 4. Input Handling
-   **Keyboard:** `W,A,S,D` or Arrow Keys for movement.
-   **Spacebar:** Dash mechanic.
-   **Tab / M:** Toggle Top-down view.
-   Ensure input is buffered (e.g., pressing 'Left' slightly before an intersection queues the turn so the player doesn't miss the corner).

## 5. Implementation Guidelines for Specific Mechanics
-   **Grid-to-3D Mapping:** The maze should be defined as a 2D array (e.g., `0` for empty, `1` for wall, `2` for pellet). The rendering engine parses this array to instantiate Three.js meshes. 1 grid unit = 1 Three.js unit.
-   **Destructible Walls:**
    -   Represented as specific indices in the 2D array.
    -   When dashed into, remove the object from the Three.js scene, play a particle effect, and update the 2D grid array so Pathfinding (Ghosts) recognizes the new path.
-   **Ghost Pathfinding:** Implement A* (A-Star) or Breadth-First Search for grid-based pathfinding, allowing ghosts to calculate routes to their targets dynamically.

## 6. Performance Constraints
-   **Draw Calls:** InstancedMesh must be used for rendering pellets and wall segments to keep draw calls low.
-   **Memory:** Clean up Three.js Geometries, Materials, and Textures properly upon level reset to prevent memory leaks.
-   **Framerate:** Target a locked 60 FPS minimum on standard hardware.
