## MPLS and Congestion Control

>Label Switching is a method of forwarding network data packets based on short fixed-length labels, rather than longer network addresses or headers. This results in faster and more efficient routing, since the network devices only have to examine the label rather than the entire packet header. Label Switching is often used in Multi-Protocol Label Switching (MPLS) networks, where it enables traffic engineering, quality of service (QoS), and other advanced networking features.

![Alt text](IMAGES/Pasted%20image%2020230204143610.png)

---
![Alt text](IMAGES/Pasted%20image%2020230204143806.png)

![Alt text](IMAGES/Pasted%20image%2020230204144001.png)

--- 
>A forwarding equivalence class is a group of messages that are all given the same label by a Label Switched Router (LSR). All messages with the same label (those in the FEC) are routed the same way, regardless of their destination of origin.

#### How can FEC be used to implement Traffic Engineering in an MPLS network?
>  When you build routing tables based on labels (those messages in an FEC), you can have Label Edge Routers (LER) put labels on packets based on their origins or destinations and afterwards the labels are the sole basis for the routing. That means that if you want to force all traffic from a particular source to go on a fixed path, you can do so by building routing tables accordingly and attaching the correct label at the LER. The packets will then be routed based on the FEC alone, letting you define paths for traffic (i.e. traffic engineering).


## LSR/LER

LSR (Label Switching Router) and LER (Label Edge Router) are terms used in MPLS (Multiprotocol Label Switching) networking.

- In an MPLS network, an LSR is a router that performs the actual label switching of MPLS packets. LSRs examine the label header of a packet and use this information to forward the packet to the next hop in the network.
- An LER, on the other hand, is a router that is located at the edge of an MPLS network. The LER is responsible for assigning MPLS labels to packets before they enter the MPLS network, and removing the labels from packets when they exit the network.
- Together, LSRs and LERs form the backbone of the MPLS network, enabling fast and efficient forwarding of MPLS packets through the network. By using MPLS labels to direct packets, MPLS networks can support sophisticated traffic engineering techniques and provide a high degree of network reliability and scalability.

## MPLS
- Transparent to you and me - ISPs and backbone providers build and maintain
- Useful for traffic engineering (TE) when combined with Quality of Service (QoS) protocols
- Allow tunneling link layer protocols (MP of MPLS)
![Alt text](IMAGES/Pasted%20image%2020230204145130.png)
![Alt text](IMAGES/Pasted%20image%2020230204145201.png)

---
![Alt text](IMAGES/Pasted%20image%2020230204145233.png)
>Traffic Engineering (TE) in MPLS is the process of optimizing the routing of network traffic to improve network performance, capacity utilization, and resource utilization. It is achieved by controlling the path that network traffic takes through the MPLS network, based on factors such as network topology, traffic patterns, and resource utilization. MPLS TE enables network administrators to direct specific traffic flows along specific paths through the network, which can improve network performance, reduce congestion, and increase overall network efficiency. MPLS TE is also used to implement Quality of Service (QoS) policies and to ensure that network resources are utilized optimally.

![Alt text](IMAGES/Pasted%20image%2020230204145340.png)
>Tunneling in MPLS is the process of encapsulating data packets from one network protocol within the packets of another protocol, typically for the purpose of transmitting the encapsulated data over a public network. In MPLS, tunneling is used to create virtual links between remote sites, which allows for the creation of a private network over a public network. The MPLS network acts as a "tunnel" for the encapsulated data packets, which are labeled and switched through the network based on their MPLS labels, rather than their original network headers. This enables MPLS to provide secure, efficient, and scalable connectivity between remote sites, while also allowing for advanced features such as traffic engineering and Quality of Service (QoS).
![Alt text](IMAGES/Pasted%20image%2020230204145417.png)
>A Virtual Private Network (VPN) built over an MPLS network is a private network that uses the public infrastructure of an MPLS network to connect remote sites or users. The VPN operates on top of the MPLS network, using MPLS labels to encapsulate and transmit the VPN data packets securely over the public network. The MPLS network provides a high-speed, secure, and scalable connection between remote sites, which enables the VPN to offer enterprise-level security, reliability, and performance to its users.

