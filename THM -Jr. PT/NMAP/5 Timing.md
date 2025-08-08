- Nmap provides various options to control timing and speed.
- Scanning at normal or default speeds might trigger an IDS or other security solutions.
- Nmap gives you 6 timing tempelates.
	- paranoid (0)
	- sneaky (1)
	- polite (2)
	- normal (3) (default)
	- aggressive (4)
	- insane (5)
- We can pick the timing template by its name or number.
- `-T0`, `-T 0` or `-T paranoid`: opt for the slowest timing.
- We can also introduce parallel service probes.
	- `--min-parallelism <numprobes>`
	- `--max-parallelism <numprobes>`
- By default, Nmap determines parallel probes automatically.
	- If the network is performing poorly, the probes might drop to one.
	- If the network is performing better, the probes might increase to several hundreds.
- We can also specify the rate, Nmap sends packets at:
	- `--min-rate <number>`
	- `--max-rate <number>`
	- The number is the number of packets per second.
	- The specified rate applies to the whole scan and not to a single host.
- If we have slow host or slow network connections, we can tell how much time are we willing to wait:
	- `--host-timeout <time>`

#### Summary
|Option|Explanation|
|---|---|
|`-T<0-5>`|Timing template – paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), and insane (5)|
|`--min-parallelism <numprobes>` and `--max-parallelism <numprobes>`|Minimum and maximum number of parallel probes|
|`--min-rate <number>` and `--max-rate <number>`|Minimum and maximum rate (packets/second)|
|`--host-timeout`|Maximum amount of time to wait for a target host|
