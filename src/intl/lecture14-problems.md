# Problem Set

**1. Class `Circle`.** Create a class `Circle` that represents a circle in
a two-dimensional coordinate system, and implement the methods below.
Assume a `Point` class already exists (`from point import Point` or
similar) — a circle's center is represented as a `Point` object.

**(1-1) `__init__`** — define the constructor so a `Circle` object can be
created. The basic information needed is a center point and a radius.
- Parameters: `self`, `c` (a `Point` object, the center), `r` (an integer,
  the radius)
- Return value: `None`

**(1-2) `__str__`** — return a string representation of the circle, in the
format `"(center_coordinates, radius)"`, e.g. `"((0,1), 5)"`.
- Parameters: `self`
- Return value: a string in the above format

**(1-3) `area`** — return the area of the circle. Use `math.pi` for
\\(\pi\\).
- Parameters: `self`
- Return value: the area of the circle

**(1-4) `getRadius`** — return the radius of the circle.
- Parameters: `self`
- Return value: the radius of the circle

**(1-5) `getCenter`** — return the center point of the circle as a `Point`
object.
- Parameters: `self`
- Return value: a `Point` object representing the center

**(1-6) `setRadius`** — set the radius of the circle to a new value.
- Parameters: `self`, `r` (the new radius)
- Return value: `None`

**(1-7) `moveTo`** — move the circle so its center is at the given `(x,y)`
coordinates.
- Parameters: `self`, `x`, `y` (integers, the new center coordinates)
- Return value: `None`

**(1-8) `move`** — move the circle by `(dx,dy)` relative to its current
position.
- Parameters: `self`, `dx`, `dy` (the distances to move along the x-axis
  and y-axis)
- Return value: `None`

```python
class Circle:
    def __init__(self, c, r):
        # ADD ADDITIONAL CODE HERE!

    def __str__(self):
        # ADD ADDITIONAL CODE HERE!

    def area(self):
        # ADD ADDITIONAL CODE HERE!

    def getRadius(self):
        # ADD ADDITIONAL CODE HERE!

    def getCenter(self):
        # ADD ADDITIONAL CODE HERE!

    def setRadius(self, r):
        # ADD ADDITIONAL CODE HERE!

    def moveTo(self, x, y):
        # ADD ADDITIONAL CODE HERE!

    def move(self, dx, dy):
        # ADD ADDITIONAL CODE HERE!
```

**2. Class `Rational`.** A rational number represents the ratio between two
integers: in `2/3`, `2` is the numerator and `3` the denominator (an
integer such as `7` is also rational, with denominator `1`). Define a class
`Rational` and implement the methods below.

**(2-1) `__init__`** — define the constructor so a `Rational` object can be
created, from a numerator and a denominator (both integers).
- Parameters: `self`, `n` (numerator), `d` (denominator)
- Return value: `None`

**(2-2) `__str__`** — return a string representation, in the form
`"numerator/denominator"`, e.g. `"7/24"`.
- Parameters: `self`
- Return value: a string

**(2-3) `toFloat`** — convert the rational number to a float value.
- Parameters: `self`
- Return value: a float (e.g. `0.2916666...`)

**(2-4) `negate`** — reverse the sign of the rational number, by changing
the sign of the numerator.
- Parameters: `self`
- Return value: `None`

**(2-5) `invert`** — swap the numerator and denominator.
- Parameters: `self`
- Return value: `None`

**(2-6) `reduce`** — reduce the rational number to its simplest form using
the greatest common divisor (e.g. `4/8`, `2/4`, and `1/2` are all
equivalent and should be reduced to `1/2`). You may use a `gcd()`
function.
- Parameters: `self`
- Return value: `None`

**(2-7) `add`** — add two rational numbers and return the result as a new
`Rational` object, reduced to simplest form. **This method should be
pure** — `self` and `r` remain unchanged.
- Parameters: `self`, `r` (another `Rational` object)
- Return value: a new `Rational` object representing the sum

**(2-8) `mul`** — multiply two rational numbers and return the result as a
new `Rational` object, reduced to simplest form. **This method should be
pure** — `self` and `r` remain unchanged.
- Parameters: `self`, `r` (another `Rational` object)
- Return value: a new `Rational` object representing the product

```python
class Rational:
    def __init__(self, n, d):
        # ADD ADDITIONAL CODE HERE!

    def __str__(self):
        # ADD ADDITIONAL CODE HERE!

    def toFloat(self):
        # ADD ADDITIONAL CODE HERE!

    def negate(self):
        # ADD ADDITIONAL CODE HERE!

    def invert(self):
        # ADD ADDITIONAL CODE HERE!

    def reduce(self):
        # ADD ADDITIONAL CODE HERE!

    def add(self, r):
        # ADD ADDITIONAL CODE HERE!

    def mul(self, r):
        # ADD ADDITIONAL CODE HERE!
```

*(This is the same pair of classes as the Korean track's Week 8 problem
set — see there for full worked test cases if useful.)*
