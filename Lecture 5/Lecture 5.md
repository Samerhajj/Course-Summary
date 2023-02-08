# Path Vector Routing

- Extensions of distance-vector routing
	- Supports flexible routing policies
	- Faster convergence (avoid count-to-infinity
- Key idea: advertise the entire path
			- Distance vector:ْsend distance metric per dest d
		- Path vector:send the entire path metric per each dest d

![Alt text](IMAGES/Pasted%20image%2020230201162938.png)

---
## Faster Loop Detection
- Node can easily detect a loop
	- Look for its own node identifer in the path
	- E.g., node 1 sees itself in the path "3,2,1"
- Node can simply discard path with loops
	- E.g.,node 1 simply discards the advertisement
![Alt text](IMAGES/Pasted%20image%2020230201163150.png)

### Flexible Policies
- Each node can apply local policies
	- Path selection:Which path to use?
	-  Path export:Wheter to advertise the path?
- Examples:
	- Node 2 may prefer the path "2,3,1" over "2,1"
	- Node 1 may not let node 3 hear the path "1,2"
	![Alt text](IMAGES/Pasted%20image%2020230201163336.png)

---
#PathVector
### Path Vectors in BGP
>Each AS has:
>	One BGP SPEAKER that advertises:
>		Local networks
>		other reachable networks(transit AS only)
>		gives path information
>In addition to the BGP speakers,the AS has one or more border "gateways" which need not to be the speakers
>The border gateway are the routers through which packets enter and leave the AS

--- 
## Distributing BGP Data
> Long lived TCP Sessions between BGP SPEAKERS (Port 179)
> 	Exchange all active routes
> 	Exchange incremental updates ( ALIVE MESSAGE,Update)
> 	Announces new routers(add IDs to new or existing paths)
> 	Withdraw routes

## Intenal and external BGP
>Internal BGP(IBGP):Sessions between routers in a single AS
>	Ex.1c talks to 1b to coordinate
>External BGP(eBGP): Sessions between router in different AS
>	Ex. 1c talks to 3a

![Alt text](IMAGES/Pasted%20image%2020230201163946.png)

>iBGP (Internal Border Gateway Protocol) and eBGP (External Border Gateway Protocol) are both routing protocols used in computer networks to exchange routing information between routers. The main difference between the two protocols is the scope of their use:
	1.iBGP:iBGP is used within a single autonomous system (AS) to exchange routing information between routers. The main purpose of iBGP is to ensure that all routers in the AS have consistent and accurate routing information
	2.eBGP, on the otherhand. is used between different ASs to exchange routing information. The main purpose of eBGP is to allow routers in different ASs to communicate with each other and exchange routing information
	3. Routing Information:iBGP routers exchange full routing information with each other, while eBGP routers only exchange routing information for routes that belong to a different AS
	4. Path Selection:iBGP routers do not update the AS_Path attribute, while eBGP routers do update the AS_Path attrbute to reflect the ASs traversed by a route

> In summary, iBGP is used within a single autonomous system to exchange routing information between routers, while eBGP is used between different autonomous systems to exchange routing information. The main difference between the two protocols is the scope of their use and the information they exchange.
---
## BGP Example Simple

![Alt text](IMAGES/Pasted%20image%2020230201164026.png)
- Speaker for AS 2 advertises reachability to P and Q
	- Network 128.96, 192.4.153, 192.4.32, and 192.4.3, can be reached directly from AS 2.
- Speaker for backbone network then advertises
	- Networks 128.96, 192.4.153, 192.4.32, and 192.4.3 can be reached along the path 〈𝐴𝑆 1, 𝐴𝑆 2〉.
- Speaker can also cancel previously advertised paths
---
## BGP Complex example
- Advertisements include: AS Path and Next Hop
![Alt text](IMAGES/Pasted%20image%2020230201164301.png)
![Alt text](IMAGES/Pasted%20image%2020230201164340.png)
![Alt text](IMAGES/Pasted%20image%2020230201164416.png)

### BGP Path Selection
- Simplest case : Shortest AS Path
	- Example:1129 to 88 on previous slides
	- Break ties by flipping a coin
- #potato  hot potato routing:Leave via closest internal router
	- iBGP at work!
![Alt text](IMAGES/Pasted%20image%2020230201164646.png)
---
![Alt text](IMAGES/Pasted%20image%2020230201164732.png)

---
## Integrating Internal and External Routes
![Alt text](IMAGES/Pasted%20image%2020230201164818.png)

---
# BGP Packet Details
![Alt text](IMAGES/Pasted%20image%2020230201164911.png)

![Alt text](IMAGES/Pasted%20image%2020230201164926.png)

![Alt text](IMAGES/Pasted%20image%2020230201164936.png)


>UPDATE in BGP (Border Gateway Protocol) refers to a message that is sent between BGP speakers to exchange routing information.

>Withdrawn routes (dest IP): BGP speakers use the Withdrawn routes field to inform their peers about the routes that have become unavailable. This could be due to a failure in the network, a change in the network topology, or other reasons.

>NLRI (CIDR range reachable): NLRI stands for Network Layer Reachability Information and it is used by BGP speakers to advertise the available routes in the network. The CIDR range reachable is the range of IP addresses that can be reached through a specific route.

>Path attributes: Path attributes are additional information that is carried along with the routing updates in BGP. Some of the important path attributes are:
	
	-   AS_Path: The AS_Path attribute contains the list of Autonomous System (AS) numbers that the route has traversed. This attribute is used by BGP speakers to determine the best path to reach a destination.
	    
	-   Next_Hop (which router): The Next_Hop attribute contains the IP address of the next hop router that should be used to reach the destination.
	    
	-   Multi_Exit_Disc (weights for incoming): The Multi_Exit_Disc attribute is used by BGP speakers to assign weights to incoming routes. This helps the BGP speaker to determine which route is the best to use based on its preference.
	    
	-   Local_Pref (weights for internal routing): The Local_Pref attribute is used to assign weights to routes for internal routing purposes. This attribute is used by BGP speakers within an Autonomous System (AS) to determine the best path to reach a destination.
	    
	-   Atomic_Aggregate (tells whether router aggregated others): The Atomic_Aggregate attribute is used to inform other BGP speakers about the aggregation of multiple routes into a single route.

>In summary, the UPDATE message in BGP is used to exchange routing information between BGP speakers. 
>The Withdrawn routes field informs peers about unavailable routes, the NLRI field carries information about available routes, and the Path attributes field contains additional information to help the BGP speaker determine the best path to reach a destination.
---
# BGP Routing Changes
![Alt text](IMAGES/Pasted%20image%2020230201164955.png)

![Alt text](IMAGES/Pasted%20image%2020230201165040.png)

---
#potato 
#### Hot Potato Routing
>Hot Potato Routing is a method of forwarding network packets in which the router closest to the destination address is responsible for forwarding the packet. In this method, the packet is sent to the closest router, which in turn passes it to the next closest router, and so on, until it reaches its final destination.

>The main advantage of Hot Potato Routing is that it minimizes the amount of time that a packet spends in transit, reducing the overall latency of the network. It also helps to reduce the amount of congestion in the network by distributing the load evenly across the routers.

>This method of routing is often used in large networks where there are many different routers involved and it is important to ensure that packets are delivered as quickly and efficiently as possible. In these networks, Hot Potato Routing helps to ensure that packets are delivered to their final destinations in the shortest possible time, thereby improving the overall performance of the network.

# BGP SPEAKER
> A BGP (Border Gateway Protocol) speaker is a network device that implements the BGP routing protocol. It is responsible for exchanging routing information with other BGP speakers and maintaining the routing table, which contains information about the network topology and the best paths to reach various destinations.

>A BGP speaker is typically a router, but it can also be a switch or a firewall that has BGP capabilities. In an autonomous system (AS), a BGP speaker is responsible for exchanging routing information with other BGP speakers in the same AS or in other ASs.

>BGP speakers use a complex set of algorithms to determine the best path to reach a given destination, taking into account various metrics such as hop count, link speed, and available bandwidth. They use this information to update their routing tables and to send routing updates to other BGP speakers in the network.

>In summary, a BGP speaker is a network device that implements the BGP routing protocol and is responsible for exchanging routing information, maintaining the routing table, and determining the best paths to reach destinations in the network.

---
# Concept Map


![[BGP CONCEPT.pdf]]