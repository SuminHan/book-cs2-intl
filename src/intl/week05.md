# Boolean Functions

## 1. Opener: This Looks Completely Reasonable

You want to check whether `x` is 1 or 2. In English that is one short
sentence, so you write it the way you say it:

```python
x = 5
print(x == 1 or 2)
```

`x` is 5. So this prints `False` — right?

**It prints `2`.**

Python read it as `(x == 1) or 2`:

- `x == 1` is `False`
- so `or` moves on and hands back `2`
- and `2` counts as true

So inside an `if`, this condition is true for every value of `x` — 5, 99,
anything.

### Say it twice

`or` joins two complete comparisons, not one comparison and a leftover number.

```python
# Correct
print(x == 1 or x == 2)     # False
```

**Why this one is dangerous:** it never crashes. It never warns you. It
just quietly says yes to everything — and an `if` that is always true looks
exactly like an `if` that works.

## 2. Topics Covered

- Defining & using boolean functions
- Common mistake: returning the strings `"True"`/`"False"` instead of the
  boolean values `True`/`False`

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*
