# Topics Covered

## Creating a 2D List

A 2D list is a list of lists — directly:

```python
table = [[1,2,3], [4,5,6]]
table[0]        # [1, 2, 3]  — the first row
table[0][0]     # 1          — the first element of that row
```

Or built up with nested loops, using a **list comprehension** to create the
row structure first, then filling it in:

```python
height, width = 2, 3
table = [[None] * width for i in range(height)]   # height rows of width Nones
for i in range(height):
    for j in range(width):
        table[i][j] = i*3 + j + 1
print(table)
```

A 3D list nests one level further — depth × height × width:

```python
depth, height, width = 2, 3, 4
table = [[[None] * width for j in range(height)] for i in range(depth)]
for i in range(depth):
    for j in range(height):
        for k in range(width):
            table[i][j][k] = i*10 + j*4 + k
```

## References, Not Data — Aliases

**In Python, a variable holding a list doesn't hold the list's data
directly — it holds a reference to it.** This matters the moment you assign
a *sublist* to another variable:

```python
nation = [["Korea", "Seoul"], ["USA", "Washington"], ["China", "Beijing"]]
a = nation[0]     # a now refers to the SAME inner list as nation[0]
a[1] = "Busan"
print(nation)     # [["Korea", "Busan"], ["USA", "Washington"], ["China", "Beijing"]]
```

`a` is not a copy — it's another name (an **alias**) for the exact same
list object `nation[0]` already pointed to. Modifying `a` modifies
`nation[0]` too, because there was only ever one list in memory. This is
the same reason `int`/`float`/`str` (immutable — reassigning makes a new
value) behave differently from `list` (mutable — modifying in place
affects every alias).

## Copying a Multi-Dimensional List — Three Ways, Not Equivalent

```python
import copy
a = [[1, 2], [3, 4], [5, 6]]
b = a                     # alias — b IS a, same object
c = a[:]                  # shallow copy — new outer list, but inner lists still shared
d = copy.deepcopy(a)      # deep copy — fully independent, all levels

a[1][1] = 40
print(a)   # [[1, 2], [3, 40], [5, 6]]
print(b)   # [[1, 2], [3, 40], [5, 6]]   — b changed too, it's the same object
print(c)   # [[1, 2], [3, 40], [5, 6]]   — c changed too! the inner lists are shared
print(d)   # [[1, 2], [3, 4], [5, 6]]    — d is untouched
```

`b = a` shares everything. `c = a[:]` (slicing) copies the *outer* list —
`c` and `a` are different list objects — but each element of `c` is still
the same inner-list object as in `a`, so a mutation through `a[1][1]`
shows up in `c` too. Only `copy.deepcopy(a)` copies every level, giving you
a result that's fully independent of the original. When you need a true,
independent copy of a nested list, `deepcopy` is the only one of the three
that actually gives you one.
