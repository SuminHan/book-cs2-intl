# Classes & Objects

## Opener: Every Student Has Their Own Scores

```python
class Student:
    scores = []

    def __init__(self, name):
        self.name = name

    def add(self, s):
        self.scores.append(s)

a = Student("Alice");  a.add(90)
b = Student("Bob");    b.add(80)
print(a.name, a.scores, "|", b.name, b.scores)
```

Expected: `Alice [90] | Bob [80]`

### They are sharing one list

```
Alice [90, 80] | Bob [90, 80]
```

`scores = []` sits directly under `class`, so it is made once, for the
class itself — not once per student. Alice and Bob are appending to the
same list.

```python
# Correct -- give each object its own
    def __init__(self, name):
        self.name = name
        self.scores = []      # made per student
```

### The question that settles it

Notice that `self.name` was fine all along. Only `scores` misbehaved —
because it was created in a different place.

**For every attribute, ask:** "Is there *one* of these for the whole
class, or *one per object*?" One per object → it belongs inside
`__init__`, with `self.`

*Once again: no error message. Just two students quietly sharing a report card.*

## Topics Covered

- Object-oriented basics: every value is an object belonging to a class
- `__init__()`, `__str__()`, `self`
- Attributes, getters/setters
- Using objects as parameters and return values
- Pure functions vs. modifier functions

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*

## Problem Set

**1. `Circle` class** — a circle with a `Point` center (assume a `Point`
class already exists) and integer radius.
- `__init__(self, c, r)` — store `center`, `radius`
- `__str__(self)` — `"(center,radius)"`, e.g. `"((0,1), 5)"`
- `area(self)` — using `math.pi`
- `getRadius(self)` / `getCenter(self)`
- `setRadius(self, r)`
- `moveTo(self, x, y)` — move center to `(x,y)`
- `move(self, dx, dy)` — move center by `(dx,dy)`

**2. `Rational` class** — a rational number (numerator/denominator).
- `__init__(self, n, d)`
- `__str__(self)` — `"numerator/denominator"`, e.g. `"7/24"`
- `toFloat(self)`
- `negate(self)` — flip sign (of the numerator)
- `invert(self)` — swap numerator/denominator
- `reduce(self)` — simplify via GCD (e.g. `4/8` → `1/2`)
- `add(self, r)` — **pure function**: return a new `Rational` sum, reduced;
  `self` and `r` unchanged
- `mul(self, r)` — **pure function**: return a new `Rational` product,
  reduced; `self` and `r` unchanged

(This is the same pair of classes as the Korean track's L08 problem set —
see there for full worked test cases if useful.)

---
*Source: 2025 offering, `week15_Class_problem.pdf`. Wording condensed; code
stubs kept close to the original.*
