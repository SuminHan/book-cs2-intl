# Topics Covered

## The Counter Pattern

Given a set (a list), count how many elements satisfy some condition — i.e.
the size of `{x in numbers | condition(x)}`. This is the **counter**
pattern: a running total, incremented once per element that qualifies.

```python
def countOdd(numbers):
    counter = 0
    for i in range(len(numbers)):
        if numbers[i] % 2 == 1:
            counter += 1
    return counter

num = [1, 7, 2, 4, 2, 3, 7, 4, 5]
print(countOdd(num))   # 5
```

The condition can be as simple as equality...

```python
def countNumber(numbers, k):
    counter = 0
    for i in range(len(numbers)):
        if numbers[i] == k:
            counter += 1
    return counter
```

...or arbitrarily complex — in which case, wrap it in a **boolean
function** (Week 5) rather than inlining it, so the loop stays readable:

```python
def isPrime(p):
    for i in range(2, p//2 + 1):
        if p % i == 0:
            return False
    return True

def countPrime(numbers):
    counter = 0
    for i in range(len(numbers)):
        if isPrime(numbers[i]):
            counter += 1
    return counter
```

(`isPrime` itself is an instance of a "for all" pattern — checking that
*no* divisor works — which next week covers in depth.)

## Toy Robot

The course uses a small robot simulator (`cs1robots`) to practice loops
and nesting on something visual. After `from cs1robots import *` and
`create_world()`, a robot appears in a grid world:

```python
from cs1robots import *
create_world()
hubo = Robot()
```

Three basic moves:

```python
hubo.move()          # one step forward
hubo.turn_left()      # turn 90° counterclockwise in place
hubo.turn_right()     # turn 90° clockwise in place
```

`hubo.set_trace("blue")` draws the path it takes; `hubo.set_pause(0.5)`
adds a delay (in seconds) after each move, so you can actually watch it
move instead of jumping straight to the end state.

Everything from here is composing those three moves with `for` loops.
Walking one edge of a square and turning at each corner:

```python
def move_square():
    for i in range(4):
        hubo.move()
        hubo.turn_left()
```

Nested loops sweep the whole grid — an outer loop for each row, an inner
loop that walks across it, with a turn at the end of each row:

```python
for j in range(4):
    for i in range(9):
        hubo.move()
    hubo.turn_left()
```

"Climbing stairs" (alternating a vertical and a horizontal move) is the
same idea with a `turn_left()`/`turn_right()` pair around each move instead
of one long straight run — trace it step by step on paper before you trust
your code to get the corners right.
