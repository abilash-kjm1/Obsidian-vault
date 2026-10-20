---
course: Jeremy's IT Lab CCNA 200-301
course_day: 6
status: Not Started
date_started:
date_completed:
tags:
  - ccna/course-day
---

# Ethernet LAN Switching (Part 2)

[⬅️ Day 05](Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201.md) · [🏠 Dashboard](../00%20-%20Start%20Here/CCNA%20Dashboard.md) · [🗺️ Roadmap](../00%20-%20Start%20Here/Course%20Roadmap.md) · [Day 07 ➡️](Day%2007%20-%20IPv4%20Addressing%20Part%201.md)

**Video:** [Ethernet LAN Switching (Part 2) | Day 6](https://www.youtube.com/watch?v=5q1pqdmdPjo) · 33:41 · ▶ links jump to that moment
**Basics used here:** [Hexadecimal](../Concepts/Hexadecimal.md) · [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md) · [Unicast and Broadcast](../Concepts/Unicast%20and%20Broadcast.md)

> [!abstract] The whole lesson in 3 lines  
> 1. You type an **IP address**, but switches deliver by **MAC address**. So before sending, a PC must find out the destination's MAC.  
> 2. **ARP** finds it: shout "Who has this IP?" to everyone (**broadcast**), and only the owner answers (**unicast**).  
> 3. Then normal traffic (like **ping**) flows, and you can inspect it with `show arp`, `show mac address-table` and Wireshark.

## 1. Ethernet Frame: Two Corrections to Day 05 ▶ [1:02](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=62s)

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-1.png)

**Header + trailer = 18 bytes, not 26.** The Preamble + SFD (8 B) are *sent with* every frame but usually **not counted as part of the header**.

```
Dest 6 + Source 6 + Type 2 + FCS 4 = 18 bytes
```

> [!info]- So is it 26 or 18? (click)  
> Both are "right." It depends on whether you count the Preamble + SFD.  
> - **26 B** = with Preamble + SFD (Day 05's slide)  
> - **18 B** = the usual definition, and the one used for the **minimum size** maths below  
> Think of the Preamble + SFD as the doorbell before the parcel: it always rings, but it isn't part of the parcel.

**Minimum frame size = 64 bytes** (header + payload + trailer, *not* counting the Preamble + SFD).

```
64 − 18 = 46 bytes  →  minimum payload
```

If the packet is smaller than 46 bytes, the sender adds **padding**: zero bytes that fill the gap.
Example: a 34-byte packet + **12 bytes of padding** = 46.

> [!info]- Why does Ethernet need a minimum size at all? (click)  
> On old shared Ethernet, a sender had to still be transmitting when a collision signal came back, so it could notice the collision. Tiny frames finished too fast to notice. 64 bytes was long enough. The rule stayed for compatibility. For CCNA, just remember **64 / 46 / padding with 0s**.

## 2. The Problem: I Know the IP, Not the MAC ▶ [2:33](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=153s)

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-2.png)

New setup: **GigabitEthernet** ports (`G0/0`, `G0/1`, `G0/2`), realistic MACs, and IPs on one network `192.168.1.0/24` (PC1 = `.1` … PC4 = `.4`). Short names: PC1 = `.9D00`, PC3 = `.3900`.

A frame carries a **packet** inside, and the packet has its own **source and destination IP**. So every message has **two pairs of addresses**:

|Layer|Address|Who uses it|
|---|---|---|
|L3: packet|Source/Destination **IP**|End-to-end: "who is this really for"|
|L2: frame|Source/Destination **MAC**|Local delivery: what **switches** read|

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-3.png)

PC1 wants to reach `192.168.1.3`. It knows its own IP and MAC and PC3's IP, but **PC3's MAC = ???**
Users type IP addresses, never MACs, so the PC has to discover the MAC itself.

## 3. ARP: Address Resolution Protocol ▶ [6:19](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=379s)

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-4.png)

**ARP finds the MAC address (L2) for a known IP address (L3).** It uses two messages:

|Message|Sent by|Sent as|Destination MAC|
|---|---|---|---|
|**ARP Request**|The one who asks|**Broadcast** (everyone)|`FFFF.FFFF.FFFF`|
|**ARP Reply**|The owner of the IP|**Unicast** (just the asker)|The asker's MAC|

> [!tip] Analogy  
> In a classroom you shout, "**Who is Rahul?** Tell me." Everyone hears it (broadcast). Only Rahul answers, directly to you (unicast).

