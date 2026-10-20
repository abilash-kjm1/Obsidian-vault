---
tags:
  - ccna/concept
course_days:
  - 5
  - 6
---

# Concept: Hexadecimal

> [!abstract] In one line  
> Hexadecimal (hex) is a way to write numbers using **16 digits** instead of 10. Networking uses it because **1 hex digit = exactly 4 bits**, so long binary values become short.

## The 16 Digits

After 9, hex borrows letters:

|Hex|0–9|A|B|C|D|E|F|
|---|---|---|---|---|---|---|---|
|Decimal|0–9|10|11|12|13|14|15|

## The `0x` Prefix

`0x` is only a **label meaning "this number is hex"**, the same way `₹` means rupees.

- `0x0800` ≠ eight hundred. Without the label you can't tell `800` (decimal) from `800` (hex).
- Leading zeros don't change the value: `0x0800` = `0x800`. They are there because the field is a fixed 4 hex digits (2 bytes).

## Place Values

Decimal columns grow ×10 (1, 10, 100, 1000). Hex columns grow **×16**:

|Column|4th|3rd|2nd|1st|
|---|---|---|---|---|
|Worth|4096|256|16|1|

## Reading 0x0800

Multiply each digit by its column, then add:

```
  0      8      0      0
× 4096 × 256  × 16   × 1
= 0   + 2048 + 0    + 0   = 2048
```

So **`0x0800` = 2048**, the EtherType value for **IPv4**.

## Reading 0x86DD

```
  8       6      D(13)   D(13)
× 4096  × 256  × 16    × 1
= 32768 + 1536 + 208   + 13   = 34525
```

So **`0x86DD` = 34525**, the EtherType value for **IPv6**.

## Reading 0x0806

```
  0      8      0      6
× 4096 × 256  × 16   × 1
= 0   + 2048 + 0    + 6   = 2054
```

So **`0x0806` = 2054**, the EtherType value for **ARP**.

|EtherType|Protocol inside the frame|
|---|---|
|`0x0800`|IPv4|
|`0x0806`|ARP|
|`0x86DD`|IPv6|

## Counting Bytes in Hex

**2 hex digits = 1 byte**, because each digit is 4 bits. That's why Wireshark shows bytes as pairs (`00`, `9d`, `ff`).

Example: padding shown as `00000000000000000000` is 20 hex digits = **10 bytes**.

## Hex and Binary

Each hex digit maps to exactly **4 bits** (a *nibble*), so you can convert digit by digit:

|Hex|Binary|Hex|Binary|
|---|---|---|---|
|0|0000|8|1000|
|1|0001|9|1001|
|2|0010|A|1010|
|3|0011|B|1011|
|4|0100|C|1100|
|5|0101|D|1101|
|6|0110|E|1110|
|7|0111|F|1111|

```
0x0800  →  0000 1000 0000 0000   (16 bits = the 2-byte Type field)
```

A 48-bit MAC address would take 48 ones and zeros. In hex it's just **12 characters**: `AAAA.AA00.0001`.

## Where You'll See Hex in CCNA

- **MAC addresses**: `E8BA.7011.2874`
- **EtherType**: `0x0800` (IPv4), `0x0806` (ARP), `0x86DD` (IPv6)
- **Broadcast MAC**: `FFFF.FFFF.FFFF` (F = 1111, so every bit is 1)
- **IPv6 addresses**: `2001:db8::1`

## Exam Points

- Hex `10` = **16**, not ten. Hex `1F` = 16 + 15 = **31**.
- 1 hex digit = 4 bits, so 2 hex digits = 1 byte.
- Shortcut: Windows Calculator → **Programmer** mode converts instantly. Practice by hand first, though.

## Self-Test

1. What is `0x05DC` in decimal?
2. What is `0x0600` in decimal?
3. How many hex digits are in a 48-bit MAC address?

> [!success]- Answers  
> 1. 5×256 + 13×16 + 12 = **1500**. That's the largest *Length* value in an Ethernet frame!  
> 2. 6×256 = **1536**. That's the smallest *Type* value. Now you know where those two numbers come from.  
> 3. 48 ÷ 4 = **12**.

## Related

- [Bits and Bytes](Bits%20and%20Bytes.md)
- [Day 05 - Ethernet LAN Switching Part 1](../01%20-%20Course%20Days/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201.md)
