- We are not discussing basic concepts such as IP address, subnet, OSI model, TCP/IP model, etc.
### Encapsulation
- Every layer attaches (encapsulates) a header or in some cases, trailer to the data it receives before sending it to the layer below.
- Encapsulation includes:
	- **Application data**: It all starts when the user inputs the data they want to send into the application. For example, you write an email or an instant message and hit the send button. The application formats this data and starts sending it according to the application protocol used, using the layer below it, the transport layer.
	- **Transport protocol segment or datagram**: The transport layer, such as TCP or UDP, adds the proper header information and creates the **TCP segment** (or UDP **datagram**). This segment is sent to the layer below it, the network layer.
	- **Network packet**: The network layer, i.e. the Internet layer, adds an IP header to the received TCP segment or UDP datagram. Then, this **IP packet** is sent to the layer below it, the data link layer.
	- **Data link frame**: The Ethernet or WiFi receives the IP packet and adds the proper header and trailer, creating a **frame**.

![[Pasted image 20250703212006.png]]

### Telnet
- Similar to SSH but uses any port that uses TCP.
- In the attached VM, we looked at
	- Echo server
	- Daytime server
	- Web (HTTP) server
- Echo and daytime servers are considered security risks.
- We noticed that the daytime server stops after giving time at port 13.
- To request a web page using `telnet`. After connecting to port 80, we need to issue the command `GET / HTTP/1.1` and identify the host where anything goes, such as `Host: telnet.thm`. Next, you need to press `Enter` twice so your last input line is a blank line. The output below shows the exchange.