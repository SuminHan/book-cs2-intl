# While Loops

## Opener: The Alarm That Never Rang

**14 August 2003, 2:14 p.m.** A control room in Ohio. A program whose only
job is to raise an alarm when the power grid is in trouble.

Two parts of that program reached for the same piece of data at the same
moment. The program did not crash. It did not print an error. It started
going round and round, and never came back out.

The screens kept showing the last thing they had seen: everything normal.

### Nobody knew anything was wrong

Power lines were failing. The operators could not see it, because the
thing that tells them was stuck in a loop.

By the end of the evening the failure had cascaded across eight US states
and into Ontario. **About 55 million people** lost power.

*The software was a widely used energy management system. The loop had run
correctly for years — it only misbehaved when two things happened at once.*

> Sources: US–Canada Power System Outage Task Force final report (2004);
> contemporaneous reporting on the GE XA/21 alarm failure.

### Why `while` deserves your respect

A `for` loop always ends: the list runs out. A `while` loop ends only if
you make it end.

```python
n = 10
while n > 0:
    print(n)
    n = n - 1        # remove this line and it never stops
```

**Ask this every single time you write `while`:** "What changes inside the
loop that will eventually make the condition false?" If you cannot point at
that line, you have written an infinite loop.

## Topics Covered

- `while` loop syntax
- Toy Robot (continued)

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*

## Problem Set

### Required

**1. `countSevens(n)`** — how many digits of `n` are `7`.
```python
print(countSevens(1723))        # 1
print(countSevens(1357924770))  # 3
```
> `while n > 0: ... n //= 10` walks the digits from the right; `n % 10` is
> the current last digit.

**2. `countEvenDigits(n)`** — how many digits of `n` are even. Same
structure as problem 1, checking `n % 2 == 0`.

**3. `gcd(a, b)`** — greatest common divisor via the Euclidean algorithm:
$\gcd(a,b) = \gcd(b, a \bmod b)$, until the second number hits 0.
```python
def gcd(a, b):
    if a < b:
        a, b = b, a
    while b != 0:
        r = a % b
        a = b
        b = r
    return a
print(gcd(36, 20))  # 4
```

**4. `walk_square_picking_all_beepers()`** — like Week 9's version, but
multiple beepers can be at one spot: replace the `if` with a `while`.

**5. `collect_garbages()`** — Toy Robot collects every beeper (garbage) into
a can north of the starting point: sweep right collecting, turn back, sweep
left, move up, drop everything, return to start.

**6. `putNumber(num)`** — Toy Robot drops beepers to spell out the digits
of `num`.
```python
while num > 0:
    digit = num % 10
    num = num // 10
    # drop `digit` beepers and move forward, instead of printing
```

### Optional Problems

*Not for submission/grading, but good practice (mostly past exam problems).*

**7–9. `estimatePI(...)`** (three variants) — approximate π using a `while`
loop until within a given error bound:
- Ramanujan's series: $\frac{1}{\pi} = \frac{2\sqrt2}{9801}\sum_{k=0}^{\infty}\frac{(4k)!(1103+26390k)}{(k!)^4 396^{4k}}$
  (target error $\le 10^{-15}$, no `n` parameter)
- Basel problem: $\pi = \sqrt{6\sum_{i=1}^{\infty}\frac{1}{i^2}}$ (parameter
  `n` from -4 to 0, stop once within $10^n$ of `math.pi`)
- Leibniz series: $\pi = 4\left(1-\frac13+\frac15-\frac17+\cdots\right)$
  (same `n`-based stopping rule)

**10. `countWeek(rateA, rateB, x)`** (`rateA < rateB`) — two lab mice start
at equal weight; `rateA`/`rateB` are their weekly growth rates. Return the
minimum number of weeks until mouse B outweighs mouse A by at least `x`%.

**11. `reverseSum(L)`** — sum of each number in `L` with its digits
reversed. E.g. `[12,40,2]` → $21+4+2=27$.

**12. `evenDigits(num)`** — integer formed from just the even digits of
`num`, in their original order (`0` if there are none). E.g. from `37153`
→ `0` (no even digits).

**13. `findMax(L)`** — `L` is a list of `[number, base]` pairs (e.g.
`[151,8]` = octal 151); return the maximum value, converted to decimal.
> Write a helper `toDecimal([number, base])` first.

**14. `countAllZeros(L)`** — total count of `0` bits across the binary
representations of the decimal numbers in `L`. E.g. `[10,20,30]` →
binary `1010,10100,11110` → $2+3+1=6$.

---
*Source: 2025 offering, `week10_while_problem.pdf`. Wording condensed; code
stubs kept close to the original.*
