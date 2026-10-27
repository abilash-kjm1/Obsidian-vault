---
tags:
  - ccna/subnetting
series: NetworkChuck - You Suck at Subnetting
episode: 5
---

# EP 5 - What is a Subnet Mask?

[⬅️ EP 4 - Binary and Decimal Conversion](EP%204%20-%20Binary%20and%20Decimal%20Conversion.md) · [EP 6 - Subnet Your Home Network ➡️](EP%206%20-%20Subnet%20Your%20Home%20Network.md)

**Series:** NetworkChuck · *You SUCK at Subnetting* · Episode 5
**Video:** [What is a Subnet Mask??? (you NEED to know it!!)](https://www.youtube.com/watch?v=oZGZRtaGyG8) · 12:58 (sponsor segment skipped: 1:18–5:16) · ▶ links jump to that moment
**Basics used here:** [Binary](../Concepts/Binary.md) · [Subnetting](../Concepts/Subnetting.md) · [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

> [!abstract] The whole lesson in 3 lines  
> 1. In binary, the subnet mask is a row of **1s then 0s**. **1 = network bit** (locked), **0 = host bit** (free for devices).  
> 2. That's *why* the EP 1 hack works: `255` = `11111111` = 8 locked bits.  
> 3. **Hosts = 2^(number of 0s) − 2.** Want more hosts? Turn a 1 into a 0. Changing the mask to fit your needs = **subnetting**.

## 1. The Question: Why Does 255 Mean "Locked"? ▶ [0:00](https://www.youtube.com/watch?v=oZGZRtaGyG8&t=0s)

![700](Attachments/EP%205%20-%20What%20is%20a%20Subnet%20Mask-1.png)

Chuck's toilet 🚽: IP **192.168.32.5**, mask **255.255.255.0**.

From [EP 1](EP%201%20-%20What%20is%20an%20IP%20Address.md) we know the trick: a `255` in the mask freezes that octet of the IP. This episode explains **why**, by looking at both in binary.

## 2. The IP Address in Binary ▶ [5:16](https://www.youtube.com/watch?v=oZGZRtaGyG8&t=316s)

![700](Attachments/EP%205%20-%20What%20is%20a%20Subnet%20Mask-2.png)

Using the [EP 4](EP%204%20-%20Binary%20and%20Decimal%20Conversion.md) method (`128 64 32 16 8 4 2 1`):

```
192.168.32.5 = 11000000.10101000.00100000.00000101
```

## 3. The Mask in Binary ▶ [5:33](https://www.youtube.com/watch?v=oZGZRtaGyG8&t=333s)

**255:** every value fits (255−128 = 127, −64 = 63, −32 = 31 … down to 0), so **all 8 bits are on**: 128+64+32+16+8+4+2+1 = 255.
**0:** nothing fits, so all 8 bits are off.

![700](Attachments/EP%205%20-%20What%20is%20a%20Subnet%20Mask-3.png)

```
255.255.255.0 = 11111111.11111111.11111111.00000000
```

> [!tip] Remember  
> **255 = `11111111`** (all on) · **0 = `00000000`** (all off). No calculation needed.

## 4. What the 1s and 0s Mean ▶ [6:44](https://www.youtube.com/watch?v=oZGZRtaGyG8&t=404s)

![700](Attachments/EP%205%20-%20What%20is%20a%20Subnet%20Mask-4.png)

Line the mask up under the IP, bit by bit:

```
IP:    11000000.10101000.00100000.00000101
Mask:  11111111.11111111.11111111.00000000
       └──── network bits (1s) ──┘└ host bits (0s)┘
```

|Mask bit|Name|Means for the IP bit above it|
|---|---|---|
|**1**|**Network bit**|Locked: identifies *which network*. Same for every device on it.|
|**0**|**Host bit**|Free: identifies *which device* on that network|

> [!important] This is the "why" behind the hack  
> `255` = eight 1s = eight **network** bits, so that whole octet is locked. `0` = eight 0s = eight **host** bits, so that octet is free.

## 5. Counting Hosts: 2^(zeros) − 2 ▶ [8:06](https://www.youtube.com/watch?v=oZGZRtaGyG8&t=486s)

![700](Attachments/EP%205%20-%20What%20is%20a%20Subnet%20Mask-5.png)

Count the **0s** in the mask: **8**. Eight host bits can make 2⁸ different combinations:

```
2^8      = 256 addresses
256 − 2  = 254 usable hosts
```

The **− 2** = the **network address** (all host bits 0 → `192.168.32.0`) and the **broadcast address** (all host bits 1 → `192.168.32.255`).

> [!info]- Why 2 to the power of the zeros? (click)  
> Each host bit can be 0 or 1, so each extra bit **doubles** the combinations: 1 bit → 2, 2 bits → 4, 3 bits → 8 … 8 bits → 256. That's 2ⁿ. It's the same doubling as the binary chart. → [Binary](../Concepts/Binary.md)

## 6. Need 500 Hosts? Borrow a Network Bit ▶ [9:23](https://www.youtube.com/watch?v=oZGZRtaGyG8&t=563s)

254 isn't enough, so **turn the last 1 into a 0**, moving one bit to the host side:

![700](Attachments/EP%205%20-%20What%20is%20a%20Subnet%20Mask-6.png)

```
11111111.11111111.11111110.00000000   ← 9 zeros now
2^9 − 2 = 512 − 2 = 510 usable hosts ✅
```

Convert the 3rd octet back: `11111110` = 128+64+32+16+8+4+2 = **254**

![700](Attachments/EP%205%20-%20What%20is%20a%20Subnet%20Mask-7.png)

**New mask: 255.255.254.0** (= **/23**, 23 ones)

> [!important] That's subnetting  
> **Subnetting = changing the subnet mask to suit your needs.**
> - More **hosts** per network → more **0s** (shorter prefix).
> - More **networks** → more **1s** (longer prefix). That's what [EP 6](EP%206%20-%20Subnet%20Your%20Home%20Network.md) does.

## 7. Masks Are Contiguous ▶ [11:56](https://www.youtube.com/watch?v=oZGZRtaGyG8&t=716s)

The 1s are always **all together on the left** and the 0s **all together on the right**. A mask like `11101000` can't exist.

> [!tip] Exam use  
> That's why a valid mask octet can only be **0, 128, 192, 224, 240, 248, 252, 254 or 255**. If you see something like `255.255.255.100`, it's **not a valid mask**. → [values table](../Concepts/Binary.md#Values%20Worth%20Memorizing)

## 8. Revision Sheet

|Concept|Remember|
|---|---|
|Mask in binary|1s (network) then 0s (host), always contiguous|
|1 bit|Network bit: locked, identifies the network|
|0 bit|Host bit: free, identifies the device|
|255 / 0|`11111111` / `00000000`|
|Total addresses|2^(number of 0s)|
|Usable hosts|2^(number of 0s) − 2|
|/24 (255.255.255.0)|8 zeros → 254 hosts|
|/23 (255.255.254.0)|9 zeros → 510 hosts|
|More hosts|Turn 1s into 0s|
|More networks|Turn 0s into 1s|
|Valid mask octets|0, 128, 192, 224, 240, 248, 252, 254, 255|

## 9. Test Yourself

Answer first, then click to check.

> [!question]- Write 255.255.255.0 in binary. How many network bits and host bits?  
> `11111111.11111111.11111111.00000000` → **24** network, **8** host

> [!question]- How many usable hosts with 255.255.254.0?  
> 9 zeros → 2⁹ − 2 = **510**

> [!question]- How many usable hosts with 255.255.255.128?  
> `10000000` → 7 zeros → 2⁷ − 2 = **126**

> [!question]- You need 1,000 hosts in one network. How many host bits do you need, and what's the mask?  
> 2⁹ − 2 = 510 (too few), 2¹⁰ − 2 = **1022** ✅ → 10 zeros → `11111111.11111111.11111100.00000000` = **255.255.252.0 (/22)**

> [!question]- Is 255.255.255.100 a valid subnet mask?  
> **No.** 100 = `01100100`: the 1s aren't contiguous.

> [!question]- Why do we subtract 2 when counting usable hosts?  
> The **network address** (all host bits 0) and **broadcast address** (all host bits 1) can't be assigned to devices.

> [!question]- What does a 1 in the subnet mask tell you about the IP bit above it?  
> It's a **network bit**: the same for every device on that network.
