# 03. 3D Asset Agent Specification

**Role:** 3D Asset Agent
**Objective:** Generate or provide prompts for creating 3D models and textures that fit the "Retro-Arcade Classic" aesthetic in a 3D context.

## 1. Aesthetic Direction
- **Style:** "Tron-like", Neon, Synthwave, Retro-Arcade.
- **Colors:** Deep blacks and dark greys for backgrounds/floors. Highly saturated neon colors (Yellow, Red, Pink, Cyan, Orange) for entities and maze borders.
- **Lighting:** Models should ideally rely on self-illuminating (emissive) textures rather than complex dynamic lighting to save performance.

## 2. Technical Constraints for Three.js
- **Format:** `.glb` or `.gltf` (GLB preferred for single-file packaging).
- **Polycount:** Low-poly. The game relies heavily on fast movement and grid logic; complex meshes will hinder performance and visual clarity.
  - Characters: < 2,000 polygons.
  - Wall segments: < 100 polygons.
- **Textures:** Bake emissive maps directly into the materials. Keep texture resolutions low (e.g., 512x512) for a pixelated/retro feel, or use pure vertex colors.

## 3. Required Assets & Generation Prompts
Use these prompts if interacting with AI 3D generators (like Meshy, Luma, CSM) or provide them to a human 3D artist.

### A. The Ghosts (x4 Variations: Red, Pink, Cyan, Orange)
- **Concept:** A 3D interpretation of the classic pixel ghost. It should have a slightly translucent or glowing material.
- **Prompt:** `Low poly 3D model of an arcade ghost, smooth rounded top, jagged bottom edge resembling a floating sheet, minimalist large glowing eyes looking forward. Synthwave aesthetic, glowing neon [Color] material. No complex textures, clean smooth geometry.`

### B. Vulnerable Ghost (Blue State)
- **Concept:** The state when a Power Pellet is eaten.
- **Prompt:** `Low poly 3D model of an arcade ghost, jagged bottom, neon deep blue color. The face features a wavy glowing white line for a mouth and white squares for eyes. Frightened expression. Glowing synthwave aesthetic.`

### C. Wall Segments (Standard & Destructible)
- **Concept:** Modular blocks to build the maze.
- **Prompt (Standard):** `A simple 3D cube wall segment for a maze. The edges of the cube are highlighted with glowing neon blue lines. The faces of the cube are dark obsidian or black glass. Minimalist retro sci-fi style.`
- **Prompt (Destructible):** `A 3D cube wall segment for a maze, dark obsidian faces with glowing neon blue edges. The faces have glowing orange cracks radiating through them, indicating it can be broken. Retro arcade aesthetic.`

### D. Pellets
- **Standard Pellet:** A simple low-poly sphere, glowing neon yellow. (Prompting usually not needed, standard Three.js sphere with `MeshBasicMaterial` is sufficient).
- **Power Pellet:** A slightly larger sphere or a glowing 3D diamond/octahedron, pulsing neon yellow/white.

### E. Pacman (Optional, primarily for Multiplayer/Top-Down view)
- **Concept:** Since the game is mostly FPS, the player doesn't see themselves. However, for Top-down or multiplayer, a model is needed.
- **Prompt:** `Low poly 3D sphere with a large wedge cut out representing a mouth. Glowing neon yellow. Simple, iconic retro arcade character translated to 3D. No eyes.`
