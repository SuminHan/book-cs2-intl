# Topics Covered

## Strings as Immutable Lists of Characters

A string behaves like a list of characters — `len(·)`, indexing, and
slicing all work the same way — with one crucial difference: **you cannot
modify a string in place.**

```python
s = "computer"
s[0] = "C"
# TypeError: 'str' object does not support item assignment
```

To "change" a string, you build and assign a *new* one. This is the
mutable/immutable distinction: `int`, `float`, `str`, and tuples are
immutable (once created, that value never changes); `list` (and `set`) are
mutable (you can modify them in place, as `.append()` and `.sort()` do).

## Indexing & Slicing

Identical rules to lists:

```python
s = "computer"
for i in range(len(s)):
    print(s[i], end=" ")

print(s[1:4])    # "omp"
print(s[:3])     # "com"    same as s[0:3]
print(s[2:])     # "mputer"
print(s[1:6:2])  # step of 2
```

## Comparison, Membership, Concatenation

```python
s1, s2 = "computer", "science"
print(s1 == s2)    # False
print(s1 < s2)      # True — lexicographic (dictionary) order
print('abc' < "XYZ")  # False — ALL uppercase letters sort before
                        # any lowercase letter in ASCII
```

`in` checks for a **substring**, not just a single character — and order
matters:

```python
s1 = "computer"
print("om" in s1)    # True
print("OM" in s1)    # False — case-sensitive
print("com" in s1)   # True  — characters in that exact order
print("cmo" in s1)   # False — right characters, wrong order
```

`+` concatenates, `*` repeats:

```python
s = "com" + "puter"    # "computer"
t = "hi" * 3             # "hihihi"
```

Building a reversed string, one character at a time, is the same
accumulator pattern from Week 2 — start from `""`, add on each iteration:

```python
s = "computer"
r = ""
for i in range(len(s)):
    r = r + s[len(s) - i - 1]
print(r)   # "retupmoc"
```

## Palindromes

A palindrome reads the same forwards and backwards (`"radar"`, `"12321"`).
The efficient check only needs to walk to the *midpoint*, comparing each
character against its mirror from the other end — once every pair up to
the middle matches, the rest are guaranteed to match too:

```python
def is_palindrome(s):
    for i in range(len(s) // 2):
        if s[i] != s[len(s) - i - 1]:
            return False
    return True

print(is_palindrome("radar"))   # True
```
