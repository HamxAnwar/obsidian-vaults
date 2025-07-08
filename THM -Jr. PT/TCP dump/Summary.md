The table below offers a summary of the command line options that we covered.

| Command                                      | Explanation                                                           |
| -------------------------------------------- | --------------------------------------------------------------------- |
| `tcpdump host IP` or `tcpdump host HOSTNAME` | Filters packets by IP address or hostname                             |
| `tcpdump src host IP` or                     | Filters packets by a specific source host                             |
| `tcpdump dst host IP`                        | Filters packets by a specific destination host                        |
| `tcpdump port PORT_NUMBER`                   | Filters packets by port number                                        |
| `tcpdump src port PORT_NUMBER`               | Filters packets by the specified source port number                   |
| `tcpdump dst port PORT_NUMBER`               | Filters packets by the specified destination port number              |
| `tcpdump PROTOCOL`                           | Filters packets by protocol; examples include `ip`, `ip6`, and `icmp` |
Consider the following examples:
- `tcpdump -i any tcp port 22` listens on all interfaces and captures `tcp` packets to or from `port 22`, i.e., SSH traffic.
- `tcpdump -i wlo1 udp port 123` listens on the WiFi network card and filters `udp` traffic to `port 123`, the Network Time Protocol (NTP).
- `tcpdump -i eth0 host example.com and tcp port 443 -w https.pcap` will listen on `eth0`, the wired Ethernet interface and filter traffic exchanged with `example.com` that uses `tcp` and `port 443`. In other words, this command is filtering HTTPS traffic related to `example.com`.