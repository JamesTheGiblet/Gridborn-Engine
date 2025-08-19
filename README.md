Gridborn Engine

Gridborn Engine is a tactical combat framework for grid-based trail games. Inspired by the elegance of TRON-style mechanics, it enforces spatial discipline, modular extensibility, and deterministic gameplay. Designed for clarity, not complexity.

---

🎯 Design Philosophy

- Small Grid Constraint: All arenas are 8×8 to 16×16. This enforces tactical density, short decision loops, and predictable collision zones.
- Trail-Based Combat: Movement leaves trails. Trails are the primary hazard and strategic tool.
- Modular Vehicles: Vehicles are defined by movement logic, trail behavior, and collision response. No lore, no fluff—just mechanics.

---

🧩 Core Modules

1. Vehicle System

Vehicles are composed of three modules:

| Module         | Description                                      | Example Values             |
|----------------|--------------------------------------------------|----------------------------|
| Movement Logic | How the vehicle moves per tick                   | Orthogonal, Diagonal, Warp |
| Trail Type     | Behavior of the trail left behind                | Solid, Phased, Delayed     |
| Collision Rule | What happens on trail or wall collision          | Explode, Bounce, Phase     |

Phased Trail: Appears intermittently (e.g. every 2 ticks), allowing partial traversal. It alters collision logic and strategic planning.

`rust
trait Vehicle {
  fn tick(&mut self, grid: &mut Grid);
  fn trail_behavior(&self) -> TrailType;
  fn on_collision(&self, other: &TrailType) -> CollisionResult;
}
`

---

2. Arena System

Arenas are defined by:

- Grid Size: 8×8 to 16×16
- Wall Layout: Static or dynamic
- Pickup Zones: Optional modifiers (e.g. speed, trail type)

Example .grid file:

`toml
[arena]
size = "12x12"
walls = ["(3,3)", "(3,4)", "(3,5)"]
pickups = ["speed_boost@5,5"]
`

Rendering is tile-based. Movement is discrete and deterministic.

---

3. Effects System

Effects are triggered by:

- Trail interactions
- Pickup collisions
- Arena triggers

Examples:

- Trail Surge: Temporarily doubles trail length
- Grid Flip: Rotates arena 90° mid-match
- Echo Pulse: Reveals opponent trail for 3 ticks

`rust
trait Effect {
  fn trigger(&self, context: &GameState) -> EffectResult;
}
`

---

4. AI System

Bots operate on a tactical decision tree:

- Scan Grid: Identify safe paths
- Predict Opponent: Estimate next 2 moves
- React: Choose movement that avoids collision and maximizes trail coverage

`rust
fn choose_move(state: &GameState) -> Direction;
`

AI modules are testable in isolation and benchmarked against deterministic scenarios.

---

🛠 Technical Stack

| Component         | Implementation                     |
|-------------------|-------------------------------------|
| Language          | Rust                                |
| Framework         | Bevy (ECS-based game engine)        |
| Multiplayer       | Peer-to-peer over QUIC              |
| Rendering         | Tile-based grid renderer            |
| State Management  | ECS with tick-based updates         |

---

🧪 Known Issues

| Issue                  | Impact Level | Fix Status |
|------------------------|--------------|------------|
| Trail collision bug    | Critical     | In progress |
| AI pathing failure     | High         | Under review |
| Arena rotation glitch  | Medium       | Queued      |

---

🚫 Removed Features

- No hackable lore systems
- No fantasy naming conventions
- No player-side scripting
- No narrative modules

Gridborn Engine is a tactical protocol, not a sandbox. Every mechanic is deterministic, every module is teachable, and every subsystem is designed for clarity.

---

📦 Getting Started

`bash

Clone the repo
git clone https://github.com/gridborn/engine.git
cd engine

Build the project
cargo build --release

Run a test match
cargo run --example duel
`

---

📚 Documentation

- Vehicle Interface Spec
- Arena File Format
- Effect System Overview
- AI Strategy Modules

---

🧠 Contributing

This engine is designed for tactical clarity and modular extension. Contributions should:
- Preserve deterministic behavior
- Avoid aesthetic drift
- Prioritize testability and teachability

Please see CONTRIBUTING.md for guidelines.

---

📄 License

MIT License. See LICENSE.md for details.

`

---
