# How Numbers Live in Memory

This page is a reference, not required reading for any single week — come
back to it whenever a type/dtype question comes up. It answers, at the bit
level, the question Week 2 raised but didn't fully resolve: **why does
`0.1 + 0.2 == 0.3` return `False`?**

## Integers

A computer stores everything as bits (0s and 1s). An `n`-bit **unsigned**
integer is just binary place value — bit `i` contributes `2^i` if it's 1:

<table>
<tr><td>bit</td>
<td style="color:#888">0</td><td style="color:#888">0</td><td style="color:#888">0</td><td style="color:#888">0</td><td style="color:#888">0</td>
<td style="color:#d6336c"><b>1</b></td><td style="color:#888">0</td><td style="color:#d6336c"><b>1</b></td></tr>
<tr><td>place value</td>
<td style="color:#888">128</td><td style="color:#888">64</td><td style="color:#888">32</td><td style="color:#888">16</td><td style="color:#888">8</td>
<td style="color:#d6336c"><b>4</b></td><td style="color:#888">2</td><td style="color:#d6336c"><b>1</b></td></tr>
</table>

Only the colored (`1`) bits contribute — the rest add `0`: `4 + 1 = 5`.

With `n` bits you can represent `2^n` distinct values, so an unsigned
`n`-bit integer ranges over `[0, 2^n - 1]`. For `n=8`: `[0, 255]`
(`uint8`, the dtype behind each RGB channel in an image, for instance).

**Signed** integers need to represent negative numbers too, and virtually
every language does this with **two's complement**: to negate a number,
flip every bit and add 1.

```
 5  =  00000101
-5  =  11111011      (flip 00000101 -> 11111010, then +1)
```

The top bit now effectively means "this contributes `-2^(n-1)` instead of
`+2^(n-1)`," which shifts the range to `[-2^(n-1), 2^(n-1) - 1]` — for
`int8`: `[-128, 127]`. Notice the range isn't symmetric (one more negative
number than positive) — that asymmetry is a direct consequence of how
two's complement works, and it's why `abs(-128)` overflows in a real
8-bit `int8` type.

Two's complement isn't an arbitrary choice — its whole point is that
addition works identically for positive and negative numbers with the
exact same circuit, no special-casing subtraction. That's why it's
universal in real hardware, not just a textbook convention.

| Type | Bits | Range |
|---|---|---|
| `int8` / `uint8` | 8 | `[-128, 127]` / `[0, 255]` |
| `int16` / `uint16` | 16 | `[-32768, 32767]` / `[0, 65535]` |
| `int32` / `uint32` | 32 | `[-2.1×10⁹, 2.1×10⁹]` / `[0, 4.3×10⁹]` |
| `int64` / `uint64` | 64 | `[-9.2×10¹⁸, 9.2×10¹⁸]` / `[0, 1.8×10¹⁹]` |

Python's plain `int` sidesteps all of this — it grows arbitrarily large
automatically, at the cost of being slower and using more memory than a
fixed-width integer for the same value. `numpy`/`pandas` arrays, by
contrast, use fixed-width types (see below) specifically to avoid that
overhead.

## IEEE 754: Floating-Point Numbers

A float isn't stored as "the digits after the decimal point" — it's
stored the way scientific notation works, in binary: **sign, exponent,
mantissa** (also called the significand).

\\[\text{value} = (-1)^{\text{sign}} \times \left(1 + 0.m_1m_2\ldots
m_n\right)_2 \times 2^{\text{exponent} - \text{bias}}\\]

where `m_1 m_2 ... m_n` are exactly the mantissa bits as stored, read as
a binary fraction (`0.m_1m_2...`) — the leading `1 +` is never stored,
it's implied for free on every normal number.

| Type | Sign bits | Exponent bits | Mantissa bits (`n`) | Total bits |
|---|---|---|---|---|
| `float16` (half) | 1 | 5 | 10 | 16 |
| `float32` (single) | 1 | 8 | 23 | 32 |
| `float64` (double) | 1 | 11 | 52 | 64 |

**Bias is a different kind of thing from the bit-counts above** — it's not
a width, it's a *value* added to the true exponent before storing it, so
the stored exponent (which is unsigned — no sign bit of its own) can still
represent negative true exponents:

