# FrameBreaker — Game Design Document

Version: 0.1 (Pre-Production)
Last updated: 2025

---

## 1. Vision Statement

FrameBreaker is a mobile-first mech-building action RPG. Players fight in arena combat against AI-controlled enemy frames, physically break enemy parts off mid-battle, collect them as loot, and use them to build an ever-evolving custom frame. The loop is: **destroy → collect → build → destroy better**.

The game is a love letter to the Gundam Breaker franchise — specifically Gundam Breaker Mobile (2019–2023) and Gundam Breaker 3 — but as original IP. No licensing encumbrance. No gacha. No whale PvP.

---

## 2. Core Loop

```
MATCH
  └─ Enter arena with current frame loadout
  └─ Fight wave of enemy frames (AI-controlled)
  └─ Break enemy parts → parts drop as loot tokens mid-battle
  └─ Collect tokens; optionally swap a part mid-match
  └─ Clear waves → Boss frame encounter
  └─ Match ends → post-match reward screen

WORKSHOP (between matches)
  └─ Review acquired parts
  └─ Upgrade/Synthesize parts
  └─ Reassemble frame (any 8 slots)
  └─ Paint, decal, customize cosmetics
  └─ Save loadout → queue next match
```

**Session feel target:** 5–10 minute matches, 2–5 minute workshop between. Designed for mobile play sessions.

---

## 3. The Break System (Core Mechanic)

### 3.1 Breakable Zones

Every enemy frame has 8 independently destructible hitbox zones:

| Zone | Break Effect (on enemy) | Drop Rarity Modifier |
|------|-------------------------|----------------------|
| Head | Removes enemy lock-on capability | +0.5★ avg |
| Torso | Reduces enemy HP pool | +1.0★ avg |
| Left Arm | Disables left-side melee | +0.25★ avg |
| Right Arm | Disables right-side melee | +0.25★ avg |
| Left Shoulder | Disables left ranged weapon | +0.0★ avg |
| Right Shoulder | Disables right ranged weapon | +0.0★ avg |
| Legs | Reduces enemy movement/dodge | +0.25★ avg |
| Backpack | Removes thrust ability + drones | +0.75★ avg |

Breaking higher-value zones drops better loot. The torso drop is the jackpot; it's also the hardest zone to expose (protected by other parts).

### 3.2 Mid-Match Part Pickup

When a zone breaks, the part physically flies off and lands in the arena as a glowing loot token. The player has **15 seconds** to pick it up before it despawns. Picking up a part during combat requires moving to it — risk/reward tension.

### 3.3 Mid-Match Hot-Swap

At any time during a match (not in EX skill animation), the player can **hot-swap** a collected part token into one of their 8 slots. The old part is discarded (not added to inventory). This creates tactical decisions:
- Do you swap your current 3★ arm for a freshly-broken 2★ arm mid-fight because the 2★ has a better EX skill for this matchup?
- Do you pick up the torso drop or stay on the boss?

---

## 4. Part System

### 4.1 Slots

Every frame has exactly 8 equipment slots. No empty slots allowed — a frame must be fully equipped to enter a match.

```
[HEAD]         [BACKPACK]
[TORSO]
[L-ARM]        [R-ARM]
[L-SHOULDER]   [R-SHOULDER]
[LEGS]
```

**Asymmetric arm loadout:** Left Arm and Right Arm are fully independent — different melee weapons, different stats, different EX skills. Two-handed weapons occupy both arm slots.

**Shoulder slots:** Can hold ranged weapons, missile pods, artillery units, drone launchers, or cosmetic Builder Parts (stat-neutral ornaments that affect visual style only).

### 4.2 Part Stats

Each part has:
- **Base stats:** HP, ATK, DEF, SPD (contributes to FPR)
- **Passive Trait(s):** 1–3 passive bonuses (e.g., "Combo Boost: +8% ATK per active combo hit", "Sensor Range +15%")
- **EX Skill:** One active ability (see section 6)
- **OP Skill:** One utility passive (see section 6)
- **Word Tag x2:** Thematic tags for synergy (see section 5)
- **Attribute:** Fire / Ice / Wind / Thunder / Light / Dark

### 4.3 Rarity Tiers

| Stars | Color | Notes |
|-------|-------|-------|
| 1★ | Grey | Starter/common drops |
| 2★ | Green | Early progression |
| 3★ | Blue | Mid-game baseline |
| 4★ | Purple | Late-game standard |
| 5★ | Gold | Endgame; unlocks Mastered Skills |
| 5★M | Gold + glow | Mastered — skill becomes portable |

Parts are obtained by breaking enemies. Rarity is determined by: enemy level, zone broken, difficulty tier, and active Breaker Booster multipliers.

---

## 5. Build Mechanics

