TCP/IP is the most fundamental protocol used in the internet. 
- Allows computers to communicate / share resources. 
- Used as a standard. 
- To bridge the gap between non-compatible platforms. 

Work on TCP/IP started in 1970s, funded by US Military.
Advanced Research Project Agency (ARPA). 
- In 1978, International Standards Organization (ISO) proposed the 7-layer OSI refernce model for network services and protocols. 
- TCP/IP does not strictly follow the OSI model. 
- It follows a simplified 4-layer model. 


![[Pasted image 20250803123039.png]

![[Pasted image 20250803123011.png]]
![[Pasted image 20250803123039.png]] 
- TCP/IP refers to a family of protocols. 
- The protocols are built on top of connectionless technology (datagrams). 
	- Data sent from one node to another as sequence of datagrams. 
	- Each datagram is sent independently. 
	- The datagrams corresponding to the same message may follow different routes. 
		- variable delay, arrival order at destination. 


## TCP / IP Family members (partial list) 


| Layers      | Members                                                         |
| ----------- | --------------------------------------------------------------- |
| Application | FTP, TFTP, SMTP, SNMP, DNS, User Process                        |
| Transport   | TCP(Transmission control protocol), UDP(User Datagram Protocol) |
| Network     | Internet Protocol (IP) , ICMP, IGMP, ARP, RARP                  |
| Datalink    | Hardware, Ethernet.                                             |

- **Address Resolution Protocol (ARP) :** Map IP addresses to hardware (MAC) addresses.
- **Reverse Address Resolution protocol (RARP) :** Map hardware addresses to IP addresses.
- **Internet Control Message Protocol (ICMP) :** A network device can send error message and other information. 
- **Internet Group Management Protocol (IGMP) :** A node can send its multicast group membership to adjacent routers.

### What does IP do?
IP transport datagrams (packets) from a source node to a destination node.
- Responsible for routing the packets. 
- Breaks a packet into smaller packets, if required.
- Unreliable service. 
	-  A Packet may be lost in transit.
	- Packets may arrive out of order.
	- Duplicate packets may be generated.

### What does TCP do?
- TCP Provides a connection-oriented, reliable service for sending message.
	- Split a message into packets.
	- Reassemble packets at destination.
	- Resend packets that were lost in transit.
- Interface with IP : 
	- Each packet forwarded to IP for delivery.
	- Error control is done by TCP.

### What does UDP do?
- UDP provides a connectionless, unreliable service for sending datagrams (packets).
	- Messages small enough to fit in a packet (e.g., DNS query).
	- Simpler (and faster ) than TCP.
	- Never split data into multiple packets.
	- Does not care about error control.
- Interface with IP : 
	- Each UDP packet sent to IP for delivery.
![[Pasted image 20250805023840.png]]

## Encapsulation : 
- As data flows down the protocol hierarchy, headers (and trailer ) get appended to it.
- As data moves up the hierarchy, headers (and trailers) get stripped off.
![[Pasted image 20250805024041.png]]

----
# The IP layer : 
- IP layer provides a connectionless, unreliable delivery system for packets. 
- Each Packet is independent of one another. 
	-  IP layer need not maintain any history. 
	- Each IP packet must contain the source and destination addresses. 
	- IP layer does not guarantee delivery of packets. 
- IP layer encapsulation 
	- Receives a data chunk from the higher layer (TCP or UDP).
	- Prepends a header of minimum of 20 bytes. 
		- Containing relevant info for handling routing and flow control. 

![[Pasted image 20250805025704.png]]

### IP header Fields : 
- **VER (4 bits) :** Version of the IP protocol in use, IPv4 or IPv6.
- **HLEN (4 bits) :** 
	-  Length of the header, expressed as the number of 32-bit words.
	- Minimum size is 5, and maximum 15.
- **Total Length (16 bits ) :** 
	- Length in bytes of the datagram, including header.
	- Maximum datagram size :: 2^16 = 65536 bytes.
- **Service Type (8 bits) :** 
	-  Allows packet to be assigned a priority.
	- Router can use this field to route packets. 
- **Time to Live (8 bits) :
	- Prevents a packet from travelling in a loop
	- Senders sets a value, that is decremented at each hop. If it reaches zero, packet is discarded. 
- **Protocol (8 bits) :**  Identifies the higher layer protocol being used.
- **Source IP address (32 bits) :** Internet address of the sender. 
- **Destination IP address (32 bits) :** Internet address of the destination. 
- **Identification, Flags, Fragment Offset :** Used for handling fragmentation. 
- **Options (variable width) :** 
	- Can be given provided router supports.
	- Source routing, for example. 
- **Header Checksum (16 bits) :** 
	- Covers only the IP header. 
	- How computed ?
		- Header treated as sequence of 16-bit integers. 
		- The integers are all added using ones complement arithmetic. 
		- Ones complement of the final sum is taken as the checksum. 
	- A mismatch in checksum causes the datagram to be discarded. 
#### viewing IP packets : 
- We can use packet sniffers to view IP packets. 
- Some popular Packet sniffers are : 
	- wireshark
	- windump
	- tcpdump
	- Tshark
	- Solarwinds