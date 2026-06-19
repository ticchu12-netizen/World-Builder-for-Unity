# World Builder

A Unity tool that builds game areas for you. You bring your own 3D models, drop them into slots, draw a layout or pick a preset, and hit Generate. It places trees, paths, rocks, landmarks, and full set-pieces like boss arenas, all following good level-design rules so the area actually feels fun to explore.

It works with any art style and any theme. Forest, beach, volcano, dungeon, whatever you are making. The tool does not come with art. It comes with simple colored shapes so you can see it working right away, and then you swap in your own models.

---

## Quick start (5 minutes)

1. Open the tool: top menu, **Tools > World Builder > Open**.
2. Click **Create Example Prefabs**. This makes a set of simple colored shapes so the tool has something to place.
3. Click **Spawn Preset Layout**. This drops a ready-made layout into your scene.
4. Click **GENERATE**.

That is it. You now have a generated area made of colored placeholder shapes. Move the camera around and look at it. Once you are happy with how it works, you swap the shapes for your real models (see "Using your own art" below).

> Tip: keep the area small while you are testing. Set **Map Half Width** and **Map Half Length** to around 20 to 30, keep **Density** low (0.1 to 0.2), and leave **Add Colliders** off. Generating is faster and lighter that way. Turn things up once you like the result.

---

## The most important tip

When you add your own models, use the **model prefab** that Unity creates when you import a file, the one with the blue box icon. Do **not** make prefab variants of your models and use those. Variants cause heavy slowdown when the tool places hundreds of them. The plain blue-box model prefab is the right thing to drag in.

If the tool ever gets slow or laggy when generating, this is almost always the reason.

---

## Using your own art

The tool reads your models from a **Biome**. A Biome is just a container that holds your prefabs, sorted into slots like "tall plants," "path tiles," "rocks," and so on.

1. After you click **Create Example Prefabs**, an example Biome is created and selected for you.
2. To use your own models, click **Select Biome Asset** (or find the Biome in your Project window and click it).
3. In the Inspector you will see a list of **Slots**. Each slot is a category. Open a slot and drag your matching models into it. For example, drag your tree models into **TallVegetation**, your path tiles into **PathTile**, your rocks into **ScatterDetail**.
4. Go back to the tool and click **GENERATE**. It now uses your models instead of the shapes.

You can put as many models as you want in each slot. The tool picks from them at random so the area has variety instead of the same tree everywhere.

If you want a clean start, make a fresh Biome: right-click in your Project, **Create > World Builder > Biome Definition**. Fill its slots with your art and drop it into the tool's **Active Biome** field.

### What each slot is for

- **TallVegetation**: your big upright things. Trees, palms, tall rocks.
- **MidVegetation**: medium things. Bushes, shrubs.
- **GroundCover**: small ground plants. Grass tufts, ferns, plants you walk over.
- **ScatterDetail**: small clutter. Rocks, logs, debris.
- **Flowers**: colorful accent plants that get placed around the edges of clearings.
- **Boundary**: the wall pieces that ring the whole area. Cliffs, big rocks, fences.
- **Landmark**: tall standout objects. These mark each area so players can navigate by them.
- **PathTile**: the tiles your paths are made of. Dirt, stone, sand.
- **Platform**: raised ground pieces, used as hills and sightline blockers.
- **Treasure**: chests and pickups.
- **Prop**: extra decoration. Pots, crates, signs.
- **Fence**: optional barriers placed along the sides of paths.
- **Candle**: optional small accents placed at the entrances of areas.
- **Enemy**: optional enemy prefabs that get placed at spawn points.

You do not have to fill every slot. Empty slots are simply skipped. The only two you really need to get started are **TallVegetation** and **PathTile**.

---

## Designing your layout

There are three ways to lay out an area. You can mix them.

### 1. Presets (fastest)

Pick a preset from the dropdown and click **Spawn Preset Layout**. You get a ready-made arrangement of areas and connections. Good starting points:

- **SmallTest**: a tiny layout for trying things out.
- **LinearJourney**: a path from start to a boss at the end, with a treasure off to the side.
- **HubAndSpokes**: a central area with branches going out.
- **SprawlingLoops**: a big interconnected layout with loops and dead-ends.

After spawning a preset, you can drag the nodes around in the scene to fit your ground.

### 2. Scene nodes (hands-on)

A **node** is a point that marks an area, like "boss arena here" or "treasure here." Each node is a small object you place in your scene.

- Drag nodes around to position your areas.
- Select a node to set its type (Hub, Boss, Treasure, and so on), its size (radius), and what it connects to.
- The tool draws paths between connected nodes automatically.

