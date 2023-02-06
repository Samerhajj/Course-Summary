
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

