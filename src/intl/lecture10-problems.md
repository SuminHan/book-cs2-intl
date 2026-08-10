# Problem Set

### Required

**1.** Write a function `countSevens` defined by:
- input parameter: a positive integer `n`
- return value: the number of occurrences of digit `7` in `n`
  - *Refer to `countDigits` from this week's lecture:*
    `while n > 0: counter += 1; n //= 10`. *What does `n % 10` give you on
    each iteration? Increment the counter only when `n % 10 == 7`.*

```python
def countSevens(n):
    # ADD ADDITIONAL CODE HERE!
print(countSevens(1723))        # 1
print(countSevens(1357924770))  # 3
```

**2.** Write a function `countEvenDigits` defined by:
- input parameter: a positive integer `n`
- return value: the number of even digits in `n`
  - *The solution is very similar to `countSevens` above. What does `n % 2`
    give you on each iteration?*

```python
# ADD FUNCTION HERE!
print(countEvenDigits(2723))        # 2
print(countEvenDigits(1326924870))  # 6
```

**3.** Write a function `gcd` defined by:
- input parameter: two positive integers `a` and `b`
- return value: the greatest common divisor of `a` and `b`

The GCD can be computed by the **Euclidean algorithm**: given positive
integers `a >= b`, let `r = a % b`. Then `gcd(a,b) == gcd(b,r)`. For
example, `gcd(36,20) = gcd(20,16) = gcd(16,4) = gcd(4,0) = 4`. Repeating
this reduction always eventually reaches a pair whose second number is 0 —
the GCD is then the other number.

```python
def gcd(a, b):
    if a < b:  # swap so that a >= b
        a, b = b, a
    # ADD ADDITIONAL CODE HERE!
    while b != 0:
        r = a % b
        a = ??
        b = ??
    return ??
print(gcd(36, 20))          # 4
print(gcd(2408208, 2790876)) # 132
```
*Hint: during the loop, `a,b` should take the values `36,20 → 20,16 →
16,4 → 4,0`.*

**4.** Write a function `walk_square_picking_all_beepers` defined by:
- input parameter: none
- return value: none
- action: make Hubo walk along the world boundary picking up all the
  beepers
  - *This is a small extension of Week 9 problem 7, allowing multiple
    beepers at one position — copy that code and replace the `if` with a
    `while`.*

**5.** Write a function `collect_garbages` defined by:
- input parameter: none
- return value: none
- action: make Hubo collect all the garbage (represented by beepers) and
  put it in the garbage can, located north of the starting point

```python
def collect_garbages():
    # move to the right wall while collecting beepers
    # turn back
    # move to the left wall
    # move upwards
    # put all the beepers down
    # move to the starting position
collect_garbages()
```

**6.** Write a function `putNumber` defined by:
- input parameter: an integer `num`
- return value: none
- action: make Hubo drop beepers that spell out the digits of `num`
  - e.g. `putNumber(2291)` makes Hubo drop the corresponding beepers.
  - *What does the following code do?*
    ```python
    while num > 0:
        digit = num % 10
        num = num // 10
        print(digit)
    ```
    *What does `digit` represent on each iteration? Replace the `print`
    with code that drops beepers and moves forward.*

```python
def putNumber(num):
    # ADD ADDITIONAL CODE HERE!
putNumber(2291)
```

### Optional Problems

*Not for submission/grading, but good practice (mostly past exam problems).*

**7.** Srinivasa Ramanujan proposed a formula to approximate \\(\pi\\):
\\[\frac{1}{\pi} = \frac{2\sqrt2}{9801}\sum_{k=0}^{\infty}
\frac{(4k)!(1103+26390k)}{(k!)^4\, 396^{4k}}\\]

Write a function `estimatePI` defined by:
- input parameter: none
- return value: an approximation of \\(\pi\\) computed by the formula above
  - *The difference from `math.pi` should be \\(\le 10^{-15}\\).*

**8.** Write a function `estimatePI` defined by:
- input parameter: an integer `n` (from -4 to 0), an error bound
- return value: an approximation of \\(\pi\\) accurate to within \\(10^n\\)
  - *Stop the `while` loop once the approximation is within \\(10^n\\) of
    `math.pi`. Use the formula* \\[\pi = \sqrt{6\sum_{i=1}^{\infty}
    \frac{1}{i^2}}\\]

**9.** Write a function `estimatePI` defined by:
- input parameter: an integer `n` (from -4 to 0), an error bound
- return value: an approximation of \\(\pi\\) accurate to within \\(10^n\\)
  - *Stop the `while` loop once the approximation is within \\(10^n\\) of
    `math.pi`. Use the Leibniz formula* \\[\pi = 4\left(1-\frac13+\frac15-
    \frac17+\frac19-\cdots\right)\\]

**10.** Two lab mice A and B start at the same weight, but grow at
different weekly rates.

Write a function `countWeek` defined by:
- input parameter: three integers `rateA, rateB, x` (with `rateA < rateB`)
  — the weekly growth rates of A and B
- return value: the minimum number of weeks until B weighs at least `x`%
  more than A

**11.** Write a function `reverseSum` defined by:
- input parameter: a list of positive integers
- return value: the sum of the numbers in the list, each with its digits
  reversed — e.g. `[12,40,2]` → `21+4+2 = 27`

**12.** Write a function `evenDigits` defined by:
- input parameter: a positive integer `num`
- return value: the integer formed from the even digits of `num`, in the
  same order they appear in `num` — `0` if `num` has no even digits (e.g.
  `37153` → `0`)

**13.** Write a function `findMax` defined by:
- input parameter: a list of `[number, base]` pairs — e.g.
  `[[151,8],[1111001,2],[-10101,2],[2731,8],[1001,10]]` represents an octal
  number 151, a binary number 1111001, a binary number -10101, an octal
  number 2731, and a decimal number 1001
- return value: the decimal representation of the maximum value in the list
  - *Implement a helper `toDecimal([number, base])` first, and use it.*

**14.** Write a function `countAllZeros` defined by:
- input parameter: a list `L` of decimal numbers
- return value: the total number of `0`s in the binary representations of
  the numbers in `L` — e.g. `[10,20,30]` → `[1010,10100,11110]` →
  `2+3+1 = 6`
