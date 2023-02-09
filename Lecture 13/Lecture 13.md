## Wireless 802.11 and Bluetooth
![Alt text](IMAGES/Pasted%20image%2020230206152353.png)
#Wireless
## Wireless (802.11)
- Spread spectrum radio
	-  2.4 GHz frequency band
- Bandwidth ranges 1,2,5.5,11,22,54,,Mbps
`Spread Spectrum radio is a method of transmitting radio signals in which the frequency of the signal is deliberately varied over a wide bandwidth, rather than transmitted at a single frequency. This helps to reduce the signal interference and increase the signal security, making it less susceptible to eavesdropping. It is used in many wireless technologies such as Wi-Fi, Bluetooth, GPS, and mobile networks.`


- Like Ethernet, 802.11 has shared medium
	- Need MAC(uses exponential backoff)
- Unlike Ethernet, in 802.11
	- No support for collision detection
	- Not all senders and receivers are directly connected


>802.11 operates in a shared medium environment, which means that multiple devices can be using the same radio frequency at the same time. To manage this, it uses a protocol called the Media Access Control (MAC) to organize access to the channel and avoid collisions. Exponential Backoff is an algorithm used by the MAC protocol to resolve collisions that occur when multiple devices attempt to transmit data at the same time. When a collision occurs, each device waits for a random amount of time before attempting to retransmit the data. The waiting time increases exponentially for each subsequent retransmission, to reduce the likelihood of another collision. In summary, 802.11 uses the MAC protocol and the Exponential Backoff algorithm to manage access to the wireless channel and ensure efficient and reliable data transmission over the air.


#Backoff
Exponential backoff is an algorithm used to handle retransmissions of lost or failed data transmissions in computer networks. The idea is that if a collision occurs when two or more devices attempt to transmit data at the same time, each device will wait for a random amount of time before attempting to retransmit the data. The waiting time increases exponentially after each subsequent retransmission attempt, to reduce the likelihood of another collision. The formula used to calculate the waiting time is typically of the form: `backoff time = random_number * multiplier^(number of retransmissions)` where `random_number` is a random number between 0 and 1, `multiplier` is a constant that sets the rate at which the waiting time increases, and `number of retransmissions` is the number of previous attempts to transmit the data. Exponential backoff is widely used in computer networks to resolve collisions and improve the reliability of data transmissions, by reducing the number of retransmission attempts and avoiding congestions in the network.

### Background
`Number of wireless (mobile) phone subscrbers now exceeds the number of wired phone subscribers

`computer nets: laptops,palmtops,PDAs,Internet-enabled phone promise anytime untethered Internet access`

`two important (but different) challenges wireless: communication over wireless link mobility: handling the mobile user who changes point of attachment to network`

![Alt text](IMAGES/Pasted%20image%2020230206152924.png)
![Alt text](IMAGES/Pasted%20image%2020230206152935.png)
![Alt text](IMAGES/Pasted%20image%2020230206152947.png)
![Alt text](IMAGES/Pasted%20image%2020230206153112.png)
![Alt text](IMAGES/Pasted%20image%2020230206153130.png)
![Alt text](IMAGES/Pasted%20image%2020230206153309.png)
![Alt text](IMAGES/Pasted%20image%2020230206153321.png)
![Alt text](IMAGES/Pasted%20image%2020230206153357.png)

---
![Alt text](IMAGES/Pasted%20image%2020230206153504.png)
`Active and passive scanning are two methods used to gather information about wireless networks. The main difference between the two is how they go about collecting that information. Active scanning involves sending probe requests to access points to gather information about the available networks. The access points then respond with probe response messages that contain information such as the network's SSID (Service Set Identifier), channel, and supported data rates. Passive scanning, on the other hand, involves listening to the beacon frames sent out by access points, without sending any probe requests. In this method, the client device listens to the airwaves to gather information about the available networks. Active scanning is faster than passive scanning, but it may also generate more network traffic and potentially interfere with other devices. Passive scanning, on the other hand, is less intrusive and does not generate network traffic, but it may also be slower, as it relies on the access points to transmit beacon frames regularly.`

![Alt text](IMAGES/Pasted%20image%2020230206153613.png)
`A wireless access point (WAP) is a device that allows other devices to connect to a wireless network. It acts as a bridge between the wireless devices and the wired network, allowing wireless devices to communicate with each other and with other devices on the wired network. WAPs come in different shapes and sizes, from small standalone device for home networks to large enterprise-grade access points for commercial use. They typically have one or more antennas to broadcast and receive wireless signals, and they support various wireless standards such as 802.11a/b/g/n/ac/ax, to ensure compatibility with different types of wireless devices. WAPs also provide security features, such as encryption and authentication, to protect the wireless network from unauthorized access. They can be configured with different types of security protocols, such as WEP, WPA, and WPA2, to provide different levels of security and protection. In summary, a wireless access point is a crucial element in a wireless network, enabling wireless devices to connect to the network, communicate with each other, and access the Internet or other network resources.

---
#MAC
## Media Access Control Layer (MAC)
![Alt text](IMAGES/Pasted%20image%2020230206153739.png)
![Alt text](IMAGES/Pasted%20image%2020230206153749.png)
![Alt text](IMAGES/Pasted%20image%2020230206153759.png)
![Alt text](IMAGES/Pasted%20image%2020230206153823.png)
![Alt text](IMAGES/Pasted%20image%2020230206153832.png)
![Alt text](IMAGES/Pasted%20image%2020230206153847.png)
![Alt text](IMAGES/Pasted%20image%2020230206153902.png)
![Alt text](IMAGES/Pasted%20image%2020230206154015.png)
![Alt text](IMAGES/Pasted%20image%2020230206154039.png)
![Alt text](IMAGES/Pasted%20image%2020230206154106.png)

---
## Packet format and addressing
![Alt text](IMAGES/Pasted%20image%2020230206154206.png)
![Alt text](IMAGES/Pasted%20image%2020230206154223.png)
![Alt text](IMAGES/Pasted%20image%2020230206154234.png)
![Alt text](IMAGES/Pasted%20image%2020230206154244.png)

---
## Advanced Capabilities
![Alt text](IMAGES/Pasted%20image%2020230206154305.png)
![Alt text](IMAGES/Pasted%20image%2020230206154322.png)
![Alt text](IMAGES/Pasted%20image%2020230206154332.png)

---
## Bluetooth
## Personal Area Network
![Alt text](IMAGES/Pasted%20image%2020230206154403.png)
![Alt text](IMAGES/Pasted%20image%2020230206154416.png)
![Alt text](IMAGES/Pasted%20image%2020230206154428.png)