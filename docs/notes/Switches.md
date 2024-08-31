A switch is a device that allows multiple users to connect at once to allow sharing of data through the use of ports.

It supports,
- Unicast
- Multicast
- Broadcast

The switch works in the layer 2 of the OSI model of network, where it uses the **MAC address** to allow data transfer between devices.

## Switch v/s Hub

In switches, we know that the message is only sent to the respective receiver, this wasn't always the case. Earlier Hubs were used, which not only sent the message to the appropriate receiver, but sent the message to every device connected to its ports.

This was a major disadvantage. The main reason for this is that the Hub only operated in **layer 1** of the OSI model, meaning it didn't have access to the MAC addresses of the devices connected to it. (MAC addresses belong to layer 2).

## CAM Tables

Content Addressable Memory table, or commonly known as CAM tables, are specially type of memory tables used by switches.

This table stores the MAC addresses of the devices connected to its ports. This makes it easy for the switch to transfer messages only to the devices in question.

The switches don't automatically have this table generated, the table is built by recording the source address and inbound port of all frames. As frames arrive on switch ports, the source MAC addresses are learned and recorded in the CAM table.

When a frame arrives at the switch with a destination MAC address of an entry in the CAM table, the frame is forwarded out through only the port that is associated with that specific MAC address. The information a switch uses to perform a lookup in a CAM table is called a key.

---

An example of a network which uses a Switch

![Pasted image 20240527140106.png](./images/Pasted%20image%2020240527140106.png)

Example of the CAM Table or MAC Forward Table

![Pasted image 20240527140303.png](./images/Pasted%20image%2020240527140303.png)