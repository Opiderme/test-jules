# 04. Audio Agent Specification

**Role:** Audio Agent
**Objective:** Generate or provide prompts for creating royalty-free sound effects (SFX) and background music (BGM) that fit the "Retro-Arcade Classic" and "Synthwave" aesthetic.

## 1. Aesthetic Direction
- **Style:** 8-bit, Chiptune, Synthwave, Dark Synth.
- **Mood:** Tense, fast-paced (BGM), sharp and satisfying (SFX).
- **Format:** `.mp3` or `.ogg` for BGM, `.wav` for short punchy SFX.

## 2. Required Sound Effects (SFX) & Prompts
Use these prompts with AI audio generators (e.g., ElevenLabs SFX, specialized synth generators) or as guidelines for a sound designer.

### A. Waka-Waka (Eating Pellet)
- **Concept:** The iconic looping sound of eating standard pellets, modernized.
- **Prompt:** `Short, synthesized 'womp' sound, 8-bit chiptune style, slightly resonant, satisfying pop. Needs to loop seamlessly when played repeatedly at 0.2-second intervals.`

### B. Power Pellet Eaten
- **Concept:** A rising, empowering sound indicating a state change.
- **Prompt:** `8-bit synth power-up sound, rapid ascending arpeggio, energetic, sudden burst of energy, retro arcade style.`

### C. Ghost Eaten
- **Concept:** A sharp sound indicating an enemy defeated.
- **Prompt:** `Short 8-bit digital crunch sound, descending pitch, retro arcade enemy defeated sound, slightly bass-heavy.`

### D. Dash Mechanic
- **Concept:** Sound for the new Dash ability.
- **Prompt:** `Quick synthetic 'whoosh', laser-like sweep, energetic dash or teleport sound effect, synthwave aesthetic.`

### E. Wall Destroyed
- **Concept:** Breaking a destructible wall.
- **Prompt:** `Digital glass shattering, heavy 8-bit explosion, bass drop, retro arcade block breaking sound.`

### F. Player Death
- **Concept:** The iconic descending/melting sound.
- **Prompt:** `Classic arcade death sound, descending synth tone, melting or deflating feeling, sad but retro 8-bit.`

## 3. Background Music (BGM) & Prompts
Use these prompts with AI music generators (e.g., Suno AI, Udio).

### A. Main Menu Theme
- **Prompt:** `Upbeat synthwave track, 120 BPM, driving bassline, retro 80s arcade feel, energetic but welcoming, instrumental.`

### B. Standard Level BGM
- **Prompt:** `Dark synthwave, tense, pulsing baseline, 130 BPM, chiptune lead melody, feels like being hunted in a neon maze, instrumental.`

### C. Power Pellet State BGM (Vulnerable Ghosts)
- **Prompt:** `High energy chiptune, 150 BPM, aggressive and triumphant, fast arpeggios, retro arcade invincibility theme, instrumental.`

## 4. Implementation Notes for Developer
- Ensure the "Waka-Waka" sound does not overlap painfully; it should be managed by an audio pool or a looping track that stops when movement stops.
- Background music should crossfade smoothly when states change (e.g., eating a Power Pellet).
