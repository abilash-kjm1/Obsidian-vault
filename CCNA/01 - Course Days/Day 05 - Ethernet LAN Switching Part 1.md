
---

# Ethernet LAN Switching (Part 1) — Complete Study Notes

[⬅️ Day 04](Day%2004%20-%20Intro%20to%20the%20CLI.md) · [🏠 Dashboard](../00%20-%20Start%20Here/CCNA%20Dashboard.md) · [🗺️ Roadmap](../00%20-%20Start%20Here/Course%20Roadmap.md) · [Day 06 ➡️](Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202.md)

**Video:** [Free CCNA | Ethernet LAN Switching (Part 1) | Day 5](https://www.youtube.com/watch?v=u2n762WG0Vo) · Jeremy's IT Lab · 38:13
_Timestamps like ▶ 4:20 jump to that point in the video._

> [!abstract] The Big Picture  
> Ethernet is the Layer 2 protocol used in virtually every LAN. Data is wrapped in an **Ethernet frame** (header + trailer). Switches read the **source MAC address** of each frame to *learn* where devices are, and the **destination MAC address** to decide whether to *forward* the frame out one port or *flood* it out all ports.

## 1. Quick Review — Layers 1 and 2

Ethernet covers **Layer 1 (Physical)** and **Layer 2 (Data Link)**. Layer 1 (cables, connectors, signals) was Day 02, so this lesson is about Layer 2.

|Layer|What it does|
|---|---|
|Layer 1 — Physical|Physical characteristics of the medium: voltage levels, max distances (UTP = 100 m), connectors, cable specs. Bits → electrical/radio signals.|
|Layer 2 — Data Link|Node-to-node data transfer (PC ↔ switch, switch ↔ router, router ↔ router). Formats data for the physical medium, detects (and possibly corrects) Layer 1 errors, uses **Layer 2 addressing** (MAC), separate from Layer 3 (IP).|

> [!important] Remember  
> **Switches operate at Layer 2.** IP addresses are Layer 3, **not** Layer 2.

## 2. Local Area Networks (LANs) ▶ [3:04](https://www.youtube.com/watch?v=u2n762WG0Vo&t=184s)

A **LAN** is a network contained within a relatively small area, such as an office floor or your home network.

- **Routers separate LANs.** Each router interface connects a different LAN.
- **Switches do not separate LANs.** Adding switches just *expands* an existing LAN.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-1.png)

How many LANs are in the diagram? **Four.**

- **LAN 1 (green):** 3 PCs + 1 switch + the router interface they connect to.
- **LAN 2 (red):** two switches connected *to each other* → still **one** LAN.
- **LANs 3 and 4 (blue):** the same devices as red, but each switch connects to a *different router interface* → **two separate** LANs.

> [!tip] Memory trick  
> Count the **router interfaces** with something connected, not the switches. Each one is a separate LAN.

This lesson covers traffic **within** a LAN (for example, PC → PC in LAN 2). Traffic **between** LANs (routing) comes later.

## 3. PDUs — Data, Segment, Packet, Frame ▶ [4:46](https://www.youtube.com/watch?v=u2n762WG0Vo&t=286s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-2.png)

|Added|PDU name|
|---|---|
|Upper-layer data|**Data**|
|+ Layer 4 header|**Segment**|
|+ Layer 3 header|**Packet**|
|+ Layer 2 header **and trailer**|**Frame**|

The Layer 2 PDU is a **frame**. Today's focus is how switches receive and forward **Ethernet frames**.

## 4. The Ethernet Frame ▶ [5:43](https://www.youtube.com/watch?v=u2n762WG0Vo&t=343s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-3.png)

An Ethernet frame = **Ethernet header + packet + Ethernet trailer**.

**Header (5 fields):**

1. **Preamble**: synchronization
2. **SFD** (Start Frame Delimiter): marks the end of the preamble
3. **Destination**: Layer 2 (MAC) address the frame is sent to
4. **Source**: Layer 2 (MAC) address of the sender
5. **Type** (or **Length**): which Layer 3 protocol is inside (almost always IPv4 or IPv6), or the length of the data

**Trailer (1 field):**

- **FCS** (Frame Check Sequence): lets the receiver detect transmission errors

## 5. Preamble and SFD ▶ [7:21](https://www.youtube.com/watch?v=u2n762WG0Vo&t=441s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-4.png)

