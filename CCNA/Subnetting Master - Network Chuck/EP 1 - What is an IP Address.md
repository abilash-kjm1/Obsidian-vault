---
tags:
  - ccna/subnetting
series: NetworkChuck - You Suck at Subnetting
episode: 1
---

# EP 1 - What is an IP Address?

[EP 2 - We Ran Out of IP Addresses ➡️](EP%202%20-%20We%20Ran%20Out%20of%20IP%20Addresses.md)

**Series:** NetworkChuck · *You SUCK at Subnetting* · Episode 1
**Video:** [what is an IP Address? // EP 1](https://www.youtube.com/watch?v=5WfiTHiU4x8) · 18:45 (the lesson ends at 15:45; the rest is a sponsor) · ▶ links jump to that moment
**Basics used here:** [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md) · [Unicast and Broadcast](../Concepts/Unicast%20and%20Broadcast.md) · [TCP-IP Model](../Concepts/TCP-IP%20Model.md) · Course version: [Day 07 - IPv4 Addressing](../01%20-%20Course%20Days/Day%2007%20-%20IPv4%20Addressing%20Part%201.md)

> [!abstract] The whole lesson in 3 lines  
> 1. An **IP address** is a device's "phone number" on a network. Your **router** hands them out automatically (**DHCP**).  
> 2. The **subnet mask** tells you which part of the address is the **network** (the street) and which part is the **host** (the house number). A `255` octet is locked; a `0` octet is free.  
> 3. Same network → talk directly. Different network → send it to the **default gateway** (your router). With `255.255.255.0` you get 256 addresses, of which **254 are usable** for devices.

## 1. What an IP Address Is ▶ [1:37](https://www.youtube.com/watch?v=5WfiTHiU4x8&t=97s)

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-1.png)

**IP** = **I**nternet **P**rotocol. An IP address is like a **phone number** for each device. Without one, a device can't talk to anything else, local or on the Internet.

> [!info]- Where does IP fit in the layers? (click)  
> IP addresses belong to **Layer 3** (Internet / Network layer): they identify **hosts** end to end across networks, and routers forward using them. → [TCP-IP Model](../Concepts/TCP-IP%20Model.md)

## 2. Find Your Own IP Address ▶ [2:17](https://www.youtube.com/watch?v=5WfiTHiU4x8&t=137s)

|Device|How|
|---|---|
|**Windows**|Open **Command Prompt** → `ipconfig`|
|**macOS**|Terminal → `ifconfig`|
|**Linux**|Terminal → `ip addr` (older systems: `ifconfig`)|
|**Phone**|Settings → Wi-Fi → tap your network|

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-2.png)

Look for three lines:

|Line|Example|Nickname in the video|Job|
|---|---|---|---|
|**IPv4 Address**|`192.168.1.204`|The star|This device's address|
|**Subnet Mask** (aka **netmask**)|`255.255.255.0`|"Mr. Subnet Mask"|Which part = network, which part = host|
|**Default Gateway** (aka **default router**)|`192.168.1.1`|"Ms. Default Gateway"|Where to send traffic for **other** networks|

The "v4" in IPv4 is the version. Ignore it for now (IPv6 is a different format).

## 3. Who Gives Out IP Addresses? ▶ [3:35](https://www.youtube.com/watch?v=5WfiTHiU4x8&t=215s)

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-3.png)

Your home **router** does. Every device that joins the network is handed an address automatically ("you get an IP, and you get an IP!" — hence Chuck calls the router **Oprah**). The protocol doing this is **DHCP** (Dynamic Host Configuration Protocol). → Course version: [Day 39 - DHCP](../01%20-%20Course%20Days/Day%2039%20-%20DHCP.md)

## 4. Anatomy: Octets ▶ [4:28](https://www.youtube.com/watch?v=5WfiTHiU4x8&t=268s)

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-4.png)

An IPv4 address = **4 numbers separated by 3 dots**. Each number is an **octet** and can be anything from **0 to 255**.

> [!info]- Why "octet", and why exactly 0–255? (click)  
> Each number is stored as **8 bits** (*octo* = eight). 8 bits can hold 2⁸ = **256** different values: `00000000` = 0 up to `11111111` = **255**. So 4 octets = **32 bits** = one IPv4 address. → [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

## 5. The Subnet Mask Hack: 255 = Locked, 0 = Free ▶ [5:17](https://www.youtube.com/watch?v=5WfiTHiU4x8&t=317s)

Line the mask up with the address, octet by octet:

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-5.png)

```
IP address:   192 . 168 .   1 . 204
Subnet mask:  255 . 255 . 255 .   0
              └── locked (same for ─┘   └ free (0–255,
                  every device here)      different per device)
```

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-6.png)

- **255** → that octet **never changes** inside this network.
- **0** → that octet **can be anything** from 0 to 255; it's different for each device.

So every device on this home network starts with **`192.168.1.`**

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-7.png)

|Part|Here|Name|
|---|---|---|
|Locked part|`192.168.1`|**Network portion**|
|Free part|`204`|**Host portion** (each device = a **host**)|

