## Intra-network Routing: RIP and OSPF

	Routing: in computer networking it refers to the process of forwarding data packets from one network to another via intermediate routers.The router selects the best path for data to travel based on various criteria such as network traffic,cost and distance.Routing enables communication between different networks and allows the internet to function.

![Alt text](IMAGES/Pasted%20image%2020230131112022.png)

---

![Alt text](IMAGES/Pasted%20image%2020230131112544.png)

![Alt text](IMAGES/Pasted%20image%2020230131114600.png)

---

# Intradomain Routing

### RIP - Routing Information Protocol
- Uses distance vector algorithm
- Limited to small nets;<15 hops

## OSPF - Open Shortest Path First
- Augumented version of link-state
- Augumentation,load balancing, and defined areas
---
## Spanning Trees (Abstractly)
![Alt text](IMAGES/Pasted%20image%2020230131115707.png)
![Alt text](IMAGES/Pasted%20image%2020230131115826.png)

---
## Distance Vector Algorithm (RIP) #RIP

### Like Spanning Tree Algorithm
- Except that information about distance to all nodes is forwarded (not just information about root)
- Sometimes called Bellman-Ford algorithm
- Each node constructs a Distance vector
	- Contains distances (costs) to reach all other node
	- Initialliy:
		- Distance to neighbors ( a simplification for now)=1
		-  $$ Distance\ to\ others ==\infty $$
	- Routing table reflects node's beliefes

![Alt text](IMAGES/Pasted%20image%2020230131120518.png)

## Iteration Steps

![Alt text](IMAGES/Pasted%20image%2020230131120636.png)

### Example Iteration Steps
![Alt text](IMAGES/Pasted%20image%2020230131120717.png)

### Details
> No single host has all routing information.
> When to send update vectors?
> 	When your routing table changes ( triggered)
> 	Periodically ("I'm alive")

