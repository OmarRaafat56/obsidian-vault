[[Game development]]

Below is a **7-day crash curriculum** designed to take you from **zero → building procedural generation systems in Godot Engine**.
Each day includes:

* 🎯 **Learning goals**
* 📚 **Topics to study**
* 🛠 **Practice tasks**
* 🧪 **Assignments/tests**

Assumes **2–4 hours per day**.

---

# 1-Week Curriculum: Procedural Generation in Godot

---

# Day 1 — Godot + Programming Foundations

🎯 **Goal:**
Understand Godot basics and start writing code in **GDScript**.

📚 Topics

* Installing and navigating Godot Engine
* Nodes and Scenes
* GDScript basics
* Variables and functions
* Loops and conditionals

🛠 Practice

1. Create a **new 2D project**
2. Add a `Node2D`
3. Attach a script
4. Print messages using `print()`

Example:

```gdscript
func _ready():
    for i in range(5):
        print("Hello ", i)
```

🧪 Assignment
Create a script that:

* Prints numbers **1 → 20**
* Prints **"even" or "odd"** next to each number

Example output:

```
1 odd
2 even
3 odd
```

---

# Day 2 — Randomness & Seeds

🎯 **Goal:**
Learn how games generate randomness.

📚 Topics

* Random numbers
* `randf()` and `randi()`
* Random ranges
* Seeds and reproducibility

Key concept: **same seed → same world**

Example:

```gdscript
func _ready():
    randomize()
    print(randi_range(0, 10))
```

🛠 Practice

Generate **10 random positions**:

```gdscript
Vector2(randf_range(0,800), randf_range(0,600))
```

🧪 Assignment

Create a script that:

* Spawns **20 colored squares**
* Places them at **random positions**
* Each run should look different

Bonus challenge:

* Add a **seed variable** so the layout can repeat.

---

# Day 3 — TileMaps & Grid Systems

🎯 **Goal:**
Learn grid-based world generation.

📚 Topics

* TileMap (Godot)
* Coordinates
* 2D arrays
* Grid logic

Concept:

```
0 = empty
1 = wall
```

Example grid:

```
0 1 0
1 0 1
0 0 0
```

🛠 Practice

Generate a **10×10 grid**:

```gdscript
for x in range(10):
    for y in range(10):
        print(x, y)
```

🧪 Assignment

Create a **20×20 tile map generator** that:

* Randomly places **walls (30%)**
* Empty space (70%)

Expected result:
A random dungeon-like grid.

Bonus:

* Print the grid to console.

---

# Day 4 — Noise Functions (Terrain)

🎯 **Goal:**
Learn terrain generation using **noise**.

📚 Topics

* Perlin Noise
* FastNoiseLite
* Height maps
* Threshold values

Example:

```gdscript
var noise = FastNoiseLite.new()

func _ready():
    print(noise.get_noise_2d(10, 20))
```

Noise outputs values:

```
-1 → 1
```

🛠 Practice

Create terrain types:

```
< -0.2 = water
-0.2 to 0.3 = grass
> 0.3 = mountain
```

🧪 Assignment

Generate a **50×50 world map** using noise.

Rules:

* water
* grass
* mountains

Display them using **different tiles or colors**.

Bonus challenge:
Make terrain look **smooth instead of random blobs**.

---

# Day 5 — Procedural Dungeons

🎯 **Goal:**
Generate dungeon layouts.

📚 Topics

* Rooms
* Corridors
* Collision checks
* Room overlap prevention

Basic algorithm:

1. Place random rooms
2. Check overlap
3. Connect rooms with corridors

🛠 Practice

Generate **5 random rectangles** (rooms).

Example structure:

```gdscript
var rooms = []

rooms.append(Rect2(x, y, w, h))
```

🧪 Assignment

Create a dungeon generator that:

* Places **10 rooms**
* Prevents overlapping rooms
* Connects them with corridors

Bonus:
Spawn a **player at the first room**.

---

# Day 6 — Polishing Generation

🎯 **Goal:**
Improve procedural worlds.

📚 Topics

* Deterministic generation
* Seeds
* Parameters
* Regeneration

Add sliders:

```
room count
map size
noise scale
```

🛠 Practice

Add a key:

```
Press R → regenerate world
```

🧪 Assignment

Add **generation settings**:

```
seed
map size
room count
```

World should regenerate when parameters change.

Bonus:
Show the seed on screen.

---

# Day 7 — Final Project

🎯 **Goal:**
Build a **procedural mini-game level**.

Project requirements:

Generate a **playable dungeon level**.

Features:

* Procedural rooms
* Corridors
* Random enemies
* Player spawn
* Exit door

🧪 Final Assignment

Build a generator that produces a **different dungeon every run**.

Minimum:

```
10 rooms
3 enemy spawns
1 exit
player spawn
```

Bonus challenges:

* Loot generation
* Different room sizes
* Enemy difficulty scaling
* Fog of war

---

# Extra Learning Resources

Study examples from games like:

* Minecraft
* No Man's Sky
* Spelunky
* Rogue

These games heavily use **procedural generation**.

---

# Skills You’ll Have After 1 Week

You’ll understand:

✔ GDScript basics
✔ Random generation
✔ Noise algorithms
✔ TileMap generation
✔ Dungeon algorithms
✔ Seeded worlds
