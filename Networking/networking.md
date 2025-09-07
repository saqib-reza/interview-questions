


## Network

<details>
<summary>In general, what do you need in order to communicate?</summary><br><b>

  - A common language (for the two ends to understand)
  - A way to address who you want to communicate with
  - A Connection (so the content of the communication can reach the recipients)

</b></details>

<details>
<summary>What is TCP/IP?</summary><br><b>

A set of protocols that define how two or more devices can communicate with each other.

To learn more about TCP/IP, read [here](http://www.penguintutor.com/linux/basic-network-reference)

</b></details>

<details>
<summary>What is Ethernet?</summary><br><b>

Ethernet simply refers to the most common type of Local Area Network (LAN) used today. A LAN—in contrast to a WAN (Wide Area Network), which spans a larger geographical area—is a connected network of computers in a small area, like your office, college campus, or even home.

</b></details>

<details>
<summary>What is a MAC address? What is it used for?</summary><br><b>

A MAC address is a unique identification number or code used to identify individual devices on the network.

Packets that are sent on the ethernet are always coming from a MAC address and sent to a MAC address. If a network adapter is receiving a packet, it is comparing the packet’s destination MAC address to the adapter’s own MAC address.

</b></details>

<details>
<summary>When is this MAC address used?: ff:ff:ff:ff:ff:ff</summary><br><b>

When a device sends a packet to the broadcast MAC address (FF:FF:FF:FF:FF:FF​), it is delivered to all stations on the local network. Ethernet broadcasts are used to resolve IP addresses to MAC addresses (by ARP) at the data link layer.
</b></details>

<details>
<summary>What is an IP address?</summary><br><b>

An Internet Protocol address (IP address) is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication.An IP address serves two main functions: host or network interface identification and location addressing.
</b></details>

<details>
<summary>Explain the subnet mask and give an example</summary><br><b>

A Subnet mask is a 32-bit number that masks an IP address and divides the IP addresses into network addresses and host addresses. Subnet Mask is made by setting network bits to all "1"s and setting host bits to all "0"s. Within a given network, out of the total usable host addresses, two are always reserved for specific purposes and cannot be allocated to any host. These are the first address, which is reserved as a network address (a.k.a network ID), and the last address used for network broadcast.

[Example](https://github.com/philemonnwanne/projects/tree/main/exercises/exe-09)

</b></details>

<details>
<summary>What is a private IP address? In which scenarios/system designs, one should use it?</summary><br><b>
Private IP addresses are assigned to the hosts in the same network to communicate with one another. As the name "private" suggests, the devices having the private IP addresses assigned can't be reached by the devices from any external network. For example, if I am living in a hostel and I want my hostel mates to join the game server I have hosted, I will ask them to join via my server's private IP address, since the network is local to the hostel.
</b></details>

<details>
<summary>What is a public IP address? In which scenarios/system designs, one should use it?</summary><br><b>
A public IP address is a public-facing IP address. In the event that you were hosting a game server that you want your friends to join, you will give your friends your public IP address to allow their computers to identify and locate your network and server in order for the connection to take place. One time that you would not need to use a public-facing IP address is in the event that you were playing with friends who were connected to the same network as you, in that case, you would use a private IP address. In order for someone to be able to connect to your server that is located internally, you will have to set up a port forward to tell your router to allow traffic from the public domain into your network and vice versa.
</b></details>

<details>
<summary>Explain the OSI model. What layers there are? What each layer is responsible for?</summary><br><b>

- Application: user end (HTTP is here)
- Presentation: establishes context between application-layer entities (Encryption is here)
- Session: establishes, manages, and terminates the connections
- Transport: transfers variable-length data sequences from a source to a destination host (TCP & UDP are here)
- Network: transfers datagrams from one network to another (IP is here)
- Data link: provides a link between two directly connected nodes (MAC is here)
- Physical: the electrical and physical spec of the data connection (Bits are here)

You can read more about the OSI model in [penguintutor.com](http://www.penguintutor.com/linux/basic-network-reference)
</b></details>

<details>
<summary>For each of the following determines to which OSI layer it belongs:

  * Error correction
  * Packets routing
  * Cables and electrical signals
  * MAC address
  * IP address
  * Terminate connections
  * 3 way handshake</summary><br><b>
  * Error correction - Data link
  * Packets routing - Network
  * Cables and electrical signals - Physical
  * MAC address - Data link
  * IP address - Network
  * Terminate connections - Session
  * 3-way handshake - Transport
</b></details>

<details>
<summary>What delivery schemes are you familiar with?</summary><br><b>

Unicast: One-to-one communication where there is one sender and one receiver.

Broadcast: Sending a message to everyone in the network. The address ff:ff:ff:ff:ff:ff is used for broadcasting.
           Two common protocols which use broadcast are ARP and DHCP.

Multicast: Sending a message to a group of subscribers. It can be one-to-many or many-to-many.
</b></details>

<details>
<summary>What is CSMA/CD? Is it used in modern ethernet networks?</summary><br><b>

CSMA/CD stands for Carrier Sense Multiple Access / Collision Detection.
Its primary focus is to manage access to a shared medium/bus where only one host can transmit at a given point in time.

CSMA/CD algorithm:

1. Before sending a frame, it checks whether another host is already transmitting a frame.
2. If no one is transmitting, it starts transmitting the frame.
3. If two hosts transmit at the same time, we have a collision.
4. Both hosts stop sending the frame and they send everyone a 'jam signal' notifying everyone that a collision occurred
5. They are waiting for a random time before sending it again
6. Once each host waited for a random time, they try to send the frame again and so the cycle starts again
</b></details>

<details>
<summary>Describe the following network devices and the difference between them:

  * router
  * switch
  * hub</summary><br><b>

A router, switch, and hub are all network devices used to connect devices in a local area network (LAN). However, each device operates differently and has its specific use cases. Here is a brief description of each device and the differences between them:

1. Router: a network device that connects multiple network segments together. It operates at the network layer (Layer 3) of the OSI model and uses routing protocols to direct data between networks. Routers use IP addresses to identify devices and route data packets to the correct destination.
2. Switch: a network device that connects multiple devices on a LAN. It operates at the data link layer (Layer 2) of the OSI model and uses MAC addresses to identify devices and direct data packets to the correct destination. Switches allow devices on the same network to communicate with each other more efficiently and can prevent data collisions that can occur when multiple devices send data simultaneously.
3. Hub: a network device that connects multiple devices through a single cable and is used to connect multiple devices without segmenting a network. However, unlike a switch, it operates at the physical layer (Layer 1) of the OSI model and simply broadcasts data packets to all devices connected to it, regardless of whether the device is the intended recipient or not. This means that data collisions can occur, and the network's efficiency can suffer as a result. Hubs are generally not used in modern network setups, as switches are more efficient and provide better network performance.
</b></details>

<details>
<summary>What is a "Collision Domain"?</summary><br><b>
A collision domain is a network segment in which devices can potentially interfere with each other by attempting to transmit data at the same time. When two devices transmit data at the same time, it can cause a collision, resulting in lost or corrupted data. In a collision domain, all devices share the same bandwidth, and any device can potentially interfere with the transmission of data by other devices.
</b></details>

<details>
<summary>What is a "Broadcast Domain"?</summary><br><b>
A broadcast domain is a network segment in which all devices can communicate with each other by sending broadcast messages. A broadcast message is a message that is sent to all devices in a network rather than a specific device. In a broadcast domain, all devices can receive and process broadcast messages, regardless of whether the message was intended for them or not.
</b></details>

<details>
<summary>three computers connected to a switch. How many collision domains are there? How many broadcast domains?</summary><br><b>

Three collision domains and one broadcast domain
</b></details>

<details>
<summary>How does a router work?</summary><br><b>

A router is a physical or virtual appliance that passes information between two or more packet-switched computer networks. A router inspects a given data packet's destination Internet Protocol address (IP address), calculates the best way for it to reach its destination, and then forwards it accordingly.

</b></details>

<details>
<summary>What is NAT?</summary><br><b>

 Network Address Translation (NAT) is a process in which one or more local IP addresses are translated into one or more Global IP address and vice versa in order to provide Internet access to the local hosts.

</b></details>

<details>
<summary>What is a proxy? How does it work? What do we need it for?</summary><br><b>

A proxy server acts as a gateway between you and the internet. It’s an intermediary server separating end users from the websites they browse.

If you’re using a proxy server, internet traffic flows through the proxy server on its way to the address you requested. The request then comes back through that same proxy server (there are exceptions to this rule), and then the proxy server forwards the data received from the website to you.

Proxy servers provide varying levels of functionality, security, and privacy depending on your use case, needs, or company policy.
</b></details>

<details>
<summary>What is TCP? How does it work? What is the 3-way handshake?</summary><br><b>

TCP 3-way handshake or three-way handshake is a process that is used in a TCP/IP network to make a connection between server and client.

A three-way handshake is primarily used to create a TCP socket connection. It works when:

- A client node sends an SYN data packet over an IP network to a server on the same or an external network. The objective of this packet is to ask/infer if the server is open for new connections.
- The target server must have open ports that can accept and initiate new connections. When the server receives the SYN packet from the client node, it responds and returns a confirmation receipt – the ACK packet or SYN/ACK packet.
- The client node receives the SYN/ACK from the server and responds with an ACK packet.
</b></details>

<details>
<summary>What is round-trip delay or round-trip time?</summary><br><b>

From [wikipedia](https://en.wikipedia.org/wiki/Round-trip_delay): "the length of time it takes for a signal to be sent plus the length of time it takes for an acknowledgment of that signal to be received"

Bonus question: what is the RTT of LAN?
</b></details>

<details>
<summary>How does an SSL handshake work?</summary><br><b>
SSL handshake is a process that establishes a secure connection between a client and a server.

1. The client sends a Client Hello message to the server, which includes the client's version of the SSL/TLS protocol, a list of the cryptographic algorithms supported by the client, and a random value.
2. The server responds with a Server Hello message, which includes the server's version of the SSL/TLS protocol, a random value, and a session ID.
3. The server sends a Certificate message, which contains the server's certificate.
4. The server sends a Server Hello Done message, which indicates that the server is done sending messages for the Server Hello phase.
5. The client sends a Client Key Exchange message, which contains the client's public key.
6. The client sends a Change Cipher Spec message, which notifies the server that the client is about to send a message encrypted with the new cipher spec.
7. The client sends an Encrypted Handshake Message, which contains the pre-master secret encrypted with the server's public key.
8. The server sends a Change Cipher Spec message, which notifies the client that the server is about to send a message encrypted with the new cipher spec.
9. The server sends an Encrypted Handshake Message, which contains the pre-master secret encrypted with the client's public key.
10. The client and server can now exchange application data.
</b></details>

<details>
<summary>What is the difference between TCP and UDP?</summary><br><b>

TCP establishes a connection between the client and the server to guarantee the order of the packages, on the other hand, UDP does not establish a connection between the client and server and doesn't handle package orders. This makes UDP more lightweight than TCP and a perfect candidate for services like streaming.

[Penguintutor.com](http://www.penguintutor.com/linux/basic-network-reference) provides a good explanation.
</b></details>

<details>
<summary>What TCP/IP protocols are you familiar with?</summary><br><b>
</b></details>

<details>
<summary>Explain the "default gateway"</summary><br><b>

A default gateway serves as an access point or IP router that a networked computer uses to send information to a computer in another network or the internet.
</b></details>

<details>
<summary>What is ARP? How does it work?</summary><br><b>

ARP stands for Address Resolution Protocol. When you try to ping an IP address on your local network, say 192.168.1.1, your system has to turn the IP address 192.168.1.1 into a MAC address. This involves using ARP to resolve the address, hence its name.

Systems keep an ARP look-up table where they store information about what IP addresses are associated with what MAC addresses. When trying to send a packet to an IP address, the system will first consult this table to see if it already knows the MAC address. If there is a value cached, ARP is not used.
</b></details>

<details>
<summary>What is TTL? What does it help to prevent?</summary><br><b>

- TTL (Time to Live) is a value in an IP (Internet Protocol) packet that determines how many hops or routers a packet can travel before it is discarded. Each time a packet is forwarded by a router, the TTL value is decreased by one. When the TTL value reaches zero, the packet is dropped, and an ICMP (Internet Control Message Protocol) message is sent back to the sender indicating that the packet has expired.
- TTL is used to prevent packets from circulating indefinitely in the network, which can cause congestion and degrade network performance.
- It also helps to prevent packets from being trapped in routing loops, where packets continuously travel between the same set of routers without ever reaching their destination.
- In addition, TTL can be used to help detect and prevent IP spoofing attacks, where an attacker attempts to impersonate another device on the network by using a false or fake IP address. By limiting the number of hops that a packet can travel, TTL can help prevent packets from being routed to destinations that are not legitimate.
</b></details>

<details>
<summary>What is DHCP? How does it work?</summary><br><b>

It stands for Dynamic Host Configuration Protocol and allocates IP addresses, subnet masks, and gateways to hosts. This is how it works:

* A host upon entering a network broadcasts a message in search of a DHCP server (DHCP DISCOVER)
* An offer message is sent back by the DHCP server as a packet containing lease time, subnet mask, IP addresses, etc (DHCP OFFER)
* Depending on which offer is accepted, the client sends back a reply broadcast letting all DHCP servers know (DHCP REQUEST)
* The server sends an acknowledgment (DHCP ACK)

Read more [here](https://linuxjourney.com/lesson/dhcp-overview)
</b></details>

<details>
<summary>Can you have two DHCP servers on the same network? How does it work?</summary><br><b>

It is possible to have two DHCP servers on the same network, however, it is not recommended, and it is important to configure them carefully to prevent conflicts and configuration problems.
- When two DHCP servers are configured on the same network, there is a risk that both servers will assign IP addresses and other network configuration settings to the same device, which can cause conflicts and connectivity issues. Additionally, if the DHCP servers are configured with different network settings or options, devices on the network may receive conflicting or inconsistent configuration settings.
- However, in some cases, it may be necessary to have two DHCP servers on the same network, such as in large networks where one DHCP server may not be able to handle all the requests. In such cases, DHCP servers can be configured to serve different IP address ranges or different subnets, so they do not interfere with each other.
</b></details>

<details>
<summary>What is SSL tunneling? How does it work?</summary><br><b>

- SSL (Secure Sockets Layer) tunneling is a technique used to establish a secure, encrypted connection between two endpoints over an insecure network, such as the Internet. The SSL tunnel is created by encapsulating the traffic within an SSL connection, which provides confidentiality, integrity, and authentication.

Here's how SSL tunneling works:

1. A client initiates an SSL connection to a server, which involves a handshake process to establish the SSL session.
2. Once the SSL session is established, the client and server negotiate encryption parameters, such as the encryption algorithm and key length, then exchange digital certificates to authenticate each other.
3. The client then sends traffic through the SSL tunnel to the server, which decrypts the traffic and forwards it to its destination.
4. The server sends traffic back through the SSL tunnel to the client, which decrypts the traffic and forwards it to the application.
</b></details>

<details>
<summary>What is a socket? Where can you see the list of sockets in your system?</summary><br><b>

- A socket is a software endpoint that enables two-way communication between processes over a network. Sockets provide a standardized interface for network communication, allowing applications to send and receive data across a network. To view the list of open sockets on a Linux system: 
***netstat -an***
- This command displays a list of all open sockets, along with their protocol, local address, foreign address, and state.
</b></details>

<details>
<summary>What is IPv6? Why should we consider using it if we have IPv4?</summary><br><b>

- IPv6 (Internet Protocol version 6) is the latest version of the Internet Protocol (IP), which is used to identify and communicate with devices on a network. IPv6 addresses are 128-bit addresses and are expressed in hexadecimal notation, such as 2001:0db8:85a3:0000:0000:8a2e:0370:7334.

There are several reasons why we should consider using IPv6 over IPv4:

1. Address space: IPv4 has a limited address space, which has been exhausted in many parts of the world. IPv6 provides a much larger address space, allowing for trillions of unique IP addresses.
2. Security: IPv6 includes built-in support for IPsec, which provides end-to-end encryption and authentication for network traffic.
3. Performance: IPv6 includes features that can help to improve network performance, such as multicast routing, which allows a single packet to be sent to multiple destinations simultaneously.
4. Simplified network configuration: IPv6 includes features that can simplify network configuration, such as stateless autoconfiguration, which allows devices to automatically configure their own IPv6 addresses without the need for a DHCP server.
5. Better mobility support: IPv6 includes features that can improve mobility support, such as Mobile IPv6, which allows devices to maintain their IPv6 addresses as they move between different networks.
</b></details>

<details>
<summary>What is VLAN?</summary><br><b>

- A VLAN (Virtual Local Area Network) is a logical network that groups together a set of devices on a physical network, regardless of their physical location. VLANs are created by configuring network switches to assign a specific VLAN ID to frames sent by devices connected to a specific port or group of ports on the switch.
</b></details>

<details>
<summary>What is MTU?</summary><br><b>
	
MTU stands for Maximum Transmission Unit. It's the size of the largest PDU (protocol Data Unit) that can be sent in a single transaction.
</b></details>

<details>
<summary>What happens if you send a packet that is bigger than the MTU?</summary><br><b>
	
With the IPv4 protocol, the router can fragment the PDU and then send all the fragmented PDU through the transaction.
	
With IPv6 protocol, it issues an error to the user's computer.
</b></details>

<details>
<summary>True or False? Ping is using UDP because it doesn't care about reliable connection</summary><br><b>

False. Ping is actually using ICMP (Internet Control Message Protocol) which is a network protocol used to send diagnostic messages and control messages related to network communication.
</b></details>

<details>
<summary>What is SDN?</summary><br><b>

- SDN stands for Software-Defined Networking. It is an approach to network management that emphasizes the centralization of network control, enabling administrators to manage network behavior through a software abstraction.
- In a traditional network, network devices such as routers, switches, and firewalls are configured and managed individually, using specialized software or command-line interfaces. In contrast, SDN separates the network control plane from the data plane, allowing administrators to manage network behavior through a centralized software controller.
</b></details>

<details>
<summary>What is ICMP? What is it used for?</summary><br><b>

- ICMP stands for Internet Control Message Protocol. It is a protocol used for diagnostic and control purposes in IP networks. It is a part of the Internet Protocol suite, operating at the network layer.

ICMP messages are used for a variety of purposes, including:
1. Error reporting: ICMP messages are used to report errors that occur in the network, such as a packet that could not be delivered to its destination.
2. Ping: ICMP is used to send ping messages, which are used to test whether a host or network is reachable and to measure the round-trip time for packets.
3. Path MTU discovery: ICMP is used to discover the Maximum Transmission Unit (MTU) of a path, which is the largest packet size that can be transmitted without fragmentation.
4. Traceroute: ICMP is used by the traceroute utility to trace the path that packets take through the network.
5. Router discovery: ICMP is used to discover the routers in a network.
</b></details>

<details>
<summary>What is NAT? How does it work?</summary><br><b>

NAT stands for Network Address Translation. It’s a way to map multiple local private addresses to a public one before transferring the information. Organizations that want multiple devices to employ a single IP address use NAT, as do most home routers.
For example, your computer's private IP could be 192.168.1.100, but your router maps the traffic to its public IP (e.g. 1.1.1.1). Any device on the internet would see the traffic coming from your public IP (1.1.1.1) instead of your private IP (192.168.1.100).
</b></details>

<details>
<summary>Which port number is used in each of the following protocols?:

  * SSH
  * SMTP
  * HTTP
  * DNS
  * HTTPS
  * FTP
  * SFTP
</summary><br><b>

  * SSH - 22
  * SMTP - 25
  * HTTP - 80
  * DNS - 53
  * HTTPS - 443
  * FTP - 21
  * SFTP - 22
</b></details>

<details>
<summary>Which factors affect network performance?</summary><br><b>

Several factors can affect network performance, including:

1. Bandwidth: The available bandwidth of a network connection can significantly impact its performance. Networks with limited bandwidth can experience slow data transfer rates, high latency, and poor responsiveness.
2. Latency: Latency refers to the delay that occurs when data is transmitted from one point in a network to another. High latency can result in slow network performance, especially for real-time applications like video conferencing and online gaming.
3. Network congestion: When too many devices are using a network at the same time, network congestion can occur, leading to slow data transfer rates and poor network performance.
4. Packet loss: Packet loss occurs when packets of data are dropped during transmission. This can result in slower network speeds and lower overall network performance.
5. Network topology: The physical layout of a network, including the placement of switches, routers, and other network devices, can impact network performance.
6. Network protocol: Different network protocols have different performance characteristics, which can impact network performance. For example, TCP is a reliable protocol that can guarantee the delivery of data, but it can also result in slower performance due to the overhead required for error checking and retransmission.
7. Network security: Security measures such as firewalls and encryption can impact network performance, especially if they require significant processing power or introduce additional latency.
8. Distance: The physical distance between devices on a network can impact network performance, especially for wireless networks where signal strength and interference can affect connectivity and data transfer rates.
</b></details>

<details>
<summary>What is APIPA?</summary><br><b>

APIPA is a set of IP addresses that devices are allocated
when the main DHCP server is not reachable

</b></details>

<details>
<summary>What IP range does APIPA use?</summary><br><b>

APIPA uses the IP range: 169.254.0.1 - 169.254.255.254.

</b></details>

#### Control Plane and Data Plane

<details>
<summary>What does "control plane" refer to?</summary><br><b>

The control plane is a part of the network that decides how to route and forward packets to a different location.
</b></details>

<details>
<summary>What does "data plane" refer to?</summary><br><b>

The data plane is a part of the network that actually forwards the data/packets.
</b></details>

<details>
<summary>What does "management plane" refer to?</summary><br><b>

It refers to monitoring and management functions.
</b></details>

<details>
<summary>To which plane (data, control, ...) does creating routing tables belong to?</summary><br><b>

Control Plane.
</b></details>

<details>
<summary>Explain Spanning Tree Protocol (STP).</summary><br><b>
</b></details>

<details>
<summary>What is link aggregation? Why is it used?</summary><br><b>
</b></details>

<details>
<summary>What is Asymmetric Routing? How to deal with it?</summary><br><b>
</b></details>

<details>
<summary>What overlay (tunnel) protocols are you familiar with?</summary><br><b>
</b></details>

<details>
<summary>What is GRE? How does it work?</summary><br><b>
</b></details>

<details>
<summary>What is VXLAN? How does it work?</summary><br><b>
</b></details>

<details>
<summary>What is SNAT?</summary><br><b>
</b></details>

<details>
<summary>Explain OSPF.</summary><br><b>


OSPF (Open Shortest Path First) is a routing protocol that can be implemented on various types of routers. In general, OSPF is supported on most modern routers, including those from vendors such as Cisco, Juniper, and Huawei. The protocol is designed to work with IP-based networks, including both IPv4 and IPv6. Also, it uses a hierarchical network design, where routers are grouped into areas, with each area having its own topology map and routing table. This design helps to reduce the amount of routing information that needs to be exchanged between routers and improve network scalability.

The OSPF 4 Types of routers are:
  * Internal Router
  * Area Border Routers
  * Autonomous Systems Boundary Routers
  * Backbone Routers

  Learn more about OSPF router types: https://www.educba.com/ospf-router-types/
</b></details>

<details>
<summary>What is latency?</summary><br><b>
	
Latency is the time taken for information to reach its destination from the source.
</b></details>

<details>
<summary>What is bandwidth?</summary><br><b>
	
Bandwidth is the capacity of a communication channel to measure how much data the latter can handle over a specific time period. More bandwidth would imply more traffic handling and thus more data transfer.
</b></details>

<details>
<summary>What is throughput?</summary><br><b>
	
Throughput refers to the measurement of the real amount of data transferred over a certain period of time across any transmission channel.
</b></details>

<details>
<summary>When performing a search query, what is more important, latency or throughput? And how to ensure that we manage global infrastructure?
</summary><br><b>

Latency. To have good latency, a search query should be forwarded to the closest data center.
</b></details>

<details>
<summary>When uploading a video, what is more important, latency or throughput? And how to assure that?</summary><br><b>

Throughput. To have good throughput, the upload stream should be routed to an underutilized link.
</b></details>

<details>
<summary>What other considerations (except latency and throughput) are there when forwarding requests?</summary><br><b>

* Keep caches updated (which means the request could be forwarded not to the closest data center)
</b></details>

<details>
<summary>Explain Spine & Leaf</summary><br><b>
"Spine & Leaf" is a networking topology commonly used in data center environments to connect multiple switches and manage network traffic efficiently. It is also known as "spine-leaf" architecture or "leaf-spine" topology. This design provides high bandwidth, low latency, and scalability, making it ideal for modern data centers handling large volumes of data and traffic.

Within a Spine & Leaf network there are two main tipology of switches:

* Spine Switches: Spine switches are high-performance switches arranged in a spine layer. These switches act as the core of the network and are typically interconnected with each leaf switch. Each spine switch is connected to all the leaf switches in the data center.
* Leaf Switches: Leaf switches are connected to end devices like servers, storage arrays, and other networking equipment. Each leaf switch is connected to every spine switch in the data center. This creates a non-blocking, full-mesh connectivity between leaf and spine switches, ensuring any leaf switch can communicate with any other leaf switch with maximum throughput.

The Spine & Leaf architecture has become increasingly popular in data centers due to its ability to handle the demands of modern cloud computing, virtualization, and big data applications, providing a scalable, high-performance, and reliable network infrastructure
</b></details>

<details>
<summary>What is Network Congestion? What can cause it?</summary><br><b>

Network congestion occurs when there is too much data to transmit on a network and it doesn't have enough capacity to handle the demand. </br>
This can lead to increased latency and packet loss. The causes can be multiple, such as high network usage, large file transfers, malware, hardware issues, or network design problems. </br>
To prevent network congestion, it's important to monitor your network usage and implement strategies to limit or manage the demand.
</b></details>

<details>
<summary>What can you tell me about the UDP packet format? What about the TCP packet format? How is it different?</summary><br><b>
</b></details>

<details>
<summary>What is the exponential backoff algorithm? Where is it used?</summary><br><b>
</b></details>

<details>
<summary>Using Hamming code, what would be the code word for the following data word 100111010001101?</summary><br><b>

00110011110100011101
</b></details>

<details>
<summary>Give examples of protocols found in the application layer</summary><br><b>

* Hypertext Transfer Protocol (HTTP) - used for the webpages on the internet
* Simple Mail Transfer Protocol (SMTP) - email transmission
* Telecommunications Network - (TELNET) - terminal emulation to allow a client access to a telnet server
* File Transfer Protocol (FTP) - facilitates the transfer of files between any two machines
* Domain Name System (DNS) - domain name translation
* Dynamic Host Configuration Protocol (DHCP) - allocates IP addresses, subnet masks, and gateways to hosts
* Simple Network Management Protocol (SNMP) - gathers data on devices on the network
</b></details>

<details>
<summary>Give examples of protocols found in the Network Layer</summary><br><b>

* Internet Protocol (IP) - assists in routing packets from one machine to another
* Internet Control Message Protocol (ICMP) - lets one know what is going such as error messages and debugging information
</b></details>

<details>
<summary>What is HSTS?</summary><br><b>
HTTP Strict Transport Security is a web server directive that informs user agents and web browsers how to handle its connection through a response header sent at the very beginning and back to the browser. This forces connections over HTTPS encryption, disregarding any script's call to load any resource in that domain over HTTP.

Read more [here](https://www.globalsign.com/en/blog/what-is-hsts-and-how-do-i-use-it#:~:text=HTTP%20Strict%20Transport%20Security%20(HSTS,and%20back%20to%20the%20browser.)
</b></details>

#### Network - Misc

<details>
<summary>What is the Internet? Is it the same as the World Wide Web?</summary><br><b>

The internet refers to a network of networks, transferring huge amounts of data around the globe.<br>
The World Wide Web is an application running on millions of servers, on top of the internet, accessed through what is known as the web browser
</b></details>

<details>
<summary>What is the ISP?</summary><br><b>

ISP (Internet Service Provider) is the local internet company provider.
</b></details>
