# 00. Master Overview: 3D Pacman Desktop Project

## 1. Project Vision
The objective of this project is to develop a complete, standalone Desktop application of a 3D Pacman game.
The core twist is the camera perspective: the player experiences the maze primarily in **First-Person Shooter (FPS) view**, but has the ability to toggle to a classic **Top-down view**.
The aesthetic direction is **Classic Retro-Arcade**, focusing on neon-like vibrant colors on dark backgrounds, but materialized in a full 3D environment.

## 2. Technical Stack
The game will be built using modern web technologies wrapped in a desktop container:
- **Container**: Electron (for packaging the web app as a Desktop executable)
- **Build Tool**: Vite (for fast, modern frontend building)
- **Language**: TypeScript (for strong typing and scalable architecture)
- **3D Engine**: Three.js (for rendering the 3D maze, entities, and handling the FPS/Top-down cameras)

## 3. Core Mechanics & "New Features"
Beyond the classic "eat pellets, run from ghosts, eat power pellets to eat ghosts" loop, the game incorporates new mechanics:
- **Perspective Toggle**: Switching between immersive FPS view and strategic Top-down view.
- **Dash Mechanic**: A quick burst of speed to escape tight situations, constrained by a cooldown.
- **Destructible Walls**: Certain maze segments can be broken, altering the maze layout dynamically.
- **Local Multiplayer**: A split-screen or shared-screen mode allowing another player to control a ghost or a second Pacman.

## 4. AI Agent Orchestration
This documentation serves as a comprehensive master specification to guide various AI agents in building the project. Each agent has a dedicated brief:

1. **[01_Game_Design_Agent.md](./01_Game_Design_Agent.md)**: Responsible for the rules, level design, game loops, HUD specs, and ghost AI behavior.
2. **[02_Developer_Agent.md](./02_Developer_Agent.md)**: Responsible for writing the code, setting up the Electron/Three.js architecture, physics, and implementation of all mechanics.
3. **[03_3D_Asset_Agent.md](./03_3D_Asset_Agent.md)**: Provides prompts and constraints for generating 3D models and textures (GLTF/GLB) fitting the Retro-Arcade style.
4. **[04_Audio_Agent.md](./04_Audio_Agent.md)**: Provides prompts for generating 8-bit/synthwave music and SFX using Audio AI tools.
5. **[05_QA_Testing_Agent.md](./05_QA_Testing_Agent.md)**: Responsible for testing protocols, performance tracking (60+ FPS in Three.js), and bug reporting.
6. **[06_Marketing_Agent.md](./06_Marketing_Agent.md)**: Responsible for crafting the pitch, store descriptions, and trailer concepts for the final game.

## 5. General Instructions for All Agents
- Always refer back to this Master Overview if unsure about the project's direction.
- Maintain the **Classic Retro-Arcade** tone across all outputs (code style, asset generation prompts, design docs).
- Cross-reference specifications (e.g., the Developer Agent must implement the Ghost AI exactly as defined by the Game Design Agent).
