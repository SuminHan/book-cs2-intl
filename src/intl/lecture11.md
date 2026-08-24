# Strings

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture11.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#F37626;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>



You have just met `.replace()`. The name says exactly what you want, so:

```python
s = "hello world"
s.replace("world", "python")
print(s)
```

What prints?

**Nothing changed:**

```
hello world
```

`.replace()` did its job perfectly — it built the new sentence and handed
it back to you. You just did not catch it, so it was thrown away.

```python
# Correct -- catch the return value
s = s.replace("world", "python")
print(s)          # hello python
```

### Why it works that way

In Python a string can never be edited. Not by `replace`, not by you:

```python
s = "Hello"
s[0] = "J"
```

```
TypeError: 'str' object does not support item assignment
```

So every string method — `.upper()`, `.strip()`, `.replace()` — has only
one option: build a new string and return it.

*This is why lists and strings behave differently. `L.append(x)` changes
`L`; `s.upper()` cannot change `s`.*
