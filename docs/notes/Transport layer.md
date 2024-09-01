Transport Layer protocols provide a **logical communication** between application processes running b/w hosts. This logical communication allows processes to send messages to each other.

The TL protocols are implemented on **end systems**. When the process wants to send message to another process, the message will pass through its application layer to its transport layer. Here the transport layer will split this message into chunks and attach a transport layer header, these chunks are called **segments**.

The segments are sent down to the network layer where they are encapsulated with the network layer header. (**datagram**)

Transport layer provides logical communication between processes in end systems whereas network layer provides logical communication b/w hosts.

> Service provided an upper layer usually depends on a service provided by a lower layer.

Transport layer packets are referred to as **segments**. Particularly, packets sent using **TCP** are **segments** and using **UDP** are **datagrams**.

Since **network layer** packets are also **datagrams**, we refer to TCP/UDP packets as segments.

Network layer has its own protocol, **Internet Protocol**. It's called a **best effort delivery service protocol**, i.e. it tries its best to deliver the packets but it doesn't guarantee the delivery of the packets. So we can call the **IP a unreliable protocol**.

The IP is aided with the UDP/TCP to make it more reliable. TL protocols extend their help to aid IP to help with its delivery service.

Although, IP aided with UDP is actually more unreliable compared to IP aided with TCP as TCP provides reliable data transfer and congestion control. 

> Congestion control allows equal share of bandwidth to TCP connections. This protocol prevents one connection from swamping the links & routers 

Extending host-to-host delivery to process-to-process is called **transport layer multiplexing and demultiplexing**.

## Multiplexing & Demultiplexing

The host-to-host delivery service provided by the network layer extended to a process-to-process delivery service for applications running on hosts. This service is required by every computer running applications.

A process can have one or more sockets at the same time, hence the sockets require a unique identifier which is the port number. But instead of sending the message directly to the socket at its port number, the msg is first sent to an intermediate port.

At the receiving end, the transport layers receives the segments and examines it for the destination port number and sends the message accordingly. This is **demultiplexing**.

The job of gathering data, port numbers (source and destination) & attaching the transport layer header to the segments and then sending this to the network layer is called **multiplexing**
![[Pasted image 20240830100108.png]]

Hence Multiplexing requires,
1. Unique identifier for ports
2. Each segment having special fields indicating the destination socket.

![Pasted image 20240830100228.png](./images/Pasted%20image%2020240830100228.png)

> Port number is 16 bit number ranging from 0 to 65535. Well known ports range from 0 to 1023.

### Connectionless mux and demux

- UDP is used this.
- During UDP socket programming, OS automatically assigns ports numbers to sockets or the application programmer can assign it their selves.
- If the programmer is implementing a well known port program, they must assign the socket the well known port itself.
- **UDP socket** is fully identified by a **two tuple**, dest. IP addr and dest. port number
- If two UDP segments have different source IP addr and/or port numbers but **same** dest. ip & port number, then the two segments are directed to the same process via the same socket.

Example

Host A (UDP port 19157) wants to send to -> Host B (UDP port 46428)

- A creates segment which includes => Dest. port, source port, and other values
- segment -> n/w layer -> encapsulated w/ n/w header -> datagram
- A datagram sent to B. 
- B transport layer receives and examines segment.
- Sends message to desired port (46428)

### Connection oriented mux and demux

- **TCP socket** is identified by a **four tuple**, source IP, source Port, dest. IP, dest Port.
- Two TCP segments with different source IP and/or port numbers are directed to two **different** sockets.
- In a simple TCP implementation application, the server side has a "welcome socket" ready to receive connection requests. The TCP client sends a **connection establishment request**.

> Connection establishment request contains nothing but the dest. port number and some special connection establishment bit set in TCP header and source port number.


#### Port security

A process on the server usually waits for requests on an **open port**. Once the client finds this open port it can easily map out the process linked to it. 

