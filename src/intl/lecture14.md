# Classes & Objects

```python
class Student:
    scores = []

    def __init__(self, name):
        self.name = name

    def add(self, s):
        self.scores.append(s)

a = Student("Alice");  a.add(90)
b = Student("Bob");    b.add(80)
print(a.name, a.scores, "|", b.name, b.scores)
```

Expected: `Alice [90] | Bob [80]`

### They are sharing one list

```
Alice [90, 80] | Bob [90, 80]
```

`scores = []` sits directly under `class`, so it is made once, for the
class itself — not once per student. Alice and Bob are appending to the
same list.

```python
# Correct -- give each object its own
    def __init__(self, name):
        self.name = name
        self.scores = []      # made per student
```

### The question that settles it

Notice that `self.name` was fine all along. Only `scores` misbehaved —
because it was created in a different place.

**For every attribute, ask:** "Is there *one* of these for the whole
class, or *one per object*?" One per object → it belongs inside
`__init__`, with `self.`

*Once again: no error message. Just two students quietly sharing a report card.*
