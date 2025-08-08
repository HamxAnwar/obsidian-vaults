- Many other ways exist to filter packet.
- Packets can be filtered based on specified lengths.
	- `greater LENGTH` or `less LENGTH`
	- Both the above commands are greater than or equal to and less than or equal to.
- We also have pcap-filter. There exist multiple filters. For now, we will look at the TCP flags based filtering.
#### Header Bytes
- The purpose here is to filter packets based on the header bytes.
- Using pcap-filter, Tcpdump allows to refer to the contents of any byte in the header using the following syntax `proto[expr:size]`, where:
	- `proto` refers to the protocol. For example, `arp`, `ether`, `icmp`, `ip`, `ip6`, `tcp`, and `udp`.
	- `expr` indicates the byte offset, where `0` refers to the first byte.
	- `size` indicates the number of bytes that interest us, which can be one, two, or four. It is optional and is one by default.
- Consider the following two examples:
	- `ether[0] & 1 != 0`
		- Takes the first byte in the Ethernet header
		- The decimal number 1 (i.e., `0000 0001` in binary)
		- Applies the `&` (the And binary operation).
		- It will return true if the result is not equal to the number 0 (i.e., `0000 0000`).
		- The purpose of this filter is to show packets sent to a multicast address.
		- A multicast Ethernet address is a particular address that identifies a group of devices intended to receive the same data.
	- `ip[0] & 0xf != 5`
		- Takes the first byte in the IP header
		- Compares it with the hexadecimal number F (i.e., `0000 1111` in binary).
		- Returns true if the result is not equal to the (decimal) number 5 (i.e., `0000 0101` in binary).
		- The purpose of this filter is to catch all IP packets with options.
- We can use `tcp[tcpflags]` to refer to the TCP flags field.
- The following TCPflags are available to compare with:
	- `tcp-syn` TCP SYN (Synchronize)
	- `tcp-ack` TCP ACK (Acknowledge)
	- `tcp-fin` TCP FIN (Finish)
	- `tcp-rst` TCP RST (Reset)
	- `tcp-push` TCP Push
Based on the above, we can write:
- `tcpdump "tcp[tcpflags] == tcp-syn"` to capture TCP packets with **only** the SYN (Synchronize) flag set, while all the other flags are unset.
- `tcpdump "tcp[tcpflags] & tcp-syn != 0"` to capture TCP packets with **at least** the SYN (Synchronize) flag set.
- `tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"` to capture TCP packets with **at least** the SYN (Synchronize) **or** ACK (Acknowledge) flags set.

You can write your own filter depending on what you are looking for.