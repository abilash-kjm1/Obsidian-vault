
---

# Ethernet LAN Switching (Part 1)

[⬅️ Day 04](Day%2004%20-%20Intro%20to%20the%20CLI.md) · [🏠 Dashboard](../00%20-%20Start%20Here/CCNA%20Dashboard.md) · [🗺️ Roadmap](../00%20-%20Start%20Here/Course%20Roadmap.md) · [Day 06 ➡️](Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202.md)

**Video:** [Ethernet LAN Switching (Part 1) | Day 5](https://www.youtube.com/watch?v=u2n762WG0Vo) · 38:13 · ▶ links jump to that moment
**Basics used here:** [Hexadecimal](../Concepts/Hexadecimal.md) · [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

> [!abstract] The whole lesson in 3 lines  
> 1. Data on a LAN travels inside an **Ethernet frame**, like a letter in an envelope.  
> 2. The envelope has a **To** and a **From** address: **MAC addresses**.  
> 3. A switch **learns** from the *From* address and **delivers** using the *To* address. If it doesn't know where *To* is yet, it **sends a copy everywhere** (floods).

## 1. Where This Fits

Ethernet = **Layer 1** (cables, signals: Day 02) + **Layer 2** (frames, MAC addresses: **today**).
**Switches work at Layer 2.** They read MAC addresses and never look at IP addresses (Layer 3).

## 2. What Is a LAN? ▶ [3:04](https://www.youtube.com/watch?v=u2n762WG0Vo&t=184s)

**LAN** = a network in a small area (a home, an office floor).

> [!tip] The one rule  
> **Routers separate LANs. Switches only make a LAN bigger.**

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-1.png)

There are **4 LANs**. Count the router ports that have something connected, not the switches. Red has two switches, but they connect to each other on one router port, so it's **1 LAN**. Blue has the same devices on **2 router ports**, so it's **2 LANs**.

## 3. Wrapping Data: PDUs ▶ [4:46](https://www.youtube.com/watch?v=u2n762WG0Vo&t=286s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-2.png)

Each layer adds its own label as data goes down the stack:
**Data → + L4 header = Segment → + L3 header = Packet → + L2 header & trailer = Frame**

The switch's job is moving **frames**.

## 4. The Ethernet Frame ▶ [5:43](https://www.youtube.com/watch?v=u2n762WG0Vo&t=343s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-3.png)

|Field|Size|Job (one line)|Envelope analogy|
|---|---|---|---|
|Preamble|7 B|"Get ready, sync your clock"|Knocking on the door|
|SFD|1 B|"Frame starts NOW"|"Here it is"|
|Destination MAC|6 B|Who it's for|**To:**|
|Source MAC|6 B|Who sent it|**From:**|
|Type / Length|2 B|What's inside (or how big it is)|"Contents: IPv4"|
|*(Packet)*|varies|The actual data|The letter|
|FCS|4 B|Was it damaged on the way?|Tamper seal|

B = [bytes](../Concepts/Bits%20and%20Bytes.md). Header + trailer = 7+1+6+6+2+4 = **26 bytes**.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-7.png)

> [!tip] Remember the sizes  
> **7-1-6-6-2 … 4**: "seven, one, six-six, two … four at the end."

## 5. Preamble and SFD ▶ [7:21](https://www.youtube.com/watch?v=u2n762WG0Vo&t=441s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-4.png)

- **Preamble** = `10101010` repeated 7 times.
- **SFD** = `10101011`. Same pattern, but the **last bit is 1**: "…11 = go!"

> [!info]- Why does the receiver need a "clock sync"? (click)  
> Bits arrive as a fast stream of signal changes. To read them correctly, the receiver must sample at exactly the right moments. The steady 1-0-1-0 rhythm of the preamble is like a band counting "1-2-3-4" before the song, so everyone locks onto the same beat. The SFD's `11` at the end says "the beat is over; real data starts next bit."

## 6. MAC Addresses (Destination and Source) ▶ [8:37](https://www.youtube.com/watch?v=u2n762WG0Vo&t=517s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-8.png)

A **MAC address** is the device's hardware ID, **burned in at the factory**. It is also called the **BIA** (Burned-In Address).

