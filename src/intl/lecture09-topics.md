# Topics Covered

## Recap: Three `for`-Loop Patterns So Far

- **Max/min** (Week 6) — track a running best value.
- **Counter** (Week 8) — track a running count of elements matching a
  condition.
- **Quantifier** (this week) — "for some" / "for all": does *any*/*every*
  element satisfy a condition?

## The Quantifier Pattern

Given a list, "does `numbers[i] > 0` for **some** `i`?" is an *existential*
question (∃); "for **all** `i`?" is a *universal* one (∀). Both are
naturally boolean functions:

```python
def somePositive(numbers):
    for i in range(len(numbers)):
        if numbers[i] > 0:
            return True
    return False              # never found one
```

```python
def allPositive(numbers):
    for i in range(len(numbers)):
        if not (numbers[i] > 0):   # found a counterexample
            return False
    return True                     # never found a counterexample
```

The shapes are near-mirror images: "for some" returns `True` the instant it
finds a match, and falls through to `False`. "For all" returns `False` the
instant it finds a *counter*example, and falls through to `True`.

This mirroring isn't a coincidence — it's **De Morgan's law** applied to
quantifiers: `not (for all x, p(x))` is the same statement as `for some x,
not p(x)`. So "for all `p(x)`" can always be written as "not (for some `x`,
`not p(x)`)" — which is exactly why the "for all" loop checks `not p(x)`
and returns `False` on a hit.

Two worked examples:

```python
# "for some": is n a sum of two squares?
def sumOfTwoSquares(n):
    b = int(math.sqrt(n))
    for i in range(1, b+1):
        for j in range(1, b+1):
            if n == i*i + j*j:
                return True
    return False

# "for all": is numbers non-decreasing?
def isIncreasingSequence(numbers):
    for i in range(len(numbers)-1):
        if not (numbers[i] <= numbers[i+1]):
            return False
    return True
```

`isPrime` from Week 8 is secretly a "for all" too — "`p` is prime" means
"for all `i` from 2 to `p//2`, `i` does not divide `p`":

```python
def isPrime(p):
    for i in range(2, p//2 + 1):
        if p % i == 0:      # found a divisor — counterexample!
            return False
    return True
```

## Toy Robot: Beepers

A beeper is a small marker the robot can only sense when standing directly
on it. Create a robot carrying some:

```python
hubo = Robot(beepers=3)
```

- `hubo.drop_beeper()` — put one down (needs at least one in pocket)
- `hubo.pick_beeper()` — pick one up (needs one at the current position)
- `hubo.on_beeper()` — `True` if there's a beeper right here
- `hubo.carries_beepers()` — `True` if Hubo is currently holding at least one

Calling `drop_beeper()` with an empty pocket, or `pick_beeper()` on an
empty square, is an error — always guard with the matching boolean
function first:

```python
if hubo.on_beeper():
    hubo.pick_beeper()
else:
    hubo.turn_left()
```

Combine with a loop to sweep an entire row, picking up (or dropping) as you
go:

```python
for i in range(9):
    hubo.move()
    if hubo.on_beeper():
        hubo.pick_beeper()
```