### 5.1 Frame Power Rating (FPR)

FPR = weighted sum of all 8 equipped parts' base stats + trait bonuses + synergy bonuses.

Displayed prominently on the build screen. Matchmaking uses FPR as a soft bracket for Campaign difficulty recommendations (not PvP gatekeeping — there is no ranked PvP).

### 5.2 Word Tag Synergy

Every part has 2 Word Tags. Tags are thematic archetypes:
- `High Mobility` — fast-moving, evasive frames
- `Heavy Arms` — artillery-focused builds
- `Coordinator` — balanced SEED-archetype stats
- `Newtype` — funnels/funnels/funnels (ranged drone focus)
- `Mobile Fighter` — close-combat specialist
- `Long Range` — sniper/beam canon builds
- `Berserker` — high risk / high ATK
- `Guardian` — defensive, shield-oriented
- `Stealth` — reduced enemy aggro range, ambush bonuses
- `Commander` — squad/support buffs (useful in co-op)
- `Striker` — melee chain combo specialist
- `Gunner` — ranged combo specialist
- (30+ tags total at launch)

**Synergy thresholds:**
- 4 matching tags: **Minor Synergy** (+5% stat in tag's domain)
- 6 matching tags: **Moderate Synergy** (+12% + unique passive effect)
- 8 matching tags: **Full Resonance** (+20% + major passive + visual aura effect)

Mixed-archetype builds sacrifice full resonance bonuses for flexibility — a valid trade.

### 5.3 Attribute Link

Equipping parts of the same attribute provides stacking stat bonuses:

| Same-Attribute Parts | Bonus |
|---------------------|-------|
| 4 | +3% ATK + +3% DEF in attribute |
| 6 | +8% ATK + +8% DEF + attribute burst proc chance |
| 8 (Full Link) | +15% ATK + +15% DEF + enhanced attribute burst + unique visual effect |

Attribute type-matchup applies in combat: Fire > Wind > Thunder > Ice > Fire (circle), Light ↔ Dark (mutual amplification). Type advantage = +15% damage.

### 5.4 Synthesis System

**Level Up:** Consume duplicate parts or generic materials to raise a part's level (1–50 base, cap increases with rarity). Level increases base stats proportionally.

**Rarity Upgrade:** Consume Synthesis Cores (earned from high-difficulty missions and Raids) to upgrade rarity. 1★ → 2★ requires 3 cores. Cost scales: 2★→3★ (8), 3★→4★ (20), 4★→5★ (50). Upgrading rarity grants new trait slots and raises the EX Skill tier.

**Cannibalize:** Select a **source part** and a **target part** of the same slot type. Absorb the source part's passive Trait into the target part as a bonus trait. Source part is destroyed. Maximum 2 cannibalizations per part. This is the primary "best of both worlds" tool — keep your aesthetic favorite, absorb the stats of something uglier.

**Skill Mastery (5★ → 5★M):** A 5★ part can be Mastered using 3 Mastery Tokens (endgame material). Mastered status means the part's EX Skill is now permanently added to your pilot's **Mastered Skill Pool** — when equipped in any future build, you can choose any Mastered Skill for that slot regardless of what part is actually equipped. Decouples EX Skills from aesthetic constraints. The "endgame unlock" that the community always wanted.

---

## 6. Skill System

### 6.1 EX Skills

Active abilities. Cost: EX Gauge bars (1–3 bars per skill).

**EX Gauge:** Builds up through combat. Max 9 bars. Fills faster with consecutive hits, zone breaks, and dodges. Empties on taking damage (partial drain).

Each part has one EX Skill. Player equips **up to 4 EX Skills** at once (drawn from any equipped part, or Mastered Skill Pool). The 4 selected skills are on independent cooldowns after use.

**EX Skill Categories:**
- Melee Rush — close-range chain combo finisher
- Beam Blast — ranged single-target high damage
- Area Denial — AoE damage or debuff field
- Defensive — shield projection, counter-dodge, reflect
- Support — heal pulse, buff aura (useful in co-op Raids)
- Summoner — deploy drone/funnel auxiliary unit
- Debuff — attribute proc, slow, sensor jam

**Burst Mode:** Full EX gauge → trigger Full Burst. All stats enhanced. Frame appearance temporarily transforms (glowing edges, trail effects). 3-bar EX Skill unlocks for duration. Burst ends after 30 seconds or on EX gauge depletion.

### 6.2 OP Skills

Passive utility skills. Each part has one OP Skill. Player equips up to **8 OP Skills** (one per slot's part by default, swappable in workshop). OP skills activate automatically on triggers:

Examples:
- "**Break Surge:**" On zone break → +20% ATK for 5s
- "**Dodge Counter:**" On successful dodge → next hit deals +40% damage
- "**Combo Shield:**" At 10+ combo count → damage taken -25%
- "**Chain Collector:**" On part pickup → EX gauge +1 bar
- "**Burst Extension:**" On Burst activation → duration +8s
- "**Repair Pulse:**" On 5-hit combo → restore 3% HP

OP Skills and EX Skills together form the "build personality" — two builds with identical parts but different equipped skills play completely differently.

---

## 7. Pilot System

Pilots are characters with passive squad bonuses and personal backstories. They are **not gacha** — earned through Campaign milestones, event rewards, and Raid completions.

Each pilot has:
- **Personal Stat Bonus:** Small flat stat contribution to the frame they're assigned to (e.g., "+5% ATK", "+8% DEF")
- **Squad Passive:** One passive that benefits the full squad in co-op Raids
- **Awakening Level:** 1–5, raised by collecting duplicate pilot cards (all earnable in-game). Each level enhances their bonuses.

Pilots are the "character collection" hook — but they're never stronger than a well-built frame. They supplement; they don't substitute.

---

## 8. Progression

### 8.1 Campaign

Story-driven missions in chapters (target: 10 chapters at launch, 2 added per season).

Three difficulty modes per chapter:
- **Standard:** Accessible, story-focused
- **Hard:** Better loot, enemies have enhanced break resistance
- **Extreme:** Endgame challenge, best possible drops, fixed enemy archetypes optimized to counter common builds

Completing all missions in a chapter on Extreme unlocks the **Chapter Challenge** — a special mission with unique enemy frame that drops a guaranteed 5★ part (random slot, archetype themed to the chapter).

### 8.2 Breaker Booster System

Earnable consumables that modify a mission's loot parameters before entry:

| Booster | Effect |
|---------|--------|
| Quantity Booster | +50% parts dropped per zone break |
| Rarity Booster | +1 average rarity on all drops |
| Attribute Booster | +50% drop rate for a selected attribute |
| Double Break | Zone breaks drop 2 tokens instead of 1 |
| XP Booster | +100% Synthesis material drops |

Earned via: S-rank clears (main earn), season pass, optional convenience IAP. **Never required; always accelerants.**

S-rank conditions: clear time under par, no frame destruction, all zones broken on boss.

### 8.3 Circuit (Weekly Content)

Rotating 5–7 mission sets per week with modifier rules:
- "Melee Only" — ranged weapons disabled
- "No Burst" — Burst Mode unavailable
- "Attribute Locked: Fire" — only Fire-attribute parts take effect
- "Speed Run" — par time is 60% of standard

Circuit rewards: Synthesis Cores, Mastery Tokens, exclusive cosmetic parts (visual-only, no stats).

### 8.4 Raids

3-player co-op. Giant enemy boss frame with 24+ breakable sub-zones. 15-minute timer. Shared loot pool — all players get drops from each zone broken (no competition for loot).

Raids are the primary source of:
- Rare Synthesis materials
- Pilot cards
- Exclusive 4★–5★ frame parts with Raid-specific EX Skills

---

## 9. Multiplayer

### 9.1 Bounty Hunt

Async PvP mode. **No ranked ladder. No FPR matchmaking gates.**

Format: Enter a match with your standard frame. Every player has a Bounty value. Defeat another player's frame (AI-piloted clone of their actual build) → absorb their Bounty → yours grows. At end of session, Bounty converts to Circuit Tokens (cosmetic/convenience currency).

**Why no ranked PvP:** GBM's shutdown was precipitated by ranked PvP becoming a pay-to-win whale environment. FrameBreaker's Bounty Hunt keeps PvP stakes low, rewards participation over meta-chasing, and ensures no player is gatekept from competitive content by their wallet.

### 9.2 Co-op Raids

See section 8.4. 3-player matchmaking. Can play with friends or random queue. Commander-tag pilots provide squad-wide bonuses in this mode.

---

## 10. Customization

### 10.1 Paint System

Per-part color customization. Each part has 2–4 independent color channels (primary, secondary, tertiary, trim/detail). Full RGB picker. Preset palettes available (including faction color palettes).

Color settings are saved per-loadout — you can have the same frame painted differently across multiple saved configs.

### 10.2 Decals & Emblems

Apply flat decal stickers to any surface. Scale, rotate, position freely. Up to 20 decals per frame. Emblem editor: layer simple shapes/symbols to create a custom faction insignia.

### 10.3 Builder Parts

Cosmetic attachments — not equipment slots. Freely positionable on any surface. Examples: antenna arrays, extra thrusters, decorative fins, sensor pods, weapon racks. No stat effect. Resize-able. Up to 8 per frame.

LED Parts: builder parts that emit light. Set color independently from the main paint scheme.

### 10.4 Workshop Mode (Diorama)

Stage your frame in scene builder mode:
- Pose any joint (head, torso twist, arm positions, leg stance)
- Place environmental props (rubble, destroyed enemy parts, landscape pieces)
- Add atmospheric effects (smoke, fire, beam trails, Burst aura)
- Set camera angle, focal length, lighting
- Export as in-game screenshot → auto-uploaded to community gallery

Community gallery: searchable by tag, sort by likes, featured weekly. Gallery submissions visible in the main hub.

---

## 11. Monetization Model

**Target:** Premium mobile title (one-time unlock IAP removes ad-optional free tier). No energy timers. No gacha.

### Revenue Streams

| Stream | Type | Notes |
|--------|------|-------|
| Base Unlock | One-time ~$9.99 | Removes ads, unlocks all base content |
| Season Pass | ~$9.99/season | New frame packs, story chapters, cosmetics — NO STATS |
| Cosmetic Bundles | $2.99–$4.99 | Decal packs, shader effects, Builder Part sets |
| Breaker Boosters | IAP pack | Convenience only; earnable through S-rank |
| Pilot Packs | $1.99–$4.99 | Pilots earnable in-game; pack = accelerant only |

**Hard rules:**
1. No part with exclusive stats sold for money
2. No energy or stamina system
3. No PvP content where paid players have a stat advantage over non-paid players
4. All game-changing content (parts, pilots, skills) earnable F2P within reasonable time

---

## 12. Technical Architecture

### Client (Godot 4)
- GDScript for UI, menus, state management
- C# for: physics, combat calculations, part break detection, EX skill system
- GLTF part format — modular skeleton rig per slot, shared attachment points
- Mobile target: Android 10+, iOS 15+, 60fps target on mid-range devices (Snapdragon 7xx / A15)

### Server (Elixir/Phoenix)
- Real-time: LiveView/channels for Raid co-op and Bounty Hunt
- REST API: account management, inventory, leaderboards, gallery
- Background jobs: event scheduling, Circuit rotation, Raid matchmaking queue

### Database
- PostgreSQL: persistent player data (inventory, builds, progress, gallery)
- Redis: session state, matchmaking queues, leaderboard scores

### Asset Pipeline
- Source: Blender (.blend)
- Export: GLTF 2.0 with Draco compression for mobile
- Texture: PBR workflow, 512px per-part textures with shared atlases
- Audio: OGG Vorbis, 48kHz

---

## 13. What We're Fixing (vs. GBM)

| GBM Problem | FrameBreaker Solution |
|-------------|----------------------|
| Whale PvP dominated rankings | No ranked PvP; Bounty Hunt is stakes-free |
| Powercreep via gacha banners | No gacha; all parts earned through gameplay |
| P2W cosmetic pricing (skin = real Gunpla price) | All stats earnable; cosmetics priced fairly |
| Abrupt shutdown with unresolved story | Open source; community can fork/continue |
| Technical performance on old hardware | Godot 4 + GLTF modularity; aggressive LOD on mobile |
| Auto-battle felt passive | Manual hack-and-slash (à la GB3/GB4) |
| Stage design (wave arenas) | Varied map types including traversal stages |
| EX Skill mastery locked to equipped part | 5★M Mastery system decouples skills from aesthetics |

---

## 14. Content Roadmap

### Launch (v1.0)
- 10 Campaign chapters
- 100+ frame types (enough for 1,500+ unique Franken-combos)
- 6 Raid bosses
- Bounty Hunt mode
- Full paint/decal system
- 20 pilots

### Season 1
- 2 new Campaign chapters
- 30+ new frame parts
- 2 new Raid bosses
- Season Pass cosmetics
- New Word Tag: `Phantom` (stealth-focused)

### Season 2
- Tag-battle event mode (same-tag builds only)
- Frame Showroom (community gallery v2 with voting/featured)
- Pilot Awakening system expansion

---

## Appendix A: Attribute Matchup Chart

```
Fire    → beats Wind
Wind    → beats Thunder
Thunder → beats Ice
Ice     → beats Fire
Light   ↔ Dark (mutual amplification: both sides deal +15%)
```

Same attribute: neutral (1.0x)
Disadvantaged: 0.85x
Advantaged: 1.15x

---

## Appendix B: EX Gauge Economy

| Action | EX Gauge Gain |
|--------|--------------|
| Hit (melee) | +0.05 bars |
| Hit (ranged) | +0.03 bars |
| Zone break | +0.5 bars |
| Successful dodge | +0.2 bars |
| EX Skill use (cost is deducted, then trigger bonus) | −X bars cost |
| Taking damage | −0.1 bars |
| Part pickup mid-match | +0.25 bars (OP Skill "Chain Collector") |

---

*Document version 0.1. All values subject to playtesting and balance iteration.*
