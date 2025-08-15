## Fragmentation : 
###### Why needed ?
- The IP layer injects a packet into the datalink layer.
	- Not responsible for the reliable transport of these packets. 
- Each layer imposes some maximum size of packets, due to various reasons.
	- Called ***Maximum Transfer Unit (MTU).*** 
- Suppose a large packet travels through a network whose MTU is too small. 
	- Fragmentation (and also reassembly ) is required.
	- Each fragmentation is transmitted as a separate IP packet.
	- Fragmentation is typically done by routers.
- Fragments reassembled later : **transparent** or **non-transparent**.

## Transparent Fragmentation : 
- Fragmentation is **transparent** to subsequent networks, through which the packet pass.
- Basic concept : 
	- An oversized packet reaches a router, which breaks it up into fragments.
	- All fragments sent to the same exit router (say, R$_e$)
	- R$_e$ reassembles the fragments before forwarding to the next network.
- #### Why called transparent ?
	- Subsequent networks are not even aware that fragmentation had occurred.
- A packet may get fragmented several times. 
### Drawbacks : 
- All packets must be routed via the same exit router. 
- Exit router must know when all the pieces have been received. 
	- Either a **count** field or **end-of-packet** field must be stored in each packet. 
- Lots of overhead. 
	- A large packet may be fragmented and reassembled repeatedly. 
## Non-Transparent Fragmentation : 
- Fragmentation is not transparent to subsequent networks. 
- Basic concepts : 
	-  Packet fragments are not reassembled at any intermediate router. 
	- Each fragment is treated as an independent packet. 
	- The fragments are reassembled at the final destination host.
- IP uses this philosophy. 

#### Advantage : 
- Multiple exit routers may be used. 
- Higher throughput.
#### Drawback : 
- When a large packet is fragmented, overhead increases.
- Each fragment must have a header (minimum 20 bytes).
![[Pasted image 20250808230947.png]]

## What does IP do?
- To allow fragment reassembly at the final destination, IP uses the following fields in the header: 
	- Identification (16 bits)
		- A datagram id set by the source. 
	- Fragment offset (13 bits) 
		- Indicates where in the original datagram this fragment belongs to.
		- Specified in multiple of 8 bytes.
	- Flags (3 bits ) -- two flags are defined
		- **D bit** :: don't fragment; prevents fragmentation from taking place. 
		- **M bit** :: more fragment; specifies if this fragment is the last one in the original packet or not. 
	![[Pasted image 20250808231620.png]]
	