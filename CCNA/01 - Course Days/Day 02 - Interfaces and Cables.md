---
course: Jeremy's IT Lab CCNA 200-301
course_day: 2
status: Not Started
date_started:
date_completed:
tags:
  - ccna/course-day
---

# Interfaces and Cables

[⬅️ Day 01](Day%2001%20-%20Network%20Devices.md) · [🏠 Dashboard](../00%20-%20Start%20Here/CCNA%20Dashboard.md) · [🗺️ Roadmap](../00%20-%20Start%20Here/Course%20Roadmap.md) · [Day 03 ➡️](Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works.md)

**Video:** [Interfaces and Cables | Day 2](https://www.youtube.com/watch?v=ieTH5lVhNaY) · 35:52 · ▶ links jump to that moment
**Basics used here:** [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

> [!abstract] The whole lesson in 3 lines  
> 1. Devices connect with **copper UTP** (cheap, up to **100 m**) or **fiber-optic** (pricier, **long distances**). Both are defined by **Ethernet** standards (IEEE 802.3).  
> 2. In 10/100 Mbps copper, one wire pair **sends** and another **receives**. Which pins do which depends on the device, so the right cable (**straight-through** or **crossover**) matters. Modern ports fix this automatically (**Auto MDI-X**).  
> 3. Fiber comes in **multimode** (shorter and cheaper) and **single-mode** (longest and most expensive).

## 1. Can You Read This Label? ▶ [0:53](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=53s)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-16.png)

`10/100/1000Base-T Ports (1–24) — Ports are Auto-MDIX`

By the end of this note you'll be able to decode every part of it. (Answer in [section 10](#10.%20Decoding%20the%20Label).)

An **interface** = a **port**: the socket you plug a cable into. Switches have many, because lots of end hosts connect to them.

## 2. RJ-45: The Ethernet Plug ▶ [1:44](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=104s)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-17.png)

**RJ-45** (**R**egistered **J**ack) is the port and plug used on **copper** Ethernet cables. It's the same plug as your home internet cable.

![500](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-18.png)

## 3. Why Standards Exist ▶ [2:30](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=150s)

**Ethernet** isn't one thing. It's a **collection of protocols and standards** for wired LANs.

> [!tip] Analogy  
> One person speaks only English and the other only Japanese, so nothing gets communicated. A **standard** is the shared language. That applies to **physical** things (plug shape, cable type) and **logical** ones (IP).
> If cable makers and switch makers didn't agree on the plug, your cable simply wouldn't fit.

## 4. Speed Is Measured in Bits ▶ [4:20](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=260s)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-19.png)

- **Bit** = one `0` or `1`. On copper, a change in the electrical signal = a bit.
- **Byte** = **8 bits**.
- Network speed = **bits per second** (Kbps, Mbps, Gbps), because data travels **one bit at a time**.
- Storage uses **bytes**. So 1 **G*B*** = 8 × 1 **G*b***.

Each unit is **× 1,000** the last: kilo → mega → giga → tera. → [Speed Units](../Concepts/Bits%20and%20Bytes.md#Speed%20Units)

## 5. Copper Ethernet Standards ▶ [6:51](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=411s)

All Ethernet standards live under **IEEE 802.3** (IEEE = Institute of Electrical and Electronics Engineers).

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-20.png)

|Speed|Common name|IEEE standard|Informal name|Max length|
|---|---|---|---|---|
|10 Mbps|Ethernet|802.3i|10BASE-T|100 m|
|100 Mbps|Fast Ethernet|802.3u|100BASE-T|100 m|
|1 Gbps|Gigabit Ethernet|802.3ab|1000BASE-T|100 m|
|10 Gbps|10 Gig Ethernet|802.3an|10GBASE-T|100 m|

> [!info]- How to read "100BASE-T" (click)  
> **100** = speed in Mbps (10G = 10 Gbps) · **BASE** = baseband signalling (beyond CCNA) · **T** = **twisted pair** copper.  
> So "1000BASE-T" = 1 Gbps over twisted pair.

> [!tip] Remember  
> **Every copper (twisted pair) standard maxes out at 100 m.** Only the speed and the 802.3 letters change.  
> Letter trick: **i** (10) → **u** (100) → **ab** (1G) → **an** (10G).

## 6. UTP: Unshielded Twisted Pair ▶ [9:10](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=550s)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-21.png)

- **Unshielded**: no metal shield, so it can pick up interference.
- **Twisted pair**: **4 pairs = 8 wires**, twisted together. The twist protects against **EMI** (electromagnetic interference).
- The RJ-45 plug has **8 pins**, one per wire.

> [!info]- Why does twisting reduce interference? (click)  
> Noise from nearby electrical sources hits both wires of a pair. Because they keep swapping positions, both pick up roughly the **same** noise, and the receiver only reads the **difference** between the two wires. The noise cancels out.

## 7. Which Pins Send, Which Receive (10BASE-T and 100BASE-T) ▶ [10:24](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=624s)

10 and 100 Mbps use only **2 pairs (4 wires)**: pins **1 & 2** and **3 & 6**.

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-22.png)

|Device|Transmits (Tx) on|Receives (Rx) on|
|---|---|---|
|Router, Firewall, PC|**1 & 2**|**3 & 6**|
|**Switch**|**3 & 6**|**1 & 2**|

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-26.png)

