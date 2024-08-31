These cables are the reason we can do things on the internet.

A standard Ethernet cable consists of **4 twisted pairs of wires** within an outer covering. But why twisted?

- In the real world, there is a lot of **Electromagnetic Interference (EMI)** that can disrupt the signals traveling through these wires.
- Another source of interference is the neighboring wires themselves. If the wires were laid out in parallel, there would be signal interference between them, known as **crosstalk**.

These types of cables are called **Unshielded Twisted Pair (UTP) cables**. There are also **Shielded Twisted Pair (STP) cables**, where the twisted pairs are shielded with an **extra coating** to provide additional protection.

Modern Ethernet cables typically contain **4 pairs** of twisted wires, all color-coded—specifically orange, blue, green, and brown. These pairs of wires transmit and receive signals, enabling communication.

This type of Ethernet is called **Cat5e Ethernet cable**, designed for **1000Base-T** networks, which refers to twisted pairs of wires capable of transmitting data at 1000 Mbps (1 Gbps).

> Cat5e refers to the specific category of twisted pair cables used in Ethernet.

---

## Internals of Ethernet Cable

Before the 8-wire cables, Ethernet used 4-wire cables, such as in the **10Base-T** and **100Base-TX** standards.

The 10Base-T Ethernet cable consisted of just 2 pairs of twisted wires (or 4 wires total).

One pair was designated for sending data, while the other was for receiving data. Data is transferred by fluctuating the voltage, representing binary data (1's and 0's), along with encoding/decoding techniques.

However, the cables alone aren't sufficient. A connector on both ends of the cable, called an **RJ-45**, completes the circuit by providing metal pins. Each pin on the connector has a specific function, and the way the wires are attached to the pins determines the cable's behavior.

### Common Cable Configurations

1. **Straight-Through Cable**
    
    - In this design, the wires are connected in the same sequence on both ends of the cable. For instance, if a wire is attached to pin 1 on one end, it will also be attached to pin 1 on the other end.
    - This configuration is ideal for connecting two different types of devices (e.g., a computer to a switch).
    - ![[Pasted image 20240829172955.png]]
1. **Crossover Cable**
    
    - In this design, the wires are crossed and connected to different pins on the opposite ends (following a specific pattern).
    - This configuration is useful when connecting two similar devices (e.g., computer to computer).
    - ![[Pasted image 20240829172943.png]]

In newer Ethernet cables, like the 1000Base-T, there are 8 wires, but only 4 of them are used for simultaneous data transmission and reception.

These modern Ethernet cables also follow the same cable configurations as discussed above.

There are also naming conventions for the wiring arrangements, known as **T568A** and **T568B**. By using a combination of these standards, we can create the desired cable configuration (straight-through or crossover), for example, using T568A on one end and T568B on the other for a crossover cable.
![[Pasted image 20240829173255.png]]

> Modern switches and Ethernet devices have a feature called **Auto MDI-X**, which allows them to automatically configure the pins, enabling the use of straight-through cables regardless of the devices being connected.