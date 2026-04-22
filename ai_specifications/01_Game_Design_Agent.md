# 01. Game Design Specification

**Role:** Game Design Agent
**Objective:** Define the rules, core gameplay loop, enemy AI, and level design principles for the 3D FPS Pacman Desktop Game.

## 1. Core Gameplay Loop
- **Objective:** Navigate the 3D maze, consume all standard pellets to clear the level, and avoid contact with ghosts.
- **Power-ups:** Consuming large 'Power Pellets' temporarily turns ghosts vulnerable (blue state), allowing the player to consume them for bonus points. Eaten ghosts return to the center 'Ghost House' to respawn.
- **Progression:** Clearing all pellets advances the player to the next, slightly faster and more difficult level.

## 2. Camera & Perspective
- **Primary View (FPS):** First-person perspective. The player sees the maze from Pacman's 'eyes'. This creates tension as visibility is limited to the immediate corridors.
- **Secondary View (Top-Down):** A classic overhead perspective.
  - *Mechanic Twist:* Activating the Top-Down view should cost a resource (e.g., a regenerating battery meter) or have a strict cooldown. It allows strategic planning but leaves the player vulnerable if used at the wrong time.

## 3. New Mechanics
- **Dash:** A rapid forward movement to escape ghosts.
  - *Constraint:* 5-second cooldown. Visualized by a HUD element.
- **Destructible Walls:** Certain wall segments (indicated by a cracked neon texture) can be destroyed using the Dash mechanic.
  - *Impact:* Alters the maze layout dynamically. Ghosts can also use these new paths.
- **Local Multiplayer:**
  - *Co-op:* Player 1 is Pacman (FPS view), Player 2 is a second Pacman (Top-down view acting as an "overseer" guiding P1).
  - *Versus:* Player 1 is Pacman, Player 2 controls a unique "Hunter Ghost".

## 4. Ghost AI Behaviors
Ghosts should mimic their classic arcade personalities but adapted for a 3D environment:
- **Blinky (Red):** The Chaser. Directly targets the player's current 3D coordinates. Increases speed slightly as pellets are cleared.
- **Pinky (Pink):** The Ambusher. Targets a position 4 units *ahead* of the player's current facing direction.
- **Inky (Cyan):** The Flanker. Uses a complex vector calculation based on Blinky's position and the player's position to try and trap the player.
- **Clyde (Orange):** The Wanderer. Chases the player if further than 8 units away; if closer, he retreats to his designated corner of the maze.

## 5. Level Design Principles
- **Grid-based logic in 3D:** While rendered in 3D, movement logic and collision should conceptually remain locked to a strict grid to ensure tight, predictable arcade controls.
- **Wrap-around Tunnels:** Maintain the classic screen-wrap tunnels. Entering the left tunnel instantly teleports the player/ghosts to the right tunnel.
- **Aesthetic:** High-contrast neon lines on black/dark-grey walls (Tron-style Retro-Arcade).

## 6. HUD (Heads Up Display)
- **Score:** Top Left.
- **Lives remaining:** Bottom Left (represented by classic Pacman icons).
- **Dash Cooldown:** Center-bottom bar.
- **Top-Down Battery/Cooldown:** Top Right.
- **Minimap:** Optional (if Top-down view is restricted, a localized minimap might be needed in FPS view).
