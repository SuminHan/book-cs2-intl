# Problem Set


[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture01.ipynb)

**1.** Add additional code to the following program so that:
- the values of the two variables `a`, `b` are changed (swapped).
  - *Hint: use multiple assignment, i.e. `a,b = b,a`.*

```python
a = input("Enter a: ")
b = input("Enter b: ")
print("Before swapping:", a, b)
# ADD ADDITIONAL CODE HERE!

print("After swapping: ", a, b)
```

**2.** Add additional code to the following program so that:
- the values of the five variables `a,b,c,d,e` are rotated: `a`'s value goes
  to `b`, `b`'s to `c`, and so on, wrapping `e`'s value back around to `a`.
  - *Hint: use multiple assignment, i.e. `a,b,c,d,e = ...`.*

```python
a = input("Enter a: ")
b = input("Enter b: ")
c = input("Enter c: ")
d = input("Enter d: ")
e = input("Enter e: ")
print("Before swapping:", a, b, c, d, e)
# ADD ADDITIONAL CODE HERE!

print("After swapping: ", a, b, c, d, e)
```

**3.** Add additional code to the following program so that:
- the value of the expression \\(ax^2+bx+c\\) is printed.
  - \\(x^2\\) can be computed by `x**2` or `x*x`.

```python
a = input("Enter a: ")
b = input("Enter b: ")
c = input("Enter c: ")
x = input("Enter x: ")
a = int(a)  # input() gives string type
b = int(b)
c = int(c)
x = int(x)
# ADD ADDITIONAL CODE HERE!

# y = ...
print("Value of the quadratic formula:", y)
```

**4.** Add additional code to the following program so that it:
- reads four integers `x1,y1,x2,y2` from the keyboard, where `x1<x2` and
  `y1<y2`;
- prints the area of the rectangle represented by the two corner points
  (`(x1,y1)` is the bottom-left corner, `(x2,y2)` is the top-right corner).

```python
x1 = int(input("Enter x1: "))
y1 = int(input("Enter y1: "))
x2 = int(input("Enter x2: "))
y2 = int(input("Enter y2: "))
# ADD ADDITIONAL CODE HERE!

# area = ...
print("Area of rectangle:", area)
```

**5.** Add additional code to the following program so that it:
- reads three float values `a,b,c` from the keyboard, where they satisfy
  the triangle inequalities `a+b>c`, `b+c>a`, `c+a>b`;
- prints the area of the triangle whose side lengths are `a,b,c`:
  \\(\sqrt{s(s-a)(s-b)(s-c)}\\) where \\(s = \frac{a+b+c}{2}\\).
  - \\(\sqrt{x}\\) (i.e. \\(x^{0.5}\\)) can be computed by `x**0.5`.

```python
a = float(input("Enter a: "))
b = float(input("Enter b: "))
c = float(input("Enter c: "))
# ADD ADDITIONAL CODE HERE!

# s = ...
# area = ...
print("Area of triangle:", area)
```

**6.** Add additional code to the following program so that it:
- reads two positive integers `a` and `b` from the keyboard;
- computes the remainder when `a` is divided by `b`, **without using the `%`
  operator** (only `-`, `*`, and `//`);
  - *What is the value of `101//16`? What is the value of `(101//16)*16`?*
- prints out the remainder.

```python
a = int(input("Enter a: "))
b = int(input("Enter b: "))
# ADD ADDITIONAL CODE HERE!

# r = ...
print("Remainder:", r)
```

**7.** Add additional code to the following program so that it:
- reads a positive float value `x` from the keyboard;
- prints the integer nearest to `x` (rounding), **without using `round()`**.
  - *What is the value of `int(2.4+0.5)`? Of `int(2.5+0.5)`? Of `int(2.6+0.5)`?*

```python
x = float(input("Enter x: "))
# ADD ADDITIONAL CODE HERE!

# y = ...
print(x, "is rounded off to", y)
```

**8.** Add additional code to the following program so that it:
- reads an integer `F` from the keyboard, representing a temperature in
  Fahrenheit;
- prints the equivalent temperature in Celsius: \\(C = (F-32) \cdot
  \frac{5}{9}\\).

```python
F = int(input("Enter F: "))
# ADD ADDITIONAL CODE HERE!

# C = ...
print("Temperature in Celcius:", C)
```
