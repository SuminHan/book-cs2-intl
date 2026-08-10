# Problem Set

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

**3. Evaluate a quadratic** — read `a, b, c, x` and print \\(ax^2+bx+c\\).
> `input()` always returns a string — convert with `int(a)` before doing
> arithmetic. `x**2` computes \\(x^2\\).

**4. Rectangle area** — read two corner points `(x1,y1)`, `(x2,y2)` (bottom-left
and top-right) and print the rectangle's area.

**5. Triangle area (Heron's formula)** — read side lengths `a, b, c` and print
the area: \\(\sqrt{s(s-a)(s-b)(s-c)}\\) where \\(s = \frac{a+b+c}{2}\\).
> `x**0.5` computes \\(\sqrt{x}\\).

**6. Remainder without `%`** — read positive integers `a, b` and compute
`a % b` using only `-`, `*`, and `//`.
> What is `101 // 16`? What is `(101 // 16) * 16`?

**7. Round to nearest integer** — read a positive float `x` and print the
nearest integer, without using `round()`.
> What is `int(2.4 + 0.5)`? `int(2.5 + 0.5)`? `int(2.6 + 0.5)`?

**8. Fahrenheit to Celsius** — read an integer Fahrenheit temperature `F` and
print the Celsius equivalent: \\(C = (F - 32) \cdot \frac{5}{9}\\).

---
*Source: 2025 offering, `week02_var_expr_problem.pdf`. Wording condensed;
code stubs kept close to the original.*
