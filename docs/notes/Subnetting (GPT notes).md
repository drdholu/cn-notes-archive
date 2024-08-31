# Subnetting in IP Networks

## Overview
Subnetting is a technique used in IP networking to divide a larger network into smaller, more manageable sub-networks (subnets). This allows for better organization, improved security, and efficient use of IP addresses. IP addresses are divided into classes: A, B, and C. Each class has a default subnet mask and a different number of networks and hosts.

## IP Address Classes

### Class A
- **Range**: 1.0.0.0 to 126.0.0.0
- **Default Subnet Mask**: 255.0.0.0 (/8)
- **Number of Networks**: 128 (2^7, minus 2 reserved addresses)
- **Hosts per Network**: 16,777,214 (2^24 - 2)

### Class B
- **Range**: 128.0.0.0 to 191.255.0.0
- **Default Subnet Mask**: 255.255.0.0 (/16)
- **Number of Networks**: 16,384 (2^14)
- **Hosts per Network**: 65,534 (2^16 - 2)

### Class C
- **Range**: 192.0.0.0 to 223.255.255.0
- **Default Subnet Mask**: 255.255.255.0 (/24)
- **Number of Networks**: 2,097,152 (2^21)
- **Hosts per Network**: 254 (2^8 - 2)

## Subnetting Class C Networks

### Key Concepts

1. **IP Address and Subnet Mask**:
   - An IP address consists of two parts: the network portion and the host portion.
   - The subnet mask determines which part of the IP address is the network portion and which part is the host portion.
   - For a Class C network, the default subnet mask is 255.255.255.0 or /24 in CIDR notation.

2. **CIDR Notation**:
   - Classless Inter-Domain Routing (CIDR) notation is a shorthand for denoting the subnet mask.
   - /24 means that the first 24 bits of the IP address are the network portion, leaving 8 bits for hosts.

3. **Subnetting**:
   - Subnetting involves borrowing bits from the host portion to create additional network bits, thus creating more subnets.
   - For example, changing from /24 to /25 (borrowing 1 bit) doubles the number of subnets but halves the number of hosts per subnet.

4. **Number of Subnets and Hosts**:
   - The number of subnets created can be calculated as 2^n, where n is the number of bits borrowed.
   - The number of hosts per subnet can be calculated as 2^(32 - subnet mask) - 2. The subtraction of 2 accounts for the network and broadcast addresses which cannot be assigned to hosts.

5. **Network ID and Broadcast Address**:
   - The network ID is the first address in a subnet, used to identify the subnet.
   - The broadcast address is the last address in a subnet, used to send data to all hosts in the subnet.
   - Usable IP addresses are those between the network ID and the broadcast address.

### Example

For a Class C network 192.168.1.0 with a subnet mask of 255.255.255.192 (/26):
   - Number of subnets: 2^(26-24) = 4 subnets.
   - Number of hosts per subnet: 2^(32-26) - 2 = 62 hosts.

The four subnets will be:
1. 192.168.1.0/26
   - Network ID: 192.168.1.0
   - Broadcast Address: 192.168.1.63
   - Usable IP Range: 192.168.1.1 - 192.168.1.62

2. 192.168.1.64/26
   - Network ID: 192.168.1.64
   - Broadcast Address: 192.168.1.127
   - Usable IP Range: 192.168.1.65 - 192.168.1.126

3. 192.168.1.128/26
   - Network ID: 192.168.1.128
   - Broadcast Address: 192.168.1.191
   - Usable IP Range: 192.168.1.129 - 192.168.1.190

4. 192.168.1.192/26
   - Network ID: 192.168.1.192
   - Broadcast Address: 192.168.1.255
   - Usable IP Range: 192.168.1.193 - 192.168.1.254

### Detailed Calculation:

1. **Subnet Mask and CIDR Notation**:
   - The subnet mask 255.255.255.192 corresponds to /26 in CIDR notation.
   - This means that the first 26 bits are for the network, and the remaining 6 bits are for hosts.

2. **Number of Subnets**:
   - We are borrowing 2 bits (26 - 24) from the host portion of the default Class C subnet mask (255.255.255.0).
   - Number of subnets = 2^2 = 4 subnets.

3. **Number of Hosts per Subnet**:
   - Number of hosts per subnet = 2^(32 - 26) - 2 = 2^6 - 2 = 64 - 2 = 62 hosts.
   - The subtraction of 2 accounts for the network address and the broadcast address, which cannot be assigned to hosts.

4. **Subnet Increment**:
   - Subnet increment = 256 / number of subnets = 256 / 4 = 64.
   - This means each subnet increases by 64 addresses.

### Calculation of Each Subnet:

#### Subnet 1: 192.168.1.0/26
- **Network ID**: The first address in the subnet range is 192.168.1.0.
- **Broadcast Address**: The last address in the subnet range is 192.168.1.63 (192.168.1.0 + 63).
- **Usable IP Range**: The addresses between the network ID and the broadcast address are 192.168.1.1 to 192.168.1.62.

#### Subnet 2: 192.168.1.64/26
- **Network ID**: The next subnet starts at 192.168.1.64 (192.168.1.0 + 64).
- **Broadcast Address**: The last address in this subnet is 192.168.1.127 (192.168.1.64 + 63).
- **Usable IP Range**: The addresses between the network ID and the broadcast address are 192.168.1.65 to 192.168.1.126.

#### Subnet 3: 192.168.1.128/26
- **Network ID**: The next subnet starts at 192.168.1.128 (192.168.1.64 + 64).
- **Broadcast Address**: The last address in this subnet is 192.168.1.191 (192.168.1.128 + 63).
- **Usable IP Range**: The addresses between the network ID and the broadcast address are 192.168.1.129 to 192.168.1.190.

#### Subnet 4: 192.168.1.192/26
- **Network ID**: The next subnet starts at 192.168.1.192 (192.168.1.128 + 64).
- **Broadcast Address**: The last address in this subnet is 192.168.1.255 (192.168.1.192 + 63).
- **Usable IP Range**: The addresses between the network ID and the broadcast address are 192.168.1.193 to 192.168.1.254.

### Why is it 256?

1. **Total Number of Addresses in One Octet**:
   - The fourth octet can have values from 0 to 255, giving a total of 256 values.
   
2. **Number of Subnets**:
   - The number of subnets is determined by the number of bits borrowed from the host portion of the address.
   - For example, if you borrow 2 bits for subnetting in a Class C network, you get \(2^2 = 4\) subnets.

3. **Subnet Increment**:
   - The subnet increment is calculated as: 
     \[
     \text{Subnet Increment} = \frac{256}{\text{Number of Subnets}}
     \]
   - In this case, with 4 subnets, the calculation is:
     \[
     \text{Subnet Increment} = \frac{256}{4} = 64
     \]

By following these steps, you can divide a Class C network into multiple subnets and determine the network ID, broadcast address, and usable IP range for each subnet.
