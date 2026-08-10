# Basic Elements

## 1.1. Opener: A Very Easy Question

You have just learned variables, expressions, and `print`. So this should be easy:

```python
print(0.1 + 0.2)
```

What does Python print? Everyone knows this one — say it out loud.

**Python disagrees:**

```
0.30000000000000004
```

```python
print(0.1 + 0.2 == 0.3)      # False
```

This is not a bug. Every computer on Earth agrees with Python here.

### Why: some numbers have no exact form

Write $1/3$ in decimal: $0.3333\ldots$ — it never ends. You have to stop
somewhere, so you store something slightly wrong. A computer stores numbers
in **binary**, and in binary $0.1$ is a number that never ends either. Here
is what is really in memory:

```
0.1  ->  0.10000000000000000555
0.2  ->  0.20000000000000001110
0.3  ->  0.29999999999999998890
```

The first two add up to a hair *more* than the third. That hair is the
`...004` you saw.

### Where this bites you

Tiny errors pile up. Add 0.1 ten times:

```python
total = 0.0
for i in range(10):
    total = total + 0.1
print(total)          # 0.9999999999999999
print(total == 1.0)   # False
```

**The rule to remember all semester:** never test two decimals with `==`.
Ask whether the gap is small enough instead: `abs(a - b) < 0.000001`.

The computer did the arithmetic perfectly. It still gave you an answer you
did not expect. Knowing what the machine will actually do is a different
skill from telling it what to do.

## 1.2. Topics Covered

- Computation in math vs. Python
- Variables & values
- Operators & expressions (`+ - * / // % **`)
- Input from keyboard, output to screen

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*

## 1.3. Problem Set

**1. Swap two variables** — given `a` and `b` read from input, print them
swapped.

```python
a = input("Enter a: ")
b = input("Enter b: ")
print("Before swapping:", a, b)
# ADD ADDITIONAL CODE HERE!
print("After swapping: ", a, b)
```
> Hint: multiple assignment — `a, b = b, a`.

**2. Rotate five variables** — given `a, b, c, d, e`, rotate their values so
`a`'s value goes to `b`, `b`'s to `c`, ..., and `e`'s wraps around to `a`.
> Hint: multiple assignment generalizes: `a,b,c,d,e = e,a,b,c,d`.

**3. Evaluate a quadratic** — read `a, b, c, x` and print $ax^2+bx+c$.
> `input()` always returns a string — convert with `int(a)` before doing
> arithmetic. `x**2` computes $x^2$.

**4. Rectangle area** — read two corner points `(x1,y1)`, `(x2,y2)` (bottom-left
and top-right) and print the rectangle's area.

**5. Triangle area (Heron's formula)** — read side lengths `a, b, c` and print
the area: $\sqrt{s(s-a)(s-b)(s-c)}$ where $s = \frac{a+b+c}{2}$.
> `x**0.5` computes $\sqrt{x}$.

**6. Remainder without `%`** — read positive integers `a, b` and compute
`a % b` using only `-`, `*`, and `//`.
> What is `101 // 16`? What is `(101 // 16) * 16`?

**7. Round to nearest integer** — read a positive float `x` and print the
nearest integer, without using `round()`.
> What is `int(2.4 + 0.5)`? `int(2.5 + 0.5)`? `int(2.6 + 0.5)`?

**8. Fahrenheit to Celsius** — read an integer Fahrenheit temperature `F` and
print the Celsius equivalent: $C = (F - 32) \cdot \frac{5}{9}$.

---
*Source: 2025 offering, `week02_var_expr_problem.pdf`. Wording condensed;
code stubs kept close to the original.*
