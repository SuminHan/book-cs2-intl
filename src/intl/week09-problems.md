# Problem Set

**1. `sumOfThreeSquares(n)`** ("for some" pattern) — can `n` be written as
the sum of squares of three positive integers? (e.g. \\(38=2^2+3^2+5^2\\))
```python
for n in range(20, 31):
    print(n, sumOfThreeSquares(n))
# 20 False  21 True  22 True  23 False  24 True ...
```

**2. `sumOfThreeDistinctSquares(n)`** — same, but the three integers must be
distinct.
> Loop template: `for i in range(1,b+1): for j in range(i+1,b+1): for k in
> range(j+1,b+1): ...`

**3. `sumOfTwoPrimes(n)`** — can `n` be written as a sum of two primes?
(e.g. \\(21=2+19\\))

**4. `sumOfTwoPrimeSquares(n)`** — can `n` be written as a sum of squares of
two primes? (e.g. \\(50=5^2+5^2\\))

**5. `somePrime(numbers)` / `allPrime(numbers)`** — "for some"/"for all"
quantifiers over primality.
```python
print(somePrime(num1), allPrime(num1))  # True False
print(somePrime(num3), allPrime(num3))  # True True
```

**6. `allDistinct(numbers)` / `allWithinRange(numbers, lower, upper)` /
`isPermutation(numbers)`** — first two are "for all" patterns; the third
(a one-liner!) uses both: a list of length `n` is a permutation if all
elements are distinct and each is in `0..n-1`.
```python
print(allDistinct([1,3,2,5,2,1]))  # False
print(isPermutation([1,0,2,5,3,4]))  # True
```

**7. `walk_square_picking_all_beepers()`** — Toy Robot walks the boundary
picking up every beeper it's standing on.
```python
def move_and_pick():
    hubo.move()
    if hubo.on_beeper():
        hubo.pick_beeper()

def walk_square_picking_all_beepers():
    # ADD ADDITIONAL CODE HERE! (reuse the Week 8 boundary-walk, but call
    # move_and_pick() instead of hubo.move())
```

**8. `whirl_picking_all_beepers()`** — same idea, along the Week 8 "whirl"
spiral path instead of the boundary.

**9. `whirl_dropping_beepers()`** — Toy Robot drops a beeper (if carrying
one) at each step of the sequence "1 L 2 L 3 L ... 9 L 9".
```python
def move_and_drop():
    hubo.move()
    if hubo.carries_beepers():
        hubo.drop_beeper()
```

---
*Source: 2025 offering, `week09_for_3_problem.pdf`. Wording condensed; code
stubs kept close to the original.*