- **48 bits = 6 bytes**, written as **12 [hex](../Concepts/Hexadecimal.md) digits** → `E8BA.7011.2874`
- **First half = OUI**: identifies the **manufacturer** (e.g. Cisco).
- **Second half**: identifies the **device**.

```
E8BA.70 | 11.2874
  OUI   |  device
(maker) | (serial)
```

> [!info]- MAC vs IP: what's the difference? (click)  
> **MAC** = like your **Aadhaar number**. It's fixed to you and works only for local identification.  
> **IP** = like your **postal address**. You configure it, it changes if you move, and it's used to reach you across networks.  
> Switches use **MAC** (Layer 2). Routers use **IP** (Layer 3).

> [!info]- Why are MAC addresses written in hex? (click)  
> 48 ones and zeros are unreadable. Each [hex digit = 4 bits](../Concepts/Hexadecimal.md#Hex%20and%20Binary), so 48 bits become just **12 characters**. The dots (`AAAA.AA00.0001`) are only for readability.

## 7. Type / Length ▶ [9:32](https://www.youtube.com/watch?v=u2n762WG0Vo&t=572s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-5.png)

A **2-byte** field that tells the receiver how to read what's inside:

|Value|Meaning|
|---|---|
|**≤ 1500**|**Length**: "the data inside is this many bytes"|
|**≥ 1536**|**Type**: "the data inside is this protocol"|

|Protocol|Type value|In decimal|
|---|---|---|
|IPv4|[`0x0800`](../Concepts/Hexadecimal.md#Reading%200x0800)|2048|
|IPv6|[`0x86DD`](../Concepts/Hexadecimal.md#Reading%200x86DD)|34525|

> [!info]- What does `0x0800` mean, and how is it 2048? (click)  
> `0x` = "this number is in **hexadecimal**" (base 16). It's a label, like ₹.  
> Hex columns are worth **4096 · 256 · 16 · 1**:  
> `0×4096 + 8×256 + 0×16 + 0×1 = 2048`  
> Full explanation → [Hexadecimal](../Concepts/Hexadecimal.md)

> [!info]- Why 1500 and 1536? Where do those numbers come from? (click)  
> - **1500** is the biggest packet a normal Ethernet frame carries, so a *length* can never be more than 1500.  
> - **1536** = `0x0600`, a round number in hex. Every *type* code starts from there, so it can never be mistaken for a length.  
> - 1501–1535 is an unused gap that separates the two meanings.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201.png)

## 8. FCS: Error Check ▶ [11:40](https://www.youtube.com/watch?v=u2n762WG0Vo&t=700s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-6.png)

**FCS** (Frame Check Sequence) is **4 bytes** at the end of the frame. It uses a **CRC** (**C**yclic **R**edundancy **C**heck) to detect damage.

> [!info]- How does CRC catch errors? (simple version, click)  
> The sender runs a math formula over the whole frame and puts the result in the FCS. The receiver runs the **same formula** on what it received.  
> - Results match → the frame is fine.  
> - Results differ → a bit got corrupted → the frame is **dropped**.  
> It's like a parcel weighing 2.0 kg at the shop. If it weighs 1.7 kg at your door, something was lost on the way.

## 9. How a Switch Thinks ▶ [19:45](https://www.youtube.com/watch?v=u2n762WG0Vo&t=1185s)

Every switch keeps a **MAC address table**: a list of *which MAC lives behind which port*.

> [!important] The two rules (the core of this lesson)  
> **LEARN:** a frame arrives → write down its **SOURCE** MAC and the port it came in on.  
> **FORWARD:** look up the **DESTINATION** MAC.  
> - Found → send it out **that one port** (**known unicast**).  
> - Not found → send a copy out **every port except the one it came in on** (**unknown unicast → flood**).

> [!info]- Why learn from the SOURCE and not the destination? (click)  
> If a frame *came in* on port F0/1 *from* PC1, then PC1 is definitely reachable via F0/1. That's proof. The destination only tells you where the frame wants to go, not where that device actually is.

> [!info]- Why flood instead of just dropping an unknown frame? (click)  
> Dropping would break communication. Flooding guarantees the frame reaches the right device. Wrong devices simply ignore it (the destination MAC isn't theirs). When the right device replies, the switch learns its port, so the next frames go directly to it.

### Walkthrough: PC1 → PC2 (one switch)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-10.png)

PCs connect on **F0/1–F0/3** (**F** = FastEthernet = 100 Mbps).

**① PC1 sends to PC2:** a **unicast** frame (one destination).

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-11.png)

**② LEARN:** SW1 records `.0001 → F0/1`. This is a **dynamic** MAC address (learned, not typed in).

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-12.png)

**③ FORWARD?** `.0002` isn't in the table → **unknown unicast → flood** out F0/2 and F0/3. PC3 ignores it ❌, PC2 accepts it ✅.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-13.png)

**④ PC2 replies:** SW1 learns `.0002 → F0/2`. `.0001` is known → **forwarded** out F0/1 only. No flood.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-14.png)