>In an MPLS VPN, each site or user is assigned a unique MPLS label, which is used to identify the VPN data packets as they traverse the MPLS network. The MPLS network switches the VPN data packets based on their MPLS labels, rather than their original network headers, which provides a high degree of security and privacy for the VPN data. MPLS VPNs are commonly used by large enterprises, service providers, and government organizations to connect remote sites, users, and applications securely and efficiently.

---
# Resource Allocation
- When we have a real network we must deal with contention and congestion
	- too many users. not enough resoiurces

- Congestion can come from:
	- too many users trying to make small connections
	- a few users making huge connections
	- Fast links that must pass over a slower link

> 	What is the goal?
> 			-Fairness
> 			- Utilization

>Fairness and utilization are two important factors in resource allocation, which is the process of distributing limited resources, such as bandwidth, CPU time, or memory, among multiple users or processes in a computer system.

Fairness refers to the distribution of resources among the users in a way that is equal, or at least proportional, to the amount of resources requested by each user. In a fair resource allocation system, each user should receive a fair share of the resources, without any one user receiving more resources than others. This ensures that each user has an equal opportunity to use the resources and achieve their goals.

Utilization refers to the percentage of the total available resources that are being used at any given time. High utilization is a good indicator of an efficient use of resources, but can also lead to resource depletion, or even starvation, if the demand for resources exceeds the supply. In resource allocation, the goal is to balance fairness and utilization, so that the resources are distributed fairly and used efficiently, without leading to resource depletion or starvation.

---
### What are we managing?
- Connection flaws
	- Data sent between sender and receiver(might miss OPEN)
	- Router sees data as moving between addresses ( ignore ports)

- Routers maintain soft state about connections
	- Detected automatically
	- Lives and dies as the connection does
	- Helps the router make better routing decisions

- Flows can be explicit or implicit
	- Difference is whether the end points tell the router before they start
	- Datagrams versus Virtual Circuits

>What is the network offering?
>	Best Effort :
>	• Basic model 
>	• Try, but no guarantee 
>	• All packets are created (more or less) equal 
>	Quality of Service (QoS):
>	 • More advanced 
>	 • Senders and receivers request the routers to guarantee a minimum amount of resources
>	  • Some protocols: RSVP, ATM

## How we managing?
- Router Centric vs Host Centric
	-  Router Centric : the router tells the hosts how fast they can send
	- Host Centric : the hosts decide how fast to send based on their experiences
- Reservation Based vs. Feedback Based
	- Reservation: send request before 
		 - Requires Router Centric 
	 -   Feedback: change based on what happens 
		  • Explicit – Router more involved 
		  • Implicit – Host more involved
- Window Based vs. Rate Based

> What is common?

| With Best Effort  	|   With QoS	|
|---	|---	|
|   • Feedback - since we can’t reserve, and therefore…	|  Reservation – normally, and therefore… 	|
|   Host centric, and often…	|   Router centric, and therefore often…	|
|   • Window based	|   Rate based	|

---
## Congestion Control vs Avoidance
![Alt text](IMAGES/Pasted%20image%2020230204150727.png)

Congestion control and congestion avoidance are two techniques used to manage network congestion.

>Congestion control is a set of algorithms and procedures used to prevent or mitigate network congestion. The goal of congestion control is to regulate the flow of data so that the network is not overwhelmed by too much traffic. This is achieved by adjusting the sending rate of data, based on feedback from the network. When the network is congested, the sending rate is reduced to prevent further congestion. When the network is not congested, the sending rate is increased to utilize available bandwidth.

>Congestion avoidance, on the other hand, is a technique used to prevent network congestion before it occurs. The goal of congestion avoidance is to prevent the network from becoming congested by proactively managing the flow of data. This is achieved by monitoring the network for signs of congestion and taking action to reduce the flow of data before congestion occurs.

>In summary, congestion control is reactive, meaning it responds to network congestion after it occurs. Congestion avoidance, on the other hand, is proactive, meaning it prevents network congestion from occurring in the first place. Both techniques are important for maintaining a stable and efficient network.

