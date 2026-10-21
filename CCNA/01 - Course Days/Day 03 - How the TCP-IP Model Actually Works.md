---
course: Jeremy's IT Lab CCNA 200-301
course_day: 3
status: Not Started
date_started:
date_completed:
tags:
  - ccna/course-day
---

# How the TCP/IP Model Actually Works

[⬅️ Day 02](Day%2002%20-%20Interfaces%20and%20Cables.md) · [🏠 Dashboard](../00%20-%20Start%20Here/CCNA%20Dashboard.md) · [🗺️ Roadmap](../00%20-%20Start%20Here/Course%20Roadmap.md) · [Day 04 ➡️](Day%2004%20-%20Intro%20to%20the%20CLI.md)

**Video:** [How the TCP/IP Model Actually Works | Day 3](https://www.youtube.com/watch?v=yM-XNq9ADlI) · 42:42 · ▶ links jump to that moment
**Basics used here:** [TCP-IP Model cheat sheet](../Concepts/TCP-IP%20Model.md) · [Bits and Bytes](../Concepts/Bits%20and%20Bytes.md)

> [!abstract] The whole lesson in 3 lines  
> 1. Networking is split into **5 layers**, each with one job: **Physical** (bits) → **Local Network** (next hop, MAC) → **Internet** (right host, IP) → **Transport** (right app, port) → **Application** (the data itself).  
> 2. Sending = **encapsulation**: each layer wraps the data in its own header, like an envelope inside an envelope. Receiving = **decapsulation**: unwrap layer by layer.  
> 3. The model is a **map, not a law**. Learn each layer's *job*. The exact names vary between books.

> [!tip] Don't panic  
> Jeremy says it himself: there isn't much to memorize here. This is the **framework** every later topic (IP, switching, TCP…) slots into.

## 1. Protocols and Standards ▶ [1:46](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=106s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-1.png)

- **Protocol** = a set of rules for how devices communicate. It's the "language" computers speak.
- Early on, each vendor (e.g. IBM) used its own **proprietary** protocols, so an Apple iMac couldn't talk to an IBM server ❌.
- **Standard** = an agreed-upon specification. With **vendor-neutral** standards, anything can talk to anything: a MacBook loads a Linux web server, a Windows PC emails an Android phone.

## 2. A Bit of History ▶ [3:24](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=204s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-2.png)

|Year|Event|
|---|---|
|1969|**ARPANET** (funded by the US DoD's **ARPA**) connects university mainframes, using **NCP**|
|1974|**Vint Cerf & Bob Kahn** start **TCP** (*Transmission Control **Program***)|
|later|TCP is split into **TCP** (*Transmission Control **Protocol***) + **IP** (Internet Protocol), giving **TCP/IP**|
|**1 Jan 1983**|ARPANET fully switches to TCP/IP|

**Why TCP/IP won:** it was **open** (any vendor could implement it) and ran over **many kinds of networks**.

## 3. Who Defines the Standards? ▶ [4:59](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=299s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-3.png)

|Organization|Defines|Examples|
|---|---|---|
|**IEEE** (Institute of Electrical and Electronics Engineers)|**LAN** tech: physical signals *and* message format|**Ethernet (802.3)**, **Wi-Fi (802.11)**|
|**IETF** (Internet Engineering Task Force)|**Internet** protocols, published as free **RFCs** (Requests for Comments)|TCP, IP, UDP, HTTP, DNS|

Vendors like Cisco then **implement** these standards, so their gear works with everyone else's.

## 4. Why Use Layers? ▶ [6:58](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=418s)

Networks do many jobs: transmit signals, deliver within a LAN, route between networks, track conversations, run apps. A **layered model** groups related jobs:
- Each layer has **one role**.
- Each layer **uses** the layer below and **serves** the layer above.
- Protocols live (mostly) at one layer. Together they form the **network stack**.

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-4.png)

**RFC 791** (the IP standard, 1981 and still current) shows a 4-layer stack: Application (Telnet, FTP, TFTP) → Transport (TCP, UDP) → Internet (IPv4, IPv6) → Link (Ethernet, Wi-Fi).

> [!info]- Why is it called the "Internet" layer? (click)  
> Not because of *the* Internet. "Internet" = **inter-network**: connecting **multiple networks** together. That's exactly the job of IP and routers.

> [!important]  
> **The model is a description, not a law.** Some books use 4 layers, some 5, and OSI uses 7. This course uses **5**.

## 5. The Mail Analogy ▶ [9:33](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=573s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-5.png)

You write a letter **To: Bob**, seal it in an envelope **To: Bob's house**, then:

① Your **car** takes it **to Post Office A** → ② a **truck** takes it **to Post Office B** → ③ a **new truck** takes it **to Bob's house** → ④ the envelope is opened and **Bob** reads the letter.

> [!important] The key insight  
> Each vehicle has a **different destination** (Post Office A → B → Bob's house), but the **envelope's address and the letter's recipient never change**. That's exactly how **MAC addresses** (change every hop) and **IP addresses** (stay the same end to end) behave.

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-6.png)

|Mail layer|Job|→ TCP/IP layer|
|---|---|---|
|**Content**|What the letter says|**Application**|
|**Recipient**|*Which person* in the house ("To: Bob" vs "To: Bob's wife")|**Transport**|
|**Address**|*Which house*|**Internet**|
|**Local Delivery**|Car/truck to the **next stop**|**Local Network**|
|**Infrastructure**|The roads|**Physical**|

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-7.png)