> [!tip] Memory trick  
> **The switch is the odd one out.** Everyone else talks on 1-2 and listens on 3-6. The switch does the opposite, because it sits in the middle and has to listen where everyone else talks.

**Full-duplex**: one pair sends while the other receives, so **both sides can talk at the same time** with no collisions.

## 8. Straight-Through vs Crossover Cables ▶ [14:16](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=856s)

**Rule:** one side's **Tx** pins must land on the other side's **Rx** pins.

**Straight-through** (pin 1 → 1, 2 → 2, …) works when the two devices are **different** types (PC/router ↔ switch):

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-23.png)

Connect two **same-type** devices with a straight-through cable and Tx hits Tx. **Nothing works**:

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-24.png)

**Crossover** swaps the pairs (1 → 3, 2 → 6, 3 → 1, 6 → 2), so Tx meets Rx again:

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-25.png)

|Connection|Cable|
|---|---|
|PC ↔ Switch, Router ↔ Switch|**Straight-through**|
|Switch ↔ Switch, Router ↔ Router, PC ↔ PC|**Crossover**|
|**PC ↔ Router**|**Crossover** (both transmit on 1 & 2!)|

> [!warning] Common trap  
> PC ↔ Router looks like "different devices," but both are in the **1&2-transmit group**. So it needs a **crossover**. Think *same group*, not *same device*.

## 9. Auto MDI-X: The Modern Fix ▶ [18:08](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=1088s)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-27.png)

**Auto MDI-X** lets a port **detect which pins its neighbor transmits on and adjust itself**. With it, **either cable type works**. Most modern devices have it. Straight-through vs crossover only matters on **old** equipment, but it is still tested.

### Gigabit and 10G copper ▶ [19:19](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=1159s)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-28.png)

**1000BASE-T** and **10GBASE-T** use **all 4 pairs** (adding **4 & 5** and **7 & 8**), and **each pair is bidirectional**: it both sends and receives. That's part of how they get much faster.

## 10. Decoding the Label

`10/100/1000Base-T Ports (1–24) — Ports are Auto-MDIX` means:

- **10/100/1000Base-T**: the copper ports run at 10 Mbps, 100 Mbps or 1 Gbps over twisted pair.
- **Ports (1–24)**: 24 RJ-45 ports.
- **Auto-MDIX**: straight-through or crossover, either cable works.

## 11. Fiber-Optic Connections ▶ [20:18](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=1218s)

When **100 m isn't enough**, use fiber. It sends **light through glass** instead of electricity through copper.

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-29.png)

Fiber ports take an **SFP transceiver** (**S**mall **F**orm-factor **P**luggable), a little module you slide in, and the fiber cable plugs into that.

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-30.png)

There are **two connectors on each end**: one strand transmits and one receives (Tx → Rx in each direction). Copper uses separate *pairs* inside one cable. Fiber uses separate *strands*.

### Inside the cable ▶ [22:08](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=1328s)

![600](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-31.png)

1. **Core**: the glass the light travels through
2. **Cladding**: reflects light back into the core
3. **Buffer**: protects the glass from breaking
4. **Jacket**: the outer cover

> [!info]- How does light stay inside a bent cable? (click)  
> The cladding acts like a mirror wall around the core. Light hitting it at a shallow angle bounces back inside, again and again, all the way to the other end. That's why fiber can bend round corners.

## 12. Multimode vs Single-Mode Fiber ▶ [22:45](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=1365s)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-32.png)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-33.png)

| |**Multimode (MMF)**|**Single-mode (SMF)**|
|---|---|---|
|Core|**Wider**|**Narrower**|
|Light|**Many angles** (modes) bounce down it|**One angle** goes straight down it|
|Transmitter|**LED**-based (cheap)|**Laser**-based (expensive)|
|Distance|Longer than UTP, shorter than SMF|**Longest**|
|Cost|Cheaper|**Most expensive**|

> [!tip] Memory trick  
> **Multi = many bounces = light spreads out = shorter.**  
> **Single = one straight beam (laser) = goes farthest = costs most.**

