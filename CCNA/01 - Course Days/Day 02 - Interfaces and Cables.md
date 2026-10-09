
# Day 02 - Interfaces and Cables


## RJ 45 Interface : 

![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables.png)

RJ => Registered Jack

### RJ 45 Connectors : 

![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-1.png)

- It is used on end of  copper  ethernet cabel

## Ethernet 

> Its a collection of network  Protocols / Standards.

### Network Protocols : 

- If 2 different persons are taking to each other and one knows English and other knows Japanese and they don't know how to communicates
	![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-2.png)

-  They  need is some kind of agreed communication  that is where protocols / standards comes in like ethernet

## Bits and Bytes : 


>  Connections between the devices in a network  operates a set speed 
>  these speeds are measured in bit per second

### Bits : 
 -
 - O's and 1's
- when we communicate using a copper cable and there will be a variation in electrical signals and that variation in electrical signals will be interpreted by the devices as 0's and 1's

### Bytes :

-  8 bits = 1 Byte
  

	![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-3.png)


> Speed is measured in ==bits== per second
![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-4.png)

![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-5.png)

## Ethernet Standards


![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-6.png)


![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-7.png)

### Types of Cables determined by Ethernet Standards

Cooper cables used in Ethernet standards are the UTP Cables

## UTP Cables :

> UTP => Unshielded Twisted pair 

Unshielded  =>  no metallic shield  means its vulnerable to the electrical interference

Twisted pair => cables twisted to each other in order to protect from EMI

4 PAIRS of wires twisted => total 8 wires


![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-8.png)

RJ 45 cables uses UTP cables and has 8 pins because it uses UTP cables 

![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-9.png)

not all ethernet standards uses all eight wires 

![](Attachments/Pasted%20image%2020261009074857.png)![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-10.png)



## Example : 

- If i want to connect the PC and switch  using a Ethernet or Fast Ethernet cable  ( 10Base-T, 100Base-T)

- Remember We are using RJ 45 connector and it uses UTP cables so 8 wires inside
- As we mentioned before not all standards uses the 8 wires 
- Here we use **10 Base- T and 100Base-T** which uses only 4 wires

	![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-11.png)

- Here  PC is using 1 and 2 to transmit the data (Tx) so switch using those to receive the data (Rx)
- Switch  using 3 and 6 to transmit data (Tx) and Pc uses that to receive the data (Rx)
- Here both devices receive and send data at the same time called **Full Duplex**
	
	![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-12.png)

![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-13.png)

2 different devices uses straight through cables 
 when we try to connect same device like pc - pc or  router - router uses cross over cable because  as we studied pc 1 and 2 pins to transmit so there will be collision thats why we use cross over cables

#### Example 

- connecting switch to switch
-  we know switch uses 1 and 2 => receive and 3 and 6  => transmit 
- so cables are crossed over 
	![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-14.png)


Another Example Router - PC

![](Attachments/Day%2002%20-%20Interfaces%20and%20Cables-15.png)


