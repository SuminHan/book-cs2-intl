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

**2. Rotate five variables** — given `a, b, c, d, e`, rotate their values so
`a`'s value goes to `b`, `b`'s to `c`, ..., and `e`'s wraps around to `a`.

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

**3. Evaluate a quadratic** — read `a, b, c, x` and print \\(ax^2+bx+c\\).

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

**4. Rectangle area** — read two corner points `(x1,y1)`, `(x2,y2)` (bottom-left
and top-right) and print the rectangle's area.

```python
x1 = int(input("Enter x1: "))
y1 = int(input("Enter y1: "))
x2 = int(input("Enter x2: "))
y2 = int(input("Enter y2: "))
# ADD ADDITIONAL CODE HERE!
# area = ...
print("Area of rectangle:", area)
```

**5. Triangle area (Heron's formula)** — read side lengths `a, b, c` and print
the area: \\(\sqrt{s(s-a)(s-b)(s-c)}\\) where \\(s = \frac{a+b+c}{2}\\).

```python
a = float(input("Enter a: "))
b = float(input("Enter b: "))
c = float(input("Enter c: "))
# ADD ADDITIONAL CODE HERE!
# s = ...
# area = ...
print("Area of triangle:", area)
```

**6. Remainder without `%`** — read positive integers `a, b` and compute
`a % b` using only `-`, `*`, and `//`.

```python
a = int(input("Enter a: "))
b = int(input("Enter b: "))
# ADD ADDITIONAL CODE HERE!
# r = ...
print("Remainder:", r)
```

**7. Round to nearest integer** — read a positive float `x` and print the
nearest integer, without using `round()`.

```python
x = float(input("Enter x: "))
# ADD ADDITIONAL CODE HERE!
# y = ...
print(x, "is rounded off to", y)
```

**8. Fahrenheit to Celsius** — read an integer Fahrenheit temperature `F` and
print the Celsius equivalent: \\(C = (F - 32) \cdot \frac{5}{9}\\).

```python
F = int(input("Enter F: "))
# ADD ADDITIONAL CODE HERE!
# C = ...
print("Temperature in Celcius:", C)
```
