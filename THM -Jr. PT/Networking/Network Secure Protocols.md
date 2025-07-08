- Important online transactions are risky without ensuring confidentiality, integrity and authenticity.
- Transport Layer Security (TLS) is also added to the existing protocols to protect communication CIA triad.
- Transport Layer Security (TLS) is added to existing protocols to protect communication confidentiality, integrity, and authenticity. Consequently, HTTP, POP3, SMTP, and IMAP become HTTPS, POP3S, SMTPS, and IMAPS, where the appended “S” stands for Secure. We will examine these protocols and the benefits we reaped from TLS.
#### Transport Layer Security (TLS)
- In the previous days, many of the data, including usernames and passwords for various services, was sent in plain text.
- Attackers could easily look at it and steal these data while being in promiscuous mode.
- Netscape Communications developed **SSL (Secure Sockets Layer)**.
	- Released the first public version in 1995 as SSL 2.0.
- IETF developed **TLS (Transport Layer Security)** in 1999.
	- Upgrade to SSL 3.0.
	- Offered various improved security measures.
	- TLS 1.3 was released 2018.
- SSL and TLS are both cryptographic protocols.
- Allows secure communication (confidentiality and integrity) between a client and a server over an insecure network.
- With the simple addition of TLS, many protocols have become secure such as:
	- HTTP : HTTPS
	- DNS : DoT (DNS over TLS)
	- MQTT : MQTTS
	- SIP : SIPS
- Every appended 'S' stands for secure.
- How TLS works?
	- Every server / client needs a signed TLS certificate to identify itself.
	- The server administrator creates a Certificate Signing Request (CSR).
	- The CSR is submitted to a Certificate Authority (CA).
	- The CA verifies the CSR and issues a digital certificate.
	- This certificate is signed.
	- Once the signed certificate is received, it can be used to identify the server / client to others, who can confirm the validity of the signature.
	- For a host to validate the signed certificate, the certificates of the signing authority need to be installed on the host.
	- Similar to recognizing the stamp of various authorities.
	- Generally, getting a certificate signed requires the payment of an annual fee.
	- **Let's Encrypt** allows us to get our certificates signed for free.
	- Sometimes, the certificates are self signed.
		- A self signed certificate cannot prove the server's authenticity as no third party has confirmed it.
#### HTTPS
- HTTP
	- Unsecured
	- Port 80
	- Sends traffic in clear text
	- Steps for HTTP request.
		- Resolve domain name to IP
		- Establish a TCP three way handshake with the target server
		- Communicate using HTTP protocol.
	- ![[Pasted image 20250705112938.png]]
	- (1) Three way handshake 
	- (2) Data sending
	- (3) Termination of TCP connection.
- HTTP over TLS (HTTPS)
	- Steps for HTTPS request
		- Establish three way handshake for TCP connection.
		- Establish TLS session.
		- Communicate using HTTP protocol.
	- ![[Pasted image 20250705113143.png]]
	- (1) Three way handshake for TCP connection
	- (2) Several packets exchange to negotiate the TLS protocol.
		- 1 and 2 are where TLS negotiation and establishment take place.
	- (3) HTTP application data exchange.
	- Port: **443**
	- The packets, if intercepted, are encrypted and the hacker would only see gibberish.
	- To know the content, we need to acquire the encryption key.
	- The TLS never changes the under laying protocols but only encrypts the data being transferred.
#### SMTPS, POP3S and IMAPS
- Almost all points in the above HTTPS applies to the SMTPS, POP3S and IMAPS.

| **Protocols** | Default Port | Default Secure Port |
| ------------- | ------------ | ------------------- |
| HTTP / HTTPS  | 80           | 443                 |
| SMTP / SMTPS  | 25           | 465 & 587           |
| POP3 / POP3S  | 110          | 995                 |
| IMAP / IMAPS  | 143          | 993                 |

#### Secure Shell (SSH) Protocol
- Telnet is risky and insecure.
- Tatu Ylönen developed SSH
	- Released SSH-1 in 1995 as freeware.
	- SSH-2 released in 1996.
	- OpenBSD developers released openSSH in 1999.
		- Open source implementation of SSH.
		- Offers several benefits:
			- **Secure authentication:** Password based authentications, public key and two-factor authentication.
			- **Confidentiality:** End to end encryption, protecting against eavesdropping. Notifies of new server keys to protect against man-in-the-middle attacks.
			- **Integrity:** Cryptography also protects the integrity of the data.
			- **Tunneling:** Creates a secure "tunnel" to route other protocols through SSH. Generates a VPN-like connection.
			- **X11 Forwarding:** Connecting to a unix-like system with a GUI, SSH allows to usethe graphical application over the network.
	- **Usage:** `ssh username@hostname/IP`
	- `-X` : This argument is required to support running graphical interfaces. E.g. `ssh username@hostname -X`

| Protocol | Port |
| -------- | ---- |
| TELNET   | 23   |
| SSH      | 22   |
#### SFTP and FTPS
- **SFTP:** SSH File Transfer Protocol
	- Allows secure file transfer.
	- Part of SSH protocol suite.
	- Shares port number 22.
	- `sftp username@hostname`
	- Commands:
		- `get filename` - download file
		- `put filename` - upload file
	- SFTP commands are Unix-like and can differ from FTP commands.
- **FTPS:** File Transfer Protocol Secure
	- Uses TLS
	- Requires certificate setup
	- Can be tricky to allow over strict firewalls as it uses separate connections for control and data transfer.

| Protocol | Ports |
| -------- | ----- |
| FTP      | 21    |
| FTPS     | 990   |
#### Virtual Private Network (VPN)
- A company can connect all its offices, at different geographical locations, and its site to its main branch.
	- Devices can utilize shared resources.
- The above can be achieved using VPN.
- Internet design focuses on the delivery of packets using TCP/IP protocol suite.
	- TCP has built-in mechanisms to detect whether a packet is received at the receiver end or not.
	- There is no mechanism to ensure that all the data entering or leaving a computer is secure from alteration and disclosure.
	- Almost all companies require private information exchange.
	- The main requirements to achieve the above are to set up a VPN (server and client) and internet connectivity.
	- ![[Pasted image 20250705130840.png]]
	- In the above diagram, VPN setup is shown.
	- VPN server is in the main branch while VPN clients in the remote branches connect to it.
		- VPN client will encrypt the traffic and pass it to main branch via established VPN tunnel (in blue).
		- The VPN traffic is limited to blue lines while the green lines would carry the decrypted VPN traffic.
	- Once a VPN connection is established, our internet traffic would move through that VPN tunnel.
	- Consequently, when accessing a web server, etc., they will see the VPN server's IP instead of our public IP.
	- VPN can be utilized to connect to prohibited sites as the ISP would only see the encrypted traffic.
- **Issues in VPN**
	- Some VPNs gives access to a virtual private network but doesn't route our traffic through it.
	- Some VPNs might leak our actual IP address.
	- Depending on why we are using VPNs, we mightrun some more tests, such as DNS leak test.