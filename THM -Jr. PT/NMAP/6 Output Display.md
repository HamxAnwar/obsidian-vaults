Two main features:
- Showing additional information while a scan takes place.
- Choosing the file format to save the scan report.
#### Verbosity and Debugging
- Sometimes the scan takes alot of time to complete and we don't know whats going on.
- We might also want to know what is going on.
- `-v`: verbose output.
- for example:
	- ![[Pasted image 20250706114752.png]]
	- ![[Pasted image 20250706114820.png]]
	- We can also increase the verbosity level by
		- `-vv` or `-v2`
		- `-vvv` or `-v3`
		- `-vvvv` or `-v4`
	- We can also increase the verbosity after the scan is started by pressing **v**
	- `-d`: If the verbosity isn't enough still, we can go for debugging level output, starting from `-d1` to `-d9`.
#### Saving Scan Report
- `-oN <filename>` - Normal output
- `-oX <filename>` - XML output
- `-oG <filename>` - grepable output (useful for `grep` and `awk`)
- `-oA <basename>` - Output in all major formats