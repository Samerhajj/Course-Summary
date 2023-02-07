![Alt text](IMAGES/Pasted%20image%2020230205150743.png)
## Application vs. Network
| Application Needs   |      Network Characteristics      |
|----------|:-------------:|
| Reliable, Ordered, SingleCopy Message Delivery |  Drops, Duplicates and Reorders Messages |
| Arbitrarily large messages |    Finite message size (MTU)   |
|Timely receipt of messages | Arbitrary delay |
|Supports multiple applications per host | Host-level addressing and delivery mechanisms (no ability to discern conversations) |
|Flow control by Receiver | No end-to-end flow control mechanisms |

---
#UDP 
# User Datagram Protocol (UDP)
![Alt text](IMAGES/Pasted%20image%2020230205151244.png)
![Alt text](IMAGES/Pasted%20image%2020230205151332.png)
>A multiplexer (also known as MUX) is a device that selects one of several input signals and forwards the selected input to a single output line. It can be thought of as a switch that directs the flow of data from multiple inputs to a single output. On the other hand, a demultiplexer (also known as a DMUX) takes a single input signal and forwards it to one of several outputs. It acts as the reverse of a multiplexer, directing the flow of data from a single input to multiple outputs. Both multiplexers and demultiplexers are essential components in digital electronics and computer systems for transmitting and receiving data.

### Using Ports
- Client contacts Server at a well-known port
	- SMTP: port 25
	- DNS: port 53
	- POP3: port 110
	- HTTP: port 80
	- Unix talk: port 517
	- In unix, ports are listed in etc/services
	- In Windows,c:\Windows\System32\drivers\etc\services
- Client and Server agree on a different port for subsequent communication

- Ports are an abstraction
	- Implemented differently on different OS's
	- Typically a message queue



>UDP stands for User Datagram Protocol, and it is one of the core protocols of the Internet Protocol (IP) suite. It is a connectionless and unreliable protocol that is used for transmitting data between applications on different computers. Unlike the Transmission Control Protocol (TCP), which provides reliable, ordered, and error-checked delivery of data, UDP is designed to be fast and efficient, with minimal overhead. This makes it ideal for applications that require real-time communication, such as online gaming, video conferencing, or streaming media. In UDP, data is sent in the form of datagrams, which are self-contained units of data that contain both the payload data and the source and destination addresses. These datagrams are sent to the recipient without any guarantee of delivery, and it is up to the application layer to handle any errors or retransmissions. Despite its unreliability, UDP is widely used because it is simple and efficient, and it provides a low-level mechanism for transmitting data between applications that don't require the overhead and complexity of TCP.
---
#TCP
## Transmission Control Protocol(TCP)
>TCP (Transmission Control Protocol) is a reliable, connection-oriented transport layer protocol used for transmitting data over the Internet. It provides flow control, error checking, and data reordering to ensure that data is transmitted accurately and completely. TCP operates at the transport layer of the Internet Protocol (IP) stack and is responsible for breaking up application data into IP packets, transmitting those packets to the recipient, and reassembling the data in the correct order at the receiving end. This makes TCP a reliable means of transmitting data across the Internet and it is widely used by many different types of applications, such as web browsers, email clients, and file transfer tools.
>
- Most widely used protocol for reliable byte systems
	- Reliable, in-order delivery of a stream of bytes
	- Full duplex:pair of streams,one in each direction
	- Flow and congestion contol mechanism
	- Like UDP,supports ports
- Built on top of IP (hence TCP/IP)
![Alt text](IMAGES/Pasted%20image%2020230205151802.png)

![Alt text](IMAGES/Pasted%20image%2020230205152106.png)

The Transmission Control Protocol (TCP) packet format includes several fields that are used for reliable data transmission. Here is a brief overview of the most important fields in a TCP packet:
-  Source Port: a 16-bit field that specifies the port number of the sender.
-  Destination Port: a 16-bit field that specifies the port number of the recipient. 
-  Sequence Number: a 32-bit field that indicates the order of the data being sent.
- Acknowledgment Number: a 32-bit field that indicates which data has been received. 
 - Header Length: a 4-bit field that specifies the length of the TCP header in 32-bit words. 
  - Flags: a set of 6 bits that specify various control information for the transmission of data. 
  - Window Size: a 16-bit field that specifies the amount of data that the recipient is able to receive.
  - Checksum: a 16-bit field that is used to detect errors in the data transmission. 
  - Urgent Pointer: a 16-bit field that is used to indicate the end of urgent data. 
  - Options: a variable-length field that includes optional information for the transmission of data. 
  
  The flags in a TCP packet include several bits that specify various control information for the transmission of data. Some of the most important flags include:
   - URG: The Urgent Pointer field is valid and indicates the end of urgent data.
   - ACK: Acknowledgment of data receipt is required. 
   - PSH: The receiver should pass the data to the application as soon as possible.
   - RST: The connection should be reset. 
   - SYN: Synchronize sequence numbers to initiate a connection.
   - FIN: The sender has no more data to transmit and wants to close the connection. 
   
   These flags are used to control the flow of data and to ensure reliable and error-free transmission of data over a TCP connection.
   
