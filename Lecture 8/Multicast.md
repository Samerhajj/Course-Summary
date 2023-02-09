## Multicast
Multicast is a communication method in computer networks where a source device sends data to multiple receivers simultaneously. This enables efficient distribution of the same data to multiple recipients, reducing network traffic and resource utilization compared to unicast (point-to-point) or broadcast (point-to-all) communication.

Multicast is used for applications such as video conferencing, IPTV, stock market data distribution, and software updates.

![Alt text](IMAGES/Pasted%20image%2020230204155405.png)
In multicast, the identification of a conversation is determined by the multicast group address. The IP multicast group address specifies a group of interested receivers for a particular multicast session. Receivers can join or leave a group at any time, and the group address is used by routers to forward multicast traffic only to the members of the group who have requested to receive it.

In multicast, the address discovery process is performed using a protocol called Internet Group Management Protocol (IGMP). Hosts send IGMP messages to their local router to join a specific multicast group and receive multicast traffic. The router then uses this information to forward the multicast traffic to only those hosts that have joined the group. This helps to minimize network traffic and conserve bandwidth.

Multicast is performed at the Network Layer (OSI Layer 3).
![Alt text](IMAGES/Pasted%20image%2020230204155648.png)
## Ethernet
![Alt text](IMAGES/Pasted%20image%2020230204155736.png)
![Alt text](IMAGES/Pasted%20image%2020230204155807.png)

### Addressess in an Ethernet Frame

- First bit =0->a ( Unicast Address)
	- Sent to one reciever
- First bit = 1-> Multicast Address
	- Sent to a group of receivers
- All bits =1 -> the Broadcast Address
	- Sent to all adapters

#### An Ethernet Adapter Receives:
1. Frames addressed to the broadcast address
2. Frames addressed to its own address
3. Frames sent to a multicast address
	- If it has been programmed to listen to that address
4. All frames
	- If the adapter has been put into promiscuous mode

## IGMP
- Internet Group Management Protocol: between router and hosts on a local area network
	- Only one router per network(designated)
	 - spanning tree algorithm

Message Types:
- Report - request sent from a host to the local IGMP router to indicate that it wants to receive packets from a particular IP multicast conversation.
- Query: Query - message sent from an IGMP router to ask which hosts on the network are interested in receiving IP multicast packets. The Report packet is sent as a response to the query packet.
- Leave Group: message sent from a host that wants to stop receiving packets from a particular IP multicast address.

### Examples
  
![Alt text](IMAGES/Pasted%20image%2020230204160533.png)
![Alt text](IMAGES/Pasted%20image%2020230204160544.png)![Alt text](IMAGES/Pasted%20image%2020230204160557.png)

---
![Alt text](IMAGES/Pasted%20image%2020230204160707.png)
ARP (Address Resolution Protocol) is a protocol used to map an IP address to a physical (MAC) address on a network. It is used by a host to resolve the physical address of another host on the same network. ARP operates at the Data Link Layer (OSI Layer 2) and is used for IP to MAC address resolution.

![Alt text](IMAGES/Pasted%20image%2020230204160754.png)
![Alt text](IMAGES/Pasted%20image%2020230204160805.png)
![Alt text](IMAGES/Pasted%20image%2020230204160813.png)
	To reach networks with multicast traffic, a multicast tree is usually built to distribute the traffic from the sender to all interested receivers in the network. The tree can be either for the whole group or per sender. The tree needs to be discovered so new networks can be added and traffic can be distributed to them. Intermediate nodes in the tree can carry traffic, but it is not always necessary. Whether they should or not depends on the specific requirements of the network. The use of multicast trees helps to reduce the amount of broadcast traffic and makes the distribution of multicast traffic more efficient.

### OVERLAPPING
Overlapping in multicast refers to the situation where two or more multicast groups have a common set of receivers. This means that some receivers receive the same multicast traffic from multiple sources, creating overlapping groups. This can lead to network congestion and bandwidth utilization issues, so it's important to manage overlapping groups effectively to ensure network efficiency and performance.

