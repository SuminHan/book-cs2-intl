# For Loops II

## 8.1. Opener: Count the Positive Numbers

```python
L = [3, -1, 4, -5, 2]

for x in L:
    count = 0
    if x > 0:
        count = count + 1

print(count)
```

There are three positive numbers. Does this print 3?

**It prints 1.**

`count = 0` sits inside the loop. So every single time around, the count is
thrown away and started again.

The number you see at the end is not a total. It is just whatever happened
on the last item — and `2` is positive, so you get 1.

*Try `L = [3, -1, 4, -5, -2]` and it prints `0`. Same code, different last item.*

### One space is the whole bug

```python
# Correct -- set up before the loop
count = 0
for x in L:
    if x > 0:
        count = count + 1
print(count)      # 3
```

**The question to ask every counter:** "Does this line need to happen
*once*, or *every time around*?" Setting up belongs outside. Only the
counting belongs inside.

## 8.2. Topics Covered

- `for` loop pattern: counter (count elements satisfying a condition)
- Toy Robot: basic moves (`move()`, `turn_left()`, `turn_right()`)

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*