> [!info]- Why do some models have 4 layers and others 5? (click)  
> The bottom two always work as a pair: going by **road** means a car or truck, by **air** a plane, by **sea** a ship. You can treat "vehicle + path" as **one** delivery layer (4-layer model) or **split** them (5-layer). Networks are the same: **Ethernet** defines both the cable signals (L1) and the frame format (L2), and so does **Wi-Fi**.

**Separation of layers:** changing the letter's content doesn't change the delivery route, and a different route doesn't change the letter. Each layer does its own job without caring how the others do theirs.

## 6. The 5 Layers on a Real Network ▶ [15:23](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=923s)

Setup: **PC1** (Chrome) → SW1 → R1 → R2 → SW2 → **SRV1** (web server **port 80** + file server **port 21**, IP **10.1.1.1**).

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-8.png)

|Layer|Problem it solves|Solved with|
|---|---|---|
|**5 Application**|Chrome must ask for a web page in a format the server understands|HTTP|
|**4 Transport**|SRV1 runs *several* services. Which one gets the request?|**Port number** (80 = web)|
|**3 Internet**|Which **host** across all these networks is SRV1?|**IP address** (10.1.1.1) + **routers**|
|**2 Local Network**|Get it to the **next device** on the path|**MAC addresses** + switches|
|**1 Physical**|Actually move the bits|Copper, fiber, radio signals|

> [!tip] Memory trick: who are you looking for?  
> **Port** = which *app* · **IP** = which *host* · **MAC** = which *next hop*

## 7. Layer by Layer (Bottom Up)

### Layer 1: Physical ▶ [19:59](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=1199s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-9.png)

Sends and receives **bits** as **electrical** (copper UTP), **optical** (fiber) or **radio** (Wi-Fi) signals. It defines cables, connectors, signal levels and speeds. Examples: UTP, fiber, Wi-Fi radios, **NICs** (network interface cards). → [Day 02](Day%2002%20-%20Interfaces%20and%20Cables.md)

### Layer 2: Local Network ▶ [21:07](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=1267s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-10.png)

**Hop-to-hop** delivery within a local network, using **MAC addresses** (one per interface).
- **Hop** = one step from one host or router to the next host or router. PC1 → R1 → R2 → SRV1 = **3 hops**.
- **Switches don't count as hops.** They just extend the local network.
- PC1 sends to R1's G1 MAC, then R1 to R2's G1 MAC, then R2 to SRV1's MAC.
- Protocols: **Ethernet**, **Wi-Fi**. → [Day 05](Day%2005%20-%20Ethernet%20LAN%20Switching%20Part%201.md)

### Layer 3: Internet ▶ [23:20](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=1400s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-11.png)

