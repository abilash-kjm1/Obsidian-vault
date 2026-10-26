---
tags:
  - ccna/concept
course_days:
  - 7
---

# Concept: IPv4 Address Classes

> [!abstract] In one line  
> The **first octet** of an IPv4 address tells you its **class** (A–E), and the class sets the **default subnet mask**, which decides how many **networks** exist and how many **hosts** each one holds.

## The Table (memorize this)

|Class|First octet|Range|Default mask|Prefix|Networks|Usable hosts per network|Used for|
|---|---|---|---|---|---|---|---|
|**A**|1–126|1.0.0.0 – 126.255.255.255|255.0.0.0|/8|126|**16,777,214**|Huge orgs|
|**B**|128–191|128.0.0.0 – 191.255.255.255|255.255.0.0|/16|16,384|**65,534**|Medium/large orgs|
|**C**|192–223|192.0.0.0 – 223.255.255.255|255.255.255.0|/24|2,097,152|**254**|Small networks|
|**D**|224–239|224.0.0.0 – 239.255.255.255|—|—|—|—|**Multicast**|
|**E**|240–255|240.0.0.0 – 255.255.255.255|—|—|—|—|**Experimental** (reserved)|

**Missing:** `127.x.x.x` = **loopback** (testing your own machine), and `0.x.x.x` is reserved too.

> [!tip] Memory trick for the first octets  
> **1 – 128 – 192 – 224 – 240**: each class starts where the one before it has used up **half** of the remaining space.

## How the Class Is Encoded: the First Bits

Write the first octet in **binary** and look at the leading bits:

|Class|First bits|First octet in binary|Decimal|
|---|---|---|---|
|A|**0**xxxxxxx|`00000000`–`01111111`|0–127|
|B|**10**xxxxxx|`10000000`–`10111111`|128–191|
|C|**110**xxxxx|`11000000`–`11011111`|192–223|
|D|**1110**xxxx|`11100000`–`11101111`|224–239|
|E|**1111**xxxx|`11110000`–`11111111`|240–255|

That's why the boundaries are 128, 192, 224 and 240: they're `10000000`, `11000000`, `11100000` and `11110000`. (Class A is formally 0–127, but 0 and 127 are reserved, leaving 1–126.)

## Where the Host Counts Come From

Host bits = the bits the default mask leaves as **0**:

|Class|Mask|Host bits|Calculation|
|---|---|---|---|
|A|255.0.0.0|24|2²⁴ − 2 = **16,777,214**|
|B|255.255.0.0|16|2¹⁶ − 2 = **65,534**|
|C|255.255.255.0|8|2⁸ − 2 = **254**|

**− 2** = the **network address** (all host bits 0) and the **broadcast address** (all host bits 1) can't be given to devices.

Networks: A = 2⁷ = 128 minus 2 reserved = **126** · B = 2¹⁴ = **16,384** · C = 2²¹ = **2,097,152**.

## Classful vs Classless

- **Classful** = using the class's **default mask** (`10.0.0.0 /8`).
- **Classless** = using **any** mask you like (`10.7.1.0 /24`). This is how real networks work today: big blocks are cut into smaller **subnets**.
- The class tells you the *default*. The mask actually configured tells you the *real* network size.

## Exam Points

- Identify the class from the **first octet** alone.
- Know the default masks: A = /8, B = /16, C = /24.
- **127.x.x.x = loopback**; D = multicast; E = experimental.
- Host formula: **2ⁿ − 2** (n = host bits).

## Self-Test

1. What class is `172.16.5.4`? Default mask?
2. What class is `10.7.1.0`, and is `10.7.1.0 255.255.255.0` classful or classless?
3. Why does Class B start at 128?
4. How many usable hosts in a Class B network?

> [!success]- Answers  
> 1. **Class B** (128–191) → **255.255.0.0**  
> 2. **Class A**. With a /24 mask instead of /8 it's **classless**.  
> 3. 128 = `10000000`: Class B addresses start with the bits **10**.  
> 4. 2¹⁶ − 2 = **65,534**

## Related

- [EP 2 - We Ran Out of IP Addresses](../Subnetting%20Master%20-%20Network%20Chuck/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses.md)
- [Day 07 - IPv4 Addressing Part 1](../01%20-%20Course%20Days/Day%2007%20-%20IPv4%20Addressing%20Part%201.md)
- [Bits and Bytes](Bits%20and%20Bytes.md) · [Unicast and Broadcast](Unicast%20and%20Broadcast.md)
