---
tags:
  - ccna/subnetting
series: NetworkChuck - You Suck at Subnetting
episode: 2
---

# EP 2 - We Ran Out of IP Addresses

[⬅️ EP 1 - What is an IP Address](EP%201%20-%20What%20is%20an%20IP%20Address.md)

**Series:** NetworkChuck · *You SUCK at Subnetting* · Episode 2
**Video:** [we ran OUT of IP Addresses!!](https://www.youtube.com/watch?v=tcae4TSSMo8) · 16:48 (sponsor segments skipped: 1:20–3:00 and from 15:50) · ▶ links jump to that moment
**Basics used here:** [IPv4 Address Classes](../Concepts/IPv4%20Address%20Classes.md) · [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md) · [Unicast and Broadcast](../Concepts/Unicast%20and%20Broadcast.md)

> [!abstract] The whole lesson in 3 lines  
> 1. IPv4 has only **2³² ≈ 4.3 billion** addresses, and they've **run out**.  
> 2. Early on they were split into **classes A–E** with fixed default masks. Class A handed single companies **16.7 million** addresses each, and big chunks (Class D, Class E, **127.x.x.x**) can't be used for hosts at all.  
> 3. Today networks are **classless**: big blocks are cut into smaller **subnets** with custom masks. That's what subnetting is.

## 1. Why We Ran Out ▶ [0:00](https://www.youtube.com/watch?v=tcae4TSSMo8&t=0s)

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-1.png)

- An IPv4 address is **32 bits**, so there are **2³² = 4,294,967,296** possible addresses (≈ 4.3 billion).
- When the Internet "launched" (TCP/IP on **1 Jan 1983**), that seemed limitless. Nobody predicted the Internet getting huge, or watches, ovens and toilets needing IPs.

Chuck's two complaints:
1. **There are IP addresses we can't use** (Class D, Class E, loopback).
2. **They gave away too many** (Class A blocks of 16 million to single companies).

> [!info]- Where does 2³² come from? (click)  
> 4 octets × 8 bits = **32 bits**. Each bit is 0 or 1, so the number of combinations is 2 × 2 × … (32 times) = 2³². → [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

## 2. The Address Classes ▶ [3:23](https://www.youtube.com/watch?v=tcae4TSSMo8&t=203s)

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-2.png)

|Class|First octet|Default mask|Hosts per network|Networks|
|---|---|---|---|---|
|**A**|1–126|255.0.0.0|16,777,214|126|
|**B**|128–191|255.255.0.0|65,534|16,384|
|**C**|192–223|255.255.255.0|254|2,097,152|
|**D**|224–239|—|— (multicast)||
|**E**|240–255|—|— (experimental)||

> [!warning] Fixes to the whiteboard  
> Chuck's chart ends Class B at `191.255.0.0` and Class C at `223.255.255.0`. The real ends are **191.255.255.255** and **223.255.255.255**. He also quotes 16,382 Class B and 2,097,150 Class C networks (older counting); the standard CCNA figures are **16,384** and **2,097,152**.

Why the ranges start at 128, 192, 224 and 240 (binary first bits) → [IPv4 Address Classes](../Concepts/IPv4%20Address%20Classes.md#How%20the%20Class%20Is%20Encoded%3A%20the%20First%20Bits)

> [!tip] The trade-off  
> **Bigger mask = more networks, fewer hosts each.** Class A: few networks, huge size. Class C: tons of networks, small size.

## 3. Class A: Way Too Big ▶ [4:38](https://www.youtube.com/watch?v=tcae4TSSMo8&t=278s)

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-3.png)

`1.0.0.0` with `255.0.0.0`: only the **first** octet is locked, so the other three are free:

```
2²⁴ − 2 = 16,777,214 hosts in ONE network
```

Compare your home network (`255.255.255.0`): **254** hosts.

Companies that were handed a whole Class A: **GE (3.x)**, **IBM (9.x)**, **AT&T (12.x)**, **Xerox (13.x)**, **HP (15.x)**. That's 16+ million addresses each.

> [!info]- Why "− 2"? (click)  
> In every network, the **first** address is the **network address** and the **last** is the **broadcast address**. Neither can be given to a device. → [EP 1, section 8](EP%201%20-%20What%20is%20an%20IP%20Address.md)

## 4. Cutting a Big Network Up: Your First Look at Subnetting ▶ [6:39](https://www.youtube.com/watch?v=tcae4TSSMo8&t=399s)

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-4.png)

**IANA** (Internet Assigned Numbers Authority; Chuck calls it the "head Oprah") **allocates** blocks to organisations. Nobody runs one network with 16 million hosts. IBM slices `9.0.0.0` into smaller pieces:

```
9.1.4.0   mask 255.255.255.0   →  "9.1.4" locked  →  256 addresses
```

The default mask (255.0.0.0) is just the **minimum**. You can always make the mask **longer** to create smaller networks.

