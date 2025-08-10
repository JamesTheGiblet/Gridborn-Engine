# 🕹️ Gridborn Engine

A hackable 8-bit arena for TRON-style games.

### **The Problem**

Most game engines are bloated. I wanted something simple: a tiny, tactical engine for `TRON`-style combat that anyone could hack on over a weekend. Something where the grid is small, the action is tight, and your trail is as much a weapon as your vehicle.

### **What I Built**

Gridborn is that engine. You pilot a vehicle around a small grid, leaving a deadly trail. The last one standing wins. It's built to be modular, so you can easily add your own vehicles, arenas, and rules without asking for permission.

Think `TRON` meets `Advance Wars`, but built for builders.

### **What's In The Box**

  * **Modular Vehicles:** It comes with motorcycles, tanks, and planes, but they're just modules. You can build your own with different movement and trail logic.
  * **Tiny Grids:** Combat happens on small grids (from 8x8 to 16x16). This keeps matches fast and tactical. No room for error.
  * **Your Trail is a Weapon:** Every move you make leaves a solid trail behind you. Use it to trap opponents or get trapped yourself.
  * **Real Obstacles:** Arenas have walls, warp zones, and other junk to keep you on your toes.
  * **Power-ups (and Downs):** Simple pickups that can give you a speed boost or mess with your opponent's controls.
  * **Hackable Lore:** All the "lore" is just in text files. If you don't like it, change it.

### **The Vehicles**

These are the starting classes. They're just examples. Each one is defined by its speed, trail, and job. Fork the repo and build your own.

| Class       | Speed  | Trail Type     | Job       | My Nickname    |
|-------------|--------|----------------|-----------|----------------|
| Motorcycle  | Fast   | Thin, long     | Agile     | Flickerblade   |
| Tank        | Slow   | Thick, short   | Zoner     | Iron Sigil     |
| Plane       | Medium | Air trail      | Flanker   | Skybrand       |
| Spaceship   | Warp   | Phased trail   | Disruptor | Void Sovereign |
| Ship        | Slow   | Wake trail     | Defender  | Tidewarden     |
| Mech Walker | Heavy  | Footstep trail | Bruiser   | Echo Stomp     |

### **Arenas & Power-ups**

  * **Arenas:** Just tilemaps defined by a size, tiles (road, water, etc.), and obstacles (walls, mines). Nothing fancy.
  * **Pickups:** Simple blessings and curses that spawn in the arena. `Sigil Surge` makes you faster, `Graviton Bind` makes you slower. You get the idea.

### **The Guts (Architecture)**

No magic here. The code is the proof. It’s organized so you can find what you need and change it.

```
src/
├── engine/       # Core loop, grid logic, collision (The important part)
├── vehicles/     # Movement modules, trail logic (Make your own here)
├── arena/        # Tilemaps, obstacles, pickups
├── fx/           # Visual and audio effects
├── lore/         # Text files with stories. Or not. Your call.
├── ui/           # HUD, menus, intro text
└── assets/       # Sprites, sounds, glyphs
```

### **Known Issues (What's Still Janky)**

  * The collision detection for `Phased trail` is a bit wonky on corners.
  * The AI for CPU opponents is dumb as a brick. It just tries not to crash.
  * There's no real menu system yet, you just launch straight into a match.

### **How to Get Started**

**Perfect is the imaginary friend of never shipped.** You don't need my permission.

1.  Clone the repo.
2.  Fire up the engine.
3.  Pick a vehicle and a grid size.
4.  Try not to crash.

Fork it, break it, and make something better. **Build first, ask permission never.**