**⑤ Cleanup:** on Cisco switches, a dynamic entry is **deleted after 5 minutes of silence**. It gets re-learned the moment the device talks again.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-15.png)

### Walkthrough: PC1 → PC3 (two switches) ▶ [26:22](https://www.youtube.com/watch?v=u2n762WG0Vo&t=1582s)

The same two rules run on **each switch independently**.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-16.png)

|Step|SW1|SW2|
|---|---|---|
|PC1 → PC3|learn `.0001 → F0/1`, flood|learn `.0001 → F0/3`, flood|
|PC3 → PC1 (reply)|learn `.0003 → F0/3`, forward|learn `.0003 → F0/1`, forward|

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-17.png)

> [!warning] Common trap  
> SW2 lists PC1 on **F0/3**, but PC1 isn't plugged into SW2. The table means "**go this way** to reach it," not "it's directly connected here."

## 10. Revision Sheet

|Concept|Remember|
|---|---|
|LAN boundary|Routers separate; switches expand|
|Frame fields|Preamble 7 · SFD 1 · Dst 6 · Src 6 · Type 2 · FCS 4 = **26 B**|
|Preamble / SFD|`10101010`×7 = clock sync / `10101011` = start|
|Type/Length|≤ 1500 length · ≥ 1536 type · IPv4 `0x0800` · IPv6 `0x86DD`|
|FCS|CRC → detects errors|
|MAC|48 bits · 12 hex · BIA · first 24 bits = OUI (maker)|
|Switch learns from|**Source** MAC|
|Switch forwards by|**Destination** MAC|
|Unknown unicast|**Flood** (all ports except incoming)|
|Known unicast|**Forward** (one port)|
|MAC aging (Cisco)|5 minutes|

## 11. Test Yourself

Answer first, then click to check.

> [!question]- Which field provides receiver clock synchronization?  
> **Preamble.** The SFD only marks where the preamble ends.

> [!question]- How long is a MAC address? (48 bits or 48 bytes?)  
> **48 bits** (6 bytes). 48 bytes would be 384 bits. → [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

> [!question]- What is the OUI of `E8BA.7011.2874`?  
> **`E8BA.70`**: the first 6 hex digits (24 bits), not the first 4.

> [!question]- Which field does a switch use to fill its MAC table?  
> **Source MAC**, paired with the port the frame arrived on.

> [!question]- What does a switch do with an unknown unicast frame?  
> **Floods** it out all ports **except** the one it arrived on.

> [!question]- The Type field says `0x86DD`. What's inside the frame?  
> An **IPv6** packet.

> [!question]- A frame's Type/Length is 1000. What does that mean?  
> 1000 ≤ 1500, so it's a **length**: the data inside is 1,000 bytes.

> [!question]- PC3 hasn't sent anything for 6 minutes. Is it still in the MAC table?  
> **No.** Dynamic entries age out after **5 minutes** of inactivity on Cisco switches.

---

## 🧠 Day Summary

### Explain the Main Concepts in My Own Words

Write without looking at the video.

### What I Still Do Not Understand

- 

_Still unclear after reviewing? Copy it to [Unresolved Questions](../04%20-%20Questions%20and%20Doubts/Unresolved%20Questions.md)._

### Review Checklist

- [ ] Watched
- [ ] Reviewed today's notes
- [ ] Answered "Test Yourself" from memory
- [ ] Revisited confusing concepts