|Field|Length|Bit pattern|Purpose|
|---|---|---|---|
|Preamble|7 bytes (56 bits)|`10101010` × 7|Lets the receiver **synchronize its receiver clock**|
|SFD|1 byte (8 bits)|`10101011`|Marks the **end of the preamble** and the start of the rest of the frame|

> [!tip] Memory trick  
> The SFD looks like a preamble byte, but its **last bit flips to 1** — "…11 = go!"

## 6. Destination and Source ▶ [8:37](https://www.youtube.com/watch?v=u2n762WG0Vo&t=517s)

- Show who is **receiving** and who is **sending** the frame (like the To/From on an email or a letter).
- They contain **MAC addresses**. MAC = **Media Access Control**.
- Each is **6 bytes (48 bits)**: the physical address of the device.

## 7. Type / Length ▶ [9:32](https://www.youtube.com/watch?v=u2n762WG0Vo&t=572s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-5.png)

A **2-byte (16-bit)** field that means one of two things, depending on its value:

|Value|Meaning|
|---|---|
|**1500 or less**|**LENGTH** of the encapsulated packet, in bytes (e.g. 1400 = a 1,400-byte packet)|
|**1536 or greater**|**TYPE** of the encapsulated packet (the length is worked out by other methods)|

|Protocol|Hex value|Decimal|
|---|---|---|
|IPv4|`0x0800`|2048|
|IPv6|`0x86DD`|34525|

The `0x` prefix means the number is written in **hexadecimal**.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201.png)

## 8. Frame Check Sequence (FCS) ▶ [11:40](https://www.youtube.com/watch?v=u2n762WG0Vo&t=700s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-6.png)

- The **only field in the Ethernet trailer**.
- **4 bytes (32 bits)**.
- Detects corrupted data by running a **CRC** algorithm over the received data.
- **CRC = Cyclic Redundancy Check.**
  - *Cyclic*: based on "cyclic codes".
  - *Redundancy*: the 4 bytes enlarge the frame without adding new information.
  - *Check*: it verifies the data for errors.

> [!important] CCNA level  
> You don't need the CRC math. Just remember: **FCS = error detection using a CRC.**

## 9. Ethernet Frame Field Sizes ▶ [12:53](https://www.youtube.com/watch?v=u2n762WG0Vo&t=773s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-7.png)

|Field|Bytes|
|---|---|
|Preamble|7|
|SFD|1|
|Destination MAC|6|
|Source MAC|6|
|Type / Length|2|
|FCS (trailer)|4|
|**Total (header + trailer)**|**26 bytes**|

> [!tip] Memory trick  
> **7-1-6-6-2 … 4** → "seven, one, six-six, two … and four at the end" = 26.

## 10. MAC Addresses ▶ [13:53](https://www.youtube.com/watch?v=u2n762WG0Vo&t=833s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-8.png)

- **6-byte (48-bit)** physical address assigned to the device **when it is made**.
  - Different from an IP address, which you configure yourself.
- Also called the **BIA (Burned-In Address)**.
- **Globally unique**: no two devices should share one. (Locally administered addresses exist, but they're rare.)
- Written as **12 hexadecimal characters**.

|Part|Bytes|Meaning|
|---|---|---|
|First half|3 bytes (24 bits)|**OUI**: Organizationally Unique Identifier, assigned to the **manufacturer**|
|Second half|3 bytes (24 bits)|Unique to the **device itself**|

**Example:** `E8BA.7011.2874` → OUI = `E8BA.70`, device part = `11.2874`

Common ways to write a MAC address:

```
AAAA.AA00.0001          (Cisco style: dot every 4 characters)
AA.AA.AA.00.00.01       (dot every 2 characters)
```

## 11. Hexadecimal Basics ▶ [15:19](https://www.youtube.com/watch?v=u2n762WG0Vo&t=919s)

- **Decimal** uses 10 digits: `0–9`. After 9 you add a **tens** column.
- **Hexadecimal** uses 16 digits: `0–9` then `A–F`. After F you add a **sixteens** column.

|Hex|A|B|C|D|E|F|
|---|---|---|---|---|---|---|
|Decimal|10|11|12|13|14|15|

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-9.png)

- Hex `10` = 1 sixteen + 0 ones = **decimal 16**.
- Hex `11` = 16 + 1 = **decimal 17**.
- Hex `1F` = 16 + 15 = **decimal 31**.

> [!note]  
> Hex comes up again in detail with IPv6. For now, just understand how it counts.

## 12. How a Switch Learns and Forwards (One Switch) ▶ [19:45](https://www.youtube.com/watch?v=u2n762WG0Vo&t=1185s)

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-10.png)