> [!info]- Why does bouncing limit distance? (click)  
> Light taking different angles travels different path lengths, so parts of the same signal arrive at slightly different times. Over a long cable they smear into each other and the bits become unreadable. A single straight path avoids this.

## 13. Fiber Standards ▶ [24:41](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=1481s)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-34.png)

|Informal name|IEEE|Speed|Fiber type|Max length|
|---|---|---|---|---|
|1000BASE-LX|802.3z|1 Gbps|MMF or SMF|550 m (MMF) / 5 km (SMF)|
|10GBASE-SR|802.3ae|10 Gbps|Multimode|400 m|
|10GBASE-LR|802.3ae|10 Gbps|Single-mode|10 km|
|10GBASE-ER|802.3ae|10 Gbps|Single-mode|30 km|

> [!tip] Decode the letters  
> **SR** = **S**hort **R**each · **LR** = **L**ong **R**each · **ER** = **E**xtended **R**each. Short → long → extended = 400 m → 10 km → 30 km.

## 14. UTP vs Fiber: When to Use Which ▶ [26:38](https://www.youtube.com/watch?v=ieTH5lVhNaY&t=1598s)

![700](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-35.png)

| |**Copper UTP**|**Fiber-optic**|
|---|---|---|
|Cost|✅ Cheaper (cable *and* RJ-45 ports)|More expensive (SFP ports; SMF > MMF)|
|Distance|~**100 m**|Much longer|
|Interference (EMI)|Vulnerable (twisting helps)|**Immune**|
|Security|Leaks a faint signal that could be copied|**No leakage**|

**Decision guide:**
- **≤ 100 m**, connecting PCs to a switch → **UTP**
- **> 100 m**, cheapest option → **multimode fiber**
- **Kilometres** → **single-mode fiber**

## 15. Revision Sheet

|Concept|Remember|
|---|---|
|RJ-45|Copper Ethernet port/plug (Registered Jack)|
|Speed unit|**bits** per second; × 1,000 per step|
|Copper max length|**100 m** for all BASE-T standards|
|802.3 letters|10 = **i**, 100 = **u**, 1G = **ab**, 10G = **an**|
|UTP|4 twisted pairs = 8 wires; twist fights EMI|
|10/100 pins|Pairs **1-2** and **3-6**|
|Tx 1-2 / Rx 3-6|Router, Firewall, PC|
|Tx 3-6 / Rx 1-2|**Switch**|
|Straight-through|Different groups (PC/router ↔ switch)|
|Crossover|Same group (switch ↔ switch, router ↔ router, PC ↔ router)|
|Auto MDI-X|Port adapts, so any cable works|
|1G/10G copper|All 4 pairs, each bidirectional|
|SFP|Small Form-factor Pluggable (fiber module)|
|Multimode|Wide core, LED, cheaper, shorter|
|Single-mode|Narrow core, laser, priciest, longest|
|Fiber vs UTP|Fiber: longer, no EMI, no leakage, costs more|

## 16. Test Yourself

Answer first, then click to check.

> [!question]- Two old routers are connected by UTP but can't communicate. Why?  
> They're probably using a **straight-through** cable. Both transmit on pins 1 & 2, so they need a **crossover** (or Auto MDI-X, which old devices may lack).

> [!question]- Two buildings are 150 m apart and costs must be kept low. Which cable?  
> **Multimode fiber.** UTP stops at 100 m, and single-mode would work but costs more.

> [!question]- Two offices are 3 km apart and costs must be kept low. Which cable?  
> **Single-mode fiber.** Neither UTP nor multimode reaches 3 km.

> [!question]- Two identical switches with Auto-MDIX ports are joined by a straight-through cable. What happens?  
> They **work normally**. Auto MDI-X adapts the pins. (Without it they wouldn't run slowly. They wouldn't work at all.)

> [!question]- Many PCs on one office floor connect to a switch in a wiring cabinet. Which cable?  
> **UTP.** Hosts and switches have plenty of RJ-45 ports, and the distance is under 100 m.

> [!question]- Which pins does a switch transmit on in 100BASE-T?  
> **3 & 6** (it receives on 1 & 2).

> [!question]- PC ↔ Router on old equipment: straight-through or crossover?  
> **Crossover.** Both transmit on pins 1 & 2.

> [!question]- What does the "T" in 1000BASE-T mean, and what's its maximum length?  
> **Twisted pair**, **100 m**.

> [!question]- How long does a 2 GB file take on a 1 Gbps link (ideal conditions)?  
> 2 GB = 16 Gb → **about 16 seconds**.

---

## 🧪 Lab Video (notes not made yet)

**Connecting Devices - Day 2 Lab** · 05:33 · [Watch on YouTube](https://www.youtube.com/watch?v=K6Qt23sY68Y)

- [ ] Watched
- [ ] Lab completed