>Detecting link/node failure
>	(1) Periodically exchange (I'm alive) ْmessages;
>	(2) Timeout mechanism

> In static Network, if all weights =1 ,Once A discovers a path to B ( cost < infinity),
> no subsequent round will discover a better path to B
> All weights  =1 called "HOP COUNT" ( Default RIP Action)
---
## Dynamic Networks
![Alt text](IMAGES/Pasted%20image%2020230131121224.png)
# Link Failure Examples
##### Example 1
![Alt text](IMAGES/Pasted%20image%2020230131121325.png)
![Alt text](IMAGES/Pasted%20image%2020230131121406.png)

![Alt text](IMAGES/Pasted%20image%2020230131121509.png)![Alt text](IMAGES/Pasted%20image%2020230131121546.png)
### Example 2
![Alt text](IMAGES/Pasted%20image%2020230131121630.png)
![Alt text](IMAGES/Pasted%20image%2020230131121652.png)
![Alt text](IMAGES/Pasted%20image%2020230131121738.png)
![Alt text](IMAGES/Pasted%20image%2020230131121804.png)

---
## Network Partition
> Loop between A and F is broken only by C's update
> 	C has real information about another path to G
> What if C's update never comes? What if C's information is false?
> 	The network is partitioned OR G is completely offline
> Other nodes will continue counting until infinity ( or the distance field reach its max)
> 
In summary, the count-to-infinity problem is a problem in routing algorithms where two devices have different information about the network and both believe that they have the shortest path to a particular destination, resulting in the distance to the destination increasing indefinitely.
## Three Rip Solutions

###### Option 1 : Infinity is small
- Don't let the distance field go above a predefined maximum
	- Say 15,20 etc(15 is the actual value)
	- The max must be greater than the diameter of the network

###### Option 2 :Include "Next Hop" in the distance vector
- ignores routers which pass via you
-Example: F recieves an update from A about a path to G
	in the example Before, F didn't know that's A path went via F Path
	If A Had sent instead

|Destination  | C  | Next Hop |
| :------------ |:---------------:| -----:|
| G    | 2 | F |

     , F Would ignore the fake path
	Called SPLIT HORIZON

###### Option 3: Route poisoning and Holddowns
- Instead of just announcing an infinitie distance for a destination,a router sends out a poison message for the destination
	- E.g. the router announces distance 16 (≡ ∞) for the destination
	- For a fixed period of time (say 3 minutes) any new offers for the destination via the sender will be rejected
		• E.g. Wait until everyone has heard the poison and then accept new offers
	-  Gives a chance for the route to be deleted by everyone
    - this helps to quickly propagate the information about an unavaliable router
	

#### Split Horizon
Split Horizon is a technique used in Routing Information Protocol (RIP) to prevent the re-advertising of information back in the direction from which it was received.

The basic idea behind Split Horizon is to prevent routing loops by not sending information back in the direction from which it was received. This is because information that was received from a particular direction may have become outdated, so it's better to not re-propagate it.

Split Horizon is implemented in RIP by not including information about a route in updates sent out on the same interface the route was received on. This way, if a route becomes unavailable, the information about the route will not be re-sent to the original source of the information, preventing the route from being looped back to the original source.

In essence, Split Horizon helps to maintain the accuracy and consistency of the routing information in the RIP network, making it more stable and reliable.

### Holddown Timers: 
In this approach, the router waits for a specified period of time after receiving a distance update before accepting any further updates. This helps to prevent the rapid propagation of incorrect information.

### Open Shortest Path First (OSPF)
![Alt text](IMAGES/Pasted%20image%2020230131124520.png)

### OSPF STEPS

`Reliable flooding is a feature of the Open Shortest Path First (OSPF) routing protocol that ensures that all devices on a network receive updated routing information in a timely and consistent manner. In OSPF, each device maintains a database of the network topology and periodically exchanges information with its neighbors to ensure that its routing information is up-to-date. With reliable flooding, the OSPF protocol guarantees that the information is transmitted reliably and that all devices receive the same information. To achieve reliable flooding, OSPF uses a series of mechanisms such as acknowledgements, retransmission, and sequence numbers. When a device receives updated information, it acknowledges the receipt of the information, and the transmitting device retransmits the information until it receives an acknowledgement. This ensures that all devices on the network receive the same information and that the information is transmitted reliably. In summary, reliable flooding in OSPF ensures that all devices on a network receive updated routing information in a timely and consistent manner. This helps to ensure that the network is operating efficiently and that all devices have a consistent view of the network topology.`

`This information is exchanged between devices using OSPF protocol data units (PDUs), also known as link state advertisements (LSAs). LSAs contain information about the network and are originated by each device. The periodic exchange of LSAs ensures that all devices on the network have a consistent view of the network topology, and it helps to ensure that all devices can find the shortest path to any other device on the network. This makes OSPF a scalable and robust routing protocol, capable of adapting to changes in the network topology in real-time. To summarise, the information that is exchanged between devices in OSPF is the database of the network topology, which includes information about the devices, links, and routes on the network. This information is transmitted using LSAs and helps to ensure that all devices on the network have a consistent view of the network topology.
`
![Alt text](IMAGES/Pasted%20image%2020230131124656.png)

### OSPF FEATURES
![Alt text](IMAGES/Pasted%20image%2020230131124717.png)

### Dijkstra’s Algorithm #Dijkstra 
> Nodes has two lists - Confirmed and Tentative - pairs of (Destiniation,Cost,Next-Hop)
##### Algorithm
1. Initializes Confirmed with an entry for self with 0 cost.
2. For the node just added in Confirmed in the prevous Step,(Next),examine its Link State Packet (LPS) #Step2 
3. For each Neigh(Neighbor) of Next,calculate  the distance to Neigh via $$ Nextcost=(self-> Next) + (Next-> Neigh)$$
	a) if Neigh isn't on Confirmed or Tentative, add (Neigh ,cost,NH) to Tentative,where NH is the way to reach Next in confirmed
	b) if Neigh is on Tentative and cost is better than old cost,replace it with (Neigh,cost,NH), where NH  is the way to reach Next in confirmed
4. If Tentative is empty,Stop.
5. Choose the node on Tentative with the lowest cost .move it to confimred, and go to #Step2

## Some examples on Dijkastra #Dijkstra

![Alt text](IMAGES/Pasted%20image%2020230131125829.png)
![Alt text](IMAGES/Pasted%20image%2020230131125846.png)