Setup: PC1, PC2 and PC3 connect to SW1 on **F0/1, F0/2, F0/3**. "F" = **FastEthernet** (100 Mbps). All three PCs share the OUI `AAAA.AA`, so they're from the same maker.

### Step 1 — PC1 sends a unicast frame to PC2

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-11.png)

**Unicast frame:** a frame destined for a **single** target (PC2 here).

### Step 2 — SW1 learns PC1's MAC from the SOURCE address

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-12.png)

SW1 reads the **source MAC** (`.0001`) and adds it to its **MAC address table** with the interface it arrived on (**F0/1**).

- This is a **dynamically learned MAC address** ("dynamic MAC address"): the switch learned it by itself, rather than it being configured manually.

> [!important] The most important idea in this lesson  
> Switches **learn** from the **SOURCE** MAC address and **forward** based on the **DESTINATION** MAC address.

### Step 3 — Unknown unicast → FLOOD

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-13.png)

SW1 has no entry for the destination (`.0002`). That makes it an **unknown unicast frame**, so the switch **floods** it:

- **Flood** = send a copy out of **all interfaces except the one it was received on** (here F0/2 and F0/3, not F0/1).
- **PC3** sees the destination MAC isn't its own → **drops** the frame.
- **PC2** sees the destination MAC matches → processes it up the OSI stack.

If PC1 sends PC2 another frame, SW1 **still floods it**, because PC2 hasn't sent anything yet, so SW1 can't have learned PC2's MAC.

### Step 4 — PC2 replies → SW1 learns PC2, known unicast → FORWARD

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-14.png)

- The frame's source and destination are now reversed (Src `.0002`, Dst `.0001`).
- SW1 learns `.0002` → **F0/2**.
- The destination `.0001` **is** in the table → **known unicast frame** → **forwarded** out F0/1 only (no flooding).
- PC1 de-encapsulates it up the stack.

### MAC address aging

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-15.png)

On Cisco switches, **dynamic MAC addresses are removed after 5 minutes of inactivity**. If the device sends traffic again, the switch simply learns it again.

## 13. Two Switches Example ▶ [26:22](https://www.youtube.com/watch?v=u2n762WG0Vo&t=1582s)

Topology: PC1 and PC2 on **SW1** (F0/1, F0/2), PC3 and PC4 on **SW2** (F0/1, F0/2). SW1 F0/3 ↔ SW2 F0/3. Both MAC tables start empty. **PC1 sends to PC3.**

1. **SW1** learns `.0001` → F0/1. The destination `.0003` is unknown → **floods** out F0/2 and F0/3. PC2 drops it.
2. **SW2** receives it on F0/3, learns `.0001` → **F0/3**. The destination is still unknown → **floods** out F0/1 and F0/2. PC4 drops it; PC3 accepts it.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-16.png)

3. **PC3 replies** to PC1. SW2 learns `.0003` → F0/1. The destination `.0001` is **known** → forwarded out F0/3.
4. **SW1** learns `.0003` → **F0/3**. The destination `.0001` is known → forwarded out F0/1 to PC1.

![700](Attachments/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201-17.png)

|SW1 MAC table||SW2 MAC table||
|---|---|---|---|
|**MAC**|**Interface**|**MAC**|**Interface**|
|.0001|F0/1|.0001|F0/3|
|.0003|F0/3|.0003|F0/1|

> [!warning] Common confusion  
> The interface in a MAC table is **the interface used to reach** that MAC, **not** necessarily a direct connection. SW2 lists PC1 on F0/3 even though PC1 is plugged into SW1.

## 14. Frame Types and What the Switch Does

|Frame type|Meaning|Switch action|
|---|---|---|
|**Unicast**|Destined for a single device|Depends on the MAC table ↓|
|**Unknown unicast**|Destination MAC **not** in the MAC table|**Flood**: out all ports except the receiving port|
|**Known unicast**|Destination MAC **is** in the MAC table|**Forward**: out the matching port only|
|Broadcast|(covered in Part 2)|—|

## 15. Quick Revision Sheet

