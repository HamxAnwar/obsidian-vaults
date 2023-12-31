- What is Kubernetes?
	- Open source orchestration system for automating, deployment, scaling and management of containerized applications.
	- Made by google.
	- Launched in 2014.
	- Also known as K8s (8 alphabets between K and S).
	- It is designed for massive scaling of containers such as millions of containers.
	- It can run anywhere from an SBC to servers and cloud.
- Why to use it?
	- What if we have hundreds or thousands of containers with many apps?
	- We need to run many containers.
	- How do you monitor that many custom scripts and manage all the environments?
	- We can do it by using kubernetes.
- Kubectl is a command line utility to interact with K8s.
- Minicube is a way to try, understand, run and learn about kubernetes.
	- Since kubernetes is very resource consuming.
	- It gives the entire experience of kubernetes in a small package called minicube for home experience and learning.
- Overview of kubernetes.
	- Control plane
		- Mastermind to control all the worker nodes.
		- We can talk to the control plane using kubectl.
	- Worker nodes (pods)
		- There could be alot of worker nodes.
		- We never interact with the worker nodes.
		- All our commands are passed to the worker nodes through the control plane.
			- Deployment
				- Take the application and put it into a pod / worker node.
				- For example, we need to deploy our database and its interface.
				- During the deployment, we only need to tell the application about the secrets one time.
			- Services
				- Along with deployment of the application, this deployment cannot talk to anyone outside.
				- We need a port to open or map to make it communicable.
				- We need to set services to set this.
				- So the services take the deployment and make it available to the organization/audience we require it to communicate with.
	- Config
		- The worker nodes have our applications deployed in them.
		- To access them, we need a URL to connect to our application e.g., database.
		- So, now we need a db URL.
		- Usually these applications are set in internal network to keep the latency low.
	- Secrets
		- These are known as environment variables.
		- These set the applications to point to specific ports, key-value pairs, etc.
		- We need to find a way to keep them secret.
	- Secret and config are sort of global variables for service and deployment.
	- The worker node will repeat for the database and its interface.
		- The difference between the two deployments could be change in some env variables and the image.
		- The services might change the mapped ports.
		- If there exist two applications such as database and its interface, the interface should know where the database exist.
	- NodePort
		- Till the above, all the applications are internally connected and cannot talk to the external world.
		- NodePort is an additional service for kubernetes.
		- It is a flag to be enabled so the applications are available to the outside world.
		- Also, we do not need to expose the database to the outside world but only the interface.
	- We can deploy multiple similar nodes like the above with ease using kubernetes.
		- Updates are easy
		- Zero downtime
		![[Pasted image 20231014150209.png]]		
- Architecture of kubernetes.
	![[Pasted image 20231011223550.png]]
	- The above is an overview of kubernetes.
	- We use both types of commands.
		- Imperative.
			- From CLI.
		- Declarative.
			- Using a conf file (YAML).
	- We will have basically two setups.
		- Control plane node
			- These worker nodes are managed by a master node.
			- The components in it would be:
				- API server
					- It is the main brain.
					- All calls go to this server.
					- It will do 3 things.
						- Authentication
						- Authorization
						- Admission
				- Scheduler
					- It intelligently finds the best fit node to run the pod (container).
					- We will define the hardware requirements for a node.
					- It will read this node and update the label.
				- etcd
					- Key value database for kubernetes cluster
				- CCM - Cloud Control Manager
					- If we have a cloud communication, we need a CCM to communicate with the cloud.
				- Controller manager
					- Controller manager comes in the end of the complete process.
					- It we want to run replicas of our application.
					- We need different types of object managed by controller manager.
					- For example, if we have multiple replicas and one goes down, it is responsibility of the controller manager to communicate with the API server to report the mismatch and ask for recreation.
		- Worker node
			- Many containers (cluster) are run on the worker nodes.
			- Some components are constant across the various worker nodes.
			- Some of the components of the worker node are:
				- Kubelet
					- It constantly communicates with API server for incoming requests. When the scheduler tells the need to run a container/pod on a worker. It goes through the API server to the kubelet which communicated with the CRI to fetch and run the image from the registry in containerd.
				- Containerd
					- The containerization interface.
				- Kube-proxy
					- It maintains the networking rules on all nodes.
					- We can say, it will have a list of IP tables.
				- Pods
			- There are some other components such as CRI, CNI and CSI.
				- CRI - Container Runtime Interface.
					- CRI talks to the containerd.
				- CNI
					- It is the network interface.
				- CSI
					- It is the storage interface.
	- The many containers we deploy (cluster) are interacted by the command ```kubectl```.
	- [[Imperative commands - Kubernetes]]
	- [[Labels and selectors - Kubernetes]]
- [[YAML]]
	- Most of the configuration files will be written in YAML in kubernetes.
	- It is a declarative command.
- [[Pods]]
	- In kubernetes, everything we run, it runs as a pod.
	- Every pod has an IP for itself.
	- In the YAML file, metadata contains the pod name while the spec contains the container name.
#### Resources:
- https://www.youtube.com/watch?v=PN3VqbZqmD8
- https://www.youtube.com/watch?v=7XDeI5fyj3w