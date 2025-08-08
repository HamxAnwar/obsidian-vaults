#### OS Detection
- `-O`: to detect OS on the scanned host.
- Not perfect OS detector but is there one out there?
#### Service and Version Detection
- We have detected several open ports and want to know what services and versions are listening on them.
- `-sV`: enables version detection for the services.
- To do all versions like `-O` and `-sV`, etc, we can do `-A` for detect all.
	- Enables OS detection, version scanning, and traceroute, among other things.
#### Forcing the Scan
- Running our port scan, such as using `-sS`, there is a possibility that the target host does not reply during the host discovery phase (e.g. a host doesn’t reply to ICMP requests).
	- Nmap marks this host as down and won’t launch a port scan against it.
	- `-Pn`: treat all hosts as online and port scan every host, including those that didn’t respond during the host discovery phase.
#### Summary

| Option | Explanation                                          |
| ------ | ---------------------------------------------------- |
| `-O`   | OS detection                                         |
| `-sV`  | Service and version detection                        |
| `-A`   | OS detection, version detection, and other additions |
| `-Pn`  | Scan hosts that appear to be down                    |
