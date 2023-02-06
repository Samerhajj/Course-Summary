
## Recitation 2

1.  What is the purpose of a HELLO message? How often is the HELLO message sent?

	`The Hello protocol is responsible for establishing and maintaining neighbor relationships. Hello packets are sent every few intervals`

2. Explain the meaning of the following fields: 
	1. (a) Hello Interval : The length of time which the router sends the interface
	2. (b) Router Dead Interval: The length of time before the router's neighbor declare it dead connection
	4. (c) Designated Router: `The Designated Router is selected on all broadcast and NBMA network by the Hello Protocol,
	    `Advertise link state for the network, network is lsa labelled with the ip address of the designated router`
	    ` if its initialzied to 0's, it means there is no designated router
	    `
	    `designated router distributes link state update to other routers on lan, any other updates are ignored`
			
	1. (d) Options: Multicast:`ability for forward OSPF link state advertisements about ip multicast routing path`


What is the purpose of the DB Description messages? What causes the sender to send a DB Description message?

The DB description message is sent from another node to announce what information it has in its database. The DB Description information must be reliably flooded to all other routers in the network to let them know what information can be requested from others.


>The Open Shortest Path First (OSPF) protocol builds routing tables using a link state algorithm. Explain the role of the following elements in OSPF

Dijkstra’s algorithm

`Once the whole topology of the network is built using the DB description messages, the nodes can retrieve the distance metrics they want and then use Dijkstra’s algorithm to calculate the shortest paths from themselves to all others in the network. The results of the algorithm are used to populate the routing table of the router.`

What does each LSA entry indicate?
- Flags
- Sequence number
- Id link(address)
- advertising router

What is the meaning of the DB Description: Master field? What is the meaning of the More field?

- To coordinate Synchronization , OSPF use master/slave data update technique
- The address of the router of highest ip address is the master,
- Other will be slave, and will listen to him
- Master send to slave, slave only respond,
- Master and slave use the more field to tell other that there is more information

What is the purpose of the LS Request message? What causes a sender to send it?
- After the DB Description exchange is done.routers ask each other for updates to complete their link database. They do that using LS Request messages

7. What is the purpose of the LS Update message? How does it differ from the DB Description message?
- Update is response to  LS Request ,They contain up to date link state information including the distance metrics, and link type

8. What is the purpose of the LS Acknowledge message? What information is included in the LSA entries?
	- The response to a sucessful update message ( flooding is reliable)

### Recitation 4
#aggregateRouting 
## Aggregate Routes

## ISP 1.1
Consider an ISP with the following address range: 192.4.0.0/14. It has the following customers:
1. Customer 1: 192.4.0.0 - 192.4.15.255
2. Customer 2: 192.4.16.0 - 192.4.31.255 
3. Customer 3: 192.4.32.0 - 192.4.47.255 
Perform the following tasks:
`(a) Write down the aggregate routes (IP address/mask) for each customer.
`(b) What would happen if Customer 3 bought the address range above, but the ISP accidentally advertised the aggregate route 192.4.32.0/19 for it?` 
`(c) Write down aggregate route for Customer 3 if it would buy 192.4.32.0 - 192.4.127.255 instead (hint: you may need more than one route).``

### Answer 1.1

1. Customer 1: $$192.4.0.0 - 192.4.15.255$$
Customer 1 First IP:
	$$11000000 \ 00000100 \ 00000000 \ 00000000$$
Customer 1 Range IP: $$11000000 \ 00000100 \ 00001111 \ 11111111$$
$$ Customer\ 1 :192.4.0.0/20$$
2. Customer 2: $$192.4.16.0-192.4.31.255$$
$$11000000 \ 00000100 \ 00010000 \ 00000000$$
$$11000000 \ 00000100 \ 00011111 \ 11111111$$
$$Customer\ 2\  : 192.4.16.0/20$$
3. Customer 3:$$192.4.32.0 - 192.4.47.255$$
$$11000000\ 00000100\ 00100000\ 00000000$$
$$11000000\ 00000100\ 00101111\ 11111111$$
$$Customer\ 3 : 192.4.32.0/20$$
b. If Customer 3 got 192.4.32.0/19 it would include addresses even not in its range and therefore cause traffic not intenden for it to be routed in its direction.

c. $$Customer \ 3:192.4.32.0 - 192.4.127.255$$
$$11000000\ 00000100\ 00100000\ 00000000$$
$$11000000\ 00000100\ 00111111\ 11111111$$
$$11000000\ 00000100\ 01000000\ 00000000$$
---
$$11000000\ 00000100\ 01111111\ 11111111$$


1. $$192.4.32.0/19$$
2. $$192.4.64.0/18$$
---

![Alt text](IMAGES/Pasted%20image%2020230206232633.png)

 8 bits. - 32 bits
 0 and 1's
$$2^{32-18}=2^{14}=16,384\ addresses.$$
b)
1. Customer 1
$$38.58.200.0\ 38.58.207.255$$
$$00100110\ 00111010\ 11001000\ 00000000$$
$$00100110\ 00111010\ 11001111\ 11111111$$
$$Customer\ 1:38.58.200.0/21$$
2. Customer 2:	$$38.58.208.0\ 38.58.215.255$$
$$00100110\ 00111010\ 11010000\ 00000000$$
$$00100110\ 00111010\ 11010111\ 11111111$$
$$Customer\ 2:38.58.208.0/21$$
3. Customer 3:$$38.58.216.0-38.58.223.255$$
$$00100110\ 00111010\ 11011000\ 00000000$$
$$00100110\ 00111010\ 11011111\ 11111111$$
$$Customer\ 3:38.58.216.0/21$$
---

![Alt text](IMAGES/Pasted%20image%2020230206234332.png)

$$Customer\ A:200.190.0.0 - 200.190.15.255$$
$$11001000\ 10111110\ 00000000\ 00000000$$
$$11001000\ 10111110\ 00001111\ 11111111$$
$$Customer\ A:200.190.0.0/20$$

$$Customer\ B:200.190.16.0 - 200.190.18.255$$
$$11001000\ 10111110\ 00010000\ 00000000$$
$$11001000\ 10111110\ 00010001\ 11111111$$
$$11001000\ 10111110\ 00010010\ 00000000$$
$$11001000\ 10111110\ 00010010\ 11111111$$
$$Customer\ B:200.190.16.0/23$$
$$Customer\ B:200.190.18.0/24$$


$$Customer\ C: 200.190.19.0 - 200.190.29.255$$
$$11001000\ 10111110\ 00010011\ 00000000$$
$$11001000\ 10111110\ 00010011\ 11111111$$
---
$$11001000\ 10111110\ 00010100\ 00000000$$

$$11001000\ 10111110\ 00010100\ 11111111$$

---
$$11001000\ 10111110\ 00011000\ 00000000$$

$$11001000\ 10111110\ 00011000\ 11111111$$
---
$$11001000\ 10111110\ 00011100\ 00000000$$
$$11001000\ 10111110\ 00011101\ 11111111$$

$$Customer\ C: 200.190.19.0/24,200.190.20.0/22,200.190.24.0/22,200.190.28.0/23$$

- Customer D:200.190.30.0-200.190.31.255
$$11001000\ 10111110\ 00011110\ 00000000$$
$$11001000\ 10111110\ 00011111\ 11111111$$
$$Customer\ D:200.190.30.0/23$$
- Customer E:200.190.32.0-200.190.159.255
$$11001000\ 10111110\ 00100000\ 00000000$$
$$11001000\ 10111110\ 00111111\ 11111111$$
---
$$11001000\ 10111110\ 01000000\ 00000000$$
$$11001000\ 10111110\ 01111111\ 11111111$$

$$11001000\ 10111110\ 10000000\ 00000000$$
$$11001000\ 10111110\ 10011111\ 11111111$$

$$Customer\ E:200.190.32/19,200.190.64.0/18,200.190.128.0/19$$

$$Customer\ F:200.190.160.0/19,200.190.192.0/18$$

 b)
200.190.0.0 - 200.190.255.255

$$11001000\ 10111110\ 00000000\ 00000000$$
$$11001000\ 10111110\ 11111111\ 11111111$$

$$ISP:200.190.0.0/16$$