\\[\text{stored exponent} = \text{true exponent} + \text{bias}, \qquad
\text{bias} = 2^{\,\text{exponent bits}-1} - 1\\]

| Type | Exponent bits | Bias |
|---|---|---|
| `float16` | 5 | \\(2^4-1=15\\) |
| `float32` | 8 | \\(2^7-1=127\\) |
| `float64` | 11 | \\(2^{10}-1=1023\\) |

E.g. in `float32`, a stored exponent of `130` means a true exponent of
`130 - 127 = 3`.

**Special values** are encoded with reserved exponent patterns: all-zero
exponent means `0` or a *denormal* (a number too small to have that
implicit leading `1 +`); all-one exponent means `±infinity` (mantissa
`0`) or `NaN` (mantissa nonzero — this is what you get from `0/0` or
`math.sqrt(-1)`).

## Why `0.1 + 0.2 != 0.3`

`0.1` in decimal is `1/10` — and `10 = 2 × 5`, so in *binary* it's a
repeating fraction, the same way `1/3` repeats forever in decimal. It gets
cut off at the mantissa's bit limit, so what's actually stored is not
`0.1` but the nearest representable neighbor:

```python
from decimal import Decimal
print(Decimal(0.1))
# 0.1000000000000000055511151231257827021181583404541015625
```

In raw bits (`float64`, 52-bit mantissa):

```
sign: 0
exponent: 01111111011   (1019, actual exponent = 1019 - 1023 = -4)
mantissa: 1001100110011001100110011001100110011001100110011010
```

`0.1` and `0.2` each round to a value a *hair* off from the true value —
and those hairs don't cancel out when added, so the sum is a hair off
from `0.3` too. Every language with IEEE 754 floats has this exact
behavior (it's not a Python bug) — the fix is never `==` on floats,
always a tolerance: `abs(a - b) < 1e-9`.

## 32-bit vs. 64-bit

"32-bit" and "64-bit" describe the width of a CPU's registers and
addresses — which, among other things, bounds how much memory a program
can address at all: exactly 4 GB for 32-bit (`2^32` bytes), and about
16 EB (`2^64` bytes, far more than any computer actually has) for 64-bit.
This is a separate axis from int8/int32/int64 *value* widths above — a
64-bit *machine* can still compute with 8-bit *values*.

<video controls width="100%">
  <source src="assets/bit-width-en.mp4" type="video/mp4">
</video>

## Why This Matters: `numpy`, `pandas`, and Model Quantization

Plain Python `int`/`float` hide all of this — but the moment you touch
`numpy`, `pandas`, or a deep learning framework, the dtype you choose
directly controls memory and speed, because now you're choosing a real
fixed-width representation:

```python
import numpy as np
np.array([1, 2, 3], dtype=np.int8)     # 1 byte per element
np.array([1, 2, 3], dtype=np.int64)    # 8 bytes per element — 8x the memory
np.array([1.0], dtype=np.float32)      # what GPUs compute fastest in
```

A `pandas` `DataFrame` column silently defaulting to `int64`/`float64`
when `int8`/`float32` would hold the same data is one of the most common
avoidable memory blowups in real data pipelines — for a column of ages
(0-120), `int8` uses 1/8th the memory of the `int64` default, with zero
loss of information.

This same tradeoff, at a much larger scale, is exactly what **model
quantization** in machine learning is about. A large language model's
weights are originally trained in `float16` or `float32` — a 3.6-billion-
parameter model in `float16` needs about `3.6B × 2 bytes ≈ 7.2 GB` just
to hold the weights, before you've run anything. Quantizing that model to
`int8` (or even `int4`, packing two values per byte) roughly halves — or
quarters — that footprint, which is exactly what lets a model that size
run on a laptop or phone instead of a server GPU. The tradeoff is real:
fewer bits means less precision per weight, so quantized models are
slightly less accurate than their `float16` originals — the same "hair of
error" from the `0.1 + 0.2` story above, just deliberately accepted in
exchange for the model fitting in memory at all.

Every dtype table above — `int8` vs `int64`, `float16` vs `float32` — is
the same underlying idea you just learned, just chosen for a different
tradeoff each time.
