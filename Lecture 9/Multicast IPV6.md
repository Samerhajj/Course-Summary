## Reverse Path Forwarding
![Alt text](IMAGES/Pasted%20image%2020230206095858.png)
### Distance Vector Multicast Routing Protocol
![Alt text](IMAGES/Pasted%20image%2020230206095923.png)
## Prune and Graft

>Prune message is a type of multicast control message used in Protocol Independent Multicast (PIM) to control the distribution of multicast traffic in a network. It is used by routers to stop forwarding multicast data to branches of a multicast distribution tree that don't have any receivers. The prune message is sent upstream to the multicast source to stop sending traffic to the specific branch. This helps to reduce the amount of unnecessary multicast traffic and improve network efficiency.

>The Graft message is used in multicast networking to request that a branch be added to an existing multicast distribution tree. It is used in cases where a multicast receiver wants to receive traffic from a new sender and the distribution tree needs to be updated to reflect this. The Graft message is sent from the new receiver to the multicast routers in the network, which use it to update their routing information and build a new branch in the distribution tree to reach the new receiver.

 ## Center Based Approach
![Alt text](IMAGES/Pasted%20image%2020230206100416.png)
## PIM (Protocol Independent Multicast)
![Alt text](IMAGES/Pasted%20image%2020230206100535.png)
![Alt text](IMAGES/Pasted%20image%2020230206100622.png)

---
## Multicast Across AS's
![Alt text](IMAGES/Pasted%20image%2020230206100920.png)
	`SR stands for Source Routing in multicast. It is a technique where the multicast sender specifies the path the multicast packets should take through the network. This allows the sender to control the distribution of the packets and to avoid unwanted network congestion.

#ipv6
# IPv6 Addresses
![Alt text](IMAGES/Pasted%20image%2020230206101429.png)
![Alt text](IMAGES/Pasted%20image%2020230206101545.png)
![Alt text](IMAGES/Pasted%20image%2020230206101608.png)

---
## Embedding IPv4 in IPv6
- To enable IPv4 and IPv6 devices to work together
- IPv4 address -> IPv6 address
	- Extend the IPv4 address with 0s
	- Denote embedded IPv4 in (.)
	- If node only understands IPv4:$$ffff:0:0/96$$
			- Example:$$::ffff:202.102.30.16$$
			- Discern dual stack (96 0's) and IPv4 only (80 0's and 16 1's)

![Alt text](IMAGES/Pasted%20image%2020230206101846.png)
The picture illustrates the concept of embedding IPv4 in IPv6, which is a technique used to allow communication between IPv4 and IPv6 networks. The main purpose of this technique is to facilitate the transition from IPv4 to IPv6 and provide compatibility between the two protocols.

>This picture is depicting a network with 3 computers, each having different IP stack configurations:

-   One computer has both IPv4 and IPv6 stack,
-   one has only IPv4 stack,
-   one has only IPv6 stack.

These computers are connected to both an IPv4 router and an IPv6 router.

When the computer with only IPv4 stack sends a message to 10.10.10.10, the IPv6 router translates it into ::ffff:10.10.10.10, which is an IPv6-encoded form of the IPv4 address.

The computer with only IPv6 stack sends a message to the IPv6 router at 2001:face:1200::8901.

The computer with both IPv4 and IPv6 stack sends messages to both the IPv4 and IPv6 routers. The message sent to the IPv4 router is 10.10.10.20 and the message sent to the IPv6 router is at 2001:face:1200:8900.

The idea behind embedding IPv4 in IPv6 is to allow devices that only support IPv4 to communicate with devices that support both IPv4 and IPv6, using IPv6 as the transport layer.

---
#IPv6
## IPv6 Packet Format
![Alt text](IMAGES/Pasted%20image%2020230206102547.png)
The IPv6 packet format consists of the following components:

1.  Version: A 4-bit field indicating the IP version, which is 6 for IPv6.
    
2.  Traffic Class: An 8-bit field used to provide Quality of Service (QoS) information.
    
3.  Flow Label: A 20-bit field used for flow-based traffic management.
    
4.  Payload Length: A 16-bit field indicating the size of the payload in octets.(bytes)
    
5.  Next Header: An 8-bit field indicating the type of the next header.
    
6.  Hop Limit: A 8-bit field indicating the maximum number of hops a packet can traverse before it is discarded.
    
7.  Source Address: A 128-bit field indicating the address of the source node.
    
8.  Destination Address: A 128-bit field indicating the address of the destination node.
    
9.  Payload: The data being carried by the packet, including any extension headers.

`An octet is a unit of digital information that consists of 8 bits.