### 3. The Tracer (draw it yourself)

Open the Tracer: **Tools > World Builder > Tracer**, or click **Open Tracer** in the main window. It gives you a top-down canvas with two modes.

**Draw Paths mode:** draw your paths as clean shapes.

- Tools: Line, Freehand, Circle, Ring, Rectangle, Polygon, Arc.
- Click and drag to draw. Your drawn paths turn into real tiled paths when you generate.
- Turn on **Fenced** before drawing if you want that path to have fences.
- Middle-mouse or Alt+drag to pan. Scroll to zoom.

**Place Nodes mode:** drop your areas onto the canvas.

- Pick a type and radius, then click to place a node.
- Click a node to select it, drag to move it.
- Turn on **Snap to Paths** to make nodes snap neatly onto the paths you drew.

Both the drawn paths and the node connections generate together, so you can draw a custom road and still use auto-connected nodes.

---

## Structure templates (boss arenas and more)

A **structure template** turns a single node into a full set-piece. Instead of just placing one object, it assembles a whole scene from parts you choose: a floor, walls, columns, a gate, stairs, and so on.

There are four kinds:

- **Boss Arena**: a walled circular arena with a floor, columns, a gate facing the path, stairs, a center piece where the boss stands, braziers, banners, and rubble.
- **Treasure Room**: a smaller walled nook with a chest on a pedestal.
- **Dungeon Entrance**: an open facade with a door, frame, stairs, and statues.
- **Shrine**: an open decorative spot with a pedestal, an idol, ring stones, and candles.

### Trying them with placeholders

In the main window, click any of the **Create Example** buttons (Boss Arena, Treasure Room, Dungeon Entrance, Shrine). Each one builds placeholder pieces and attaches the template to the matching nodes in your scene. Then click **GENERATE** to see it.

### Using your own pieces

1. Find the template asset in your Project (in the Examples/Arena folder) and click it.
2. In the Inspector you will see slots like Floor, Walls, Columns, Gate. Drag your models into each one.
3. Each slot has a Scale and a Y Offset so you can adjust how big each piece is and how high it sits.
4. The shape settings (wall count, entrance gap, column count) let you change the overall look without touching any models.

To make a fresh template: right-click in your Project, **Create > World Builder > Structure Template**, set its Kind, and fill the slots. Then drag it onto a node's **Structure Template** field.

The entrance always faces the path the player walks in from, so paths lead to the door, not through a wall.

---

## Fences and candles

- **Fences** get placed along the sides of paths. Turn them on globally in the main window, or per-path in the Tracer, or per-node with the "Fence All My Paths" checkbox. Fences are turned to run along the path. If your fence model faces the wrong way, set **Fence Yaw Offset** on the Biome to 90.
- **Candles** get placed at the entrances of areas. Turn them on in the main window.

---

## Settings worth knowing

- **Map Half Width / Map Half Length**: the size of your area. Half width 100 means the area is 200 wide. Your ground needs to cover this, centered on the world origin.
- **Density**: how packed with objects the area is. Start low.
- **Scatter Budget**: a hard cap on how many scattered objects get placed. A safety limit so generating cannot run away and freeze.
- **Path Width** and **Path Tile Spacing**: how wide paths are and how many tiles they use. Wider spacing means fewer tiles, which is faster on big maps.
- **Add Colliders**: off by default so you can preview quickly. Turn on when you want collision.
- **Showcase Scale**: multipliers to make landmarks, structures, fences, or everything bigger. Handy for screenshots and videos.

Your settings are saved automatically, so they stick around after you close the window.

---

## If something goes wrong

- **The tool is slow or freezes when generating.** You are probably using prefab variants instead of the plain model prefabs. Use the blue-box model prefabs. Also try a smaller map, lower density, and a higher Path Tile Spacing.
- **Models show up bright purple.** That is a material problem, not the tool. Your models are using a material that does not match your render pipeline. Use **Edit > Rendering > Materials > Convert** to fix Built-in materials for URP.
- **Objects float or sink.** Check that your model's pivot point is at its base, not its center.
- **Nothing generates.** Make sure you have a Biome assigned (or click Create Example Prefabs), and that you have at least one node in the scene (spawn a preset or place one in the Tracer).

---

## Need starter art?

If you do not have models yet, there is a separate prompt file you can paste into an AI to generate a full matching set. See **ASSET_PROMPT.md**.

---

Made for indie devs. Free to use. If it helped, a mention is always nice.
