---

title: TCP/IP Model and Network Communication  
tags:

- ccna
    
- networking
    
- tcp-ip
    
- osi-model
    

---

# TCP/IP Model and Network Communication

> [!abstract] In Simple Words  
> Computers communicate using agreed-upon rules called **protocols**. The TCP/IP model divides network communication into five layers, with each layer performing a specific job. Data travels down the sender's layers, across the network, and up the receiver's layers.

## 1. Protocols and Standards

- **Protocol:** Rules that define how devices communicate.
    
- **Standard:** An agreed specification that allows different vendors' devices to work together.
    
- **Protocol stack:** A collection of protocols working together across layers.
    

### Who defines the standards?

|Organization|Examples|
|---|---|
|IEEE|Ethernet (802.3), Wi-Fi (802.11)|
|IETF|TCP, IP, UDP and other Internet protocols|

The IETF publishes technical documents called **RFCs** (Requests for Comments).

**Networking history:** ARPANET launched in 1969. TCP/IP became the standard protocol suite for ARPANET on January 1, 1983.

## 2. The 5-Layer TCP/IP Model

Each layer has a specific responsibility. It uses services from the layer below and provides services to the layer above.

|Layer|Name|Main responsibility|Address / identifier|PDU|
|---|---|---|---|---|
|5|Application|Network services for applications|Application protocols|Data|
|4|Transport|Communication between application processes|Port numbers|Segment (TCP) / Datagram (UDP)|
|3|Internet|Delivery across networks|IP address|Packet|
|2|Local Network|Delivery over a local link|MAC address|Frame|
|1|Physical|Transmit bits as signals|Not applicable|Bits|

### Layer 1 — Physical

Transmits raw bits as electrical, optical, or radio signals.

Examples: Ethernet cables, fiber-optic cables, Wi-Fi radio signals and physical interfaces.

### Layer 2 — Local Network

Delivers frames over a local network using MAC addresses.

Examples: Ethernet, Wi-Fi and Ethernet switches.

### Layer 3 — Internet

Uses IP addresses to deliver packets between networks. Routers examine destination IP addresses to choose where packets should go next.

### Layer 4 — Transport

Delivers data to the correct application process using port numbers.

- **TCP:** Provides reliable, ordered delivery.
    
- **UDP:** Provides connectionless delivery with less protocol overhead.
    

Examples: TCP port 80 for HTTP and port 21 for FTP.

### Layer 5 — Application

Provides protocols used by network applications to exchange and interpret data.

Examples: HTTP/HTTPS for web communication, DNS for name resolution and SMTP for sending email.

> [!important] CCNA Tip  
> The TCP/IP model has five layers, but the OSI model has seven. TCP/IP's Application layer combines the functions of the OSI Application, Presentation and Session layers. In industry, people sometimes refer to application-level traffic as Layer 7 traffic using OSI terminology.

## 3. How Data Travels: Encapsulation

**Encapsulation** happens when data moves down the sender's network stack. Each layer adds its own control information.

**Decapsulation** happens when the receiver processes that information and passes the data up the stack.

```
flowchart TD
    A["Application: Data"] --> B["Transport: Segment / Datagram"]
    B --> C["Internet: Packet"]
    C --> D["Local Network: Frame"]
    D --> E["Physical: Bits"]
    E --> F["Network medium"]
    F --> G["Receiver processes bits"]
    G --> H["Frame → Packet → Segment / Datagram → Data"]
```

### Example: Opening a website

1. Your browser creates an HTTP request.
    
2. Layer 4 adds transport information, including port numbers.
    
3. Layer 3 adds source and destination IP addresses.
    
4. Layer 2 adds MAC addresses and a trailer for error detection.
    
5. Layer 1 transmits the bits across the physical medium.
    
6. The receiving device processes the data in reverse order.
    

**Important:** Routers remove the incoming Layer 2 frame and create a new frame for the next link. The IP packet is generally forwarded onward, although some IP fields change during routing.

## 4. Protocol Data Units (PDUs)

A **Protocol Data Unit (PDU)** is the name for data as processed at a particular layer.

|Layer|PDU|Contains|
|---|---|---|
|4|Segment / Datagram|Transport header + data|
|3|Packet|IP header + transport data|
|2|Frame|Frame header + packet payload + trailer|
|1|Bits|Physical signals representing bits|

**Payload** is the data carried inside a PDU, excluding that PDU's own header and trailer.

Remember: a packet is encapsulated inside a frame for transmission over a link. The frame does not remain the same across every routed link.

## 5. Hops and Layer Interactions

**Hop:** A step along a network path, commonly measured between Layer 3 devices such as hosts and routers.

Example:

`PC1 → Switch1 → Router1 → Router2 → Switch2 → Server1`

There are three routed hops: PC1 to Router1, Router1 to Router2, and Router2 to Server1. The switches are not counted as separate routed hops in this example.

### Two types of layer interaction

- **Adjacent-layer interaction:** Neighboring layers exchange services within the same device.
    
- **Same-layer interaction:** Matching layers on different devices communicate logically using their respective protocols.
    

Layering allows technologies to work together. For example, a network can use Wi-Fi instead of Ethernet without necessarily changing the IP protocol or the application.

## 6. TCP/IP vs. OSI Model

|TCP/IP 5-layer model|OSI 7-layer model|
|---|---|
|Application|Application, Presentation, Session|
|Transport|Transport|
|Internet|Network|
|Local Network|Data Link|
|Physical|Physical|

The **OSI model** is a seven-layer reference model used to understand networking and troubleshoot problems. TCP/IP is the practical protocol suite used for Internet communication.

## Quick Revision

- Protocols define communication rules; standards help devices from different vendors interoperate.
    
- Layer 2 uses MAC addresses; Layer 3 uses IP addresses; Layer 4 uses port numbers.
    
- Encapsulation adds headers as data moves down the sender's stack.
    
- Decapsulation processes and removes headers as data moves up the receiver's stack.
    
- Memorize the PDU names: **Segment/Datagram → Packet → Frame → Bits**.
    
- IEEE defines Ethernet and Wi-Fi standards; the IETF develops Internet protocols.
    

## Test Yourself

1. What is the difference between a MAC address and an IP address?
    
2. Which layer uses port numbers to identify application processes?
    
3. What is the difference between encapsulation and decapsulation?
    
4. What are the PDU names at Layers 4, 3 and 2?
    
5. What is the difference between the TCP/IP and OSI models?
    

> [!question]- Show answers
> 
> 1. MAC addresses identify interfaces on a local link; IP addresses provide logical addressing across networks.
>     
> 2. Layer 4 — Transport.
>     
> 3. Encapsulation adds protocol information; decapsulation processes and removes it.
>     
> 4. Segment/datagram, packet and frame.
>     
> 5. TCP/IP uses five layers in this model; OSI uses seven reference layers.
>     

## Related Notes

- [[OSI Model]]
    
- [[Ethernet Switching]]
    
- [[IP Addressing]]
    
- [[TCP vs UDP]]
    
- [[MAC Address vs IP Address]]
    
- [[Network Devices]]