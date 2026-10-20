---
tags:
  - ccna/concept
course_days:
  - 5
---

# Concept: Bits and Bytes

> [!abstract] In one line  
> A **bit** is a single 0 or 1. A **byte** is a group of **8 bits**. Networking sizes are given in both, so you must convert quickly.

## The Units

|Unit|Size|Example|
|---|---|---|
|Bit|one `0` or `1`|`1`|
|Nibble|4 bits = **1 hex digit**|`1010` = `A`|
|Byte|8 bits = **2 hex digits**|`10101010` = `AA`|

## Converting

- **bytes × 8 = bits**
- **bits ÷ 8 = bytes**

|Thing|Bytes|Bits|Hex digits|
|---|---|---|---|
|MAC address|6|**48**|12|
|IPv4 address|4|**32**|—|
|Preamble|7|56|—|
|FCS|4|32|—|

## Speeds vs Sizes

- **Link speeds** use **bits**: 100 **Mbps** = 100 mega**bits** per second (FastEthernet).
- **File sizes** use **bytes**: 100 **MB** = 100 mega**bytes**.
- Lowercase **b** = bits, uppercase **B** = bytes.

## Exam Trap

> [!warning]  
> "48 bytes" vs "48 bits": a MAC address is **48 bits**. 48 bytes would be 384 bits. Read the unit in every answer option.

## Related

- [Hexadecimal](Hexadecimal.md)