> [!info]- Why can the reply be unicast but the request can't? (click)  
> The asker doesn't know the target's MAC, so it can only shout to everyone. But the request carries the **asker's own MAC** as its source, so the replier already knows exactly where to send the answer.

### Walkthrough: PC1 asks for PC3's MAC ▶ [7:37](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=457s)

**① PC1 builds an ARP request:** destination MAC = **`FFFF.FFFF.FFFF`** ([broadcast](../Concepts/Unicast%20and%20Broadcast.md)).

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-5.png)

**② SW1** learns `.9D00 → G0/0` (dynamic) and **floods** the broadcast out G0/1 and G0/2. PC2 checks the *target IP* (`.3`), sees it isn't its own, and **ignores it** ❌.

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-6.png)

**③ SW2** learns `.9D00 → G0/2` and floods out G0/0 and G0/1. PC4 ignores it ❌. **PC3: "That's my IP!"** ✅

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-7.png)

**④ PC3 sends an ARP reply (unicast)** to `.9D00`. SW2 learns `.3900 → G0/0`. The destination is in its table, so this is a **known unicast** and it's **forwarded**, not flooded. SW1 does the same, and PC1 receives it.

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-8.png)

**⑤ PC1 saves `192.168.1.3 → 0C2F.B06A.3900` in its ARP table**, so it doesn't need to ask again for a while.

> [!warning] Don't mix up the two tables  
> |Table|Lives on|Maps|Command|
> |---|---|---|---|
> |**ARP table**|PCs, routers|**IP → MAC**|`arp -a` (PC) · `show arp` (Cisco)|
> |**MAC address table**|Switches|**MAC → port**|`show mac address-table`|

### ARP table on a PC ▶ [11:58](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=718s)

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-9.png)

```
arp -a        ← Windows, macOS and Linux
```

|Column|Meaning|
|---|---|
|Internet Address|IP address (L3)|
|Physical Address|MAC address (L2)|
|Type **static**|A default, built-in entry|
|Type **dynamic**|**Learned through ARP**|

## 4. Ping: Testing Reachability ▶ [15:30](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=930s)

**Ping** checks whether a device can be reached and measures the **round-trip time** (there and back). It uses two **ICMP** messages: **Echo Request** → **Echo Reply**. Both are **unicast**.

```
ping 192.168.1.3
```

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-10.png)

Because ping is unicast, it **needs the destination MAC first**. That's why ARP always runs before the first ping to a new device.

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-11.png)

Reading Cisco's ping output:

|Part|Meaning|
|---|---|
|`Sending 5, 100-byte ICMP Echos`|Cisco default: **5 pings × 100 bytes**|
|`!`|Success|
|`.`|Failed (timed out)|
|`.!!!!` → `80 percent (4/5)`|First one failed, the rest succeeded|
|`min/avg/max = 20/20/22 ms`|Round-trip times|

> [!info]- Why did the first ping fail? (click)  
> PC1 didn't know PC3's MAC yet. While ARP was asking and waiting for the answer, the first echo request timed out. Once ARP finished, pings 2–5 worked. **A first `.` followed by `!!!!` is normal and points to ARP**, not a network problem.

`show arp` (Cisco, privileged EXEC) shows PC1's ARP table: its own entry, plus `192.168.1.3 → 0c2f.b06a.3900`.

### What it looks like in Wireshark ▶ [18:26](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=1106s)

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-12.png)

1. **ARP:** `Who has 192.168.1.3? Tell 192.168.1.1` (destination = Broadcast)
2. **ARP:** `192.168.1.3 is at 0c:2f:b0:6a:39:00` (unicast to PC1)
3. **4 × ICMP echo request/reply** pairs

> [!note] Tools mentioned  
> **Wireshark** captures packets so you can read every field. **GNS3** runs real Cisco IOS (free to use, but you need your own IOS images). **Packet Tracer** simulates devices and is free. It's used for this course's labs.

## 5. The MAC Address Table on a Cisco Switch ▶ [20:50](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=1250s)

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-13.png)

```
show mac address-table
```

|Column|Meaning|
|---|---|
|**Vlan**|Virtual LAN (default **1**; covered later)|
|**Mac Address**|The learned MAC|
|**Type**|**DYNAMIC** = learned automatically|
|**Ports**|The interface used to reach that MAC|

> [!warning] Watch the hyphens  
> It's `mac address-table`: a **space**, then a hyphen. Old IOS used `mac-address-table`. Exam options play tricks with these hyphens.