> [!warning] The hack has limits  
> It only works when every mask octet is **255** or **0**. Masks like `255.255.255.192` need real subnetting, which the rest of this series teaches.

> [!info]- Why does almost everyone's address start with 192.168.1? (click)  
> **192.168.x.x** is a **private** address range, reserved for home and office networks (never used directly on the Internet). Most home routers ship configured to hand out `192.168.1.x` or `192.168.0.x`, so millions of homes use the same addresses without conflict.

## 6. The Street Analogy ▶ [7:23](https://www.youtube.com/watch?v=5WfiTHiU4x8&t=443s)

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-8.png)

|Street analogy|IP address|
|---|---|
|Street name: **Privet Drive**|**Network portion** `192.168.1`|
|House number: **4**, 5, 6…|**Host portion** `.204`, `.48`, `.105`…|
|Walk next door to hand Bernard (#6) the coffee|Same network → send **directly**|
|Need **UPS** to reach Dr. Strange on Bleecker Street|Different network → send to the **default gateway**|

## 7. Talking to Another Network: the Default Gateway ▶ [9:46](https://www.youtube.com/watch?v=5WfiTHiU4x8&t=586s)

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-9.png)

Your laptop (`192.168.1.48`) wants **netflix.com** (`3.225.92.8`):

① The laptop compares Netflix's address with its own, using the subnet mask.
② Netflix doesn't start with `192.168.1` → **not my network**.
③ So the laptop sends the traffic to the **default gateway** `192.168.1.1` (the router).
④ The router knows how to forward it toward Netflix.

> [!important] Core rule  
> **Same network → deliver directly. Different network → hand it to the default gateway.**
> The router plays both roles from this lesson: it **hands out IP addresses** (DHCP) *and* it's the **default gateway**.

## 8. How Many Devices Fit? ▶ [11:11](https://www.youtube.com/watch?v=5WfiTHiU4x8&t=671s)

With `192.168.1.x` and mask `255.255.255.0`, the last octet can be 0–255 = **256 addresses**. But two are reserved:

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-10.png)

|Address|Name|Why you can't give it to a device|
|---|---|---|
|`192.168.1.0` (first)|**Network address**|Names the network itself (the "street")|
|`192.168.1.255` (last)|**Broadcast address**|Anything sent here goes to **every** device ("Chatty Kathy"). → [Broadcast](../Concepts/Unicast%20and%20Broadcast.md)|

```
256 total − 2 reserved = 254 usable host addresses
254 − 1 for the router (192.168.1.1) = 253 left for your other devices
```

> [!warning] Caption check  
> The auto-captions say "250 usable" here, but the arithmetic Chuck describes (256 minus 3) gives **253**. On exams, "**usable host addresses**" for a `/24` (`255.255.255.0`) = **254**, because the router is a host too.

## 9. Recap ▶ [13:38](https://www.youtube.com/watch?v=5WfiTHiU4x8&t=818s)

![700](Attachments/EP%201%20-%20What%20is%20an%20IP%20Address-11.png)

## 10. Revision Sheet

|Concept|Remember|
|---|---|
|IP address|Device's "phone number"; 4 octets, e.g. `192.168.1.204`|
|Octet|8 bits → 0–255; 4 octets = 32 bits|
|Find it|`ipconfig` (Windows) · `ifconfig` (Mac) · `ip addr` (Linux)|
|Who assigns it|Router, using **DHCP**|
|Subnet mask|`255` octet = locked (network) · `0` octet = free (host)|
|Network portion|The street (same for every device on the network)|
|Host portion|The house number (unique per device)|
|Default gateway|The router; used for any **other** network|
|192.168.x.x|Private range used in homes and offices|
|Network address|First address (`.0`), not usable|
|Broadcast address|Last address (`.255`), reaches everyone, not usable|
|Usable hosts (`255.255.255.0`)|256 − 2 = **254** (253 after the router)|

## 11. Test Yourself

Answer first, then click to check.

> [!question]- Your PC is `192.168.1.204` with mask `255.255.255.0`. Which part is the network and which is the host?  
> Network = **192.168.1** · Host = **204**

> [!question]- Is `192.168.1.77` on the same network as your PC? What about `192.168.2.77`?  
> `192.168.1.77` → **yes** (first three octets match). `192.168.2.77` → **no**: the third octet differs, so traffic goes via the default gateway.

> [!question]- Your laptop wants to reach `3.225.92.8`. Where does it send the traffic first?  
> To the **default gateway** (`192.168.1.1`), because that address isn't on its own network.

> [!question]- Why can't a device use `192.168.1.0` or `192.168.1.255`?  
> `.0` is the **network address** and `.255` is the **broadcast address**. Both are reserved.

> [!question]- How many usable host addresses does `255.255.255.0` give?  
> **254** (256 − network − broadcast).

> [!question]- What gives your phone its IP address when it joins home Wi-Fi?  
> The **router**, using **DHCP**.

> [!question]- Why can an octet never be 256 or higher?  
> An octet is **8 bits**, and the biggest 8-bit number is `11111111` = **255**.

> [!question]- On a Windows PC, which command shows the IP address, subnet mask and default gateway?  
> **`ipconfig`**
