# FrameBreaker

> Break enemies apart. Steal their parts. Build your ultimate frame.

A mobile mech-building action RPG inspired by the discontinued *Gundam Breaker Mobile* (2019–2023). FrameBreaker captures everything fans loved — cross-series Franken-building, part-break loot, EX skill combos — without the predatory gacha that killed the original.

## Concept

You are a pilot competing in sanctioned Frame Battle circuits. Each match is a real-time arena fight against enemy AI frames. Destroy an enemy's arm? That arm flies off and drops to the ground. Pick it up. Install it mid-match. Use their own weapon against them.

Between matches you return to your workshop: upgrade parts, swap loadouts, paint your frame, and theorize the next build. Then queue up and do it again.

**Core pillars:**
- **Break → Collect → Build** — the core loop never changes
- **Cross-series Franken-building** — heads, torsos, arms, legs, weapons from hundreds of frame archetypes that can be mixed freely
- **Aesthetic ≠ Stats** — any part can be made viable through the Synthesis system; you never have to choose between looking cool and being effective
- **Skill expression, not wallet expression** — no gacha; progression is earned through play

## Gameplay Overview

### The Break System
Enemy frames have **8 breakable zones**: head, torso, L/R arms, L/R legs, backpack, and shield. Targeting specific zones breaks off those parts and spawns them as loot. Break a leg → enemy slows. Break the backpack → they lose their ranged artillery. Break the head → they lose target-lock. Strategic destruction matters.

### Part Slots (per frame)
| Slot | Notes |
|------|-------|
| Head | Affects sensor range, lock-on speed |
| Torso | Core HP + passive trait pool |
| Left Arm | Independent melee weapon slot |
| Right Arm | Independent melee weapon slot |
| Left Shoulder | Ranged weapon or builder attachment |
| Right Shoulder | Ranged weapon or builder attachment |
| Legs | Movement speed, dodge stats |
| Backpack | Thruster, wing, or utility unit |

Both arms have independent loadouts — run dual blades, dual cannons, or mix. Two-handed weapons occupy both arm slots for maximum single-weapon power.

### EX Skills
Every part carries an **EX Skill** — a powerful active ability (beam burst, blade rush, shield slam, AoE mine, etc.). You equip up to **4 EX Skills** simultaneously drawn from any of your equipped parts. The EX gauge fills through combat. Chain skills for combos.

**Burst Mode:** Fill the burst bar fully → activate → temporary supercharge with enhanced stats and a frame-specific Burst EX. Visually transforms your frame's appearance during the burst window.

### OP Skills
Up to **8 passive OP Skills** (cooldown-driven utility abilities) run in the background: auto-heal on break, counter-dodge, chain boost, combo extender, etc.

### Word Tags & Synergy
Every part carries **two Word Tags** (e.g., `High Mobility`, `Coordinator`, `Newtype`, `Long Range`, `Mobile Fighter`). Stack matching tags across your 8 slots to trigger **Synergy Bonuses** — the deeper the match, the stronger the bonus. Thematic mono-builds get rewarded. Mixed-archetype builds require smarter tag choices.

### Elemental Attributes
Six attributes: **Fire, Ice, Wind, Thunder, Light, Dark**. Each part has an attribute. Stack same-attribute parts for **Attribute Link** bonuses at 8 / 10 / 12 link points. Attribute type-matchups add a soft strategic layer to matchmaking.

## Progression

### Frame Power Rating (FPR)
A composite stat across all 8 slots — quick read on overall build strength.

### Synthesis System
- **Level Up:** Feed duplicate parts or materials to increase a part's level cap
- **Rarity Upgrade:** Use Synthesis materials to raise a part from 1★ → 5★
- **Skill Transfer (5★ Mastered):** At max rarity, a part's EX Skill becomes **Mastered** — permanently portable to any future build regardless of which part is equipped. Build what looks good; your best skills travel with you.
- **Cannibalize:** Absorb a part's abilities into another part. Keep your favorite aesthetic piece; transplant the stats from something uglier but powerful.

### Pilot System
Separate character roster: licensed frame pilots with passive squad bonuses and unique support triggers. Pilots are earned through gameplay and events — **not gacha**. Assign pilots to frames for their passive stacks.

## Game Modes

| Mode | Description |
|------|-------------|
| **Campaign** | Story-driven missions, three difficulty tiers. Harder = better loot. |
| **Circuit** | Rotating weekly mission sets with special ruleset modifiers. |
| **Raids** | 3-player co-op boss battles against giant enemy frames. |
| **Bounty Hunt** | Async PvP: every player has a bounty; defeating others increases yours. No ranked ladder. |
| **Workshop** | Build, paint, pose, and photograph your frames. Share to the community gallery. |

## Monetization Philosophy

**Buy-to-play with cosmetic DLC only.** No gacha. No energy timers. No PvP powercreep.

- One-time purchase (mobile premium or free with ad-removal IAP)
- **Season Passes:** New frame packs (parts, story missions, cosmetics) — never stats
- **Cosmetic bundles:** Decal sets, paint shaders, builder ornament packs
- **Breaker Boosters:** Consumable loot multipliers earnable through S-rank clears; also purchasable for convenience — never mandatory

The lesson from GBM's shutdown: whale PvP killed the community. FrameBreaker has no ranked PvP that can be pay-to-win by design.

## Tech Stack (Target)

**Engine:** Godot 4 (open source, mobile-friendly, strong 3D performance on mid-range Android/iOS)

**Architecture:**
- Client: GDScript / C# hybrid (performance-critical systems in C#)
- Server: Elixir/Phoenix (real-time multiplayer, co-op raids, leaderboards)
- Database: PostgreSQL + Redis
- Asset pipeline: Blender → GLTF → Godot

**Target platforms:** Android (primary), iOS, PC (via Godot export)

## Repo Structure

```
framebreaker/
├── docs/
│   ├── DESIGN.md          # Full game design document
│   ├── SYSTEMS.md         # Individual system specs
│   ├── ART_DIRECTION.md   # Visual style guide
│   └── ROADMAP.md         # Milestone plan
├── client/                # Godot 4 project
├── server/                # Elixir/Phoenix backend
├── assets/                # Source art, models, audio
└── tools/                 # Build scripts, asset pipeline
```

## Status

**Pre-production.** Design documentation phase. No playable build yet.

Contributions welcome — especially:
- Game designers with mobile action RPG experience
- Godot 4 generalists
- 3D artists familiar with mech/robot aesthetics
- Backend engineers (Elixir/Phoenix preferred)

## Inspiration

Built on the shoulders of *Gundam Breaker Mobile* (2019–2023, Bandai Namco), *Gundam Breaker 3*, and *Gundam Breaker 4*. FrameBreaker is an original IP — no Gundam licensing, no IP encumbrance. The mechanic DNA is the inspiration; the world is entirely new.

---

*"The best Gunpla is the one you built yourself."*

---

## License

MIT — build it, fork it, make it yours.
