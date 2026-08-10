# Topics Covered

## Classes and Objects

Python is object-oriented: every piece of data — `123`, `"hello"`, `[1,2,3]`
— is an **object** belonging to a **class** (`int`, `str`, `list`
respectively). A class is a blueprint; an object is one specific instance
built from it. Analogy: the Sonata *blueprint* specifies an engine, a
color, an efficiency rating, and behaviors like accelerating and braking —
*your* Sonata is one object built from that blueprint, with its own
specific attribute values, that can perform the behaviors the blueprint
defines.

You can define your own classes:

```python
class Point:                      # class name, capitalized by convention
    def __init__(self, px, py):
        self.x = px                # attribute
        self.y = py

p1 = Point(1, 2)
p2 = Point(4, 6)
```

## `__init__` and `self`

`__init__` is the **constructor** — it runs automatically whenever you
create a new object (`Point(1, 2)` calls it). Every method's first
parameter is, by convention, `self` — it refers to *this* object, and
Python passes it automatically; you never write it explicitly at the call
site. `self.x`, `self.y` are **state variables** (attributes): data that
belongs to this specific object, distinct from any local variable of the
same name inside a method that isn't written as `self.something`.

## `__str__`

By default, `print`ing an object shows you a memory address — not useful.
Defining `__str__` tells Python how to turn the object into a readable
string; it's called automatically whenever the object is printed:

```python
def __str__(self):
    return "(" + str(self.x) + "," + str(self.y) + ")"

print(p1)   # (1,2)
```

## Getters and Setters

You *can* read/write `p1.x` directly, but the convention is to go through
**getter**/**setter** methods instead:

```python
def getX(self):
    return self.x
def setX(self, v):
    self.x = v

p1 = Point(1, 2)
print(p1.getX())    # 1
p1.setX(5)
print(p1)             # (5,2)
```

(`setX`, like any function without an explicit `return`, gives back `None`
— printing its result directly is a bug, not a way to see the new value.)

## Methods That Take Another Object as a Parameter

A method's parameters can themselves be objects of the same class:

```python
def distance(self, p):
    dx = self.x - p.x
    dy = self.y - p.y
    return (dx**2 + dy**2)**0.5

print(p1.distance(p2))   # 5.0
print(p2.distance(p1))   # 5.0 — symmetric, as expected
```

## Pure Functions vs. Modifiers

A **pure function** leaves the object unchanged and returns a new result.
`add` below builds and returns a brand-new `Point` — `p1` and `p2` are
untouched:

```python
def add(self, p):
    x = self.x + p.x
    y = self.y + p.y
    return Point(x, y)

p3 = p1.add(p2)
print(p1)   # (1,2) — unchanged
print(p2)   # (4,6) — unchanged
print(p3)   # (5,8) — the new object
```

A **modifier** does the opposite: it changes `self` in place and returns
`None`:

```python
def add_as_modifier(self, p):
    self.x = self.x + p.x
    self.y = self.y + p.y

p3 = p1.add_as_modifier(p2)
print(p3)   # None — modifiers don't return the new state
print(p1)   # (5,8) — p1 itself changed
```

Know, for every method you write, which one it is — and say so in how you
use it: call a pure function for its return value, call a modifier for its
side effect, never both at once.

## Putting a Class Under Test

A common pattern: keep a `..._main()` function with your test/demo calls,
and only run it when the file is executed directly (not when it's
imported):

```python
def point_main():
    p1 = Point(1, 2)
    p2 = Point(4, 6)
    print(p1, p2)
    print(p1.distance(p2))
    p3 = p1.add(p2)
    print(p3)

if __name__ == '__main__':
    point_main()
```
