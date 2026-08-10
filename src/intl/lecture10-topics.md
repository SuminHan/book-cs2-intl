# Topics Covered

## `while` Loops

```python
while boolean_expression:
    statements
```

Repeats the body for as long as the condition stays true — checked *before*
every iteration, including the first. Counting the digits of `n = 713`:

```python
def countDigits(n):
    counter = 0
    while n > 0:
        counter += 1
        n = n // 10
    return counter
```

Trace it: `n=713 → counter=1,n=71 → counter=2,n=7 → counter=3,n=0`, loop
condition now false, return `3`.

## `for` vs. `while`

Any `for` loop can be rewritten as a `while` loop:

```python
for i in range(n):        # becomes:
    total += i             i = 0
                            while i < n:
                                total += i
                                i += 1
```

**Use `for` when you know the number of iterations in advance** (a fixed
range, a list you're walking through). **Use `while`** when you don't —
`countDigits` above has to keep going until `n` reaches `0`, and there's no
way to know ahead of time how many digits `n` has without... counting
them.

## `while True` + `break`

When the loop-continuation condition is awkward to state directly, loop
forever (`while True:`) and `break` out explicitly once some condition is
met inside the body:

```python
while True:
    ...
    if some_condition:
        break     # exit immediately, skip everything after
    ...
```

```python
# equivalent to the countDigits loop above, written with break instead
while True:
    counter += 1
    n = n // 10
    if n == 0:
        break
```

## Toy Robot with `while`

Some robot tasks don't have a fixed number of steps, which is exactly the
`for`-can't-do-it case. "Pick up beepers here, however many there are":

```python
while hubo.on_beeper():
    hubo.pick_beeper()
```

"Drop every beeper Hubo is carrying, walking forward after each":

```python
hubo = Robot(beepers=50)
while hubo.carries_beepers():
    hubo.drop_beeper()
    hubo.move()
```

If the condition is already false before the first check — e.g. Hubo was
created with zero beepers — the loop body never runs at all, not even
once. That's different from a `for` loop over a nonempty range, and worth
double-checking when a `while` loop "does nothing."

Composing two `while` loops handles "walk until you reach a pile of
beepers, then pick them all up":

```python
while not hubo.on_beeper():
    hubo.move()
while hubo.on_beeper():
    hubo.pick_beeper()
```
