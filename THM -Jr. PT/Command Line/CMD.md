- set: gives the path variable.
- ver: gives version of the windows.
- systeminfo: give information related to system.
- driverquery: queries the installed drivers.
- ipconfig: gives the IP of the system
	- ipconfig /all: gives information about all the network cards.
- ping: pings a website/IP
- tracert: traces the route of a given IP/web link.
- nslookup: looks up a host/domain and returns its IP address.
- netstat: displays current network connections and listening ports.
- cd: change directory
	- cd without parameters is equivalent to where am i.
- dir: displays child directories.
	- dir /a: displays all files and directories including hidden ones.
	- dir /s: display directories and sub-directory trees.
- mkdir: make directory
- rmdir: remove directory
- type: gives the content of a .txt file.
- copy: copies files
- move: moves files
- del / erase: deletes files
- tasklist: gives out a terminal based process manager. Similar to top in linux.
	- tasklist /?: gives help for the tasklist command.
	- tasklist /FI "imagename eq sshd.exe": lists tasks with a filter equal to processes for sshd.exe.
	- taskkill /PID "target_PID": kills the PID process for the target_PID.
- chkdsk: checks the file system and disk volumes for errors and bad sectors.
- driverquery: displays a list of installed device drivers.
- sfc /scannow: scans system files for corruption and repairs them if possible.
- /?: help