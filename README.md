# NetPractice

This practical exercise helps develop a deeper understanding of how routing and network division work in real-world scenarios.

Model TCP/IP - 4 layers, model OSI - 7 layers.

| Layer    | Description                                  |
|----------|----------------------------------------------|
| Layer 4  | Web browser, email clients                  |
| Layer 3  | ex. TCP (80 - HTTP, 443 - HTTPS, 25 - SMTP), UDP (53 - DNS, 67 - DHCP) |
| Layer 2  | Routing and IP addressing                   |
| Layer 1  | Ethernet cables                             |

IPv4 - 32 bits
IPv6 - 128 bits

**Network Address** – the first address in the network, indicates the beginning of the address range of a given network.

**Broadcast Address** – the last address in the network, used for sending messages or packets to all devices in that network simultaneously.

**Subnet Mask** – a number that defines which part of the IP address refers to the network and which part refers to hosts in the network. It helps determine whether a machine belongs to a specific network.

**Router** – sends packets between different networks based on IP addresses.

**Switch** – allows multiple devices to connect to the same network.

**Modem** – a device that enables data transmission between computers over a telecommunication network. Its main function is converting digital signals from a computer into analog signals that can be transmitted over phone lines, fiber optics, TV cables, or other transmission media – and vice versa. It allows networks to connect to the Internet by translating data between these two types of signals.

**Gateway** – a "gateway" between two networks that enables communication between them.

**Loopback Address** – a special IP address used for testing internal network communication within a device without going out to the network. A special range of IP addresses (127.0.0.0 to 127.255.255.255) reserved for internal communications within a device.

**IP Header** – a part of the IP packet that contains essential information required for the correct transmission of data across the network. It manages the transmission of the packet through the network, ensuring it reaches its destination correctly and as intended.

 ### Subnet cheat sheet:
![Subnet cheat sheet](https://i.pinimg.com/originals/7c/98/5b/7c985b0e47c09329458fa17edaab29c6.png)

If you have IP address 10.20.4.13 with a /29 subnet mask:

1. 32 - 29 = 3 → The last 3 bits are zeros: 11111111.11111111.11111111.11111000
2. This means the subnet mask is 255.255.255.248.
3. Perform a bitwise AND operation between 10.20.4.13 and 255.255.255.248.
4. After the operation, the network address is 10.20.4.8.
5. 2^3 = 8 (this represents the number of addresses per subnet).
6. 10.20.4.8 + 2^3 gives the broadcast address, which is 10.20.4.15.
7. 8 - 2 = 6, which represents the number of available IP addresses for hosts.
8. The available host IP range is from 10.20.4.9 to 10.20.4.14.

- **Network ID:** `10.20.4.8`
- **First ID:** `10.20.4.9`
- **Last ID:** `10.20.4.14`
- **Broadcast ID:** `10.20.4.15`
- **Next ID:** `10.20.4.16`

### Subnetting:
For example: Our network is 158.46.67.0/26

1. Understanding CIDR Notation (/26)
/26 means that the first 26 bits of the IP address are reserved for the network part, and the remaining 6 bits are for the host part.
The number of available IP addresses in this network is 2^6 = 64 addresses (including the network address and the broadcast address).

2. Determining the Subnet Mask
The subnet mask for /26 is:
+ In binary: 11111111.11111111.11111111.11000000
+ In decimal: 255.255.255.192

3. Subnet Division
To divide the 158.46.67.0/26 network into smaller subnets, you need to "borrow" bits from the host part and allocate them to the network part. The more bits you borrow, the more subnets you get, but each subnet will have fewer available IP addresses.

Example: Dividing into 4 subnets
+ To get 4 subnets, you need to borrow 2 bits from the host part (because 2^2 = 4).
+ The new subnet mask will have a length of /28 (26 + 2 = 28).

4. Calculating Subnet Ranges
For a /28 mask:
+ The number of available IP addresses in each subnet: 2^4 = 16 (including the network address and broadcast address).
+ The subnet increment (step) is 16 (since each subnet has 16 addresses).

List of subnets:
* 158.46.67.0 – 158.46.67.15
* 158.46.67.16 – 158.46.67.31
* 158.46.67.32 – 158.46.67.47
* 158.46.67.48 – 158.46.67.63

Each subnet has 16 IP addresses, with:
+ The first one address being the network address (e.g., 158.46.67.0).
+ The last one address being the broadcast address (e.g., 158.46.67.15).
+ The fourteen addresses available for hosts.

5. Other Subnetting Options:
+ You can divide the 158.46.67.0/26 network into a different number of subnets, depending on your needs:
+ The eight subnets: Borrow 3 bits (new mask /29), each subnet will have 8 addresses.
+ The sixteen subnets: Borrow 4 bits (new mask /30), each subnet will have 4 addresses.

### Topics covered
- IPv4 address calculations
- Subnetting and CIDR notation
- Network and broadcast addresses
- IP range allocation
