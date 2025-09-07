Internet Routing protocols broadly has two options : 
## 1. Connection-Oriented : 
- Network layer protocol first makes a connection.
- All packets delivered as per the connection.
## 2. Connection-Less : 
- Network layer protocol treats each packet independently.
- No relationship between packets.

###### - IP protocol uses connection-less approach for packet delivery. 

### Packet Delivery Options : 
##### 1. Direct Delivery : 
- Host to host. 
- Router to host. 

```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.9.7 - 15.41pm.drawing",
	"width": 998,
	"aspectRatio": 3.168253968253968
}
```
##### 2. Indirect Delivery : 
- Through one or more routers. 

```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.9.7 - 15.45pm.drawing",
	"width": 1122,
	"aspectRatio": 4.1402214022140225
}
```
### Routing Methods : 
- Several alternatives possible : 
	- Next-hop routing
	- Network-specific routing 
	- Host-specific routing 
	- Default routing 

#### 1. Next-hop routing : 
- routing tables based on next hop 
![[Pasted image 20250907155615.png]]
#### 2. Network-specific routing : 
- Routing table based on destination network address.
![[Pasted image 20250907155707.png]]
#### 3. Host-specific routing : 
- Can specify the address of a host. 
![[Pasted image 20250907155743.png]]
#### 4. Default routing : 
- Follow a default path if no match found.
![[Pasted image 20250907155822.png]]

## Types of Routing table 
#### 1. Static 
- Contains information inserted manually.
- Does not change with time. 
#### 2. Dynamic 
- Updated periodically depending on network condition. 
- Uses protocols like RIP, OSPF, BGP, etc. 

## Typical Fields in a Routing Table : 
- Subnet mask
- Destination IP address
- Next hop address
- Flags 
	- U : router is up and running 
	- G : Destination is in another network
	- H : host-specific address 
	- D : added by redirection
	- M : modified by redirection
- Interface.
![[Pasted image 20250907160139.png]]
### How to view the routing table ?
- On unix / Linux system : 
	 `netstat -r`
- On Windows system : 
	 `route print` 

## Types of Routing protocols 
#### 1. Interior : 
- Routing information protocol (RIP). 
- Open Shortest Path First (OSPF). 
#### 2. Exterior : 
- Border Gateway Protocol (BGP). 
## Autonomous System (AS)
- A set of routers and networks ***Managed by a single organisation*** is called AS. 
- The routers within the AS exchange information using a common routing protocols. 
- The AS graph is connected (in the absence of failure). 

- Every autonomous system is assigned a unique **AS number**. 
- Routing protocols within an AS and across different AS's can be different. 
	- Interior versus Exterior
![[Pasted image 20250907160835.png]]
## Which class of protocols to use ?
- #### Interior : 
		RIP or OSPF 
- #### Exterior : 
		BGP
### Routing Information Protocols (RIP). 
- It is an interior routing protocol. 
- Routers within an autonomous system exchange messages. 
	- Distance vector routing using hop count. 
	- Table entries updated using values received from neighbors. 
	- Maintain timers to detect failed links 
	- Used in first generation ARPANET. 
### Problems with RIP 
- Slow convergence for larger networks. 
- If a network becomes inaccessible, it may take long time for all other routing tables to know this. 
	- After a number of message transfers. 
	- A drawback of routing table updation using distance vectors.
- Routing loops may take a long time to be detected. 
	- Counting to infinity problem. 
- Too much bandwidth consumed by routing updates. 
### Open Shortest Path First (OSPF). 
- Widely used as the interior routing protocol in TCP/IP networks. 
	- Updates routing tables based on link state advertisements. 
- Basic concept : 
	- Computes a route that incurs the least cost. 
		- User configurable: delay, data rate, cost, etc.
	- Each Router maintains a database.
		- Topology of the autonomous system to which the router belongs. 
		- Vertices and edges. 
- Two Types of vertices : 
	- Router
	- Network
- Two Types of (weighted ) edges : 
	- Two router connected to each other by direct point-to-point link.
	- A router is directly connected to a network. 
- A router calculates the least-cost path to all destination networks.
	- Using Dijkstra's algorithm.
	- Only the next hop to the destination is used in the forwarding process. 
- In the steady state.
	- All routers know the same network topology. 
	- "Hello" packets sent every 10 seconds (configurable) to neighbors. 
	- Link State Advertisement (LSA) flooded initially from each router.
	- Absence of "Hello" packet for 40 seconds indicate failure of neighbor.
		- Causes LSA to be flooded again.
	- LSAs re-flooded every 30 minutes anyway.
![[Pasted image 20250907162046.png]]
#### OSPF Packets : 
- Packet types : 
	- **Hello** : check if neighbor is up
	- **Database Description** : synchronise database at beginning. 
	- **Link State Request** : request specific LSA.
	- **Link State Update** : LSAs flooded.
	- **Link State Acknowledgement** : flooded LSAs are explicitly ack-ed -reliable flooding. 
- Authentication type : 
	- Cleartext
	- Encrypted (MD5 Hash, others possible)