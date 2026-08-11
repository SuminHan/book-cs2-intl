# Problem Set

**1.** Write a function `sumOfThreeSquares` ("for some" pattern) defined by:
- input parameter: a positive integer `n`
- return value: a boolean — `True` if `n` can be written as a sum of squares
  of three positive integers (e.g. \\(38=2^2+3^2+5^2\\), \\(43=3^2+3^2+5^2\\)),
  `False` otherwise
  - *Refer to `sumOfTwoSquares` from this week's lecture.*

```python
def sumOfThreeSquares(n):
    # ADD ADDITIONAL CODE HERE!

    b = int(n**0.5)
    for i in range(1, b+1):
        for j in range(1, b+1):
            for k in range(1, b+1):
                ...

for n in range(20, 31):
    print(n, sumOfThreeSquares(n))
```
Output: `20 False, 21 True, 22 True, 23 False, 24 True, 25 False, 26 True,
27 True, 28 False, 29 True, 30 True`

**2.** Write a function `sumOfThreeDistinctSquares` ("for some" pattern)
defined by:
- input parameter: a positive integer `n`
- return value: a boolean — `True` if `n` can be written as a sum of squares
  of three *distinct* positive integers, `False` otherwise
  - *Use the loop template from `closestPair` (Week 7):*
    `for i in range(1,b+1): for j in range(i+1,b+1): for k in
    range(j+1,b+1): ...`

```python
def sumOfThreeDistinctSquares(n):
    # ADD ADDITIONAL CODE HERE!

for n in range(20, 31):
    print(n, sumOfThreeDistinctSquares(n))
```
Output: `20 False, 21 True, 22 False, 23 False, 24 False, 25 False, 26 True,
27 False, 28 False, 29 True, 30 True`

**3.** Write a function `sumOfTwoPrimes` ("for some" pattern) defined by:
- input parameter: a positive integer `n`
- return value: a boolean — `True` if `n` can be written as a sum of two
  primes (e.g. `21=2+19`, `22=11+11`), `False` otherwise

```python
def isPrime(p):
    for i in range(2, p//2 + 1):
        if p % i == 0:
            return False
    return True

def sumOfTwoPrimes(n):
    # ADD ADDITIONAL CODE HERE!

    for i in range(2, n-1):
        for j in range(2, n-1):
            if isPrime(i) and isPrime(j) and n == i+j:
                ...

for n in range(20, 31):
    print(n, sumOfTwoPrimes(n))
```
Output: `20 True, 21 True, 22 True, 23 False, 24 True, 25 True, 26 True,
27 False, 28 True, 29 False, 30 True`

**4.** Write a function `sumOfTwoPrimeSquares` ("for some" pattern) defined
by:
- input parameter: a positive integer `n`
- return value: a boolean — `True` if `n` can be written as a sum of squares
  of two primes (e.g. `50=5²+5²`, `53=2²+7²`), `False` otherwise

```python
def isPrime(p):
    for i in range(2, p//2 + 1):
        if p % i == 0:
            return False
    return True

def sumOfTwoPrimeSquares(n):
    # ADD ADDITIONAL CODE HERE!

for n in range(50, 61):
    print(n, sumOfTwoPrimeSquares(n))
```
Output: `50 True, 51 False, 52 False, 53 True, 54 False, 55 False, 56 False,
57 False, 58 True, 59 False, 60 False`

**5.** Write functions `somePrime` and `allPrime` ("for some" and "for all"
patterns) defined by:
- input parameter: a list of positive integers
- return value: a boolean — for `somePrime`, `True` if there is a prime in
  the list; for `allPrime`, `True` if every number in the list is prime;
  `False` otherwise

```python
def isPrime(p):
    for i in range(2, p//2 + 1):
        if p % i == 0:
            return False
    return True

# "for some" pattern
def somePrime(numbers):
    # ADD ADDITIONAL CODE HERE!

    for i in range(len(numbers)):
        if isPrime(numbers[i]):
            ...

# "for all" pattern
def allPrime(numbers):
    # ADD ADDITIONAL CODE HERE!

num1 = [217, 287, 143, 163, 319]
num2 = [217, 287, 143, 169, 319]
num3 = [223, 281, 227, 151, 149]
print(somePrime(num1), allPrime(num1))  # True False
print(somePrime(num2), allPrime(num2))  # False False
print(somePrime(num3), allPrime(num3))  # True True
```

**6.** Write a function `allDistinct` ("for all" pattern) defined by:
- input parameter: an integer list `numbers`
- return value: a boolean — `True` if `numbers[0], numbers[1], ...` are all
  distinct, `False` otherwise

```python
def allDistinct(numbers):
    # ADD ADDITIONAL CODE HERE!

    for i in range(len(numbers)):
        for j in range(i+1, len(numbers)):
            ...

print(allDistinct([1,3,2,5,2,1]))  # False
print(allDistinct([1,0,2,5,3,4]))  # True
```

Write a function `allWithinRange` ("for all" pattern) defined by:
- input parameter: an integer list `numbers` and two integers `lower,upper`
- return value: a boolean — `True` if `lower <= numbers[i] <= upper` for
  every `i`, `False` otherwise

```python
def allWithinRange(numbers, lower, upper):
    # ADD ADDITIONAL CODE HERE!

print(allWithinRange([1,0,2,6,3,4], 0, 5))  # False
print(allWithinRange([1,0,2,5,3,4], 0, 5))  # True
```

Using `allDistinct` and `allWithinRange` above, write a function
`isPermutation` defined by (*this is simple — one line is enough!*):
- input parameter: an integer list `numbers`
- return value: a boolean — `True` if `numbers` (length `n`) is a
  permutation (all elements distinct **and** `0 <= numbers[i] <= n-1` for
  every `i`), `False` otherwise

```python
print(isPermutation([1,3,2,5,2,1]))  # False
print(isPermutation([1,0,2,5,3,4]))  # True
print(isPermutation([1,0,2,6,3,4]))  # False
```

**7.** Write a function `walk_square_picking_all_beepers` defined by:
- input parameter: none
- return value: none
- action: make Hubo walk along the world boundary, picking up every beeper
  it stands on
  - *Use the Week 8 boundary-walk code — `for j in range(4): for i in
    range(9): hubo.move(); hubo.turn_left()` — but replace `hubo.move()`
    with `move_and_pick()` below.*

```python
def move_and_pick():
    hubo.move()
    if hubo.on_beeper():
        hubo.pick_beeper()

def walk_square_picking_all_beepers():
    # ADD ADDITIONAL CODE HERE!

walk_square_picking_all_beepers()
```

**8.** Write a function `whirl_picking_all_beepers` defined by:
- input parameter: none
- return value: none
- action: make Hubo visit the entire world (as in Week 8's `whirl` spiral
  pattern), picking up every beeper it stands on
  - *Replace `hubo.move()` with `move_and_pick()` from problem 7.*

```python
def whirl_picking_all_beepers():
    # ADD ADDITIONAL CODE HERE!

whirl_picking_all_beepers()
```

**9.** Write a function `whirl_dropping_beepers` defined by:
- input parameter: none
- return value: none
- action: make Hubo visit the world dropping beepers
  - *Using `L` for "turn left" and a number for "move that many steps
    forward," Hubo's action sequence is: `1 L 2 L 3 L ... 9 L 9`. Replace
    `hubo.move()` with `move_and_drop()` below.*

```python
def move_and_drop():
    hubo.move()
    if hubo.carries_beepers():
        hubo.drop_beeper()

def whirl_dropping_beepers():
    # ADD ADDITIONAL CODE HERE!

whirl_dropping_beepers()
```
