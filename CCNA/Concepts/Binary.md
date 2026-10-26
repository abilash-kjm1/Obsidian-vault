---
tags:
  - ccna/concept
course_days:
  - 7
  - 13
---

# Concept: Binary

> [!abstract] In one line  
> Binary is base 2: only **0** (off) and **1** (on). Each position is worth **double** the one to its right, so any octet (0–255) is just a sum of **128 · 64 · 32 · 16 · 8 · 4 · 2 · 1**.

## The Powers-of-Two Chart

Write this down before every conversion. It's the "decoder ring".

|Power|2⁷|2⁶|2⁵|2⁴|2³|2²|2¹|2⁰|
|---|---|---|---|---|---|---|---|---|
|**Value**|**128**|**64**|**32**|**16**|**8**|**4**|**2**|**1**|

Build it either way: start at 1 and **double** leftwards, or compute 2⁰ … 2⁷.

> [!info]- Why does each place double? (click)  
> It's the same as decimal, but with base 2. In decimal each place is ×10 (1, 10, 100, 1000) because there are 10 digits. In binary there are only 2 digits, so each place is ×2. `10` in binary = one 2 + zero 1s = **2**.

## Binary → Decimal: Add the "On" Values

Line the 8 bits up under the chart and add the values wherever there's a **1**.

**Example `10101000`:**

```
128  64  32  16   8   4   2   1
  1   0   1   0   1   0   0   0
128     + 32     + 8              = 168
```

## Decimal → Binary: Subtract Left to Right

Go left to right. **If the value fits** in what's left, write **1** and subtract it. If it doesn't, write **0**.

**Example `172`:**

|Value|Fits in what's left?|Bit|Left over|
|---|---|---|---|
|128|172 ≥ 128 ✅|1|44|
|64|44 < 64 ❌|0|44|
|32|44 ≥ 32 ✅|1|12|
|16|❌|0|12|
|8|✅|1|4|
|4|✅|1|0|
|2|❌|0|0|
|1|❌|0|0|

**172 = `10101100`**

## Values Worth Memorizing

These show up in every subnet mask:

|Binary|Decimal|
|---|---|
|`10000000`|128|
|`11000000`|192|
|`11100000`|224|
|`11110000`|240|
|`11111000`|248|
|`11111100`|252|
|`11111110`|254|
|`11111111`|255|

> [!tip] Pattern  
> Each extra leading 1 adds the next value: 128 → +64 = 192 → +32 = 224 → +16 = 240 → +8 = 248 → +4 = 252 → +2 = 254 → +1 = 255.

## Exam Points

- 8 bits per octet → values **0–255**. 4 octets → **32 bits** per IPv4 address.
- `11111111` = 255 (all on) · `00000000` = 0 (all off).
- Practise until you can convert any octet in under 10 seconds. Subnetting depends on it.

## Self-Test

1. `11000000` = ?
2. `00010101` = ?
3. 34 in binary?
4. 240 in binary?

> [!success]- Answers  
> 1. 128 + 64 = **192**  
> 2. 16 + 4 + 1 = **21**  
> 3. 32 + 2 → **`00100010`**  
> 4. 128 + 64 + 32 + 16 → **`11110000`**

## Related

- [EP 4 - Binary and Decimal Conversion](../Subnetting%20Master%20-%20Network%20Chuck/EP%204%20-%20Binary%20and%20Decimal%20Conversion.md)
- [Bits and Bytes](Bits%20and%20Bytes.md) · [Hexadecimal](Hexadecimal.md) · [IPv4 Address Classes](IPv4%20Address%20Classes.md)
