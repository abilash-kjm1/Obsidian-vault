---
tags:
  - ccna/concept
course_days:
  - 13
  - 14
  - 15
---

# Concept: Subnetting (the 4-Step Method)

> [!abstract] In one line  
> To split one network into several, **borrow host bits** and turn them into network bits. Each borrowed bit **doubles** the number of networks and **halves** each network's size.

## Key Terms

|Term|Meaning|Example|
|---|---|---|
|**Network bits**|The 1s in the mask: the locked part|`11111111.11111111.11111111.11000000`|
|**Host bits**|The 0s in the mask: addresses inside the network|last 6 bits above|
|**CIDR / prefix**|Number of network bits, written as `/n`|255.255.255.192 = **/26**|
|**Increment** (block size)|Value of the **last network bit**: the gap between networks|64|

## The 4 Steps

**Example:** split `192.168.1.0/24` into **4** networks.

① **How many bits to borrow?** Find the first power of 2 that is ≥ the networks you need: 4 = 2² → **2 bits**.

|Bits borrowed|1|2|3|4|5|6|7|8|
|---|---|---|---|---|---|---|---|---|
|Networks (2ⁿ)|2|**4**|8|16|32|64|128|256|

② **Borrow (flip) them:** the first 2 host bits become 1s → `11000000` = **192** → mask **255.255.255.192 = /26**.

③ **Increment** = the value of the last network bit → in the [chart](Binary.md#The%20Powers-of-Two%20Chart) the 2nd bit is **64**.

④ **List the networks**, counting up by the increment:

|Network|Range|Broadcast|Usable hosts|
|---|---|---|---|
|192.168.1.**0**|.1 – .62|.63|62|
|192.168.1.**64**|.65 – .126|.127|62|
|192.168.1.**128**|.129 – .190|.191|62|
|192.168.1.**192**|.193 – .254|.255|62|

**Hosts per network** = 2^(host bits) − 2 = 2⁶ − 2 = **62**.

## /24 Cheat Table (last octet)

|Prefix|Mask (last octet)|Networks from a /24|Increment|Usable hosts|
|---|---|---|---|---|
|/25|128|2|128|126|
|/26|192|4|64|62|
|/27|224|8|32|30|
|/28|240|16|16|14|
|/29|248|32|8|6|
|/30|252|64|4|2|

> [!tip] Patterns  
> Increment = **256 − mask value** (256 − 192 = 64). Usable hosts = **increment − 2**.

## Exam Points

- More networks = borrow more bits = longer prefix = **fewer hosts** each.
- Need *n* networks → smallest 2ˣ ≥ n (17 networks → 32 → **5 bits**).
- First address = network ID, last = broadcast. Neither is usable.

## Self-Test

1. Split `192.168.1.0/24` into 5 networks. New mask? Increment?
2. What's the broadcast of the network starting at `192.168.1.64/26`?
3. How many usable hosts in a /28?

> [!success]- Answers  
> 1. Need 8 → **3 bits** → **/27 = 255.255.255.224**, increment **32** (.0, .32, .64 … .224: 8 networks, 30 hosts each)  
> 2. 64 + 64 − 1 = **192.168.1.127**  
> 3. 2⁴ − 2 = **14**

## Related

- [EP 6 - Subnet Your Home Network](../Subnetting%20Master%20-%20Network%20Chuck/EP%206%20-%20Subnet%20Your%20Home%20Network.md)
- [Binary](Binary.md) · [IPv4 Address Classes](IPv4%20Address%20Classes.md)
- [Day 13 - Subnetting Part 1](../01%20-%20Course%20Days/Day%2013%20-%20Subnetting%20Part%201.md)
