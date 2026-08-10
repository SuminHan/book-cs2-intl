# Topics Covered

## `.append(·)`

A second way to build a list, growing it one element at a time instead of
pre-sizing with `[None] * n`:

```python
L = [1, 2, 3, 4, 5]
n = len(L)
M = []
for i in range(n):
    M.append(L[i] * 2)     # each call adds one element to the end
```

## Slicing

`L[i:j]` — elements `L[i]` through `L[j-1]` (note: `L[j]` itself is
**excluded**). Omitting `i` means "from the start"; omitting `j` means "to
the end"; omitting both copies the whole list.

```python
L = [0, 10, 20, 30, 40, 50]
print(L[1:4])   # [10, 20, 30]
print(L[:3])    # [0, 10, 20]     same as L[0:3]
print(L[2:])    # [20, 30, 40, 50]  same as L[2:6]
print(L[:])     # [0, 10, 20, 30, 40, 50]
```

`L[i:j:k]` adds a step: take every `k`-th element from `L[i]` up to (not
including) `L[j]`.

```python
L = [0, 10, 20, 30, 40, 50, 60, 70, 80, 90]
print(L[1:9:2])    # [10, 30, 50, 70]
print(L[1::2])     # [10, 30, 50, 70, 90]
print(L[1:-1:2])   # [10, 30, 50, 70]   (-1: stop before the last element)
```

## Comparison, Membership, Concatenation

```python
L, M, N = [1,2,3], [1,2,3], [1,3,2]
print(L == M)   # True  — same values, same order
print(L == N)   # False — same values, different order

print(3 in [0,1,2,3,4,5])          # True
print([1,2] in [0,1,2,3,4,5])       # False — [1,2] is not itself an element
print([1,2] in [0,[1,2],3])         # True  — here it is

L = [0,1] + [2,3,4,5]   # [0,1,2,3,4,5]  concatenation
M = [0,1] * 3            # [0,1,0,1,0,1]  repetition
```

## Built-In Functions

`sum(L)`, `max(L)`, `min(L)` work on lists of numbers directly — no loop
needed. `L.sort()` is different from the rest: it's a **method** (called as
`L.sort()`, not `sort(L)`), it sorts `L` **in place**, and it returns
`None` — printing the return value of `.sort()` is a reliable way to
accidentally print `None` instead of your sorted list.

```python
L = [1, 2, 3, 2, 3, 2]
M = L.sort()
print(M)   # None  — NOT the sorted list
print(L)   # [1, 2, 2, 2, 3, 3]  — L itself was modified
```

## List Comprehension

A compact way to build a list from a loop, written `[expr for var in
iterable]` — optionally with an `if` filter:

```python
a = [x for x in "hello"]              # ['h','e','l','l','o']
b = [x**2 for x in range(6)]          # [0,1,4,9,16,25]
c = [x**2 for x in range(10) if x%2==1]   # only odd x: [1,9,25,49,81]
```

Nested comprehensions build nested (2D) lists, the outer loop changing
which row, the inner loop filling that row:

```python
d = [[i+j for i in range(4)] for j in range(3)]
# [[0,1,2,3], [1,2,3,4], [2,3,4,5]]
```

A comprehension is optional — anything it does, a `for` loop with
`.append()` also does. Use whichever reads more clearly for the problem at
hand; a `for`-loop version is never wrong.
