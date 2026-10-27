---
tags:
  - ccna/subnetting
series: NetworkChuck - You Suck at Subnetting
episode: 6
---

# EP 6 - Subnet Your Home Network

[⬅️ EP 5 - What is a Subnet Mask](EP%205%20-%20What%20is%20a%20Subnet%20Mask.md)

**Series:** NetworkChuck · *You SUCK at Subnetting* · Episode 6
**Video:** [let's subnet your home network // EP 6](https://www.youtube.com/watch?v=mJ_5qeqGOaI) · 9:39 (sponsor segments skipped: 0:45–1:58 and from 9:11) · ▶ links jump to that moment
**Basics used here:** [Subnetting (4-step method)](../Concepts/Subnetting.md) · [Binary](../Concepts/Binary.md) · [Private IP Addresses](../Concepts/Private%20IP%20Addresses.md)

> [!abstract] The whole lesson in 3 lines  
> 1. To split one network into several, **steal host bits** and turn them into network bits.  
> 2. Need **4** networks → 4 = 2² → steal **2** bits → `255.255.255.192` = **/26**.  
> 3. The **increment** (value of the last network bit = **64**) gives the ranges: .0–.63, .64–.127, .128–.191, .192–.255, with **62** usable hosts each.

## 1. The Goal ▶ [0:00](https://www.youtube.com/watch?v=mJ_5qeqGOaI&t=0s)

Your home network is one big flat network: `192.168.1.0/24`, mask `255.255.255.0`, **254** usable addresses. Every device (laptop, smart TV, toilet…) sits together, which is **insecure**.

The plan: split it into **4 smaller networks**: **Wireless**, **IoT**, **DMZ** and **Users**.

> [!info]- Why separate devices into different networks? (click)  
> If a cheap IoT camera gets hacked on a flat network, the attacker can reach everything. In separate networks, traffic between them has to pass a router or firewall, where it can be filtered.  
> - **IoT** = smart devices (bulbs, cameras, plugs)  
> - **DMZ** (demilitarized zone) = servers the Internet can reach, kept apart from your private stuff

## 2. Network Bits vs Host Bits ▶ [2:00](https://www.youtube.com/watch?v=mJ_5qeqGOaI&t=120s)

![700](Attachments/EP%206%20-%20Subnet%20Your%20Home%20Network-1.png)

Convert the mask to [binary](../Concepts/Binary.md):

```
255.255.255.0 = 11111111.11111111.11111111.00000000
                └──── 24 network bits ────┘└ 8 host bits ┘
```

- **1s = network bits**: describe the network.
- **0s = host bits**: room for devices.

> [!important] The core rule  
> **Need more networks? Steal host bits** and flip them to 1 (Chuck: "bring them over to the dark side").

## 3. Step ①: How Many Bits to Steal? ▶ [3:04](https://www.youtube.com/watch?v=mJ_5qeqGOaI&t=184s)

![700](Attachments/EP%206%20-%20Subnet%20Your%20Home%20Network-2.png)

Chuck adds a second chart under the usual one, the "brother" chart, where each value is doubled. Read it as **how many networks you get** from borrowing that many bits:

|Bits stolen|1|2|3|4|5|6|7|8|
|---|---|---|---|---|---|---|---|---|
|Networks|2|**4**|8|16|32|64|128|256|

Need **4** → that's at **2 bits**.

![700](Attachments/EP%206%20-%20Subnet%20Your%20Home%20Network-3.png)

What if you needed **17**? 16 isn't enough, so jump to **32** → **5 bits**. Always round **up** to the next power of 2.

## 4. Step ②: Steal the Bits → New Mask ▶ [4:27](https://www.youtube.com/watch?v=mJ_5qeqGOaI&t=267s)

![700](Attachments/EP%206%20-%20Subnet%20Your%20Home%20Network-4.png)

Flip the first 2 host bits:

```
11111111.11111111.11111111.11000000
                           └ 128 + 64 = 192
```

**New mask = 255.255.255.192**

**CIDR notation** = count the network bits: 8 + 8 + 8 + 2 = **/26**.

> [!info]- What is CIDR notation? (click)  
> **CIDR** (Classless Inter-Domain Routing) writes the mask as a slash and the number of 1-bits. `255.255.255.0` = **/24**, `255.255.255.192` = **/26**. It's shorter and is what you'll see everywhere (`192.168.1.0/26`).

## 5. Step ③: Find the Increment ▶ [5:23](https://www.youtube.com/watch?v=mJ_5qeqGOaI&t=323s)

![700](Attachments/EP%206%20-%20Subnet%20Your%20Home%20Network-5.png)

**Increment = the value of the last network bit.** In `11000000`, the last 1 sits under **64** → increment = **64**. It's the size of each new network.

> [!tip] Shortcut  
> Increment = **256 − last mask octet** → 256 − 192 = **64**.

## 6. Step ④: Create the Networks ▶ [6:07](https://www.youtube.com/watch?v=mJ_5qeqGOaI&t=367s)

Start at 0 and keep adding 64:

![700](Attachments/EP%206%20-%20Subnet%20Your%20Home%20Network-6.png)

|#|Use (Chuck's plan)|Network → Broadcast|
|---|---|---|
|1|Wireless|192.168.1.**0** – 192.168.1.**63**|
|2|IoT|192.168.1.**64** – 192.168.1.**127**|
|3|DMZ|192.168.1.**128** – 192.168.1.**191**|
|4|Users|192.168.1.**192** – 192.168.1.**255**|

All four use mask **255.255.255.192 /26**.

> [!warning] Off-by-one trap  
> The first network ends at **.63**, not .64. Counting from 0, 64 addresses = .0 to .63. The next network **starts** at .64.

## 7. How Many Hosts per Network? ▶ [7:03](https://www.youtube.com/watch?v=mJ_5qeqGOaI&t=423s)

![700](Attachments/EP%206%20-%20Subnet%20Your%20Home%20Network-7.png)

Host bits left = **6** (you borrowed 2 of the 8).

```
2^6 = 64 addresses − 2 (network + broadcast) = 62 usable hosts
```

You traded size for count: 1 network × 254 hosts became **4 networks × 62 hosts**.

## 8. Homework: 5 Networks ▶ [8:08](https://www.youtube.com/watch?v=mJ_5qeqGOaI&t=488s)

Chuck's challenge: split the same `192.168.1.0/24` into **5** networks. Give the mask (decimal and CIDR) and the ranges.

> [!success]- Answer (try first!)  
> ① 5 isn't a power of 2 → round up to **8** → **3 bits**  
> ② `11100000` = 224 → **255.255.255.224 = /27**  
> ③ Increment = **32**  
> ④ .0–.31 · .32–.63 · .64–.95 · .96–.127 · .128–.159 · .160–.191 · .192–.223 · .224–.255  
> That's **8** networks (use 5, keep 3 spare), each with 2⁵ − 2 = **30** usable hosts.

The same 4 steps work for Class A and B too. They just feel different at first. → [Subnetting cheat table](../Concepts/Subnetting.md#%2F24%20Cheat%20Table%20%28last%20octet%29)

## 9. Revision Sheet

|Step|Do|This example|
|---|---|---|
|①|Bits to steal = smallest 2ⁿ ≥ networks needed|4 → **2 bits**|
|②|Flip those host bits → new mask|**255.255.255.192 /26**|
|③|Increment = value of last network bit (or 256 − mask)|**64**|
|④|Count up by the increment|.0 · .64 · .128 · .192|
|Hosts|2^(host bits) − 2|2⁶ − 2 = **62**|

## 10. Test Yourself

Answer first, then click to check.

> [!question]- You need 3 networks from a /24. How many bits do you borrow, and what's the mask?  
> Round up to 4 → **2 bits** → **/26 (255.255.255.192)**

> [!question]- You need 17 networks. How many bits?  
> 16 < 17 ≤ 32 → **5 bits**

> [!question]- Mask 255.255.255.224: increment?  
> 256 − 224 = **32**

> [!question]- In 192.168.1.0/26, which network does 192.168.1.100 belong to?  
> **192.168.1.64/26** (range .64–.127)

> [!question]- What's the broadcast address of 192.168.1.128/26?  
> **192.168.1.191**

> [!question]- How many usable hosts in a /26?  
> 2⁶ − 2 = **62**

> [!question]- Borrowing more bits does what to the number of networks and to hosts per network?  
> Networks **double** per bit, hosts per network **halve** (roughly).
