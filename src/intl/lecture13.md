# Multi-Dimensional Lists

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture13.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#F37626;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>



A 2-D list of cells. Each is alive (`#`) or dead (`.`). Every step, every
cell looks at its 8 neighbours and follows three rules:

- Alive with 2 or 3 living neighbours → stays alive.
- Alive with anything else → dies.
- Dead with exactly 3 living neighbours → becomes alive.

That is the whole program. No randomness, no AI, nothing else. What can
three rules possibly do?

### Watch this shape

```
step 0        step 1        step 2        step 3        step 4
.#....        ......        ......        ......        ......
..#...        #.#...        ..#...        .#....        ..#...
###...        .##...        #.#...        ..##..        ...#..
......        .#....        .##...        .##...        .###..
```

Step 4 is the same shape as step 0 — moved one square down and one square
right.

**It walks. Nobody wrote "walk."** (This is the classic *glider* from
Conway's Game of Life.)

### Why this is your week

Everything you need is what you are learning right now:

- a **2-D list** to hold the grid
- **nested `for` loops** to visit every cell
- an **`if`** for the three rules
- and **a second grid** — because if you edit the first one while reading
  it, you will be reading cells that have already changed

That last point is this week's real trap, and it is the same trap as
Week 11: do not modify the thing you are walking through.
