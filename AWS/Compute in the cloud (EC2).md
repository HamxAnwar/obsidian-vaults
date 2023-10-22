- #### What is EC2?
	- We need servers to power our applications.
	- AWS uses virtual servers called EC2.
	- AWS has servers/ remote machines already.
	- AWS runs EC2 or virtual servers on them.
	- We just need to demand and use the virtual servers based on our need.
	- We do not get access of remote machine completely but rather share it with multiple other resources.
	- A hypervisor shares the physical resources among the virtual machines.
	- This idea of sharing underlying hardware between virtual machines is known as multitenancy.
- #### Configurable EC2 parameters:
	- OS
	- What type of software we want?
		- Internal business apps
		- web apps
		- data bases
		- third-party software
	- Resizeable on the go
	- Network
- Each EC2 instance type is grouped under an instance family and is optimized for various types of tasks.
- #### Types of EC2 families:
	- General purpose
		- Provides a balance of compute, memory and networking resource.
		- Can be used for:
			- Web servers
			- Code repositories
	- Compute optimized
		- Ideal for compute intensive tasks such as:
			- Gaming servers
			- High performance computing (HPC)
			- Scientific modelling.
	- Memory optimized
		- Ideal for memory intensive tasks.
	- Accelerated computing
		- The are good for:
			- Floating point number calculations
			- Graphics processing
			- Data pattern matching
		- They utilize hardware accelerators.
	- Storage optimized
		- Good for workloads with high performance for locally stored data
- #### Pricing of EC2
	- On-demand
		- Depends on how long we use an instance.
		- What family of instance are we using?
	- Savings plans
		- Low prices for a certain amount of time (mostly years) on the account of continuous EC2 usage measured in dollars/hour.
	- Reserved instances
		- Suited for steady state workloads
		- Offers a discount of upto 75% as compared to on-demand pricing if we qualify.
	- Spot instances
		- We can request spare amazon EC2 computing capacity for up to 90% of on-demand prize.
		- These instances can be reclaimed at anytime by AWS with a 2 minute warning.
		- Good if our workloads can tolerate interruption.
	- Dedicated hosts
		- Hosts are dedicated to us and no one else shares the resources of that host.
- #### Scaling AWS-EC2
	- What if our clients are increasing or decreasing with time.
	- We can have increased or decreased EC2 with us.
	- This is scaling our Amazon EC2.
		- Amazon not only provides scaling manually but also auto-scaling.
		- There are two types of auto-scaling:
			- Dynamic scaling
				- Responds to changing demand.
			- Predictive scaling
				- Automatically schedules the number of EC2 instances based on predicted demand.
			- Both can be used together as well.
	- When we set up auto-scaling of EC2, we can set a minimum capacity, a desired capacity and the maximum capacity.
		- In case of no desired capacity specified, it defaults to the minimum capacity.
- #### Diverting traffic with Elastic Load Balancing
	- We can have lots of traffic going to a single EC2 instance.
	- This could result in a single EC2 container processing all the load where other EC2 containers remain free.
	- We need to route requests to free instances to process them.
	- Load balancer is an application that takes in requests and routes them to be processed.
	- We have many 3rd party load balancers. The operations team would be responsible to deploy and maintain it.
	- Elastic Load balancing
		- It is a regional construct, i.e. it runs on the regional level instead of containers.
		- An ELB is responsible to direct traffic towards the least working container.
		- It also is responsible for local traffic routing.
			- It lets the frontend talk to the backend to route traffic easily.
		![[Pasted image 20231021232300.png]]
- #### Messaging & Queuing
	- Applications need to talk to each other, what if one dies.
	- The data from the sender will be dropped and lost.
		- This is called tightly coupled.
		- A tightly coupled system fails if only one of its components fails as it starts causing problems for other components.
	- AWS prevents that by introducing buffers called the messaging and queue.
		- This architecture is called loosely coupled.
		- The buffer holds the messages sent by sender application.
		- Even if the processing application gets failed, the buffer would hold the messages until the application B is back online or the buffer is out of memory.
	- There are two services that assist in this regard.
		- Amazon Simple Queue Service (SQS)
			- A SQS is responsible for sending, receiving and storing messages between software components at any volume.
			- It does this without loosing messages or requiring other services to be available.
			- The data contained by messages is called payload.
		- Amazon Simple Notification Service (SNS)
			- SNS is similar as it can send out messages but it can also send out notifications to end user.
			- It uses a publish-subscribe (pub/sub) model.
			- So we can make a topic, configure subscribers for that topic and make publishers to publish notifications on that topic.
			- It can be used to broadcast/multicast messages as well as push notifications to multiple end users through SMS, mobile push or email.
- #### Additional Compute Services
	- EC2 instances are virtual machines.
		- It is great for various purposes.
		- It is flexible, reliable and scalable.
		- EC2 should be managed over time by the user.
			- Patching
			- Scaling
		- But our requirements might lead us to various other compute methods.
		- So what are offers are there by AWS for compute that are more management friendly.
		- We can look out for serverless options.
			- A serverless means we cannot see or access the underlying infrastructure or instances.
			- All of their management are taken care for us by AWS.
			- What are the options put forth by AWS?
	- ##### AWS Lambda
		- Serverless compute option.
		- It allows us to upload our code to a lambda function.
		- We configure a trigger and then the service waits for that trigger to execute code.
		- After trigger, the code automatically runs in a managed environment.
		- As our trigger increases, AWS will scale the lambdas automatically based on the demand.
		- ##### Note:
			- Made for running processes under 15 minutes.
			- Not for long running processes such as deep learning.
			- Hence, more suitable for quick processes:
				- Web backend
				- Handling requests
				- Backend expense report processing service.
	- ##### AWS Container Services
		- If we need the similar management but want to access the underlying infrastructure, we can opt out for AWS container services.
			- Amazon Elastic Container Service (ECS)
			- Amazon Elastic Kubernetes Service (EKS)
				- These both are container orchestration tools.
				- The containers are docker containers.
				- These containers run on top of EC2 instances.
	- ##### AWS Fargate
		- What if we do not need access to underline OS or manage EC2 instances, we can use fargate.
		- It is a serverless compute platform for ECS and EKS.

|   **EC2**   |   **Lambda**   |   **ECS/EKS**   |
|:-----|:-----|:-----|
|   Host traditional applications   |    Host short running functions   |   Docker containers based workloads on EC2   |
|   Full access to the OS   |     Service-oriented applications   |   Docker containers based workloads on serverless fargate   |
|   -   |   Event-driven applications   |   -   |
|   -   |   No managing servers   |   -   |

- There are many other compute services too other than these.