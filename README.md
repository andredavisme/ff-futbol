# Field Frame ⚽

A browser-based soccer physics arena game with real-time collision, obstacle navigation, session tracking, and a global leaderboard — powered by a Canvas physics engine and Supabase.

🎮 **[Play Field Frame →](https://andredavisme.github.io/ff-futbol/)**

> *Find out what happens after the players leave the field — play **[The Thread: Prospect Run](https://andredavisme.github.io/the-thread-prospect-run/)**, a sales intelligence game set in the world beyond the pitch.*

---

## Player Manual

### Objective

Score points within a **3-minute match** by sending the pink target ball or your own avatar through the **center goal** at the top of the field. Chain goals across multiple matches to climb the global bracket tiers.

| Action | Points |
|---|---|
| Target ball through goal | **3 pts** |
| Player avatar through goal | **1 pt** |

---

### Controls

| Key | Action |
|---|---|
| `↑` Arrow | Accelerate forward |
| `↓` Arrow | Reverse (half power) |
| `←` `→` Arrows | Rotate left / right |
| `Space` | **Boost** — burst impulse in facing direction |
| `Right Ctrl` | **Brake** — rapid deceleration |
| `P` | Pause / Resume |

> **Tip:** Hold `Space` repeatedly for sustained high speed. Boost speed is uncapped — use it to send the target flying toward the goal.

---

### Scoring the Target

- Drive your avatar into the **pink ball** to kick it. Faster hits and boost-assisted strikes launch the ball with significantly more force and a natural upward arc.
- You must send the ball fully through the **green goal opening** at the top-center of the field.
- After a goal, the ball respawns near the center with a short cooldown before scoring re-arms.

### Scoring with Your Avatar

- Navigate your avatar through the same **center goal opening** at the top.
- You respawn at the lower portion of the field after ~1.5 seconds.

---

### The Field

```
┌──────────┤ GOAL ├──────────┐
│                            │
│     [Obstacle zone]        │
│                            │
│       ● Target ball        │
│                            │
│     ▷ Your avatar          │
│                            │
└────────────────────────────┘
```

- **Walls** — left, right, and bottom are solid. The top wall has a single center gap: the goal.
- **Obstacles** — 3–6 randomly placed blocks appear each match in the upper-mid zone. The target bounces off them with lively deflections; use them to set up bank shots.
- **Avatar spawn** — you always start in the lower portion of the field, below all obstacles and the target spawn area.

---

### Physics

| Interaction | Behavior |
|---|---|
| Target vs walls | High restitution bounce + slight random lateral deflection |
| Target vs obstacles | Elastic bounce + small randomized nudge for unpredictability |
| Target vs player | Full mass-weighted elastic collision + kick launch bonus |
| Player vs walls | Medium restitution bounce |
| Player vs obstacles | Medium restitution bounce |

Wall and obstacle hits on the target produce a brief **white glow flash**. A direct player-to-target kick spawns **spark particles** at the contact point.

---

### Sessions & Leaderboard

- When you start a game you are assigned a **Session ID** (UUID). Save it — you can resume the same session later to keep accumulating lifetime points.
- Points from every match in a session add to your **Lifetime Points** total on the global leaderboard.
- To resume a session, click **↩ Resume Session** in the header and paste your saved UUID.

#### Bracket Tiers

| Tier | Label |
|---|---|
| 🥇 Pot 1 | Elite |
| 🔵 Pot 2 | Contender |
| 🟢 Pot 3 | Challenger |
| ⚪ Pot 4 | Rising |

Tier placement is based on **lifetime points** across all sessions under your display name.

---

### Tips & Strategy

- **Angle first, then boost** — rotate to face the goal before boosting for the most direct kick trajectory.
- **Use obstacles** — a well-placed bank shot off an obstacle can redirect the ball straight into the goal without needing a clean approach.
- **Boost kicks hit harder** — the kick launch bonus scales with your speed, so a full-boost contact sends the ball much faster toward the goal.
- **Player exits are free points** — if you're already lined up with the goal, don't hesitate to fly through it for the bonus point.
- **Watch your cooldowns** — the Boost has a small cooldown between bursts to prevent spam; time your approach accordingly.

---

## Tech Stack

- **Frontend:** Vanilla HTML/CSS/JS — single-file Canvas game, no build step
- **Physics:** Custom 2D rigid-body engine (elastic collisions, COR, mass-weighted impulse)
- **Backend:** [Supabase](https://supabase.com) — PostgreSQL for player records, sessions, match results, and leaderboard view
- **Hosting:** GitHub Pages

---

*Built by [Andre Davis](https://github.com/andredavisme)*