This can be useful in finding which network applications are running on the host. But this can also lead to a security vulnerability, if the open port has a known security flaw, then the host is doomed for an attack.

### Web server & TCP

Earlier web servers created a new process which had its own socket for every new TCP connection made. But new high-performing web servers use only **one connection**. 

Servers create threads for each new connection with a new socket for each connection. So there could be at a given moment there could multiple sockets pointing to the same process.

In a persistent connection, one socket is responsible for HTTP communication between client and server.

In non-persistent connection, multiple sockets are created and closed for each request & response between the client and server. This can create load on a busy server.

## Connectionless Transport: UDP

- UDP is a connectionless protocol with little error checking and mux & demux functions.
- UDP adds almost nothing to IP.

We know, 
- UDP takes the message from application process, attaches **source & dest** port number for mux & demuxing and other small fields.
- This segment is encapsulated with the transport layer header and sent to the network layer. Then it's further encapsulated with the network header to form the IP datagram. This datagram is then sent to the destination.
- As we see, there is no handshaking done between the source & destination. Hence UDP is connectionless.

And,
- DNS is another application layer protocol that uses UDP as its underlying protocol.
- The **host side** UDP makes its segment, passes it to the network layer to make the datagram and this is sent to the **name server**
- If DNS application at the host side doesn't get any reply, it tries sending a query again & if after repeated trying it doesn't get a reply, it informs the invoking application.

Why UDP over TCP if it's unreliable?
1. **Finer application layer control over when data is sent**
	- UDP quickly encapsulates the message w/ the headers and port information and sends it to the network layer. 
	- On the other hand TCP has congestion control & does a three-way handshake. TCP keeps on sending a packet until it receives the ack. packet back from destination.
2. **No connection establishment**
	- UDP just blasts away without any formal preliminaries. UDP doesn't introduce any delays.
	- This is probably the reason why DNS using UDP. Even HTTP.
	- Google Chrome browsers use QUIC, Quick UDP Internet Connection. Which uses UDP as its underlying transport protocol and implements reliability in an application layer protocol on top of UDP.
3. **No connection state**
	- TCP maintains a connection for each request and response whereas UDP doesn't maintain any connection and doesn't track any parameters
4. **Small packet header overhead**
	- UDP has only 8 bytes of header and TCP has 20 bytes of header.

> But the delays introduced by HTTP over TCP is necessary to download important documents.

![Pasted image 20240901135722.png](./images/Pasted%20image%2020240901135722.png)

- UDP provides no congestion protocol but this protocol needed in a congested state in which very little useful work is done.
- When there is a congested state, all the UDP packets wouldn't traverse from source to destination. This would in turn block the TCP packets.
- Although, reliability is something that can be implemented in the application itself while using UDP as the underlying protocol.
- QUIC is an example of such thing.
### UDP segment structure

- **Application data** contains DNS query or response message or application data itself.
- **UDP header** has four fields, each of 2 bytes.
- **Length field** specifies the number of bytes in the UDP segment.
- **Checksum** field tells whether any error has occurred or not.
![Pasted image 20240901141812.png](./images/Pasted%20image%2020240901141812.png)

### Checksum

- Checksum is a method to check for any errors/if any bits are manipulated in the segment.
- First addition of the 16 bit words in the segment is done, Any overflow encountered is wrapped around.
- After getting the sum, 1's complement on the sum is performed. This resulting 16 bits are sent along with the other 16 bit words.
- The destination receives this segment and adds up these 16 bit words along with the checksum. If the result is just 16 1's, then there is no error. If there is a 0, then there is an error.

But why does UDP need this error detection method?
- No guarantee about error checking between source and destination
- In router memory could destory bits.
- UDP provides error checking on an **end to end** basis
- Although UDP provides this error checking method, it doesn't provide any method to overcome it.

> OS fundamental **end to end** principle: Functions provided at the lower level maybe redundant or of little value when compared to the cost of providing them at the higher level.