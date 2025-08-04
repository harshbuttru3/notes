#### Tags:  #Week1 #OSI_Model  

## Data Communication over a network
### 1. Circuit Switching :  

- A dedicated communication path is established between two stations. 
- The path follows a fixed sequence of intermediate links.
- A logical channel gets defined on each physical link. 
 
In circuit switching, Three steps are required for communication, 
1. **Connection establishment :** Required before data transmission
2. **Data transfer :** Can proceed at maximum speed.
3. **Connection termination :** Required after data transmission is over, For deallocation of network resources. 

#### Drawbacks: 
- Channel capacity is dedicated during the entire duration of communication. 
	- Acceptable for voice communication
	- Very inefficient for bursty traffic like data.
- There is an initial delay for connection establishment.

### 2. Packet Switching : 
- Modern form of long-distance communication
- Network resources are not dedicated.
- A link can be shared. 
- The basic technology has evolved over time
- Basic concepts has remained the same. 

- Data are transmitted in short packets (~Kbytes). 
	- A Longer message is broken up into smaller **Chunks**. 
	- The chunks are called **Packets**. 
	- Every packet contains a **Header**. 
		- Relevant information for routing, etc.


 
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.7.31 - 17.23pm.drawing",
	"width": 696,
	"aspectRatio": 2.118872242747309
}
```

- Packet switching is based on store-and-forward concept. 
	- Each intermediate network node receives a whole packet. 
	- Decides the route. 
	- Forwards the packet along the selected route. 
- Each intermediate note (router) maintains a **routing table**. 

#### Advantages : 
- Links can be shared; so link utilization is better. 
- Suitable for computer-generated (bursty) traffic. 
- Buffering and data rate conversion can be performed easily.
- Some packets may be given priority over others, if desired. 

#### How are packets transmitted?
 - Two alternative approaches: 
	 - a) Virtual Circuits
	 - b) Datagram
### a) Virtual Circuit Approach : 
Similar in concept to circuit switching. 
 - A route is established before packet transmission starts. 
 - All packets follow the same path. 
 - The links comprising the path are not dedicated. 
	 - Different from circuit switching in this respect.
##### Analogy : 
Telephone systems. 
#### How it works?
- Route is established a prior. 
- Packet forwarded from one node to the next using store-and-forward scheme.
- only the virtual circuit number need to be carried by a packet. 
	- Each intermediate node maintains a table.
	- Created during route establishment.
	- Used for packet forwarding.
- No dynamic routing decision is taken by the intermediate nodes.

### b) Datagram Approach : 
- No route is established beforehand. 
- Each packet is transmitted as an independent entity.
- Does not maintain any history.
##### Analogy : 
- Postal System.


Every Intermediate node has to take routing decisions dynamically. 
 - Makes use of a **routing table**.
 - Every packet must contain **Source and Destination addresses**.

#### Problems : 
- Packets may be delivered out of order
- If a node crashes momentarily, all of its queued packets are lost. 
- Duplicate Packets may also be generated.

#### Advantages : 
- Faster than virtual circuit for smaller numbers of packets. 
	- No route establishment and termination. 
- More flexible. 
- Packets between two hosts may follow different paths.
	- can handle congestion/failed link

## Comparative Study 
Three types of delays must be considered : 
1. **Propagation Delay :** Time taken by a data signal to propagate from one node to the next. 
2. **Transmission Time :** Time taken to send out a packet by the transmitter. 
3. **Processing Delay :** Time taken by a node to process a packet. 


| Circuit Switching                                                                  | Virtual Circuit Packet Switching                             | Datagram Packet Switching               |
| ---------------------------------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------- |
| After initial circuit establishment, data bits sent continuously without any delay | The **call request** packet sent from source to destination. | No initial delay.                       |
|                                                                                    | The **call Accept** packet returns back.                     | The packets are sent out independently. |
|                                                                                    | Packets send sequentially in a pipelined fashion             | May follow different paths.             |
|                                                                                    | Store-and-forward approach.                                  | Also follows store-and-forward approach |
## Layered Network Architecture : 
Open systems interconnection (OSI) reference model.
- Seven layer model
- Communication functions are partitioned into a hierarchical set of layers. 
#### Objective : 
- Systematic approach to design
- Changes in one layer should not require changes in other layers. 

![[Pasted image 20250803102912.png]]
### Layer Functions :
##### 1. Physical : 
Transmit raw bit  stream over a physical medium (eg. copper wire, Ethernet cable, fibre optics)
##### 2. Data link : 
Reliable transfer of frames over a point-to-point link (flow control, error control ). 
##### 3. Network : 
- Establishing, maintaining and terminating connections.
- Routes packets through point-to-point links. 

##### 4. Transport : 
End-to-end reliable data transfer, with error recovery and flow control.

##### 5. Session : 
Manages sessions.

##### 6. Presentation : 
provides data independence

##### 7. Application : 
interface point for user applications.

![[Pasted image 20250803103758.png]]

## Internetworking Devices : 
#### 1. Hub
Extends the span of a single LAN.
#### 2. Bridge / Layer-2 Switch : 
- connects two or more LANs together.
- Works at data link layer level. 

#### 3. Router / Layer-3 Switch : 
- Connects any combination of LANs and WANs. 
- Works at network layer level.



