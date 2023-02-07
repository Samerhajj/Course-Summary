## Autonomoys Systems, CIDR

### Intra-network vs Inter-network routing

>Intra-network routing, also known  as interior routing, refers to the routing of data packets within a single network.In this type of routing, routers use routing protocols to determine the best path for data packets to travel from one point to another within the same network. The **Goal of intra-network routing** is to optimize network performance and ensure reliable delivery of data packets.

>Inter-network routing,also known as exterior routing. refers to the routing of data packets between different networks.This type of routing is used when data packets need to be sent from one network to another, such as from a local network to the internet. In inter-network routing, routers use routing protocols to determine the best path for data packets to travel between networks. **The goal of inter-network routing** is to optimize the flow of data packets between networks and ensure reliable delivery of data packets between different networks

##### Summarization
>Intra-network routing focuses on optimizing the flow of data packets within a single network . while inter-network routing focuses on optimizing the flow of data packets between different networks.
---
#AS 
### Autonomous System(AS)
>An Autonomous System (AS) is a collection of interconnected routers under the control of a single administrative entity, that uses a common routing policy to exchange data packets between networks. It is also known as a routing domain.

>An AS acts as a self-contained entity in terms of routing, meaning that the routers within the AS make routing decisions independently of routers in other ASs. This autonomy allows an AS to implement its own routing policies and configurations,seperate from other ASs.

>An AS can be a single network, such as a large enterprise network, or a group of networks connected together, such as a service provider network. The routers within an AS exchange routing information using routing protocols,such as BGP(Border Gateway Protocol), to determine the best path for data packets to travel from one network to another within an AS.

>The use of ASs allows for the creation of large-scale,hierachial network design that are more manageable and scalable.It also allows for the implementation of advanced network services, such as  load balancing and traffic engineering. Overall, the concept of an Autonomous System is a key aspect of modern networking, providing a framework for routing and network management.

---

#LoadBalancing
## What is load balancing?
>Load Balancing is a technique used in computer networking to distribute workloads evenly accross multiple servers or network resources. The goal of load balancing is to ensure that no single server or resource becomes overwhelmed with too much work, leading to poor performance or even failure.

>Load balancing can be achieved through hardware devices, such as load balancers, or through software solutions, such as virtual load balancers.Load balancing can be used in various types of networks,including web servers,application servers, and databases, to distribute workloads and improve performance

>Load balancing can be accomplished in several ways,Including:
>	Round-robin:Requests are distributed evenly to each server in turn.
>	Least connections:The server with the fewest current connections is selected
>	IP Hash:The incoming IP address is used to determine which server should recieve the request

>Load balancing can also be performed at different levels of the network stack, such as at the transport layer(TCP/UDP) or the application layer(HTTP).

>In summary: load balancing is a key technique used to improve the performance and reliability of networks by distributing workloads evenly across multiple resources.

---
#AS 
## Network Types
>A Stub network is a network that only has one connection to another network and does not act as a transit network for traffic from other networks.A stub network typically only recieves and sends traffic from its own devices and does not act as a relay for traffic from other networks.
>Examples of stub networks , include small branch offices or individual homes connected to the internet.college.

>A Transit network is a network that acts as a relay for traffic from other networks.A transit network is responsible for routing traffic from one network to another and is often used by service providers to connect multiple networks.A transit network has multiple connections to other networks and acts as a hub for traffic routing.

>Multihomed networks is a term used in computer networking to describe a network that has multiple connections to other networks. A multihomed network can connect to multiple service providers or autonomous systems(AS) for increased redundancy,load balancing. and improved network performance,
>They are often used by large organizations,data centers and ISPs to provide redundancy and improve network reliablility, By having connections to different networks. they can continue to function even if one of the connection fails!

### Summary
>A stub network is a simple,single-homed network that only recieves and sends traffic from its own devices, while a transift network is a multi-homed network that acts as a relay for traffic from other networks.

![Alt text](IMAGES/Pasted%20image%2020230207181326.png)

![Alt text](IMAGES/Pasted%20image%2020230201134859.png)

---
## Challenges of inter-AS routing
>The inter-AS routing is the routing between different Autonomous Systems (AS) in computer networking. The following are some of the challenges of inter-AS routing:

1. Scale: As networks grow in size,inter-AS routing can become increasingly complex and challenging to manage. Large networks with multiple ASs require efficient and scalable routing protocols to ensure reliable and efficient data transfer.
2. Load balancing:Load balancing between different ASs is an importmant consideration in intern-AS routing. Load balancing helps distribute traffic evenly across multiple ASs, reducing the risk of network congestion and improving overall network performance.
3. Privacy:Maintaining the privacy of internal network information is a challenge in inter-AS routing. Service providers need to ensure that sensitive information, such as internal network topology, is not disclosed to the unauthorized parties.
4. Policy:Implementing routing policies that prioritize certain types of traffic, prevent malicious activity, and respond to the changes in network conditions is importmant in intern-AS routing. Service providers must have the ability to control and configure routing policies to meet the needs of their customers and ensure a secure and reliable network.

### Summary
>Inter-AS routing presents several challenges including scalability,load balancing,privacy and policy management.To overcome these challenges, service providers must employ efficient and scalable routing protocols, implement robust security measures, and have the ability to control and configure routing policies.


---
## CIDR

![Alt text](IMAGES/Pasted%20image%2020230201135953.png)

#IP 
>Class A :16,777,214
>Class B:65,534
>Class C:254

>How can we deal with running out of ip addressess?

- Aggregate Routes
- Very similar to Subnetting
- Use addresses and masks – 
- Requires us to allocate addresses contiguously
- Technique: Classes Interdomain Routing

- If we give out 16 Class C Networks:192.4.16-192.4.31
	$$ 192.4.16: 11000000 00000100 00010000 00000000$$$$192.4.31: 11000000 00000100 0001111100000000$$
			The top 20 bits are the same
			that means
			We can write it as 
			$$192.4.16/20 ->bits $$
			– Means the top 20 bits matter
			Identical to using the subnet mask: 255.255.240.0 • 11111111.11111111.11110000.00000000
#aggregateRouting 
> Aggregate routes in CIDR is a technique used to simplify routing tables and reduce the ammount of routing information that needs to be exchanged between routers. In CIDR, multiple smaller routers can be combined into a single,larger route known as an aggregate route.

> By combining multiple routers into a single aggregate route, routers can simplify their routing tables and reduce the ammount of routing information that needs to be exchanged between them. This helps improve routing performance and reduce the risk of routing loops.

>In summary, aggregate routes in CIDR is a technique used to simplify routing tables and reduce the ammount of routing information exchanged between routers. By combining multiple routes into a single ,larger route, routers can improve routing performance and reduce the risk of routing loops.



dest
and Mask

---
output

Subnetting is the process of dividing a larger network into smaller subnetworks, called subnets. Each subnet has its own network address and can be used to create logical groupings of devices within a larger network. This allows administrators to better manage the network by dividing it into smaller, more manageable segments. Subnetting is performed by borrowing bits from the host portion of an IP address to create a new subnet mask. This new subnet mask defines the size of the subnetwork and determines the number of available hosts within each subnet. By subnetting a network, administrators can improve network security and performance by better controlling the flow of traffic within the network. Additionally, subnetting can help to conserve IP addresses by allowing administrators to reuse the same address space for different subnets. In summary, subnetting is the process of dividing a larger network into smaller subnetworks, called subnets, to improve network security and performance, and to conserve IP addresses.