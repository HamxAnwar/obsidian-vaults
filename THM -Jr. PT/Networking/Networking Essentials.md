#### Dynamic Host Configuration Protocol (DHCP)
- Devices connect to the network and automatically gets configured.
	- How does that happen?
- When we want to access any network, we least require:
	- IP address / subnet mask
	- Router address (gateway)
	- DNS server
- It is better to manually configure servers with the above.
	- They do not switch networks.
	- They are mostly configured on static IPs.
- But manually configuring IPs for mobile devices could result in IP conflict between two devices.
- Dynamic Host Configuration Protocol (DHCP) resolves the above issue.
	- Application level protocol
	- Uses UDP
	- Server listens on port 67
	- Client sends from port 68
	- Devices are usually configured to use DHCP by default
- DHCP uses four steps:
![[Pasted image 20250703223810.png]]

- DORA
	- **DHCP Discover**: Client broadcasts DHCP discover message.
	- **DHCP Offer**: Server responds with DHCP offer with an IP address available for the client to accept.
	- **DHCP Request**: Client responds with a DHCP request to indicate that it has accepted the IP.
	- **DHCP Acknowledge**: Server responds with acknowledgement (DHCP ack) to confirm the offered IP address is now assigned to the said client.
![[Pasted image 20250703224247.png]]

- A DHCP server provides particularly:
	- A leased IP address.
	- The gateway to route packets outside of local network.
	- A DNS server to resolve domain names.
#### Address Resolution Protocol (ARP)
- Bridges layer 3 addressing to layer 2 addressing.
- Layer 3 (IP link) to layer 2 (Data link)
	- An IP packet is encapsulated within a data link frame
- Two common data link layers used are Ethernet (IEEE 802.3) and WiFi (IEEE 802.11).
- On the same network, devices send data link layer frame.
- Although it knows the IP address, it needs to look up the target's MAC address to create the proper data link header.
- Devices on the same network doesn't need to know the MAC addresses of other device all the time but only while communicating.
- Everything revolves around IP addresses.
- ARP helps find the MAC of devices on a network.
- For example:
	- A host with the IP address 192.168.66.89 wants to communicate with another system with the IP address 192.168.66.1.
	- It sends an ARP request, asking the host with the IP 192.168.66.1 to respond.
	- The ARP request uses senders MAC and sends the request to broadcast MAC address ff:ff:ff:ff:ff:ff.
	- The ARP reply is sent by the address 192.168.66.1 with its MAC address.
	- From this point, the two hosts can exchange data link frames.
	- An ARP Request or ARP Reply is not encapsulated within a UDP or even IP packet; it is encapsulated directly within an Ethernet frame.
	- ARP is layer 2 because it deals with MAC addresses.
#### Internet Control Message Protocol (ICMP)
- Mainly used for network diagnostics and error reporting.
- Two main commands use ICMP:
	- **ping**: 
		- Uses ICMP to test connectivity to a target system.
		- Measures round trip time (RTT).
		- ping command sends the **ICMP echo request** (ICMP type 8).
		- The computer on the receiving end responds with an **ICMP echo reply** (ICMP type 0).
		- Not getting a reply:
			- Target system might be offline.
			- Firewall might block the packets.
			- etc.
	- **tracert / traceroute**: 
		- Uses ICMP to discover the route from host to the internet.
		- Internet Protocol has a field called Time-to-live (TTL).
			- Tells through how many routers, a packet could move through before getting dropped.
			- Every time, the packet gets to a router, the field is decremented.
			- TTL = zero, packet is dropped and the router sends **ICMP Time Exceeded message** (ICMP Type 11).
			- Sometimes, the ICMP Time Exceeded message doesn't reach us
				- Gets blocks
				- Router doesn't respond and drops the packet.
		- The traversed route may change when we rerun the command `traceroute`.
#### Routing
- Multiple routers between devices on the internet.
- Which path to be selected to route the packets.
- Various algorithms
	- **Open Shortest Path First (OSPF)**
		- Allows routers to share information about the network topology and calculate the most efficient paths for data transmission.
		- Routers exchange updates about the state of their connected links and networks.
		- Each router has a complete map of the network.
	- **Enhanced Interior Gateway Routing Protocol (EIGRP)**
		- CISCO proprietary routing protocol.
		- Combines aspects of various routing protocols.
		- Sends the router connections with the cost (bandwidth and delay) to get most efficient path.
	- **Border Gateway Protocol (BGP)**
		- Primary routing protocol used on the internet.
		- ISPs can exchange routing information and establish paths.
		- Helps ensure data can be routed efficiently across the internet, even when traversing multiple networks.
	- **Routing Information Protocol (RIP)**
		- Simple routing protocol used in small networks.
		- Routers share information about:
			- The networks they can reach.
			- The number of hops (routers) required to get there.
		- Each router builds a routing table, choosing the routes with the fewest hops to reach each destination.
#### Network Address Translation (NAT)
- IPv4 is closing down.
- To make the IPs reusable, we use NAT.
- One public IP address to provide internet access to many private IP addresses.
- Routers that support NAT must find a way to track ongoing connections.
- Maintains a table translating network addresses between internal and external networks.
	- Internal network : private IP range
	- External network : a public IP address
![[Pasted image 20250704002445.png]]

- Remember, we are limited by the ports.
	- If a router has unlimited processing power, it can still still maintain only 65535 simultaneous TCP connections.