## Queuing Techniques
- First In First Out(FIFO)
- Priority Queue(PQ)
- Fair Queuing(FQ)
- Weighted Fair Queuing(WFQ)
---
### FIFO
	- Rule: Packets are sent out the router as they arrive

![Alt text](IMAGES/Pasted%20image%2020230204151934.png)
- What if the queue is full?
	- Tail Drop
	- Random Drop

> Tail drop and random drop are two queue management algorithms used in First-In-First-Out (FIFO) queuing systems.

- Tail drop, in tail drop, When a queue reaches its maximum size.new incoming packets are simply dropped,while existing packets continued to be processed.This results in a drop in the average queue size,and in the average utilization of the network
- Random drop: In random drop, when a queue reaches its maximum size, packets are randomly dropped from the queue, rather than dropping only new incoming packets. This helps to spread the loss of packets evenly across different flows, reducing the impact of congestion on any single flow.

Both tail drop and random drop are used to control network congestion, but random drop is considered a more sophisticated approach as it helps to avoid global synchronization of flows, leading to a more stable and efficient network.

---
## Priority Queuing
![Alt text](IMAGES/Pasted%20image%2020230204152353.png)
Priority queuing is a queue management algorithm used in computer networks to provide differentiated service to different types of traffic.

In priority queuing, traffic is divided into different priority levels, with each level being assigned a queue. Packets are processed based on their priority level, with higher priority packets being processed first. This helps to ensure that critical traffic, such as real-time voice and video, receives the necessary bandwidth to function effectively, while lower priority traffic may experience delay or even be dropped during periods of congestion.

Priority queuing helps to provide a more predictable and consistent network performance for time-sensitive applications, and can also help to improve the overall efficiency of the network by reducing the impact of congestion on high priority traffic.

---
## Some examples for queuing types
![Alt text](IMAGES/Pasted%20image%2020230204152446.png)
![Alt text](IMAGES/Pasted%20image%2020230204152457.png)
![Alt text](IMAGES/Pasted%20image%2020230204152507.png)
![Alt text](IMAGES/Pasted%20image%2020230204152522.png)

---
# Fair Queuing
- FIFO can be easily overrun by an out-of-control sender
	- the router can intervene to make things fairer
- Fair Queuing:
	- Gives each flow a queue
	- Manages each flow seperately and service them Round Robin
	- If one's flow queue is full,we need to drop(Somehow)
	- Each queue gets to send one packet at a time,but we don't interrupt.
	- But what if someone sends 1000B packets and another sends 500B packet?

- For each packet:
	- Imagine there are no other flows on the router
		- Determine when it would have finished being sent based on when it arrived - save it with the packet in the queue
		- Think that a 500B packet takes 500 `ticks` to send
- Packet i arrives at time Ai,it has size Pi,and begins being sent at Si
	- Then it finishes being sent at  $$ F_i = S_i+P_i$$
- What is `S_i`?
	- Case 1: there is another Packet F_(i-1) from the flow being sent on the line  - then  $$ S_i = F_{i-1}$$
	- Case 2: The line is free - then $$S_i=A_i$$
- Result: $$ F_i=max(F_{i-1},A_i)+P_i$$
• But there are other flows on the router too
– The “tick” should be when each flow had a chance to send 1 byte
– So slow down the clock calculations for 𝐴𝑖 based on the number of active queues
– If there are 3 active queues, 𝐴 increments in 0.333 instead of 1
– This means that the 𝐴 doesn’t match the real “wall clock” time 

---

### Skewing
Skewing refers to an imbalance in the distribution of network traffic among different network resources, such as queues, routers, or links.

Skewing can occur due to a variety of reasons, including differences in the processing capabilities of different resources, imbalanced workload distribution, or network congestion. When skewing occurs, it can lead to a degradation in network performance, as some network resources become overloaded while others remain underutilized.

To address skewing, network administrators can use a variety of techniques, such as load balancing, traffic shaping, or resource allocation, to ensure that network traffic is distributed evenly among all available resources. This helps to improve the overall efficiency of the network and prevent performance degradation due to skewing.
