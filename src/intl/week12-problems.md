# Problem Set

**1. `countChar(s, c)`** — count of a single character `c` in string `s`.
```python
print(countChar("AbAA","A"))  # 3
print(countChar("abc","A"))   # 0
```

**2. `reverse(s)`** — reversed string.
```python
print(reverse("abcDF"))  # FDcba
```
> Build the result by starting from `""` and concatenating characters with
> `+`.

**3. `lenPrefix(s1, s2)`** — length of the longest common prefix of two
strings.
```python
print(lenPrefix("ababade", "ababeee"))    # 4
print(lenPrefix("predicate", "prediction")) # 6
```

**4. `duration(t1, t2)`** — time difference between two `"hhmm"`-format
times, formatted like `"4 h 40 m"`.
```python
print(duration("1800","0920"))  # 8 h 40 m
print(duration("0910","0910"))  # 0 m
print(duration("0910","1310"))  # 4 h
```
> Both times are valid 24-hour times.

**5. `sortId(L)`** — a list where student IDs and names alternate; sort the
whole list by ID.
```python
print(sortId(["20-012","Kim","20-009","Kang","22-005","Na","21-003","Kim"]))
# ['20-009','Kang','20-012','Kim','21-003','Kim','22-005','Na']
```
> `L[::2]` pulls out just the IDs. `L.index(x)` gives the index of the first
> occurrence of `x`.
