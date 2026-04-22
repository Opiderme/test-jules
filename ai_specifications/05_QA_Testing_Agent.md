# 05. QA & Testing Agent Specification

**Role:** QA (Quality Assurance) Testing Agent
**Objective:** Establish testing protocols, performance benchmarks, and automated testing strategies for the Electron/Three.js application.

## 1. Core Testing Areas

### A. Gameplay & Logic (Unit/Integration Testing)
- **Grid Movement:** Verify the player and ghosts snap correctly to grid coordinates conceptually, even while moving smoothly in 3D.
- **Collision Detection:** Ensure player cannot pass through standard walls, but can pass through destructible walls *only* when using the Dash ability.
- **Ghost AI:**
  - Verify Blinky tracks direct position.
  - Verify Pinky targets the tile ahead of the player.
  - Verify ghosts switch to "Frightened" state immediately upon Power Pellet consumption and reverse their current direction.
  - Verify eaten ghosts return to the ghost house and respawn.
- **State Management:** Ensure score increments correctly, lives decrease upon collision, and level resets/advances properly when all pellets are cleared.

### B. Performance Testing (Three.js)
- **Framerate:** The game must maintain a strict 60 FPS minimum on standard hardware.
- **Memory Leaks:** Monitor RAM and VRAM usage over multiple level loads. Ensure Three.js `dispose()` methods are called for Geometries, Materials, and Textures when transitioning or resetting levels.
- **Draw Calls:** Monitor WebGL draw calls. Ensure the maze walls and pellets are utilizing `InstancedMesh` to keep draw calls below 100 per frame.

### C. Desktop Integration (Electron)
- **Window Management:** Test resizing (if allowed) and fullscreen toggles.
- **Packaging:** Ensure the app builds correctly for target OS (Windows `.exe`, macOS `.dmg`, Linux AppImage) without missing assets.
- **IPC (Inter-Process Communication):** Ensure smooth communication between the renderer (game) and main process (e.g., saving high scores to local disk).

## 2. Recommended Testing Tools
- **Vitest:** For unit testing pure TypeScript logic (grid logic, math, pathfinding).
- **Playwright or Cypress:** For End-to-End testing the Electron app (verifying rendering, UI overlays, and input).
- **Three.js Spector.js Extension:** For profiling WebGL draw calls and shader performance during development.

## 3. Bug Reporting Format
When reporting a bug, the QA agent (or human tester) must provide:
1. **Title:** Concise description.
2. **Environment:** OS, Hardware specs, Game Version.
3. **Steps to Reproduce:** Numbered list.
4. **Expected Result:** What should happen.
5. **Actual Result:** What actually happened.
6. **Performance Logs:** FPS drop, memory spike, or console errors if applicable.
