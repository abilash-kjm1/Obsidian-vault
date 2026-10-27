---
tags:
  - ccna/subnetting
series: NetworkChuck - You Suck at Subnetting
episode: 4
---

# EP 4 - Binary and Decimal Conversion

[⬅️ EP 3 - Private IP Addresses and NAT](EP%203%20-%20Private%20IP%20Addresses%20and%20NAT.md) · [EP 5 - What is a Subnet Mask ➡️](EP%205%20-%20What%20is%20a%20Subnet%20Mask.md)

**Series:** NetworkChuck · *You SUCK at Subnetting* · Episode 4
**Video:** [i bet you can't do this (because you still suck at subnetting)](https://www.youtube.com/watch?v=2-i5x8KCfII) · 18:45 (sponsor segments skipped: 6:10–8:50 and from 15:55) · ▶ links jump to that moment
**Basics used here:** [Binary](../Concepts/Binary.md) · [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

> [!abstract] The whole lesson in 3 lines  
> 1. Computers see an IP address as **32 bits** of 1s and 0s: 4 octets × 8 bits.  
> 2. The **powers-of-two chart** (128 64 32 16 8 4 2 1) converts each octet.  
> 3. **Binary → decimal:** add the values under the 1s. **Decimal → binary:** subtract the values left to right. This is the foundation of subnetting ("leg day — don't skip it").

## 1. Your IP Address "in the Matrix" ▶ [0:00](https://www.youtube.com/watch?v=2-i5x8KCfII&t=0s)

![700](Attachments/EP%204%20-%20Binary%20and%20Decimal%20Conversion-1.png)

```
Decimal (how we read it):     192   .   168    .    1     .    21
Binary  (how computers see it): 11000000.10101000.00000001.00010101
```

Same address, two notations. **Why bother?** Subnet masks only make sense in binary, so this is the "wax on, wax off" skill for subnetting.

## 2. Bits, Bytes and Octets ▶ [1:46](https://www.youtube.com/watch?v=2-i5x8KCfII&t=106s)

![700](Attachments/EP%204%20-%20Binary%20and%20Decimal%20Conversion-2.png)

- Count the digits: **32**. Each is a **bit**, the smallest unit of data a computer stores.
- **8 bits = 1 byte**, so an IPv4 address = **32 bits = 4 bytes**.
- Each dotted section has 8 bits, so it's called an **octet** (*octo* = eight).

Sizes from big to small: gigabytes (a 4K video, ~60 GB) → megabytes (a photo, ~10 MB) → bytes (a short text file, 29 B) → **bits**. → [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

## 3. 1 = On, 0 = Off ▶ [3:46](https://www.youtube.com/watch?v=2-i5x8KCfII&t=226s)

Binary has only two digits. Think of **8 light switches** per octet: each one is **on (1)** or **off (0)**, and *which* ones are on spells out the number.

## 4. The Decoder Ring: Powers of Two ▶ [4:55](https://www.youtube.com/watch?v=2-i5x8KCfII&t=295s)

![700](Attachments/EP%204%20-%20Binary%20and%20Decimal%20Conversion-3.png)

|2⁷|2⁶|2⁵|2⁴|2³|2²|2¹|2⁰|
|---|---|---|---|---|---|---|---|
|**128**|**64**|**32**|**16**|**8**|**4**|**2**|**1**|

Two ways to build it: 2⁰ up to 2⁷, **or** start at 1 and keep doubling. Eight columns, one per bit in an octet.

> [!tip] Exam habit  
> Write `128 64 32 16 8 4 2 1` on your scratch paper **before** any subnetting question.

## 5. Binary → Decimal: Add What's On ▶ [8:51](https://www.youtube.com/watch?v=2-i5x8KCfII&t=531s)

Put each octet under the chart and **add the values where the bit is 1**.

**① 11000000**

![700](Attachments/EP%204%20-%20Binary%20and%20Decimal%20Conversion-4.png)

128 + 64 = **192**

**② `10101000`**

![700](Attachments/EP%204%20-%20Binary%20and%20Decimal%20Conversion-5.png)

128 + 32 + 8 = **168**

**③ `00000001`** → only the 1 is on = **1**

**④ `00010101`**

![700](Attachments/EP%204%20-%20Binary%20and%20Decimal%20Conversion-6.png)

16 + 4 + 1 = **21**

✅ `11000000.10101000.00000001.00010101` = **192.168.1.21**

## 6. Decimal → Binary: Subtract Left to Right ▶ [11:18](https://www.youtube.com/watch?v=2-i5x8KCfII&t=678s)

Convert **172.16.34.3**. For each chart value, left to right: **can I subtract it from what's left?** Yes → write **1** and subtract. No → write **0**.

**① 172**

![700](Attachments/EP%204%20-%20Binary%20and%20Decimal%20Conversion-7.png)

|128|64|32|16|8|4|2|1|
|---|---|---|---|---|---|---|---|
|172−128 = 44 → **1**|44 < 64 → **0**|44−32 = 12 → **1**|12 < 16 → **0**|12−8 = 4 → **1**|4−4 = 0 → **1**|**0**|**0**|

172 = **`10101100`**

**② 16** → 128, 64 and 32 don't fit; 16 − 16 = 0 → **`00010000`**

**③ 34** → 34 − 32 = 2, then 2 − 2 = 0 → **`00100010`**

**④ 3** → 3 − 2 = 1, then 1 − 1 = 0 → **`00000011`**

![700](Attachments/EP%204%20-%20Binary%20and%20Decimal%20Conversion-8.png)

✅ **172.16.34.3** = `10101100.00010000.00100010.00000011`

> [!info]- Shortcut: once you hit 0, the rest are 0s (click)  
> As soon as the remainder reaches **0**, nothing else can be subtracted, so fill the remaining bits with 0. For 16, after the 16 column you're done: `0001` + `0000`.

> [!warning] Common mistake  
> Always write **all 8 bits**, including leading zeros. `3` is `00000011`, not `11`. Otherwise the octets won't line up with the subnet mask later.

## 7. Revision Sheet

|Concept|Remember|
|---|---|
|IPv4 size|32 bits = 4 bytes = 4 octets × 8 bits|
|Binary|Base 2: 1 = on, 0 = off|
|Chart|128 · 64 · 32 · 16 · 8 · 4 · 2 · 1|
|Binary → decimal|Add the values under the 1s|
|Decimal → binary|Subtract left to right; fits → 1, doesn't → 0|
|Always|Write all 8 bits per octet|
|Example|192.168.1.21 = 11000000.10101000.00000001.00010101|
|Example|172.16.34.3 = 10101100.00010000.00100010.00000011|

## 8. Test Yourself

Answer first, then click to check.

> [!question]- How many bits in an IPv4 address? How many bytes?  
> **32 bits** = **4 bytes**

> [!question]- Convert `11111111` to decimal.  
> 128+64+32+16+8+4+2+1 = **255**

> [!question]- Convert `10000001` to decimal.  
> 128 + 1 = **129**

> [!question]- Convert 200 to binary.  
> 200−128 = 72 → 72−64 = 8 → 8−8 = 0 → **`11001000`**

> [!question]- Convert 10.0.0.1 to binary.  
> `00001010.00000000.00000000.00000001`

> [!question]- Convert `11000000.10101000.00001010.01100100` to decimal.  
> **192.168.10.100** (8 + 2 = 10; 64 + 32 + 4 = 100)

> [!question]- Why is the biggest octet 255 and not 256?  
> 8 bits all on = 255. With 0 included that's **256 values** (0–255), so 256 itself needs a 9th bit.

> [!question]- What's 255.255.255.0 in binary?  
> `11111111.11111111.11111111.00000000`: 24 ones, then 8 zeros. (That's why it's written **/24**, coming up in subnetting.)
