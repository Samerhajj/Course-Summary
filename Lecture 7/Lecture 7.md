
## Weighted Fair Queuing,Congestion Avoidance
---
# Weighted Fair Queuing
- Give a weight to each flow to give it more of the bandwidth
- Flow A gets 1,Flow B gets 2,Flow C gets 3
	- $$Flow\ A \ has \ {1\over6 } \ of \ the \ flow$$
	- $$Flow\ B \ has \ {2\over6 } \ of \ the \ flow$$
	- $$Flow\ C \ has \ {3\over6 } \ of \ the \ flow$$

	- Calculate by dividing the size p_i by the weight of the flow
		- $$Packet\ A1\ =\ 300B\ =\ 300\ Ticks$$
		- $$Packet\ B1\ =\ 300B\ =\ {300\over2} =\ 150\ Ticks$$
		- $$Packet\ C1\ =\ 300B\ =\ {300\over3} =\ 100\ Ticks$$
---
## Congestion Avoidance
- Congestion occurs when there are too many packets and not enough bandwidthin the pipe to fit them
-  What if we could prevent congestion in the first place?
	- Tell the senders to slow down so we never need to drop packets
	- How could we do this?
		- Explicit notification
		- Implicit notification
---
## Explicit Notification :DECbit
- Designed  for Digital Network Architecture
	- Connectionless with a connection-orineted transport protocol
		- Just like TCP/IP
- Add a bit to the header - the congestion bit
	- Router sets it when it sees its queue length are too long
		- If the average queue length is greater than 1 over the last busy/idle interval
	- The receiver copies the bit to the acknowledge field
The sender measures the percent of arriving packets with the congestion bit set over the last send window
   - If > 50% have it set,reduce congestion window to 87.5%
   - If <50% have it set,add 1 packet to the congestion window. AIMD!


DECbit is a method in network routing that helps to prevent loops in the network. It uses an explicit notification mechanism to signal changes in the routing information between routers. The DECbit is set when a change occurs in the routing information, and routers receiving the update check the DECbit to determine if the update should be accepted or discarded. This helps to prevent looping of routing information and ensures the stability of the network.

---
## Implicit Notification: RED
- Observation:When TCP sees that a packet has dropped, it lowers the congestion window to half
	- We can use that to "advise" TCP senders to reduce their sending speed before things get too bad

The Details:
- The router tracks the average queue lenght to decide
	- $$AvgLen = (1-Weight}x AvgLen +Weight+SampleLen$$
	- Weight must be chosen to balance new vs old state
		- It takes atleast 1 RTT for the drop to have effect
		- Sample value: Weight =0.002
![Alt text](IMAGES/Pasted%20image%2020230205115613.png)
![Alt text](IMAGES/Pasted%20image%2020230205120536.png)

---
# Red Algorithm
Choose a MinThreshold,MaxThreshold
When a packet arrives:
1. Recalculate AvgLen
2. If AvgLen ≤ MinThreshold
	- Queue it
3. If 𝑀𝑖𝑛𝑇ℎ𝑟𝑒𝑠ℎ𝑜𝑙𝑑 < 𝐴𝑣𝑔𝐿𝑒𝑛 < 𝑀𝑎𝑥𝑇ℎ𝑟𝑒𝑠ℎ𝑜𝑙d
	- Calculate the dropped probability      ->p
	- Drop the packet with probability p
4. If 𝑀𝑎𝑥𝑇ℎ𝑟𝑒𝑠ℎ𝑜𝑙𝑑 ≤ 𝐴𝑣𝑔𝐿𝑒𝑛
	- Drop the packet

Note: Since 𝐴𝑣𝑔𝐿𝑒𝑛 changes slowly over time, the queues may be longer than 𝑀𝑎𝑥𝑇ℎ𝑟𝑒𝑠ℎ𝑜𝑙𝑑 at any given time. – If there is really no room for the packet, (tail) drop ![Alt text](IMAGES/Pasted%20image%2020230205120803.png)

### Choosing Weight
![Alt text](IMAGES/Pasted%20image%2020230205120844.png)

## Red Drop Probability
The dropping probability changes over time and is affected by how long it's been since the last drop
	- Prevents clustering of drops in burstly sending

Define MaxP(maximum drop probability)
- $$TempP = MaxP\ x {(Avglen-MinThreshoold)\over MaxThreshold-MinThreshold}$$
- $$P= {TempP\over 1-(count\ x\ TempP)}$$
![Alt text](IMAGES/Pasted%20image%2020230205121134.png)

## RED Dropping Example 1
>MinThreshold=10,MaxThreshold=20,MaxP=0.02,Count=0
1. Assume AvgLen=15
2. $$TempP=0.02\ × {15-10\over20-10}=0.01$$
	$$P={0.01\over1-0×0.01}=0.01({99\over100}packets\ make\ it)$$
3. If count =50 (no drops in 50 packets)
	$$TempP=0.02×{15-10\over20-10}=0.01$$
	$$P={0.01\over1-50×0.01}=0.02$$
4. If count = 99(no drops in 99 packets)
$$TempP=0.01$$
$$P={0.01\over1-99×0.01}=1(the\ next\ packet\ is\ dropped$$
![Alt text](IMAGES/Pasted%20image%2020230205121637.png)

---
## Another Example
![Alt text](IMAGES/Pasted%20image%2020230205121704.png)
![Alt text](IMAGES/Pasted%20image%2020230205121711.png)

---
## Comparing RED to Tail Drop

![Alt text](IMAGES/Pasted%20image%2020230205121746.png)

Implicit Notification RED (Random Early Detection) is a congestion control technique used in computer networks to prevent congestion. It works by monitoring the average queue size at a network node and selectively dropping packets when the queue reaches a certain threshold. The goal of this technique is to encourage sources to reduce their sending rate before the network becomes congested, which reduces the risk of congestion collapse. The selective dropping of packets is achieved through a random process, hence the name Random Early Detection.