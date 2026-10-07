# 2D Dungeon Fighter

A top-down 2D dungeon combat game built with **Unity** and **C#**. Fight enemies, collect pesos from chests, upgrade your weapon, heal at fountains and level up as you work through the dungeon to the portal at the end.

**[Watch gameplay video](https://drive.google.com/file/d/19ihPZcDGN73lu2VAwtvD4JDODVRIzou6/view?usp=sharing)**

![Gameplay screenshot showing the player with a sword, a chest and a healing fountain](screenshots/gameplay.png)

## Why I built it

Dungeon fighter games are popular, but many feel shallow: weak level design, dated art, difficulty that is too hard for beginners or too easy for experienced players, and no progression system to keep people playing. I wanted to build a game with a clear sense of progression (XP, levels and weapon upgrades) and a dark pixel-art style, based on feedback from the players I was making it for.

## Features

- **Player movement and combat:** move with `W A S D` or the arrow keys and swing your sword with `Space`, with a swing animation and knock-back on hit.
- **Enemy AI:** enemies use a simple state machine (idle and chase). They chase the player when they come into range and are limited by a maximum chase distance from their starting position.
- **Progression:** killing enemies gives XP. When you level up, your health is restored to full.
- **Economy and upgrades:** every room has a chest that gives pesos, which you spend to upgrade your weapon (higher damage and a new weapon sprite, up to a maximum level).
- **Healing fountains:** stand on a fountain to heal gradually.
- **Floating text:** damage taken, damage dealt, XP gained and healing all appear as floating text.
- **Character menu:** shows your level, pesos, health and an XP bar. You can also change your player sprite and upgrade your weapon from here.
- **Game flow:** start menu (play and instructions), death screen with respawn, and a victory screen.
- **Levels:** a start level and an enemy level with 5 rooms and 7+ enemies. Player data (health, XP, pesos, weapon) carries over between scenes.
- **Dark pixel-art theme:** black, purple, brown and grey, chosen with feedback from players.

## Controls

| Action | Key |
| --- | --- |
| Move | `W A S D` or arrow keys |
| Swing sword | `Space` |
| Menus | Mouse |

## How it's built

The project is decomposed into small C# scripts, each with one job, using object-oriented programming:

| Script | Responsibility |
| --- | --- |
| `Mover` | Abstract base class with shared movement logic, inherited by `Player` and `Enemy` |
| `Player` | Input, health and interaction with objects |
| `Enemy` | Chase behaviour (state machine), damage to the player, XP reward |
| `Weapon` | Weapon stats, swing mechanics and animation |
| `Collidable` | Shared collision handling for objects in the world |
| `Damage` | Data structure for damage amount and push force |
| `HealingFountain` | Gradual healing logic |
| `TextSystem` / `TextSystemManager` | Floating text, with text objects reused instead of repeatedly created |
| `GameManager` | Coordinates systems and saves and loads game state between scenes |
| `CharacterMenu` | UI for stats, sprite selection and weapon upgrades |
| `Portal` | Moves the player between scenes |
| `CameraMotor` | Camera follows the player |

Computational thinking used: decomposition (one script per feature), abstraction (a simple two-state enemy AI rather than a complex one), inheritance (shared `Mover` base class), and planning with pseudocode before coding.

## Development process

I used an agile approach, building the game in **14 iterations**. After each one I tested the new features (recording screen captures as evidence), fixed any failures, and asked players for feedback. I wrote success criteria at the start (covering design, logic, game data, floating text and animation) and evaluated each one at the end.

One bug I found and fixed during testing: the health bar did not update when the player was healed, which I fixed by calling the game manager's hit-point update after healing.

## Running the game

**Requirements (macOS):** macOS 10.13 or later, Metal support, Intel or Apple Silicon, 4 GB RAM minimum (8 GB recommended), keyboard and mouse.

1. Clone the repository: `git clone https://github.com/Abdel432/finalWork.git`
2. Open Unity Hub, choose **Add project from disk** and select the cloned folder.
3. Open it with Unity version **[add your Unity version here]**.
4. Open the start menu scene and press **Play**.

## What I'd improve

- More enemy types, with extra states such as patrolling, and different kinds of damage
- More levels and rooms, plus checkpoints
- Difficulty options and a shop for potions
- A score counter on the death screen
- Player accounts so several people can keep separate progress on one device
- Different colours or fonts for player and enemy damage text, so they're easy to tell apart

## Credits

- Code, design and game development: Abdelfatah Alasow
- Pixel-art tileset: [16x16 Dungeon Tileset](https://0x72.itch.io/16x16-dungeon-tileset) by [0x72](https://0x72.itch.io/), used with the artist's approval
