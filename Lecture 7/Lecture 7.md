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