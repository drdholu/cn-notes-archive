The need of network models arose when different networks consisting of different machines could not communicate with each other.

For example, in the 1960's, many companies developed their own networks based on the ideology of the ARPANET, but these networks could not communicate with each other as they were proprietary.

With this need of some kind of standard model, came two models, **TCP/IP and the OSI** network models.

## TCP/IP vs OSI

### TCP/IP

The Transmission control protocol/Internet protocol (aka TCP/IP) has a layered architecture consisting of 4 layers.

1. Application
2. Transport
3. Network
4. Physical

> At times, Physical layer is divided into two layers, Physical and Data Link layer

### OSI

Open system interconnect (aka OSI). This model is mostly a conceptual model used in network comms by network engineers.

It has a 7 layers architecture where most of the layers are similar to the TCP/IP

1. Application
2. **Presentation**
3. **Session**
4. Transport
5. Network
6. **Data link**
7. Physical

> The Presentation and Session layers are stuffed as one to form the application layer in the TCP/IP model.

![Pasted image 20240529130332.png](./images/Pasted%20image%2020240529132527.png)

#### Acronyms

- **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing
- **P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way


> The process of taking data and merging it with important related info is called **encapsulation**.

## Data traversal through model layers

When the user wants to send data to another device, the data has to go down all the layers and get enclosed in a figurative envelope and then go up through all the layers and get opened in each layers, one by one.

Lets understand this in a bit detail.

Starting from the senders side, say we want to access a website. We will need to send a request to that website. To send this request we use the **HTTPS** protocol.

### Application Layer

First this request will go through the **application** layer. It goes in the form of data which contains the info about the request and the protocol used.
### Transport Layer

Now this data goes down to the **transport** layer. Here in the transport layer, there are two protocols we mainly use, TCP (Transmission control protocol) and UDP (user datagram protocol)

High-level difference between the two protocols

| TCP           | UDP  |
| ------------- | ---- |
| More reliable | Fast |

In this layer (L4 or transport), along with the data, another **header** is attached which contains info about the protocol.

There is info like the destination port (ex: 1234) and the source port (which can be 443 -> port number for HTTPS traffic).

This data is called **segments**.
### Network layer

This segment of data is now passed down to the **network** layer where we further encapsulate it with **headers**. This header contains info about the IP addresses of the source and destination.

This header is important for the router (the **router can only understand IP addresses** i.e. L3 addr.) to get directions.

The data in this layers is also referred to as **packets**.

### Data Link layer

The packet is now sent down to the **data link layer**. Here, instead of just adding a **header**, a **trailer** is also added. 

The header here contains the **mac addr.** of the source and destination. This is needed to give directions to the switch (the switch only understands MAC address i.e. L2 addr.)

The data in this layer is also called **frames**

### Physical layer

Finally after all the encapsulation, we receive the frames from data link layer, and now we can send the frames to the website we wanted access.

### Receivers End

In the receivers side, the data isn't just taken as a frame, the frame must go through the procedure of un-encapsulation so that the routers, switches can read the address of the destination.

One by one, up the layer, each header/trailer is removed until we reach the application layer and finally receive the data.

