#### Filtering by Host
- `tcpdump host <IP / HOSTNAME>`
	- Will limit the search to the single IP / hostname.
- `tcpdump src host <IP / HOSTNAME>`
	- To filter to the source IP / hostname.
- `tcpdump dst host <IP / HOSTNAME>`
	- To filter to the destination IP / hostname.
#### Filtering by Port
- We can also filter by port.
	- `port 53`: limits the traffic capture on port 53.
	- `src port <number>`: Limit to the source port.
	- `dst port <number>`: Limit to the destination port.
#### Filtering by Protocol
- We can filter by protocol.
- We can limit capture by just specifying the specific protocol
	- `ip`
	- `ip6`
	- `udp`
	- `tcp`
	- `icmp`
#### Logical Operators
- Three logical operators that can be handy:
	- `and`: Captures packets where both conditions are true.
		- For example: `tcpdump host 1.1.1.1 and tcp`
		- captures tcp traffic with host 1.1.1.1
	- `or`: Captures packets when either one of the conditions is true.
		- For example, `tcpdump udp or icmp`
		- captures UDP or ICMP traffic.
	- `not`: Captures packets when the condition is not true.
		- For example, `tcpdump not tcp`
		- captures all packets except TCP segments
		- we expect to find UDP, ICMP, and ARP packets among the results.