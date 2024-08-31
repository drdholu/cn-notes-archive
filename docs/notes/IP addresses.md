When IP addresses were first created, they looked like this: `255.255.255.255`. This is called an **IPv4 address**, which consists of **4 octets separated by 3 dots**. Each octet can range from **0 to 255**.

This IP address configuration allowed for over 4 billion possible addresses to be assigned to devices worldwide. However, due to inefficient management of these addresses, we eventually ran out of them. Let’s look at how this happened.

### IP Address Classes

IP addresses are classified into different classes, with each class having a specific range of addresses. The classes are **A, B, C, D, and E**.

|Class|Range|Subnet Mask|No. of Networks|
|---|---|---|---|
|A|0 - 127|255.0.0.0|128|
|B|128 - 191|255.255.0.0|16,384|
|C|192 - 223|255.255.255.0|2,097,152|
|D|224 - 239|N/A|N/A|
|E|240 - 255|N/A|N/A|

> The subnet mask defines which part of the IP address is the network portion and which part is the host portion. The octets that match `255` in the subnet mask are fixed and define the network, while the octets that don’t match `255` can vary and define individual hosts within that network.

Class A addresses, which provide a large number of host addresses, are typically assigned to large organizations and government entities.

> When an IP address conforms to the class and subnet mask specifications, it is part of a **Classful network**. However, if we take an IP address and apply a different subnet mask than the default for its class, it belongs to a **Classless network**.
> 
> For example, the IP address `9.0.0.0` with a subnet mask of `255.0.0.0` is in a classful network. But if we take an address from this network, say `9.1.4.0`, and assign it a subnet mask of `255.255.255.0`, it becomes part of a classless network.

The subnet mask also tells us how many networks and how many hosts per network we can have. Class C provides the most networks with fewer hosts per network compared to Classes A and B.

Class D is used for multicasting, while Class E is reserved for experimental purposes and is not commonly used.

The range `127.0.0.0` is reserved as a **loopback** address, which is used for testing and diagnostics on a local machine. The most common loopback address is `127.0.0.1`, often referred to as "localhost." This means we have about 16 million addresses dedicated to testing purposes.

### Private IP Addresses

As the available IPv4 addresses began to run out, **RFC 1918** was introduced to help mitigate the issue.

The solution was to designate certain ranges from the existing classes (A, B, and C) as **private addresses**. These private IP address ranges are:

- **Class A**: 10.0.0.0 - 10.255.255.255 (Subnet Mask: 255.0.0.0)
- **Class B**: 172.16.0.0 - 172.31.255.255 (Subnet Mask: 255.240.0.0)
- **Class C**: 192.168.0.0 - 192.168.255.255 (Subnet Mask: 255.255.0.0)

Private IP addresses are used within local networks and are not routable on the public internet. This means that multiple devices across different networks can have the same private IP addresses without causing conflicts.

However, devices within a local network using private IP addresses need a way to communicate with the internet. This is achieved through **Network Address Translation** (NAT), a process performed by your router.

When a device with a private IP wants to communicate with the internet, the router uses a public IP address provided by your ISP. NAT translates the private IP to the public IP, allowing the device to communicate externally. When a response is received, the router uses NAT to direct the response to the correct device within the local network.

Even with NAT, the exhaustion of IPv4 addresses remained a problem, leading to the development and adoption of IPv6, which provides a much larger address space.