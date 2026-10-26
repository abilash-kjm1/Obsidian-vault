---
tags:
  - ccna/concept
course_days:
  - 7
  - 44
---

# Concept: Private IP Addresses (RFC 1918)

> [!abstract] In one line  
> Three IPv4 ranges are reserved for **inside** networks. Anyone can reuse them, but they **can't be routed on the Internet**, so traffic leaving the network goes through **NAT**, which swaps them for a public address.

## The Three Ranges (memorize)

|Range|Block|Class it was taken from|Typical use|
|---|---|---|---|
|**10.0.0.0 – 10.255.255.255**|10.0.0.0**/8**|A|Large companies|
|**172.16.0.0 – 172.31.255.255**|172.16.0.0**/12**|B|Medium networks|
|**192.168.0.0 – 192.168.255.255**|192.168.0.0**/16**|C|Home routers (192.168.0.x / 192.168.1.x)|

> [!warning] Common trap: 172.16 – 172.**31**  
> `172.32.0.1` is **public**, not private. The 172 block covers exactly 16 second-octet values: 16 to 31.

> [!info]- Why /12 for the 172 range? (click)  
> A /12 locks the first **12 bits**: 8 bits of `172` plus the first 4 bits of the second octet. 16 = `0001 0000` and 31 = `0001 1111` share the first 4 bits `0001`, so 172.16–172.31 is exactly one /12 block (16 Class B-sized networks).

## Public vs Private

| |**Public**|**Private**|
|---|---|---|
|Unique?|**Globally unique**: like a phone number|**Reused** by millions of networks|
|Routable on the Internet?|✅ Yes|❌ No: Internet routers drop them|
|Who assigns|IANA → regional registries → your **ISP**|You / your router (DHCP)|
|Example|`11.5.4.28`, `23.227.38.65`|`192.168.1.204`, `10.7.1.203`|

## How Private Addresses Reach the Internet: NAT

**NAT** (Network Address Translation) runs on your router. Outgoing traffic: private source IP → **the router's one public IP**. Replies come back to that public IP, and the router remembers which inside device asked and forwards the reply to it.

## Exam Points

- Know the three RFC 1918 ranges and their prefixes: **10/8, 172.16/12, 192.168/16**.
- Private ≠ routable on the Internet. They need **NAT**.
- Check `ipconfig` to see your **private** IP, and "what is my IP" in a browser to see your **public** IP.

## Self-Test

1. Is `172.20.1.1` private? What about `172.40.1.1`?
2. Is `10.200.5.5` private?
3. Why can two houses both use `192.168.1.10` without a conflict?

> [!success]- Answers  
> 1. `172.20.1.1` = **private** (16–31). `172.40.1.1` = **public**.  
> 2. **Yes**: anything in 10.x.x.x.  
> 3. Private addresses only have to be unique **inside** each network. On the Internet, each house appears as its own **public** IP (via NAT).

## Related

- [EP 3 - Private IP Addresses and NAT](../Subnetting%20Master%20-%20Network%20Chuck/EP%203%20-%20Private%20IP%20Addresses%20and%20NAT.md)
- [IPv4 Address Classes](IPv4%20Address%20Classes.md)
- [Day 44 - NAT Part 1](../01%20-%20Course%20Days/Day%2044%20-%20NAT%20Part%201.md)