**End-to-end** delivery **between hosts** across multiple networks, using **IP addresses** (like a home address). **Routers** work here, forwarding by destination IP. Protocols: **IPv4, IPv6, ICMP**.

### Layer 4: Transport ▶ [24:24](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=1464s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-12.png)

**End-to-end** communication **between application processes** ("process-to-process"), using **port numbers**: 80 = web server, 21 = file server.
- Runs mainly **on the two hosts**. Routers normally ignore it.
- Protocols: **UDP** (simple, efficient) and **TCP** (adds reliability features).

> [!warning] "Port" has two meanings  
> A **physical port** = a socket on a switch (Day 01–02). A **transport port** = a **number** identifying a process. Different things!

### Layer 5: Application ▶ [26:03](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=1563s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-13.png)

Where the network meets apps. It defines how data is **formatted, sent and interpreted**.
- Web: **HTTP/HTTPS** · Files: **FTP, TFTP** · Email: **SMTP, POP3, IMAP**
- Usually called **Layer 7** (borrowed from OSI, see section 11).
- Routers and switches **don't look at it**. Only the two communicating hosts do.

## 8. Encapsulation and Decapsulation ▶ [27:36](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=1656s)

**Sending (encapsulation):** each layer adds its header on the way **down**.

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-14.png)

① **Data** (e.g. an HTTP request) → ② + **L4 header** (ports) → ③ + **L3 header** (IPs) → ④ + **L2 header *and* trailer** (MACs; the trailer checks for errors) → ⑤ **L1** sends it as bits. The L2 header goes out first and the trailer last.

**Receiving (decapsulation):** the reverse, on the way **up**.

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-15.png)

① Receive bits → ② read and **remove** the L2 header + trailer → ③ remove the L3 header → ④ remove the L4 header → ⑤ the **data** reaches the app, which may reply back down its own stack.

> [!tip] Analogy: Russian dolls  
> The sender puts the data into a doll, that doll into a bigger one, and so on. The receiver opens them from the outside in.

## 9. PDU Names ▶ [31:12](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=1872s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-16.png)

|What it is|Name|Also called|Its payload|
|---|---|---|---|
|L4 header + data|**Segment** (TCP) / **Datagram** (UDP)|L4PDU|The application data|
|L3 header + segment|**Packet**|L3PDU|The segment/datagram|
|L2 header + packet + L2 trailer|**Frame**|L2PDU|The packet|

- **PDU** = Protocol Data Unit: the message's name at each layer.
- **Payload** = what's *inside*, not counting that layer's own header/trailer.
- **Only frames travel on the wire.** You never see a bare packet on a cable.

> [!tip] Memory trick  
> **TCP → Segments, UDP → Datagrams** ("**T**CP **S**egments", "**U**DP **D**atagrams").

## 10. How Layers Interact ▶ [32:51](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=1971s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-17.png)

**Adjacent-layer interaction** (inside **one** device, up and down): each layer **serves the one above** and is **served by the one below**.
- L4 → L5: delivers data to the right app (ports)
- L3 → L4: delivers segments to the right host (IP)
- L2 → L3: delivers packets to the next hop (MAC)
- L1 → L2: sends the frame's bits as signals

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-18.png)

**Same-layer interaction** (**across** devices, sideways): each layer "talks" to the **same layer** on the other device. A segment is addressed to the other host's **port**, a packet to its **IP**, a frame to the **next hop's MAC**.

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-19.png)

**Modularity:** swap HTTP/TCP for **TFTP/UDP**, or Ethernet for **Wi-Fi**, and the other layers don't change. Each layer keeps its "contract" with its neighbours.

## 11. The OSI Model and Layer Names ▶ [35:51](https://www.youtube.com/watch?v=yM-XNq9ADlI&t=2151s)

![700](Attachments/Day%2003%20-%20How%20the%20TCP-IP%20Model%20Actually%20Works-20.png)

