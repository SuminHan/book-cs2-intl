# Week 10: While Loops

## 1. Opener: The Alarm That Never Rang

**14 August 2003, 2:14 p.m.** A control room in Ohio. A program whose only
job is to raise an alarm when the power grid is in trouble.

Two parts of that program reached for the same piece of data at the same
moment. The program did not crash. It did not print an error. It started
going round and round, and never came back out.

The screens kept showing the last thing they had seen: everything normal.

### Nobody knew anything was wrong

Power lines were failing. The operators could not see it, because the
thing that tells them was stuck in a loop.

By the end of the evening the failure had cascaded across eight US states
and into Ontario. **About 55 million people** lost power.

*The software was a widely used energy management system. The loop had run
correctly for years — it only misbehaved when two things happened at once.*

> Sources: US–Canada Power System Outage Task Force final report (2004);
> contemporaneous reporting on the GE XA/21 alarm failure.

### Why `while` deserves your respect

A `for` loop always ends: the list runs out. A `while` loop ends only if
you make it end.

```python
n = 10
while n > 0:
    print(n)
    n = n - 1        # remove this line and it never stops
```

**Ask this every single time you write `while`:** "What changes inside the
loop that will eventually make the condition false?" If you cannot point at
that line, you have written an infinite loop.

## 2. Topics Covered

- `while` loop syntax
- Toy Robot (continued)

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*
