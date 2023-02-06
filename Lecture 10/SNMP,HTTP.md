## Network Management
- When you have hundred of servers and routers, it's hard to manage them all manually-> remote protocol
	- Allows network admin to track status
- Simple Network Management Protocol
	- Request/Reply protocol(GET/SET)
	- Traps(notifications) from managed devices to Admin computer
	- Runs on top of UDP(can also run on Datagram TLS)
- Requests from network nodes in information types(Management Information Base-MIB)
	- System:General parameters
	- Interfaces:Physical addresses,packets sent on each interface
	- Address translation:ARP and translation tables
	- IP:Routing table,number of successfully routed packets,reassembly,drops
	- TCP:Connections,timeouts,reset,per connection information
	- UDP: Datagrams sent and received

`SNMP is a network management protocol used to manage and monitor network devices such as servers and routers. It uses a request/reply protocol (GET/SET) and traps (notifications) to send information about the status of network devices to a network administrator. SNMP requests information about different types of network parameters such as system, interfaces, address translation, IP, TCP, and UDP from network nodes and stores it in a management information base (MIB). The information includes physical addresses, packets sent and received, routing tables, connections, and datagrams. SNMP runs on top of UDP and can also run on Datagram TLS.`

---
#SNTP
## SNTP Schematic
![Alt text](IMAGES/Pasted%20image%2020230206111021.png)
The diagram is an illustration of a Simple Network Management Protocol (SNMP) management system. It consists of three main components:

1.  The managed devices, represented by the routers and servers, which store information about the network and are being monitored.
    
2.  The Network Management System (NMS), which is responsible for collecting and storing information about the network, and displaying it in a useful format to the network administrator.
    
3.  The SNMP agent, which is installed on each managed device and is responsible for responding to requests from the NMS and sending traps (notifications) to the NMS in the event of an error or change in the network.

The administrator uses a computer with a Network Management System (NMS) to remotely manage the network devices such as printers and switches using Simple Network Management Protocol (SNMP)

The diagram shows a flow of information between the NMS and the managed devices. The NMS sends requests to the agents, who in turn send back information about the network. The SNMP protocol uses UDP or Datagram TLS to communicate between the NMS and the agents.

![Alt text](IMAGES/Pasted%20image%2020230206111959.png)
-   Type field is an 8-bit field which can be either 1 byte or multiple bytes, depending on the requirement.
-   Length field specifies how many bytes are present in the value field.
    -   If the length field is less than 127, then the length of the value field is given directly in the length field.
    -   If the length field is greater than 127, then the length field tells us how many bytes are needed to represent the length of the value field. In this case, the first bit of the length field is ignored and the rest 7 bits are used to specify the number of bytes.
-   Value field contains the actual data in the form of nested data items.

![Alt text](IMAGES/Pasted%20image%2020230206112704.png)
OID stands for Object Identifier, which is a unique identifier for a managed object in the Simple Network Management Protocol (SNMP) management information base (MIB) hierarchy. It is used to identify a specific information element in the MIB tree and can be represented in a dotted decimal notation. An OID is used to access the value of a managed object in a network device, for example, the IP address, number of received packets, and more.

---
#HTTP
#World #Wide #Web
# World Wide Web(HTTP)
![Alt text](IMAGES/Pasted%20image%2020230206113122.png)
![Alt text](IMAGES/Pasted%20image%2020230206113142.png)
`Stateless servers are servers that do not maintain information or context about individual clients between requests. They process client requests independently and do not store client information in memory or on disk. This makes stateless servers scalable and flexible, as they can easily handle multiple clients simultaneously without the need for memory allocation for each client. Examples of stateless servers include HTTP servers, DNS servers, and DHCP servers.`
![Alt text](IMAGES/Pasted%20image%2020230206113559.png)
![Alt text](IMAGES/Pasted%20image%2020230206121032.png)
![Alt text](IMAGES/Pasted%20image%2020230206121338.png)
![Alt text](IMAGES/Pasted%20image%2020230206121501.png)
![Alt text](IMAGES/Pasted%20image%2020230206121606.png)
![Alt text](IMAGES/Pasted%20image%2020230206121657.png)
![Alt text](IMAGES/Pasted%20image%2020230206121722.png)
![Alt text](IMAGES/Pasted%20image%2020230206121752.png)
## HTTP Response Message
> Status line (protocol ---> HTTP/1.1 200 ok)
> Status code status phrase)
![Alt text](IMAGES/Pasted%20image%2020230206121906.png)
![Alt text](IMAGES/Pasted%20image%2020230206121932.png)
![Alt text](IMAGES/Pasted%20image%2020230206122012.png)
![Alt text](IMAGES/Pasted%20image%2020230206122035.png)

![Alt text](IMAGES/Pasted%20image%2020230206122127.png)
![Alt text](IMAGES/Pasted%20image%2020230206122400.png)
![Alt text](IMAGES/Pasted%20image%2020230206122510.png)
![Alt text](IMAGES/Pasted%20image%2020230206122537.png)
