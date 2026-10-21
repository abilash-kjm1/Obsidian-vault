---
tags:
  - ccna/concept
course_days:
  - 3
---

# Concept: TCP/IP Model (5 Layers)

> [!abstract] In one line  
> Networking is split into **5 layers**, each with **one job**: get the bits across the wire (L1), to the next hop (L2), to the right host (L3), to the right app (L4), in a format the app understands (L5).

## The Cheat Sheet

|#|Layer (common name)|Jeremy's name|Job|Address used|Key devices / protocols|PDU|
|---|---|---|---|---|---|---|
|5 (7)|**Application**|Application|Format and interpret the data|—|HTTP(S), FTP, TFTP, DNS, email|Data|
|4|**Transport**|Transport|End-to-end, **app ↔ app**|**Port numbers**|TCP, UDP|**Segment** (TCP) / **Datagram** (UDP)|
|3|**Network**|Internet|End-to-end, **host ↔ host**, across networks|**IP addresses**|IPv4, IPv6, ICMP · **routers**|**Packet**|
|2|**Data Link**|Local Network|**Hop-to-hop** inside a local network|**MAC addresses**|Ethernet, Wi-Fi · **switches**|**Frame**|
|1|**Physical**|Physical|Send **bits** as electrical, light or radio signals|—|Cables, connectors, NICs, radios|Bits|

> [!tip] Memory trick (top → bottom)  
> **A**ll **T**eachers **N**eed **D**ata **P**ackets: **A**pplication, **T**ransport, **N**etwork, **D**ata Link, **P**hysical.

## Why the Application Layer Is "Layer 7"

The older **OSI model** has **7 layers**. TCP/IP's single Application layer covers OSI's top **three** (Application, Presentation, Session). People borrow OSI's numbering, so "Layer 7" = application.

|OSI (7)|TCP/IP (5)|
|---|---|
|7 Application · 6 Presentation · 5 Session|Application|
|4 Transport|Transport|
|3 Network|Network (Internet)|
|2 Data Link|Data Link (Local Network)|
|1 Physical|Physical|

## Exam Points

- Know each layer's **job**, its **address type** and its **PDU name**.
- **Segment = TCP**, **datagram = UDP**; packet = L3; frame = L2 (the only thing that actually travels on the wire).
- **Switch = L2**, **router = L3**.
- **Payload** = everything inside a PDU except that layer's own header/trailer.

## Self-Test

1. Which layer uses port numbers?
2. What's the PDU name at Layer 3?
3. A router mainly works at which layer?

> [!success]- Answers  
> 1. **Transport (L4)**  
> 2. **Packet**  
> 3. **Layer 3 (Network/Internet)**: it forwards using IP addresses.

## Related

- [Day 03 - How the TCP-IP Model Actually Works](../01%20-%20Course%20Days/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works.md)
- [Unicast and Broadcast](Unicast%20and%20Broadcast.md) · [Bits and Bytes](Bits%20and%20Bytes.md)
