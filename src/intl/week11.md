# List II

## 10.1. Opener: Remove Every Negative Number

You have just learned `.remove()`. This reads perfectly:

```python
def remove_negatives(L):
    for x in L:
        if x < 0:
            L.remove(x)
    return L

print(remove_negatives([1, -2, -3, 4, -5, -6]))
```

Expected: `[1, 4]`

**Half of them survived:**

```
[1, -3, 4, -6]
```

A `for` loop walks by position: 0, 1, 2, ... But `remove` pulls everything
after it one step left.

So when `-2` at position 1 is deleted, `-3` slides into position 1 — and
the loop has already moved on to position 2. Every second negative is skipped.

```python
# Correct -- build a new list instead
def remove_negatives(L):
    return [x for x in L if x >= 0]
```

### The rule

> Never change a list while you are walking through it.

Make a new one, or walk it backwards.

*And notice again: no crash, no warning. Just a quietly wrong answer.*

## 10.2. Topics Covered

- `.append()`, slicing `[:]`
- List operations: `==`, `+`, `in`
- Built-in functions: `sum()`, `max()`, `min()`, `sort()`
- List comprehension

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*

## 10.3. Problem Set

**1. `deleteThree(L)`** — new list with every `3` removed from `L`.
```python
def deleteThree(L):
    # ADD ADDITIONAL CODE HERE!
print(deleteThree([2,5,7,3,2,8,3,3]))  # [2,5,7,2,8]
```
> `L.pop()` shifts indices as you go — build a fresh empty list and append
> only the values that aren't 3, instead of removing in place.

**2. `kthSmallest(L, k)`** — the `k`-th smallest value in `L`
(`1 ≤ k ≤ len(L)`).
```python
print(kthSmallest([3,4,2,8,8], 1))  # 2
print(kthSmallest([3,4,2,8,8], 3))  # 4
```
> `L.sort()` sorts in place, then index into the result.

**3. `same(L1, L2)`** — do the two lists contain exactly the same elements
with the same multiplicities, regardless of order?
```python
print(same([2,3,2,7],[2,7,2,3]))  # True
print(same([2,5,7,8],[2,3,4,5]))  # False
```
> `L1 == L2` only returns `True` if elements *and order* match exactly.

**4. `makeSet(L)`** — sorted list containing each distinct element of `L`
exactly once.
```python
print(makeSet([1,1,3,5]))         # [1,3,5]
print(makeSet([3,4,5,6,7,3,4]))   # [3,4,5,6,7]
```
> Don't use the `set` type here — use `in`/`not in` instead.

**5. `multiple(L1, L2)`** — is every number in `L1` a multiple of *some*
number in `L2`? ($\forall x \in L_1,\, \exists y \in L_2$ s.t. `x` is a
multiple of `y`)
```python
print(multiple([14,24,18,35,39], [6,13,7]))  # True
print(multiple([14,24,18,35,39], [5,13,7]))  # False
```

---
*Source: 2025 offering, `week11_List2_problem.pdf`. Wording condensed; code
stubs kept close to the original.*
