
# Day 01 - Network Devices


## What is Computer Network

- Computer Network is a digital telecommunication  network  which allow the **nodes** to ==🟠share their resources==


## Nodes : 


![154](Attachments/Day%2001%20-%20Network%20Devices.png)  ![123](Attachments/Day%2001%20-%20Network%20Devices-1.png)  ![136](Attachments/Day%2001%20-%20Network%20Devices-2.png)  ![112](Attachments/Day%2001%20-%20Network%20Devices-3.png) ![103](Attachments/Day%2001%20-%20Network%20Devices-4.png)


> Client and Servers  => Sometimes called End Hosts or End points


## Clients 

- Its a device that ==access==  the ==service== made available by the **==🔴server==**
- Example : PC, laptop, mac , phone, imac etc..

## Server

- Is a device that ==provides== functions or **services** for  **clients**


![](Attachments/Day%2001%20-%20Network%20Devices-5.png)

PC1 = Client  [Because its  requesting for  a resources]
PC2 = server [ It provides the resources]


![](Attachments/Day%2001%20-%20Network%20Devices-6.png)

>  The ==🔵same device== can be a client in some situations, and a server in other situations.


## Switch

![](Attachments/Day%2001%20-%20Network%20Devices-8.png)

> A **switch** is a network hardware device that connects multiple hosts within a LAN and allows them to communicate with each other using **MAC addresses**.

![](Attachments/Day%2001%20-%20Network%20Devices-9.png)

Example : Catalyst 9200 and Catalyst 3650

### Characteristics of Switches : 

- Has Many Ports to connect  [ Usually 24+ ] 
- Connects the hosts within the LAN
- Does Provide the connectivity between the LANs / Over  the Internet

## Routers : 

> A **router** is a networking device that connects different networks and forwards IP packets between them using IP addresses.

![](Attachments/Day%2001%20-%20Network%20Devices-10.png)

Example : 
1. ISR 1000
2. ISR 900
3. ISR 4000

![](Attachments/Day%2001%20-%20Network%20Devices-11.png)

### Characteristics of Router

- Less Ports Compared to Switches
-  Provide Connectivity between the LANs
-  So Its sends data over the Internet

## Firewalls

> A **firewall** is a network security device that monitors and controls incoming and outgoing network traffic based on predefined security rules. It helps protect a network by allowing legitimate traffic and blocking unauthorized or unwanted traffic.

- Firewalls can be placed outside the network and also it can be placed inside the Network

	![](Attachments/Day%2001%20-%20Network%20Devices-12.png)


- Needs to be configure with the **security rules**  to determine which traffic should be allowed and denied
![](Attachments/Day%2001%20-%20Network%20Devices-13.png)

Example : 
1. ASA5500 - X  => Cisco classic Firewall
2. Firepower 2100 => Next Gen Firewall

 ### Characteristics of Firewall : 
 - Monitors and controls the traffic based on the configured rules
 - placed inside or outside the network
 - Also Known as the Next-Generation Firewalls  => Includes modern and advanced filtering capabilities


  > Network Firewalls :
  > The above discussed are the network firewalls  : which is a hardware devices that filters the traffic between the networks

> Host Based Firewalls : 
>  Software applications that filters the traffic entering and exiting a host machine like pc 