- **OSI** (Open Systems Interconnection) was a 7-layer model by the **ISO** (International Organization for Standardization) in the late 1970s–80s. Governments pushed it, but its protocols came **too late and were too complex** (top-down committees vs TCP/IP's bottom-up approach). **TCP/IP won**.
- OSI survives as a **teaching and reference model** and for **layer numbers**.

|#|Most books (5-layer, OSI names)|This course|OSI (7)|
|---|---|---|---|
|7|**Application**|Application|Application, Presentation, Session|
|4|**Transport**|Transport|Transport|
|3|**Network**|Internet|Network|
|2|**Data Link**|Local Network|Data Link|
|1|**Physical**|Physical|Physical|

> [!info]- Why is Application "Layer 7" if there are only 5 layers? (click)  
> OSI's top three layers (Application, Presentation, Session) are squeezed into TCP/IP's single Application layer. People still use OSI's numbering, so app-level traffic is called **Layer 7**. There's no "Layer 5" or "Layer 6" in everyday talk.

In practice people just say "Layer 2" and "Layer 3", and **the CCNA won't quiz you on layer names**. Know the **jobs**.

## 12. Revision Sheet

|Concept|Remember|
|---|---|
|Protocol|Rules for communicating ("language")|
|Standard|Agreed spec; vendor-neutral, so everything interoperates|
|IEEE / IETF|LAN tech (802.3 Ethernet, 802.11 Wi-Fi) / Internet protocols in free RFCs|
|TCP/IP history|ARPANET 1969 (NCP) → Cerf & Kahn 1974 → full switch 1 Jan 1983|
|L1 Physical|Bits as signals: cables, NICs, radios|
|L2 Local Network / Data Link|Hop-to-hop, **MAC**, switches, Ethernet/Wi-Fi|
|L3 Internet / Network|Host-to-host end to end, **IP**, routers, IPv4/IPv6/ICMP|
|L4 Transport|App-to-app end to end, **ports**, TCP/UDP|
|L5 (7) Application|Data format: HTTP(S), FTP, TFTP, SMTP…|
|Hop|Host/router → next host/router (switches don't count)|
|Encapsulation|Add headers going **down**; L2 also adds a **trailer**|
|Decapsulation|Remove headers going **up**|
|PDUs|Segment (TCP) / datagram (UDP) → packet → frame|
|Payload|What's inside a PDU, minus its own header/trailer|
|Adjacent-layer|Up and down inside one device (serves / served by)|
|Same-layer|Across devices (communicates with the same layer)|
|OSI|7 layers; lost to TCP/IP; gives us "Layer 7" and the Network/Data Link names|

## 13. Test Yourself

Answer first, then click to check.

> [!question]- SRV1 runs a web server and a file server. What tells it which one should get a message?  
> The **destination port number** (Layer 4), e.g. 80 for web, 21 for files.

> [!question]- PC1 → SW1 → R1 → R2 → SW2 → SRV1. How many hops?  
> **3** (PC1→R1, R1→R2, R2→SRV1). Switches don't count.

> [!question]- In the mail analogy, what changes at every post office and what stays the same?  
> The **vehicle's destination** changes (like the **MAC** at each hop). The **house address** and **recipient** stay the same (like **IP** and **port**).

> [!question]- Name the PDU at each layer.  
> L4: **segment** (TCP) or **datagram** (UDP) · L3: **packet** · L2: **frame**

> [!question]- Which layer adds a trailer, and why?  
> **Layer 2.** The receiver uses it to **check for transmission errors**.

> [!question]- What is a packet's payload?  
> The **segment/datagram**: the L4 header plus the data.

> [!question]- Do routers normally look at port numbers or application data?  
> **No.** Routers work at **Layer 3** (IP addresses). Ports and app data are for the end hosts.

> [!question]- Layer 4 delivering data to the right app for Layer 5 is an example of…?  
> **Adjacent-layer interaction.**

> [!question]- You replace Ethernet with Wi-Fi. Which layers change?  
> Only **Layers 1 and 2**. That's the benefit of **modularity**.

> [!question]- Why is the Application layer called "Layer 7"?  
> It borrows the **OSI** numbering, where Application is layer 7. OSI's layers 5–7 are merged into one in TCP/IP.

---

## 🧪 Lab Video (notes not made yet)

**OSI Model - Day 3 Lab** · 08:05 · [Watch on YouTube](https://www.youtube.com/watch?v=7nmYoL0t2tU)
