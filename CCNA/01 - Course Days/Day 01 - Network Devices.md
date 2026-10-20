---
course: Jeremy's IT Lab CCNA 200-301
course_day: 1
status: Not Started
date_started:
date_completed:
tags:
  - ccna/course-day
---

# Network Devices

[🏠 Dashboard](../00%20-%20Start%20Here/CCNA%20Dashboard.md) · [🗺️ Roadmap](../00%20-%20Start%20Here/Course%20Roadmap.md) · [Day 02 ➡️](Day%2002%20-%20Interfaces%20and%20Cables.md)

**Video:** [Network Devices | Day 1](https://www.youtube.com/watch?v=H8W9oMNSuwo) · 30:26 · ▶ links jump to that moment

> [!abstract] The whole lesson in 3 lines  
> 1. A **network** = devices (**nodes**) connected so they can **share resources**. Even two PCs and one cable count.  
> 2. **End hosts** are **clients** (ask for a service) and **servers** (provide it). The same device can be either.  
> 3. **Switches** connect hosts **inside** a LAN, **routers** connect **different** networks (and the Internet), and **firewalls** decide what traffic is **allowed in or out**.

## 1. Can You Name These? ▶ [2:21](https://www.youtube.com/watch?v=H8W9oMNSuwo&t=141s)

![700](Attachments/Day%2001%20-%20Network%20Devices-14.png)

Cloud = **the Internet** · round icon with arrows = **router** · square with arrows = **switch** · screens = **PCs**. By the end of this note you'll know what each one does.

## 2. What Is a Network? ▶ [2:42](https://www.youtube.com/watch?v=H8W9oMNSuwo&t=162s)

> "A computer network is a digital telecommunications network which allows **nodes** to **share resources**." (Wikipedia)

**Node** = any device on the network. The five types in this lesson:

![700](Attachments/Day%2001%20-%20Network%20Devices-15.png)

|Node|Role|Kind|
|---|---|---|
|**Router**|Connects *different* networks|Network device|
|**Switch**|Connects hosts *inside* one LAN|Network device|
|**Firewall**|Allows or blocks traffic|Network (security) device|
|**Server**|*Provides* a service|**End host** (endpoint)|
|**Client**|*Uses* a service|**End host** (endpoint)|

> [!tip] Two families  
> **End hosts / endpoints** = where data starts and ends (clients, servers).  
> **Network devices** = what moves and protects data in between (switches, routers, firewalls).

### The smallest possible network ▶ [5:18](https://www.youtube.com/watch?v=H8W9oMNSuwo&t=318s)

![700](Attachments/Day%2001%20-%20Network%20Devices-16.png)

Two PCs + one cable = **a network**. They're connected and can share resources, which meets the definition.

## 3. Clients and Servers ▶ [6:00](https://www.youtube.com/watch?v=H8W9oMNSuwo&t=360s)

|Term|Definition|Example|
|---|---|---|
|**Client**|A device that **accesses a service** made available by a server|Your phone watching YouTube|
|**Server**|A device that **provides functions or services** for clients|YouTube's computer sending the video|

![700](Attachments/Day%2001%20-%20Network%20Devices-17.png)

Clients can be laptops, desktops, iMacs, phones…

![700](Attachments/Day%2001%20-%20Network%20Devices-18.png)

Servers *can* be powerful rack machines in data centres, but **any device can be a server**.

> [!tip] Analogy: a restaurant  
> **Client** = the customer who orders. **Server** = the waiter who brings the food.  
> It's about the **role in that moment**, not the type of person (or device).

### Spot the client and server ▶ [7:49](https://www.youtube.com/watch?v=H8W9oMNSuwo&t=469s)

![700](Attachments/Day%2001%20-%20Network%20Devices-19.png)

PC1: "Give me image.jpg." → PC2: "Here you are." So **PC1 = client** (asks) and **PC2 = server** (provides).

![700](Attachments/Day%2001%20-%20Network%20Devices-20.png)

Your computer = **client** → the request crosses **the Internet** (drawn as a **cloud**) → YouTube server = **server**. It streams the video back bit by bit, not all at once.

> [!info]- Why do diagrams draw the Internet as a cloud? (click)  
> The Internet is huge and complex. When those details don't matter for the diagram, a cloud means "data goes in here and comes out there, and we don't care how." You'll see clouds used like this throughout the course.

![700](Attachments/Day%2001%20-%20Network%20Devices-21.png)

AirDrop: **your** phone asks (client) and your **friend's** phone sends (server).

> [!important] Key idea  
> **The same device can be a client in one situation and a server in another.** Your friend's iPhone is a client when watching YouTube and a server when it AirDrops you a file.

## 4. Switches: Connecting Hosts Inside a LAN ▶ [11:02](https://www.youtube.com/watch?v=H8W9oMNSuwo&t=662s)

You don't usually wire PCs directly to each other. Instead, every host connects to a **switch**.

![700](Attachments/Day%2001%20-%20Network%20Devices-22.png)

**LAN** (Local Area Network) = hosts in one small area: an office floor, a small office, your home. Here the New York branch is one LAN and Tokyo is another.

![700](Attachments/Day%2001%20-%20Network%20Devices-23.png)

**Switches:**
- have **many ports** (usually **24+**) for end hosts
- connect hosts **within the same LAN**
- **do NOT** connect different LANs or reach the Internet

Cisco examples: **Catalyst 9200**, **Catalyst 3650** (Catalyst = Cisco's enterprise switch line).

> [!tip] Analogy  
> A switch is a **power strip for network cables**: lots of sockets so everyone in the room can plug in and talk to each other. But it can't reach the building next door.

More on how switches work → [Day 05 - Ethernet LAN Switching](Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201.md)

## 5. Routers: Connecting Networks ▶ [14:09](https://www.youtube.com/watch?v=H8W9oMNSuwo&t=849s)

![700](Attachments/Day%2001%20-%20Network%20Devices-24.png)

Each switch connects to a **router**, and the routers connect over the Internet. PC1 (New York) → SW1 → **R1** → Internet → **R2** → SW2 → SRV1 (Tokyo). The reply takes the reverse path.

![700](Attachments/Day%2001%20-%20Network%20Devices-25.png)

**Routers:**
- have **fewer ports** than switches
- connect **between** LANs
- so they're what sends data **over the Internet**

Cisco examples: **ISR 900, ISR 1000, ISR 4000** (ISR = Integrated Services Router).

> [!tip] Switch vs router in one line  
> **Switch = inside the neighbourhood. Router = between neighbourhoods.**  
> A home Wi-Fi "router" is really a router, switch, firewall and wireless access point combined in one box.

## 6. Firewalls: Network Security ▶ [16:08](https://www.youtube.com/watch?v=H8W9oMNSuwo&t=968s)

An **attacker** somewhere on the Internet wants in. Routers have only basic security, so we add a **firewall**.

![700](Attachments/Day%2001%20-%20Network%20Devices-26.png)

- **Configured with rules** saying which traffic to **allow** and which to **deny**.
- Placement: **outside** the router (FW1, filters before the router) or **inside** it (FW2, after the router). Some networks use both.
- With good rules, PC1 ↔ SRV1 is **allowed** and the attacker is **blocked**.

![700](Attachments/Day%2001%20-%20Network%20Devices-27.png)

Cisco examples: **ASA 5500-X** (Adaptive Security Appliance, the classic) and **Firepower 2100**. Both are **next-generation firewalls (NGFW)**.

> [!info]- What makes a firewall "next-generation"? (click)  
> A traditional firewall filters on basic information such as addresses and ports. An **NGFW** adds more advanced filtering, such as recognising specific applications and **IPS** (Intrusion Prevention System: spotting and blocking attack patterns). It's covered later in the security section.

### Network vs host-based firewalls ▶ [19:21](https://www.youtube.com/watch?v=H8W9oMNSuwo&t=1161s)

![700](Attachments/Day%2001%20-%20Network%20Devices-28.png)

| |**Network firewall**|**Host-based firewall**|
|---|---|---|
|What|**Hardware device**|**Software** on a PC/server|
|Protects|Traffic **between networks**|Traffic in/out of **one host**|
|Example|Cisco ASA, Firepower|Windows Defender Firewall|

> [!tip] Defence in depth  
> Use **both**. Even behind a network firewall, every PC should run its own host-based firewall as an extra layer.

## 7. Revision Sheet

|Concept|Remember|
|---|---|
|Network|Nodes connected to share resources (2 PCs + a cable is enough)|
|End hosts / endpoints|Clients and servers|
|Client|**Accesses** a service|
|Server|**Provides** a service|
|Same device?|Can be client **and** server, depending on the moment|
|Internet in diagrams|Cloud|
|Switch|Many ports (24+), connects hosts **within** a LAN, not between LANs|
|LAN|Hosts in a small area (floor, office, home)|
|Router|Fewer ports, connects **between** LANs, sends data over the Internet|
|Firewall|Allows/denies traffic by **configured rules**; inside or outside the network|
|NGFW|Firewall with advanced filtering (e.g. IPS)|
|Network vs host firewall|Hardware between networks vs software on one host|
|Cisco models|Switches: Catalyst 9200/3650 · Routers: ISR 900/1000/4000 · Firewalls: ASA 5500-X, Firepower 2100|

## 8. Test Yourself

Answer first, then click to check.

> [!question]- Your department needs to connect 30 PCs. Which device?  
> A **switch**: many ports for end hosts in one LAN. Routers and firewalls don't have 30 ports, and a server is an end host itself.

> [!question]- You receive a video from your friend's iPhone via AirDrop. What was their iPhone acting as?  
> A **server**: it provided the file.

> [!question]- What is your device acting as while you watch a YouTube video?  
> A **client**. ("End host" is true too, but it describes what the device *is*, not its *role*.)

> [!question]- Your company needs to connect its separate networks together. Which device?  
> A **router**. (A firewall *can* connect networks, but its real job is filtering.)

> [!question]- Your company wants to upgrade an old firewall to one with more advanced features. What should it buy?  
> A **next-generation firewall**. ("Next-level" and "top-layer" firewalls don't exist; host-based is software on a PC.)

> [!question]- Can a switch connect a LAN to the Internet on its own?  
> **No.** Switches only connect hosts within a LAN. You need a router.

> [!question]- Is a firewall on your laptop a network firewall?  
> **No.** It's a **host-based** firewall (software protecting one host).

---

## 📚 Other Day 1 Videos (notes not made yet)

- **Anki Flashcards - Day 1 Extra** · 14:56 · [Watch on YouTube](https://www.youtube.com/watch?v=6Atw8oMtVTA)
- **Packet Tracer Introduction - Day 1 Lab** · 15:18 · [Watch on YouTube](https://www.youtube.com/watch?v=a1Im6GYaSno)
