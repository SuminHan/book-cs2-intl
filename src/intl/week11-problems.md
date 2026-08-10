# Problem Set

**1. Removing all 3's from a list.** Write a function `deleteThree` that
takes as input a list `L` consisting of integer values, and returns a new
list containing all elements of `L` except those equal to the integer `3`.

*Hint: when using `L.pop()`, the indices change as you go — instead of
removing `3` directly from the original list, create a new empty list and
add only the values that are not `3`.*

```python
def deleteThree(L):
    # ADD ADDITIONAL CODE HERE!
print(deleteThree([2,5,7,3,2,8,3,3]))  # [2,5,7,2,8]
print(deleteThree([3,3,7,3,2,8,3,3]))  # [7,2,8]
```

**2. Finding the k-th smallest integer in a list.** Write a function
`kthSmallest` that takes as input a list `L` consisting of integer values
and an integer `k`, and returns the `k`-th smallest integer in `L`. Assume
`k` is always between `1` and `len(L)`, inclusive.

*Hint: use `L.sort()` to sort the list, then index into it to find the
desired element.*

```python
def kthSmallest(L, k):
    # ADD ADDITIONAL CODE HERE!
print(kthSmallest([3,4,2,8,8], 1))  # 2
print(kthSmallest([3,4,2,8,8], 3))  # 4
print(kthSmallest([3,4,2,8,8], 4))  # 8
```

**3. Checking if two lists contain the same elements regardless of order.**
Write a function `same` that takes as input two lists `L1` and `L2`, each
consisting of integer values, and checks whether the two lists contain
exactly the same elements with the same multiplicities, regardless of
order.

*Hint: remember that `L1 == L2` returns `True` only if the elements *and*
their order are identical.*

```python
def same(L1, L2):
    # ADD ADDITIONAL CODE HERE!
print(same([2,3,2,7], [2,7,2,3]))  # True
print(same([2,5,7,8], [2,3,4,5]))  # False
```

**4. Creating a sorted list of distinct integers.** Write a function
`makeSet` that takes as input a list `L` consisting of integer values and
returns a sorted list containing each distinct element of `L` exactly once.

*Hint: although this can be solved easily using the `set` type, do not use
type conversion functions here — use operators such as `in`/`not in`
instead.*

```python
def makeSet(L):
    # ADD ADDITIONAL CODE HERE!
print(makeSet([1,1,3,5]))          # [1,3,5]
print(makeSet([2,1,2,8,8]))        # [1,2,8]
print(makeSet([3,4,5,6,7,3,4]))    # [3,4,5,6,7]
```

**5. Checking if every element of one list is a multiple of some element in
another list.** Write a function `multiple` that takes as input two lists
`L1` and `L2`, each consisting of integer values, and checks whether every
number in `L1` is a multiple of at least one number in `L2`. Formally:
\\(\forall x \in L_1,\, \exists y \in L_2\\) such that `x` is a multiple of
`y`.

For example, `multiple([14,24,18,35,39], [6,13,7])` should return `True`,
because `14` and `35` are multiples of `7`, `24` and `18` are multiples of
`6`, and `39` is a multiple of `13`.

```python
def multiple(L1, L2):
    # ADD ADDITIONAL CODE HERE!
print(multiple([14,24,18,35,39], [6,13,7]))  # True
print(multiple([14,24,18,35,39], [5,13,7]))  # False
```
