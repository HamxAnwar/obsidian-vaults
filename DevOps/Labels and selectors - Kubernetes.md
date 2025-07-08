![[Pasted image 20231012003752.png]]
#### Labels
- In kubernetes, we can make our objects meaningful using labels using key:value pairs.
- After creating a pod, labels could be automatically generated as key:value pairs.
- These labels can be get from:
	- ```kubectl get pods --show-labels```
- To give your own labels, we can:
	- ```kubectl label pod <pod name> key=value```
#### Selectors
- Pods and services in a cluster can be selected based on labels.
- For example, if we want to send a traffic to a certain pod, we can do this on the basis of its labels.
- If we have multiple replicas, all of them should have same labels.
- We include them in the metadata in the declarative YAML.