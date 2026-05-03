# 🌟 Neon Tree Generator

*Recursive fractal tree generator. Adjust branch angle, length decay, recursion depth, branchiness (2–4), base thickness, color hue/hue-shift, animation speed. Watch neon trees grow branch by branch. Randomize for infinite patterns. Meditative generative art toy.*

---

## What is this?

A fractal tree generator that draws glowing neon trees using recursive branching. Each branch splits into multiple child branches at specified angles, with length decay per level. The tree grows in real time — watch each branch extend before splitting. Adjust every parameter: branch spread angle, how much shorter each generation becomes, recursion depth, number of splits per node (2, 3, or 4), trunk thickness, base hue, hue shift per depth, and animation speed. Hit Random to discover surprising forms. It's part math toy, part art generator, part screensaver.

---

## Features

- **Recursive branching** — classic fractal tree algorithm
- **Real-time animated growth** — branches extend before sprouting children
- **Fully adjustable parameters:**
  - Branch Angle (5°–90°) — spread of child branches
  - Length Decay (0.3–0.85) — multiplier for child branch length
  - Recursion Depth (4–13) — number of branching generations
  - Branchiness (2–4) — how many children per branch
  - Base Thickness (4–25 px) — trunk width
  - Start Hue (0–360) — base color
  - Hue Shift (0–90) — color shift per depth level
  - Animation Speed (0.5–3×)
- **Randomize** — generates random parameter set
- **Grow** — restart animation with current parameters
- **Stats** — branch count, FPS
- **Single HTML file** — no dependencies

---

## How to Use

1. Open `index.html`
2. Adjust sliders to change the tree's structure:
   - **Branch Angle** — wider angle = more open, fan-like trees; narrow = spindly
   - **Length Decay** — higher = shorter branches; lower = longer sprawling limbs
   - **Depth** — more depth = exponentially more branches (and slower)
   - **Branchiness** — 2 = binary tree, 3 = trident style, 4 = dense bush
   - **Thickness** — trunk/branch line width
   - **Hue** — starting color
   - **Hue Shift** — how much color changes per level (creates gradients)
   - **Speed** — growth animation speed
3. Click **Grow** to animate a new tree
4. Click **Random** to randomize all parameters and grow
5. Watch the branch count climb as the tree fills the screen

---

## Technical Notes

- Each branch is an object storing start point, length, angle, depth, thickness, hue, and animation progress
- Growth updates: `progress += speed * 0.02 * (1 - depth * 0.05)` — deeper branches grow slower
- When a branch completes (`progress >= 1`), it spawns `split` children with:
  - New angle = parent angle ± offset (or symmetric offsets for 3/4 splits)
  - New length = parent length × decay
  - New position = tip of parent
  - New depth = parent depth + 1
  - New hue = (parent hue + hueShift) mod 360
- Rendering: full canvas redraw each frame (`ctx.fillRect` black clear) then draw all branches at current progress
- Glow: `ctx.shadowBlur = 10` with `shadowColor` matching stroke color
- Performance: branch count grows exponentially with depth; depth 11 with split=3 can reach tens of thousands of branches, still fine on modern canvas

---

## The Real Story

Fractal trees are a classic demo scene motif. There's something deeply satisfying about the recursive self-similarity — a branch grows, then sprouts smaller branches that grow just like their parent, only smaller. Watching it animate branch-by-branch is weirdly therapeutic. The neon glow makes it feel like a cybernetic organism. Randomize often: you'll get everything from palm-tree-like shapes to crystalline structures to chaotic scribbles.

No goal. Just grow something pretty.

---

*Made with ✨ and a lot of recursive functions during a heartbeat build cycle.*

**Repo:** https://github.com/Kiloooai/neon-tree-generator
