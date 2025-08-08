#### DNS: Remembering Addresses
- IP addresses are never memorized mostly.
- This is made possible due to Domain Name System (DNS).
- Maps domain names to IP addresses.
- Operates at application layer (layer 7)
- DNS traffic uses UDP port 53 by default and TCP port 53 as a default fallback.
- **A record**: Maps a hostname to one or more IP addresses.
- **AAAA record**: Similar to A record but for IPv6.
- **CNAME record (Canonical Name)**: Maps a domain name to another domain name.
- **MX record (Mail Exchange)**: Specifies the mail server responsible for handling emails for a domain.
- We can use `nslookup` to lookup IP addresses for websites.
#### WHOIS
- WHOIS has records of the registrants of the domain name buyers.
- There are privacy services that would hide your information from the whois servers.

#### HTTP(S)
- Browsers mainly use HTTP or HTTPS protocols.
- Relies on TCP.
- Commands for HTTP(S):
	- `GET`: Retrieves data frin a server.
	- `PUT`: Allows us to submit new data such as a form or a file.
	- `POST`: Creates a new resource on the server and to update and overwrite existing information.
	- `DELETE`: Deletes a specified file or information.
- Ports used:
	- Common: **80** and **443**
	- Less comon: **8080** and **8443**
- We can get contents from the server using the GET.
	- For example, to get the file.html from server, we can:
		- `GET /file.html HTTP/1.1`
#### FTP
- Used to transfer files.
- Achieves higher speeds than HTTP.
- Commands:
	- `USER`: inputs username
	- `PASS`: enter password
	- `RETR` (retrieve): download a file from the FTP server to the client
	- `STOR` (store): upload a file from clientto FTP server
- Port **21**. Data transfer uses another connection from client to the server.
- If available, we can use the **anonymous** user without a password.
#### Simple Mail Transfer Protocol (SMTP)
- How an email client talks with a mail server and how a mail server talks with another.
- An SMTP session analogy includes:
	- Go to a post office.
	- Greet employee.
	- Tell them the destination address.
	- Provide sender's information.
	- Hand them the package.
	- Sender might be asked to show your identity card.
- Commands for an SMTP session:
	- `HELO` or `EHLO`: initiate an SMTP session
	- `MAIL FROM`: sender's email address
	- `RCPT TO`: recipient's email address
	- `DATA`: indicates that the client will begin sending the contentof the email message
	- `.`: is sent on a line by itself to indicate the end of the email message
- SMTP server port: **25**
#### Post Office Protocol (POP3)
- Downloading an email to your local mail client, we use POP3 protocol.
- Client communicate with an email server and retrieve email messages.
- An email client uses SMTP to send emails and POP3 to retrieve them.
- Common POP3 commands:
	- `USER <username>`: idetifies the user
	- `PASS <password>`: provides user password
	- `STAT`: requests the number of messages and total size
	- `LIST`: lists all messages and their sizes
	- `RETR <message number>`: retrieves the specified messages
	- `DELE <message number>`: marks a message for deletion
	- `QUIT`: ends the POP3 session applyingchanges such as deletions
- Port: **110**
#### Internet Message Access Protocol (IMAP)
- POP3 works for single device.
- Sometimes, when we need to access email from various devices.
- We need a protocol to synchronize messages instead of deleting them after retrieving.
- IMAP is the protocol for that.
	- Synchronizes read, moved and deleted messages.
	- Convenient when checking emails from multiple clients.
	- Uses more storage as email is kepr on the server and synchronized accross email clients.
- Commands:
	- `LOGIN <username> <password>`: authenticates the user
	- `SELECT <mailbox>`: selects the mailbox folder to work with
	- `FETCH <mail number> <data item name>`: Example `fetch 3 body[]` to fetch message number 3, header and body
	- `MOVE <sequence set> <mailbox>`: moves the specified messages to another mailbox
	- `COPY <sequence set> <data item number>`: copies specified messages to another mailbox
	- `LOGOUT`: logs out
- Port: **143**

| Protocol | Transport Protocol | Default Port Number |
| -------- | ------------------ | ------------------- |
| TELNET   | TCP                | 23                  |
| DNS      | UDP or TCP         | 53                  |
| HTTP     | TCP                | 80                  |
| HTTPS    | TCP                | 443                 |
| FTP      | TCP                | 21                  |
| SMTP     | TCP                | 25                  |
| POP3     | TCP                | 110                 |
| IMAP     | TCP                | 14                  |
