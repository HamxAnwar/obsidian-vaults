#### Specify the Network Interface
- First thing to decide is the interface to listen to.
- `tcpdump -i <INTERFACE>`
	- To listen to all interfaces
		- `tcpdump -i any`
#### Save captured packets
- Captured packets are big and should be able to view the captures later.
- `tcpdump -w <FILE>`
	- File extension: **.pcap**
	- No data scrolling
	- Can see the saved file later in wireshark
#### Read Captured Packets from a File
- We can also view captured packets from saved file
	- `tcpdump -r <FILE>`
	- Useful for learning about protocol behaviour.
	- We can capture network traffic over a suitable time frame to inspect a specific protocol, then read the captured file while applying filters to display the packets we are interested in.
	- It might be a packet capture file that contains a network attack that took place, and we inspect it to analyze the attack.
#### Limit the Number of Captured Packets
- Specify the number of packets to capture 
	- `-c COUNT`
	- Without specifying a count, the packet capture will continue till we interrupt it.
#### Don’t Resolve IP Addresses and Port Numbers
- Tcpdump will resolve IP addresses and print friendly domain names where possible.
- To avoid making such DNS lookups, we can use the `-n` argument.
- Similarly, if we don’t want port numbers to be resolved, such as `80` being resolved to `http`, we can use the `-nn` to stop both DNS and port number lookups.

The following image captured and displayed five packets without resolving the IP addresses.

```
user@TryHackMe$ sudo tcpdump -i ens5 -c 5 -n
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode

listening on ens5, link-type EN10MB (Ethernet), capture size 262144 bytes

08:55:18.989213 IP 10.10.117.2.22 > 10.11.81.126.53378: Flags [P.], seq 2888580014:2888580210, ack 771262362, win 922, options [nop,nop,TS val 3216251159 ecr 33295823], length 196

08:55:18.989446 IP 10.10.117.2.22 > 10.11.81.126.53378: Flags [P.], seq 196:424, ack 1, win 922, options [nop,nop,TS val 3216251159 ecr 33295823], length 228

08:55:18.989576 IP 10.10.117.2.22 > 10.11.81.126.53378: Flags [P.], seq 424:620, ack 1, win 922, options [nop,nop,TS val 3216251159 ecr 33295823], length 196

08:55:18.989839 IP 10.10.117.2.22 > 10.11.81.126.53378: Flags [P.], seq 620:816, ack 1, win 922, options [nop,nop,TS val 3216251159 ecr 33295823], length 196

08:55:18.989958 IP 10.10.117.2.22 > 10.11.81.126.53378: Flags [P.], seq 816:1012, ack 1, win 922, options [nop,nop,TS val 3216251159 ecr 33295823], length 196

5 packets captured
6 packets received by filter
0 packets dropped by kernel        
```
#### Produce (More) Verbose Output
- More details about the packets:
- `-v`: Produce a slightly more verbose output.
	- will print “the time to live, identification, total length and options in an IP packet” among other checks.
- `-vv`: Produce more verbose output.
- `-vvv`: Provide even more verbosity.

| Command                | Explanation                                                       |
| ---------------------- | ----------------------------------------------------------------- |
| `tcpdump -i INTERFACE` | Captures packets on a specific network interface                  |
| `tcpdump -w FILE`      | Writes captured packets to a file                                 |
| `tcpdump -r FILE`      | Reads captured packets from a file                                |
| `tcpdump -c COUNT`     | Captures a specific number of packets                             |
| `tcpdump -n`           | Don’t resolve IP addresses                                        |
| `tcpdump -nn`          | Don’t resolve IP addresses and don’t resolve protocol numbers     |
| `tcpdump -v`           | Verbose display; verbosity can be increased with `-vv` and `-vvv` |