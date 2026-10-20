---
tags:
  - ccna/concept
course_days:
  - 5
  - 6
---

# Concept: Unicast and Broadcast

> [!abstract] In one line  
> **Unicast** = a frame for **one** device. **Broadcast** = a frame for **every** device on the LAN. The destination MAC address tells you which one it is.

## The Two Types

|Type|Destination MAC|Who receives it|Analogy|
|---|---|---|---|
|**Unicast**|one device's MAC, e.g. `0C2F.B06A.3900`|that one device|A letter addressed to one person|
|**Broadcast**|**`FFFF.FFFF.FFFF`**|**all** devices on the LAN|An announcement over the school loudspeaker|

> [!info]- Why is broadcast all F's? (click)  
> Hex `F` = binary `1111`, so `FFFF.FFFF.FFFF` is **all 48 bits set to 1**. That address is reserved to mean "everyone." No real device has it. → [Hexadecimal](Hexadecimal.md#Hex%20and%20Binary)

## What a Switch Does With Each

|Frame|Destination in MAC table?|Switch action|
|---|---|---|
|Known unicast|Yes|**Forward** out that one port|
|Unknown unicast|No|**Flood** out all ports except the incoming one|
|Broadcast|— (it's for everyone)|**Flood** out all ports except the incoming one|

> [!tip] Memory trick  
> **Only known unicast goes out one port.** Everything else floods.

## Where You'll See Them

- **ARP request**: broadcast ("Who has 192.168.1.3?")
- **ARP reply**: unicast (straight back to the asker)
- **Ping (ICMP echo)**: unicast

## Exam Points

- Broadcast MAC = `FFFF.FFFF.FFFF`.
- Broadcast and unknown unicast are both flooded. Known unicast is not.
- Broadcasts stay **inside the LAN**. Routers don't forward them.

## Self-Test

1. A frame has destination `FFFF.FFFF.FFFF`. What does the switch do?
2. Which two frame types does a switch flood?
3. Is an ARP reply unicast or broadcast?

> [!success]- Answers  
> 1. Floods it out all ports except the one it arrived on.  
> 2. Broadcast and unknown unicast.  
> 3. Unicast. The replier already learned the asker's MAC from the request.

## Related

- [Hexadecimal](Hexadecimal.md)
- [Day 05 - Ethernet LAN Switching Part 1](../01%20-%20Course%20Days/Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201.md)
- [Day 06 - Ethernet LAN Switching Part 2](../01%20-%20Course%20Days/Day%2006%20-%20Ethernet%20LAN%20Switching%20Part%202.md)
