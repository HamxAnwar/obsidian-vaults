- Docker uses apps and libraries necessary to run a certain system.
- It shares the host's kernel and the hardware resources.
![[Pasted image 20231009225128.png]]
- Docker has its own cache so we include ```--no-cache-dir``` in our pip command inside our dockerfile.
#### Important topics covered in [[Docker basics]]
- Installation
- Images
- Containers
- Commands
- VSCode for Docker
- Compose
- Docker networks
- Docker Swarm vs Kubernetes
- Docker Swarm
#### Why these Notes?
- These notes are to give a overview of docker as well as the end result is to make a docker container running ROS-noetic for my [[Thesis work]].
	- Image name: ros_thesis_image
	- Container name: thesis_container
	- Container type: ROS Noetic
	- Volume name: ros_thesis
	- Workspace name: event_ws
#### Resources
- https://www.youtube.com/playlist?list=PLunhqkrRNRhaqt0UfFxxC_oj7jscss2qe
- https://www.youtube.com/watch?v=0H2miBK_gAk
- https://www.youtube.com/watch?v=DM65_JyGxCo
- https://github.com/docker/awesome-compose
- https://www.youtube.com/watch?v=PSbFK1y9PHs
- https://www.youtube.com/watch?v=bKFMS5C4CG0
- https://www.youtube.com/watch?v=thb21co4Gw0#
- https://www.youtube.com/watch?v=W-DD3QPlRHo 
- PDF file: ![[thesisbot.pdf]]