## HandShake
![Alt text](IMAGES/Pasted%20image%2020230205152136.png)

---
## TCP Transitions
![Alt text](IMAGES/Pasted%20image%2020230205152206.png)
![Alt text](IMAGES/Pasted%20image%2020230205152215.png)
![Alt text](IMAGES/Pasted%20image%2020230205152305.png)

---
![Alt text](IMAGES/Pasted%20image%2020230205152335.png)

---
![Alt text](IMAGES/Pasted%20image%2020230207171930.png)
![Alt text](IMAGES/Pasted%20image%2020230207172034.png)
![Alt text](IMAGES/Pasted%20image%2020230207172123.png)
![Alt text](IMAGES/Pasted%20image%2020230207172234.png)
![Alt text](IMAGES/Pasted%20image%2020230207172330.png)

---
# We found an error
- What should the sender and the receiver do?

- Acknowledgements (ACK)
	- Small contrl frame/packet(little data)
	- When sender gets an ACK, recipient has successfully gotten a frame

- Timeouts
	- If sender doesn't get an ACK after "reasonable" time it retransmits the original

- General strategy called Automatic Repeat Request (ARQ)

In TCP, an acknowledgement is a message sent from the receiving end of a communication back to the sender to confirm receipt of a previous message. The timeout is the amount of time the sender will wait for an acknowledgement before resending the previous message or assuming the connection is lost. These two features are crucial for ensuring reliable transmission of data over a network using TCP.

## Stop-and-Wait
- Simplest scheme
	- After transmitting one frame,sender waits for an ACK
	- If the ACK doesn't arrive,sender retransmits
![Alt text](IMAGES/Pasted%20image%2020230205152735.png)
![Alt text](IMAGES/Pasted%20image%2020230205152748.png)
![Alt text](IMAGES/Pasted%20image%2020230205152818.png)![Alt text](IMAGES/Pasted%20image%2020230205152844.png)
![Alt text](IMAGES/Pasted%20image%2020230205152906.png)
![Alt text](IMAGES/Pasted%20image%2020230205152918.png)
![Alt text](IMAGES/Pasted%20image%2020230205152930.png)

---
# Sliding Window Algorithm
	- Sender assigns a sequence number to each frame:SeqNum
	- For now,Assume SeqNum can grow infinitely
- Send Window size(SWS)
	- Upper bound on # of unacknowledgements frames sender can transmit
- Last ACK Received(LAR)
	- Sequence number of last ACK
- Last Frame Sent(LFS)

![Alt text](IMAGES/Pasted%20image%2020230205153208.png)
![Alt text](IMAGES/Pasted%20image%2020230205153221.png)
#### Receiver Algorithm
- When packet numbered SeqNum arrives
	- If(SeqNum≤LFR) Or (SeqNum>LAF)discard
	- Else accept the packet
- Define :SeqNumToAck
	- Largest unACK'ed sequence number such that all earlier frames have been accepted
- Receiver sends ACK(SeqNumToAck)
- $$LFR=SeqNumToAck$$
- $$LAF=LFR+RWS$$
## Example Sliding Window Protocol
![Alt text](IMAGES/Pasted%20image%2020230205153616.png)
![Alt text](IMAGES/Pasted%20image%2020230205153631.png)
![Alt text](IMAGES/Pasted%20image%2020230205153644.png)
![Alt text](IMAGES/Pasted%20image%2020230205153659.png)
![Alt text](IMAGES/Pasted%20image%2020230205153711.png)
![Alt text](IMAGES/Pasted%20image%2020230205153733.png)
![Alt text](IMAGES/Pasted%20image%2020230205153749.png)
![Alt text](IMAGES/Pasted%20image%2020230205153813.png)
![Alt text](IMAGES/Pasted%20image%2020230205153823.png)

---
## Variants on Sliding Window
- Receiver doesn't transmit redundant ACKs
- Receiver transmits selective ACKS
	- Ack indicate exactly which frames have been accepted

### Window Sizes
	- If RTT × Bandwidth product is known then ideal is:

$$SWS=RTT×{Bandwidth\over Framesize}$$
- Common receive window size settings:
	- 1 means no buffering out-of-order frames
	- RWS = SWS buffers as many as can be in flight
	- Note that RWS > SWS is not sensible

### Roles of Sliding Window Algorithm
![Alt text](IMAGES/Pasted%20image%2020230205154126.png)

### TCP's Sliding Window
![Alt text](IMAGES/Pasted%20image%2020230205154148.png)

## Examples

![Alt text](IMAGES/Pasted%20image%2020230205154205.png)

---
## TCP Sender and Receiver
![Alt text](IMAGES/Pasted%20image%2020230205154220.png)