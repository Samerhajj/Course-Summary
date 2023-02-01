#CIDR #BGP

## Classless interdomain Routing

- Routers can now store aggregate routing information
	- Address/Length for each organization/network
	- Requires us to change the way the routers work
- Good for aggregation networks which are all accesses via the same main router

![Alt text](IMAGES/Pasted%20image%2020230201141636.png)
#ISP
## ISP Example

- ISP sells addresses in the blocks :192.4.0.0-192.4.63.255
- Customers are:
	-  Customer 1:192.4.0.0/20
	-  Customer 2:192.4.16.0/20
	-  Customer 3:192.4.32.0/20
	-  Left avaliable to sell:192.4.48.0-192.4.63.255
![Alt text](IMAGES/Pasted%20image%2020230201141923.png)

>Now routing packets require looking at the address and the prefixes
>	Same algorithm such as subnetting

>Longest mask wins
>	Means it's more specific

>Advantage:Collapse many areas into a single routing table line.

>CIDR(Classless Inter-Domain Routing) is a method of allocating ip addresses and routing Internet Protocol(IP) packets. It replaces the original IP address allocation scheme, called classfull addressing, with a more flexible and efficient system.

>CIDR provides a way to assign and manage IP addresses to more efficiently by allowing a single IP address to represent many unique addressess. This helps conserve the limited number of avaliable IP addresses and reduce the size of routing tables.

>In CIDR, an IP address is represented by a combination of network address and a subnet mask. The subnet mask defines the portion of the IP address that represents the network address and the portion that represents the host address.

>Cidr is widely used in today's internet and is the backbone of modern IP addressing and routing.

>In summary, CIDR is a method of allocating IP addresses and routing IP packets that is more flexible and efficient than the original classful addressing scheme. it allows for a single IP address to represent many unique addresses, helping conserve IP addresses and reduce the size of routing tables.
---
#EGP
![Alt text](IMAGES/Pasted%20image%2020230201142822.png)
### EGP
- Does not support aggregation routes
- Did not allow for the topology to become general
- Forced tree-like topology
	- Single backbone
	- As's connected only as parents and children(not peers)

![Alt text](IMAGES/Pasted%20image%2020230201142954.png)


### EGP VS BGP
>Both are routing protocols used in computer networks to exchange routing information between routers.However, there are some key differences between the two protocols:
- Purpose:EGP was one of the first exterior gateway protocols and was used to exchange routing information between routers in different autonomous systems(AS), BGP, on the other hand, is the de facto standard for exchanging routing information between routers in different ASs.
- Complexity:EGP was a simple protocol and had limited capabilities. BGP , on the other hand, is a more complex protocol that provides a wide range of features for inter-AS routing, including support for multiple paths, route aggregation, and policy-based routing.
- Stability:EGP was prone to routing loops and instability, BGP on the other hand, is designed to prevent routing loops and provides more stability in inter-AS routing.
- Routing Information:EGP only exchanged basic routing information between routers, BGP, on the other hand, can exchange more detailed routing information, including attributes such as path length,origin and community.

>In summary, EGP and BGP are both routing protocols used in computer networks. EGP was one of the first exterior gateway protocols and was used to exchange routing information between routers in different ASs. BGP is the de facto standard for inter-AS routing and provides a wide range of features, including support for multiple paths, route aggregation, and policy-based routing.
---
![Alt text](IMAGES/Pasted%20image%2020230201143642.png)