# What is the Internet

## Nuts and Bolts Description

The internet is a computer network that interconnects billions of computing devices throughout the world. On the internet, all of these devices are called **hosts or end systems**.

![Internet Diagram](Pasted%20image%2020240719174112.png)

End systems are connected to each other by a network of **communication links (coaxial, copper, optical, etc.) and packet switches**. Different links can transmit data at different rates.

> Transmission rate of a link is measured in bits/second.

When data is to be transferred, it isn't just sent as raw data; it's modified and merged with additional information required by both end systems.

**Sending data system => Data + Header bytes (**packets**)**

The receiving end system receives the packets and de-structures them to get the original data.

How does this packet reach the receiver end system though? Something called a **packet switch** is used to **forward** the packet received and send it to the appropriate end system based on the headers present.

The two most prominent types of packet switches are **Routers** and **Link-Layer switches**.

> **Routers** => Access networks (An access network is a type of network which physically connects an end system to the immediate router (also known as the “edge router”) on a path from the end system to any other distant end system.)
>
> **Link Layer Switches** => Network core (Part of a telecom system that connects users and the network)

The sequence of communication links and switches that are traversed by a packet is known as a **route** or **path**.

The internet provided to the End systems allows the transfer of data. The internet is provided through **Internet Service Providers (ISPs)**.

Essentially, each ISP in itself is a network of packet switches and communication links.

Examples of some network access provided by ISPs are Cable modem/DSL & mobile wireless access.

Now there are multiple tiers of ISPs that have to be interconnected to provide internet access.

1. Lower Tier
2. National Tier
3. International Upper Tier

Each of these ISPs are managed and runs the IP Protocol and adheres to the standards that are set by some organizations.

The IP protocol mentioned above isn't the only protocol, and it isn't only run by ISPs. End systems, switches, and other devices present on the internet also run the protocols.

The two most important protocols on the internet are:
1. Transmission Control Protocol (TCP)
2. Internet Protocol (IP)

These two protocols are collectively called **TCP/IP**.

As for the standards mentioned, the Internet standards are developed by the **Internet Engineering Task Force (IETF)**.

The IETF standards documents are called **Request for Comments (RFCs)**. RFCs define protocols such as TCP, IP, HTTP, etc. There are currently 7,000 RFCs.

## Services Description

The previous section described the internet using its components. But we can also describe it as an **infrastructure that provides services to applications**.

Traditional applications (email, web surfing, messaging, maps, etc.) are said to be **distributed applications** since they involve **multiple end systems** that exchange data with each other.

The internet primarily runs on the end systems, and the packet switches help with the exchange of data among end systems.

But how do these applications run on the end systems? To even make an application first, we need to **write it using a language such as C, JAVA, etc.** 

These programs can be run on end systems independently, but for these programs to transfer data and communicate, we need something called a **socket interface**, which is provided by the Internet.

The socket interface specifies how a program on the end systems asks the Internet to deliver data to a specific destination.

Again, this socket interface also has to follow a set of rules that the sending program must follow.

## What is a Protocol?

A protocol is exactly what it says; all activity on the internet that involves two or more communicating remote entities is governed by a protocol.

A simple example where a protocol is used is on the Web. When we first type the URL of a Web page into a web browser, the computer sends a request to the server. The server receives this and sends an **OK** for the connection. Following this, the computer then sends a **GET** request to the server to load the web page. At last, the server returns the web page to the computer.

> A protocol defines the format and the order of messages exchanged between two or more communicating entities, as well as the actions taken on the transmission and/or receipt of a message or other event.


![Protocol Example](Pasted%20image%2020240719184457.png)


