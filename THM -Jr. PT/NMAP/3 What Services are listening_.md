- We want to discover what services are listening to and on which ports.
- There could be various services including web servers on TCP port 80 or 443 or DNS services using UDP or TCP on port 53.
#### Connect Scan
- `-sT`: Nmap will try to connect to every TCP port using the TCP three-way handshake.
	- If connection is established, the TCP port is open, Nmap tears down the connection 
	- In the screenshot below, our scanning machine has the IP address `192.168.124.148` and the target system has TCP port 22 open and port 23 closed. In the part marked with 1, you can see how the TCP three-way handshake was completed and later torn down with a TCP RST-ACK packet by Nmap. The part marked with 2 shows a connection attempt to a closed port, and the target system responded with a TCP RST-ACK packet.
	- ![[Pasted image 20250706105559.png]]
#### SYN Scan (Stealth)
- `-sS`: SYN (Stealth) scan
	- Instead of completing a three-way handshake, the SYN scan only executes the first step:
		- it sends a TCP SYN packet.
		- The TCP three-way handshake is never completed.
		- Advantage
			- Expected to lead to fewer logs as the connection is never established.
			- Considered a relatively stealthy scan.
	- In the screenshot below, we scan the same system with port 22 open. The part marked with 1 shows the listening service replying with a TCP SYN-ACK packet. However, Nmap responded with a TCP RST packet instead of completing the TCP three-way handshake. The part marked with 2 shows a TCP connection attempt to a closed port. In this case, the packet exchange is the same as in the connect scan.
	- ![[Pasted image 20250706105941.png]]
#### Scanning UDP Ports
- Why scan UDP ports?
	- DNS
	- DHCP
	- NTP (Network Time Protocol)
	- SNMP (Simple Network Management Protocol)
	- VoIP (Voice over IP)
- Since it doesn't require three-way handshake, it doesn't require to close connection.
- `-sU`: Scan UDP ports.
#### Limiting the Target Ports
- Nmap scans the most common 1000 ports by default.
- `-F`: Fast mode, scans the 100 most common ports.
- `-p[range]` allows to specify a range of ports to scan.
	- `-p10-1024`: scans from port 10 to port 1024
	- `-p-25`: scan all the ports between 1 and 25.
	- `-p-`: scans all the ports, equivalent to `-p1-65535`.

#### Summary

| Option      | Explanation                                          |
| ----------- | ---------------------------------------------------- |
| `-sT`       | TCP connect scan – complete three-way handshake      |
| `-sS`       | TCP SYN – only first step of the three-way handshake |
| `-sU`       | UDP scan                                             |
| `-F`        | Fast mode – scans the 100 most common ports          |
| `-p[range]` | Specifies a range of port numbers                    |
| `-p-`       | Scans all the ports                                  |
