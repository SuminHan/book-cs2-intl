# Problem Set

**1. Counting occurrences of a character in a string.** Write a function
`countChar` that takes as input a string `s` consisting of alphabetic
characters and a single-character string `c`, and returns the number of
times `c` appears in `s`.

*(Note: a "single character" means a string of length 1, such as `"a"`.)*

```python
def countChar(s, c):
    # ADD ADDITIONAL CODE HERE!
print(countChar("AbAA","b"))         # 1
print(countChar("AbAA","A"))         # 3
print(countChar("DbDD","D"))         # 3
print(countChar("bcdAAAdfAA","A"))   # 5
print(countChar("abc","A"))          # 0
```

**2. Reversing a string.** Write a function `reverse` that takes as input a
string `s` and returns a new string that is the reverse of `s`.

*Hint: initialize an empty string `""` and build the reversed string by
concatenating characters one by one with `+`.*

```python
def reverse(s):
    # ADD ADDITIONAL CODE HERE!
print(reverse("abc"))    # cba
print(reverse("abcDF"))  # FDcba
print(reverse("abcd"))   # dcba
```

**3. Finding the length of the longest common prefix.** Write a function
`lenPrefix` that takes as input two strings and returns the length of their
longest common prefix.

```python
def lenPrefix(s1, s2):
    # ADD ADDITIONAL CODE HERE!
print(lenPrefix("ababade", "ababeee"))       # 4
print(lenPrefix("predicate", "prediction"))  # 6
print(lenPrefix("ababade", "xabds"))         # 0
```

**4. Calculating the duration between two times.** Write a function
`duration` that takes as input two times in `"hhmm"` format (hours and
minutes) and calculates the time difference between them in hours and
minutes. For example, given `"0910"` and `"1350"`, the function should
output `"4 h 40 m"`.

*(Assumption: times are given in 24-hour format, and only valid times are
provided — hours 0-23, minutes 0-59.)*

```python
def duration(t1, t2):
    # ADD ADDITIONAL CODE HERE!
print(duration("1800","0920"))  # 8 h 40 m
print(duration("0910","0910"))  # 0 m
print(duration("0910","1310"))  # 4 h
```

**5. Sorting students by ID.** Write a function `sortId` that takes as
input a list of strings where student IDs and names appear alternately, and
returns the result of sorting the list based on the student IDs.

*Hint: to sort by ID, you can use `L[::2]` to create a list containing only
the IDs. Also, if `y = L.index(x)`, then `y` is the index of the first
occurrence of `x` in `L`.*

```python
def sortId(L):
    # ADD ADDITIONAL CODE HERE!
print(sortId(["20-012","Kim","20-009","Kang","22-005","Na","21-003","Kim"]))
# ['20-009','Kang','20-012','Kim','21-003','Kim','22-005','Na']
```