- LAN = network in a small area; **routers separate LANs**, switches expand them.
- PDUs: Data → **Segment** (L4) → **Packet** (L3) → **Frame** (L2).
- Ethernet header: **Preamble 7 · SFD 1 · Dest 6 · Source 6 · Type/Length 2**. Trailer: **FCS 4**. Total = **26 bytes**.
- Preamble = `10101010` × 7 → **clock synchronization**.
- SFD = `10101011` → **end of the preamble**.
- Type/Length: **≤ 1500 = length**, **≥ 1536 = type**. IPv4 = `0x0800`, IPv6 = `0x86DD`.
- FCS = **CRC** (Cyclic Redundancy Check) → **error detection**.
- MAC = **Media Access Control**, **48 bits / 6 bytes / 12 hex digits**, a.k.a. **BIA**.
- **OUI** = first 24 bits = the manufacturer.
- Hex: A–F = 10–15; hex `10` = 16.
- Switch **learns from the SOURCE MAC**, **forwards by the DESTINATION MAC**.
- Unknown unicast → **flood**; known unicast → **forward**.
- Dynamic MACs age out after **5 minutes** of inactivity (Cisco).

## 16. Active Recall Flashcards

### Q1. Which field provides receiver clock synchronization?

Answer: The **Preamble** (7 bytes of `10101010`).

### Q2. What does the SFD do, and what is its bit pattern?

Answer: It marks the end of the preamble and the start of the frame. Its pattern is `10101011`.

### Q3. How long is a MAC address?

Answer: 48 bits = 6 bytes = 12 hex characters.

### Q4. What does a Type/Length value of 1400 mean? What about 0x0800?

Answer: 1400 (≤ 1500) = the packet is 1,400 bytes long. `0x0800` (2048, ≥ 1536) = the packet type is IPv4.

### Q5. What does FCS stand for, and what does it use?

Answer: Frame Check Sequence. It uses a CRC (Cyclic Redundancy Check) to detect errors.

### Q6. What is the OUI?

Answer: The first 3 bytes (24 bits) of a MAC address, assigned to the manufacturer.

### Q7. Which field does a switch use to populate its MAC table?

Answer: The **source** MAC address.

### Q8. What does a switch do with an unknown unicast frame?

Answer: Floods it out all interfaces except the one it was received on.

### Q9. How long until a dynamic MAC is removed on a Cisco switch?

Answer: 5 minutes of inactivity.

### Q10. What is hex `1A` in decimal?

Answer: 16 + 10 = **26**.

## 17. Video Quiz ▶ [31:31](https://www.youtube.com/watch?v=u2n762WG0Vo&t=1891s)

1. Which field of an Ethernet frame provides receiver clock synchronization?
   a) Preamble b) SFD c) Type d) FCS
2. How long is the physical address of a network device?
   a) 32 bytes b) 32 bits c) 48 bytes d) 48 bits
3. What is the OUI of `E8BA.7011.2874`?
   a) E8BA b) E8BA.70 c) 7011 d) E8BA.7011
4. Which field does a switch use to populate its MAC address table?
   a) Preamble b) Length c) Source MAC d) Destination MAC
5. What kind of frame does a switch flood out all interfaces except the one it was received on?
   a) Unknown unicast b) Known unicast c) Allcast

### Quiz Answers

1. **a) Preamble.** The SFD only marks the end of the preamble; Type identifies the packet; FCS detects errors.
2. **d) 48 bits.** 48 bytes would be 384 bits. (An IPv4 address is 32 bits.)
3. **b) E8BA.70.** The OUI is the first half (24 bits).
4. **c) Source MAC.** It's linked to the interface the frame arrived on.
5. **a) Unknown unicast.** Known unicast is forwarded, not flooded. "Allcast" doesn't exist.

## 18. Common Mistakes

- Thinking switches create separate LANs. Only **routers** separate LANs.
- Mixing up **bits and bytes**: a MAC is 48 **bits**, not 48 bytes.
- Saying the switch learns from the **destination** MAC. It learns from the **source**.
- Thinking the MAC table interface means "directly connected." It means "the way to reach it."
- Forgetting the switch **never floods back out the receiving port**.
- Treating the Type/Length field as always a type. **≤ 1500 means length.**
- Calling the OUI the first 4 hex digits. It's the first **6** hex digits (3 bytes).

---

## 🧠 Day Summary

### What I Learned

1.
2.
3.

### Explain the Main Concepts in My Own Words

Write without looking at the video.

### What I Still Do Not Understand

- 

_Still unclear after reviewing? Copy it to [Unresolved Questions](../04%20-%20Questions%20and%20Doubts/Unresolved%20Questions.md)._

### Review Checklist

- [ ] Watched
- [ ] Reviewed today's notes
- [ ] Answered the flashcards from memory
- [ ] Revisited confusing concepts
