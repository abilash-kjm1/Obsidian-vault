---
tags:
  - ccna/subnetting
series: NetworkChuck - You Suck at Subnetting
episode: 3
---

# EP 3 - Private IP Addresses and NAT

[⬅️ EP 2 - We Ran Out of IP Addresses](EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses.md) · [EP 4 - Binary and Decimal Conversion ➡️](EP%204%20-%20Binary%20and%20Decimal%20Conversion.md)

**Series:** NetworkChuck · *You SUCK at Subnetting* · Episode 3
**Video:** [we're out of IP Addresses….but this saved us (Private IP Addresses)](https://www.youtube.com/watch?v=8bhvn9tQk8o) · 15:02 (sponsor segments skipped: 0:42–2:48 and from 13:47) · ▶ links jump to that moment
**Basics used here:** [Private IP Addresses](../Concepts/Private%20IP%20Addresses.md) · [IPv4 Address Classes](../Concepts/IPv4%20Address%20Classes.md) · [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

> [!abstract] The whole lesson in 3 lines  
> 1. **Public** IPs must be globally unique, and there aren't enough for every device.  
> 2. **RFC 1918** (1996) carved out **private** ranges (10/8, 172.16/12, 192.168/16) that every home and company can reuse, but they **can't reach the Internet** on their own.  
> 3. **NAT** on your router swaps all those private addresses for **one public IP** from your ISP. That "band-aid" kept IPv4 alive; the long-term fix is **IPv6** (2¹²⁸ addresses).

## 1. The Band-Aid: RFC 1918 ▶ [2:48](https://www.youtube.com/watch?v=8bhvn9tQk8o&t=168s)

![700](Attachments/EP%203%20-%20Private%20IP%20Addresses%20and%20NAT-1.png)

Recap: only 2³² ≈ 4.3 billion IPv4 addresses, badly managed (see [EP 2](EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses.md)). In **1996**, **RFC 1918** introduced **private IP addresses**: the band-aid's first half.

> [!info]- What's an RFC? (click)  
> **RFC** = *Request for Comments*: the numbered documents in which the **IETF** publishes Internet standards. They're free to read online. RFC 791 defines IP; RFC 1918 defines private addresses. → [Day 03](../01%20-%20Course%20Days/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works.md)

## 2. Public IP Addresses Must Be Unique ▶ [3:19](https://www.youtube.com/watch?v=8bhvn9tQk8o&t=199s)

![700](Attachments/EP%203%20-%20Private%20IP%20Addresses%20and%20NAT-2.png)

Everything we've covered so far = **public** addresses: reachable on the Internet. Think of the Internet as **one giant network**, so every address on it must be **unique**. If you and David Bombal both had `128.1.4.43`, it'd be like two people with the same phone number: both phones ring.

Problem: Chuck alone has **200+** devices at home. There's no way every device on Earth gets its own public IP.

## 3. Private Ranges ▶ [4:24](https://www.youtube.com/watch?v=8bhvn9tQk8o&t=264s)

![700](Attachments/EP%203%20-%20Private%20IP%20Addresses%20and%20NAT-3.png)

They took a chunk out of each class and declared it **private**:

|Class|Private range|Default mask|
|---|---|---|
|A|**10.0.0.0 – 10.255.255.255**|255.0.0.0|
|B|**172.16.0.0 – 172.31.255.255**|255.255.0.0|
|C|**192.168.0.0 – 192.168.255.255**|255.255.255.0|

That's why Chuck "knew" your home network was `192.168.1.0 / 255.255.255.0`: home routers use the private Class C range.

> [!warning] Common trap  
> The B range ends at **172.31**, not 172.255. `172.32.x.x` and above are public. → [why it's a /12 block](../Concepts/Private%20IP%20Addresses.md)

**Private addresses are NOT unique.** You, Chuck, David Bombal and Chuck's brother can all use `192.168.1.0`. That solves the shortage…

> [!important] …but creates a new problem  
> **Private addresses are not routable on the Internet.** Internet routers won't carry traffic to or from them. On its own, your `192.168.1.204` laptop **can't reach YouTube**.

## 4. The Other Half: NAT ▶ [5:57](https://www.youtube.com/watch?v=8bhvn9tQk8o&t=357s)

**NAT** = **N**etwork **A**ddress **T**ranslation. It runs on your **router** right now.

![700](Attachments/EP%203%20-%20Private%20IP%20Addresses%20and%20NAT-4.png)

① Your router gives every home device a **private** IP (`192.168.1.45`, `.89`, `.105`, `.25`…).
② Your **ISP** (Internet Service Provider, e.g. AT&T) lends your router **one public IP**, e.g. `11.5.4.28`.

![700](Attachments/EP%203%20-%20Private%20IP%20Addresses%20and%20NAT-5.png)

③ Your smart toilet (`192.168.1.25`) wants **networkchuck.coffee** (`23.227.38.65`, a public server).
④ As the packet leaves, the router **translates** the source `192.168.1.25` → `11.5.4.28`.
⑤ The server only ever sees `11.5.4.28`.

> [!tip] Analogy: an office reception desk  
> Every employee has an internal extension (private IP). Outsiders only see the company's one main number (public IP). The receptionist (NAT) connects calls out and routes each reply to the right extension.

## 5. See It Yourself: Two Different IPs ▶ [8:50](https://www.youtube.com/watch?v=8bhvn9tQk8o&t=530s)

|Where you look|What you see|Which kind|
|---|---|---|
|Google "**what is my IP address**"|Your router's address as the Internet sees it|**Public** (one per home)|
|`ipconfig` (Windows)|Your device's own address|**Private**, e.g. `192.168.1.204`, `10.7.1.203`|

![700](Attachments/EP%203%20-%20Private%20IP%20Addresses%20and%20NAT-6.png)

Every device in your home shares that **one public identity** when it reaches Netflix, YouTube or anything else.

## 6. The Reply Comes Back ▶ [9:33](https://www.youtube.com/watch?v=8bhvn9tQk8o&t=573s)

![700](Attachments/EP%203%20-%20Private%20IP%20Addresses%20and%20NAT-7.png)

The server replies to `11.5.4.28`. The router **remembers** which inside device started the conversation and forwards the reply to `192.168.1.25` (the toilet 🚽).

> [!info]- How does the router know which device the reply is for? (click)  
> The router keeps a **NAT translation table**. With many devices sharing one public IP (**PAT**, Port Address Translation, also called "NAT overload"), each conversation gets its own **port number** on the public side, e.g. `11.5.4.28:50001` ↔ `192.168.1.25`. The reply arrives on that port, and the table says who it belongs to. → [Day 44 - NAT Part 1](../01%20-%20Course%20Days/Day%2044%20-%20NAT%20Part%201.md)

Homes **and** big businesses work this way: private addresses inside, a few public addresses at the edge.

## 7. Still Not Enough: IPv6 ▶ [10:24](https://www.youtube.com/watch?v=8bhvn9tQk8o&t=624s)

![700](Attachments/EP%203%20-%20Private%20IP%20Addresses%20and%20NAT-8.png)

Even with private IPs and NAT, **IPv4 ran out**. Its successor is **IPv6** (there was no "IPv5" in practice):

| |**IPv4**|**IPv6**|
|---|---|---|
|Looks like|`192.168.1.0`|`2001:db8:3333:4444:5555:6666:7777:8888`|
|Size|32 bits → 2³² ≈ 4.3 billion|**128 bits → 2¹²⁸** (≈ 340 undecillion)|
|Format|4 decimal octets, dots|8 groups of [hex](../Concepts/Hexadecimal.md), colons|

- 2¹²⁸ is so big that every device can have its own **public** address, with plenty to spare.
- Your **phone on mobile data** already has a public IP, very often **IPv6** (AT&T, Bell, Orange…).
- IPv4 isn't going anywhere soon, so you still need to master it. IPv6 comes later in the course. → [Day 31 - IPv6 Part 1](../01%20-%20Course%20Days/Day%2031%20-%20IPv6%20Part%201.md)

## 8. Revision Sheet

|Concept|Remember|
|---|---|
|Public IP|Globally unique, routable on the Internet, from your ISP|
|Private IP|Reusable, **not** routable on the Internet|
|RFC 1918 (1996)|Defined the private ranges|
|Private ranges|**10.0.0.0/8 · 172.16.0.0–172.31.255.255 · 192.168.0.0/16**|
|NAT|Router translates private ↔ public addresses|
|ISP|Gives your home **one** public IP|
|Your public IP|Google "what is my IP"|
|Your private IP|`ipconfig`|
|IPv6|128 bits, 2¹²⁸ addresses, hex with colons; the long-term fix|

## 9. Test Yourself

Answer first, then click to check.

> [!question]- Which of these are private: `10.1.1.1`, `172.15.0.1`, `172.30.9.9`, `192.169.1.1`, `192.168.50.2`?  
> **Private:** `10.1.1.1`, `172.30.9.9`, `192.168.50.2`. **Public:** `172.15.0.1` (below 172.16) and `192.169.1.1` (not 192.168).

> [!question]- Why can't your laptop with `192.168.1.204` reach YouTube without NAT?  
> Private addresses **aren't routable on the Internet**. The router must translate it to its public IP.

> [!question]- Google says your IP is `11.5.4.28`, but `ipconfig` says `192.168.1.204`. Why?  
> Google sees your **public** IP (your router's, after NAT). `ipconfig` shows your device's **private** IP.

> [!question]- How many public IPv4 addresses does a typical home get from its ISP?  
> Usually **one**, shared by every device through NAT.

> [!question]- Can two companies both use `10.0.0.0/8` inside their networks?  
> **Yes.** Private addresses only need to be unique within each network.

> [!question]- What two "band-aids" kept IPv4 alive, and what's the real fix?  
> **Private addresses (RFC 1918) + NAT.** The real fix is **IPv6**.

> [!question]- How many bits in an IPv6 address vs an IPv4 address?  
> IPv6 = **128 bits** · IPv4 = **32 bits**

---

**Next:** Chuck says the series now focuses on IPv4 addresses and subnetting.
