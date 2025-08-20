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
## Basic IP addressing 
- Each host connected to the internet is identified by a unique  IP address.
- An IP address is a 32-bit quantity
	-  Expressed as a dotted decimal notation W.X.Y.Z, Where dots are used to separate each of these four octets of the address.
	- Consists of two logical parts : 
		- A network number
		- A host number
	- This partition defines the ***IP address classes.*** 
![[Pasted image 20250820071430.png]]

# Hierarchical Addressing
- A computer on the internet is addressed using a two-tuple: 
	- The network number
		-  Assigned and managed by central authority.
	- The host number 
		-  Assigned and managed by local network admin.
- When routing a packet to the destination network, only the network number is looked at. 

## IP address classes 
- There are five defined IP address classes. 
	- Class A   UNICAST
	- Class B   UNICAST 
	- Class C   UNICAST
	- Class D   MULTICAST
	- Class E   RESERVED
- Identified by the first few bits in the IP address.
- There also exists some special purpose IP addresses.
- The class-based addressing is also known as the ***classful model*** . 


#### Class A address : 

| 0   | Network | Host | Host | Host |
| --- | ------- | ---- | ---- | ---- |

- **Network bits :** 7
				Number of networks = 2$^7$ - 1 = 127
- **Host bits :** 24
				Number of hosts = 2$^{24}$ - 1 = 16,777,214
- **Address range :** 
	- 0.0.0.0 to 127.255.255.255

---
#### Class B address : 

| 0   | Network | Network | Host | Host |
| --- | ------- | ------- | ---- | ---- |

- **Network bits :** 14
				Number of networks = 2$^{14}$ - 1 = 16,383
- **Host bits :** 16
				Number of hosts = 2$^{16}$ - 1 = 65,534
- **Address range :** 
	- 128.0.0.0 to 191.255.255.255

--- 
#### Class A address : 

| 0   | Network | Host | Host | Host |
| --- | ------- | ---- | ---- | ---- |

- **Network bits :** 7
				Number of networks = 2$^7$ - 1 = 127
- **Host bits :** 24
				Number of hosts = 2$^{24}$ - 1 = 16,777,214
- **Address range :** 
	- 0.0.0.0 to 127.255.255.255
---
#### Class C address : 

| 0   | Network | Network | Network | Host |
| --- | ------- | ------- | ------- | ---- |

- **Network bits :** 21
				Number of networks = 2$^{21}$ - 1 = 2,097,151
- **Host bits :** 24
				Number of hosts = 2$^{8}$ - 1 = 254
- **Address range :** 
	- 192.0.0.0 to 223.255.255.255

---
#### Class D address : 

| 0   | Network | Network | Network | Network |
| --- | ------- | ------- | ------- | ------- |

- **Address range :** 
	- 224.0.0.0 to 239.255.255.255


## Special Purpose IP addresses 
- Reserved for private use
	- 10.x.x.x                          (class A)
	- 172.16.x.x - 172.31.x.x  (class B)
	- 192.168.x.x                    (class C)
- Loopback / local address
	- 127.0.0.0 - 127.255.255.255
- Default network 
	-  0.0.0.0
- Limited broadcast 
	- 255.255.255.255
### Some Conventions 
- Within a particular network (Class A, B or C), the first i.e **all 0** and last i.e **all 1** addresses serve special functions.
	- The fist address represents the ***Network number***. 
		- For example, 118.0.0.0
	- The last address represents the directed ***broadcast address*** of the network.
		- For example, 118.255.255.255