`The type of next header in IPv6 refers to the type of payload data contained within the packet. It helps the router to understand the type of data being sent over the network and forward it accordingly to the correct protocol layer. Different protocols have different values assigned to the type of next header field, such as 6 for TCP, 17 for UDP, and 58 for ICMPv6. The type of next header field is located in the IPv6 header and is used to determine the type of data in the payload.

![Alt text](IMAGES/Pasted%20image%2020230206103025.png)
In the IPv6 packet format, the "Extensions" refer to the optional fields that can be added to the header for specific purposes such as hop-by-hop options, destination options, and routing headers. These fields are inserted between the basic IPv6 header and the upper-layer protocol data, and are identified by the "Next Header" field in the IPv6 header. The extensions provide more flexible and advanced functionality in IPv6 compared to IPv4, and can be used to support new protocols, manage flow labeling, and allow for better routing, among other things.

### IPv6 Extension Header List
![Alt text](IMAGES/Pasted%20image%2020230206103314.png)
![Alt text](IMAGES/Pasted%20image%2020230206103338.png)
![Alt text](IMAGES/Pasted%20image%2020230206103528.png)
	`Static IP address assignment involves manual configuration of IP address, subnet mask, default gateway and DNS server information on a device. This method is typically used in small networks where a limited number of devices are connected and the administrator wants to ensure that each device has a unique, unchanging IP address.

	Dynamic Host Configuration Protocol (DHCP) is a client-server protocol used to automatically assign IP addresses and other network configuration information (such as subnet mask, default gateway and DNS server) to devices on a network. The DHCP server maintains a pool of available IP addresses and assigns an unused address to each device that requests one. This method is commonly used in larger networks where the number of devices is dynamic and it is not practical to manually configure IP addresses for each device.

## Tunneling
![Alt text](IMAGES/Pasted%20image%2020230206104204.png)
`Tunneling is a method of encapsulating one protocol within another protocol in order to facilitate the communication between two networks that use different protocols. Teredo is a protocol that encapsulates IPv6 packets inside IPv4 UDP packets to traverse Network Address Translation (NAT) and to hide the external address and port in the address. ISATAP (Intra-Site Automatic Tunnel Addressing Protocol) is a protocol that embeds IPv4 addresses in IPv6 addresses. 6to4 (IPv6 over IPv4) is a protocol that routes between IPv6 routing areas over IPv4. These tunneling protocols are used to enable communication between networks that use different protocols and provide a way for transition from IPv4 to IPv6.`

![Alt text](IMAGES/Pasted%20image%2020230206110150.png)
`The image depicts a scenario of IPv6 over IPv4 tunneling, also known as 6to4 tunneling.

`In this scenario, there are two networks, one IPv6 network and one IPv4 network, which are not directly connected. A computer in the IPv6 network wants to communicate with a computer in the IPv4 network. To achieve this, the IPv6 network encapsulates IPv6 packets inside IPv4 packets and sends them to a 6to4 relay router. This router is connected to both the IPv6 and IPv4 networks and is responsible for removing the IPv4 header and forwarding the IPv6 packets to the IPv4 network.

`The computer in the IPv4 network receives the IPv6 packets, and if it is capable of handling IPv6, it can process and respond to the communication. If not, the packets are discarded.

`This diagram illustrates a possible solution to the challenge of connecting two networks with different protocols (IPv6 and IPv4), by encapsulating the IPv6 packets inside IPv4 packets, making it possible to traverse the IPv4 network and reach the intended destination.`
