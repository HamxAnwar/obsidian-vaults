![[Dockerfile]]

- For linux
	- dialout group: access serial ports.
	- docker group: run containers.
	- UID: user id.
		- A root uid is always 0.
		- The default user uid is always 1000.
	- GID: group id.
		- A root gid is always 0.
		- The default user gid is always 1000.
	- We can use different usernames then our system's username since it will have the same uid.
	- We can use the terminal command to #run_a_container_with_a_specific_user.
	- The entrypoint file is as under:

![[entrypoint.sh]]

- After the entry point, it takes the argument as ```bash``` and runs it on the start.
- We can provide other arguments when we run the image.
- We can use ```WORKDIR``` argument inside the dockerfile to specify the working directory, i.e. the directory, the containers starts with.