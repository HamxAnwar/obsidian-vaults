![[Pasted image 20231011224021.png]]
- Widely used in the cloud native space.
- Human readable data serialization language.
- YAML = YAML Ain't Markup Language.
- Indentation sensitive.
- Syntax:
	- Everything is Key:Value object.
	- We can have objects.
		- Objects have attributes.
	- List - e.g. multiple containers.
		- We will define list items with -
	- To write multi-line strings, we use pipe symbol ( | ).
	- To use place-holders, we can use {{ }}.
	- We also define environment files with a $ sign.
	- If we have multiple files/objects, we can use ---
- A YAML file will always have some constant parameters.
	![[Pasted image 20231011225752.png]]
	- apiVersion
	- kind
	- metadata
		- labels
			- run
		- name: <pod name>
	- spec
		- containers
			- image
			- name: <container name>