### Clearing entries ▶ [22:03](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=1323s)

Dynamic entries **age out after 5 minutes** without traffic. You can also clear them yourself:

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-14.png)

```
clear mac address-table dynamic                             ← all dynamic entries
clear mac address-table dynamic address 0c2f.b011.9d00      ← one MAC
clear mac address-table dynamic interface gi0/0             ← everything learned on one port
```

## 6. Proof in Wireshark: Padding and EtherType ▶ [24:11](https://www.youtube.com/watch?v=5q1pqdmdPjo&t=1451s)

**Padding.** A 36-byte ping (`ping 192.168.1.3 size 36`) is 10 bytes short of the 46-byte minimum → **10 bytes of padding**:

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-15.png)

`00000000000000000000` = 20 hex digits = **10 bytes**, because [2 hex digits = 1 byte](../Concepts/Hexadecimal.md#Counting%20Bytes%20in%20Hex).

**EtherType.** The Type field tells you what's inside:

![700](Attachments/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202-16.png)

|Type|Inside|
|---|---|
|[`0x0800`](../Concepts/Hexadecimal.md#Reading%200x0800)|IPv4|
|[`0x0806`](../Concepts/Hexadecimal.md#Reading%200x0806)|**ARP** (new today)|
|[`0x86DD`](../Concepts/Hexadecimal.md#Reading%200x86DD)|IPv6|

## 7. Revision Sheet

|Concept|Remember|
|---|---|
|Header + trailer|**18 B** (without Preamble + SFD); 26 B with them|
|Minimum frame|**64 B** → minimum payload **46 B** → padding with `00` bytes|
|ARP|Known **IP → find MAC**|
|ARP request|**Broadcast**, dest MAC `FFFF.FFFF.FFFF`|
|ARP reply|**Unicast** to the asker|
|ARP table|IP → MAC on hosts · `arp -a` · `show arp`|
|MAC table|MAC → port on switches · `show mac address-table`|
|MAC table columns|**Vlan, Mac Address, Type, Ports**|
|Ping|ICMP **Echo Request / Echo Reply**, unicast; Cisco default 5 × 100 B|
|`!` / `.`|Success / timeout (the first `.` is usually ARP)|
|Flooded frames|**Broadcast** + **unknown unicast**|
|Clear table|`clear mac address-table dynamic [address X / interface Y]`|
|EtherTypes|IPv4 `0x0800` · ARP `0x0806` · IPv6 `0x86DD`|

## 8. Test Yourself

Answer first, then click to check.

> [!question]- You ping with a 36-byte payload and see a run of zeros at the end of the Ethernet payload. What are they?  
> **Padding bytes.** 46 − 36 = 10 bytes of zeros, added to reach the 46-byte minimum payload.

> [!question]- Which message is sent to all hosts on the LAN: ARP request, ARP reply, ICMP echo request or ICMP echo reply?  
> **ARP request.** The other three are unicast.

> [!question]- What fields does `show mac address-table` display?  
> **Vlan, Mac Address, Type, Ports.** ("Internet Address, Physical Address, Type" is the output of `arp -a` on a PC.)

> [!question]- Which frame types does a switch flood?  
> **Broadcast and unknown unicast.** Known unicast is forwarded out one port.

> [!question]- Which command clears all dynamic MACs learned on one interface?  
> `clear mac address-table dynamic interface <interface-id>`. Note the space after `mac` and the hyphen in `address-table`.

> [!question]- PC2 receives PC1's ARP request for 192.168.1.3. Why does it ignore it?  
> The **target IP** in the ARP request isn't PC2's IP. (The destination MAC is broadcast, so PC2 has to check the IP.)

> [!question]- Your first ping shows `.!!!!`. Is the network broken?  
> **No.** The first echo timed out while ARP was learning the MAC. After that, all pings succeeded.

> [!question]- What's the minimum Ethernet frame size, and what's the minimum payload?  
> **64 bytes** frame (without Preamble + SFD) → **46 bytes** payload.

> [!question]- A frame's Type field is `0x0806`. What's inside?  
> An **ARP** message.

---

## 🧪 Lab Video (notes not made yet)

**Analyzing Ethernet Switching - Day 6 Lab** · 10:29 · [Watch on YouTube](https://www.youtube.com/watch?v=Ig0dSaOQDI8)

- [ ] Watched
- [ ] Lab completed