## 5. Classful vs Classless ▶ [7:50](https://www.youtube.com/watch?v=tcae4TSSMo8&t=470s)

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-5.png)

|Term|Meaning|Example|
|---|---|---|
|**Classful**|Uses the class's **default** mask|`10.0.0.0` / `255.0.0.0`|
|**Classless**|Uses **any** mask|Chuck's home: `10.7.1.0` / `255.255.255.0` (a Class A address with a /24 mask)|

> [!important] Today everything is classless  
> Classes still tell you the **default**, but real networks use whatever mask fits. Carving networks to the right size = **subnetting**, the rest of this series.

## 6. Class B and Class C ▶ [8:44](https://www.youtube.com/watch?v=tcae4TSSMo8&t=524s)

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-6.png)

**Class B** `128.0.0.0` / `255.255.0.0`: first **2** octets locked → 2¹⁶ − 2 = **65,534** hosts per network. Still huge.

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-7.png)

**Class C** `192.0.0.0` / `255.255.255.0`: first **3** octets locked → **254** hosts per network, and over **2 million** networks. Chuck's verdict: if *every* block had been sized like this, IPv4 would have lasted much longer.

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-8.png)

## 7. Addresses We Can't Use: Class D and E ▶ [11:20](https://www.youtube.com/watch?v=tcae4TSSMo8&t=680s)

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-9.png)

|Class|Range|Reserved for|
|---|---|---|
|**D**|224–239|**Multicast**|
|**E**|240–255|**Experimental**|

Neither has a default mask, because you never assign them to a host.

> [!info]- What is multicast? (click)  
> **Unicast** = one sender → one receiver. **Broadcast** = one → *everyone* on the LAN. **Multicast** = one → a **chosen group** that subscribed (e.g. routers running OSPF listen on `224.0.0.5`, or a live video stream sent once to many viewers). → [Unicast and Broadcast](../Concepts/Unicast%20and%20Broadcast.md)

## 8. The Missing 127: Loopback ▶ [11:59](https://www.youtube.com/watch?v=tcae4TSSMo8&t=719s)

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-10.png)

Class A ends at **126** and Class B starts at **128**. The whole **127.0.0.0/8** block (16+ million addresses) is **loopback**: a virtual address that always means "**this computer**".

![700](Attachments/EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses-11.png)

Test it yourself (Command Prompt or Terminal):

```
ping 127.0.0.1
```

- **Ping** = "are you alive?" It sends an echo request and waits for a reply. It's the #1 troubleshooting tool.
- Replies from 127.0.0.1 mean your own computer's network software is working.
- **Any** 127.x.x.x works (e.g. `ping 127.15.15.8`). Chuck's complaint: one address would have been enough, but 16 million are reserved.

> [!tip] Memory trick  
> "There's no place like **127.0.0.1**" = there's no place like home.

## 9. Revision Sheet

|Concept|Remember|
|---|---|
|Total IPv4 addresses|2³² = 4,294,967,296 (≈ 4.3 billion)|
|Class A|1–126 · /8 · 16,777,214 hosts · 126 networks|
|Class B|128–191 · /16 · 65,534 hosts · 16,384 networks|
|Class C|192–223 · /24 · 254 hosts · 2,097,152 networks|
|Class D|224–239 · multicast|
|Class E|240–255 · experimental|
|127.x.x.x|Loopback, "this computer" · `ping 127.0.0.1`|
|Hosts formula|2ⁿ − 2 (n = host bits)|
|Classful|Default mask|
|Classless|Any mask; how real networks work|
|IANA|Assigns IP address blocks|
|Why we ran out|Too few addresses + wasteful classful allocation|

## 10. Test Yourself

Answer first, then click to check.

> [!question]- What class is `172.16.10.5`, and what's its default mask?  
> **Class B** (128–191) → **255.255.0.0**

> [!question]- What class is `200.1.1.1`? How many usable hosts with the default mask?  
> **Class C** → 255.255.255.0 → **254** hosts

> [!question]- Why can't you assign `230.1.1.1` to a PC?  
> It's **Class D (multicast)**: reserved for group communication, never a host address.

> [!question]- Your friend's PC is `10.7.1.50` with mask `255.255.255.0`. Classful or classless?  
> **Classless**: a Class A address (default /8) using a /24 mask.

> [!question]- What does `ping 127.0.0.1` test?  
> That **your own computer's** TCP/IP networking works (loopback). It never leaves the machine.

> [!question]- Where's the number 16,777,214 from?  
> A Class A mask leaves **24** host bits: 2²⁴ − 2 (network + broadcast) = **16,777,214**.

> [!question]- Why did IPv4 run out so fast?  
> Only 4.3 billion addresses, **classful** allocation gave huge blocks to single organisations, and large ranges (D, E, 127) can't be used for hosts, while the number of devices exploded.

> [!question]- Which octet do you look at to find the class?  
> The **first** octet.

---

**Next episode:** the "massive band-aid" that bought IPv4 more time (NAT and private addresses).
