# Problem Set

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
