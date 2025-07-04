- Various linux shells
	- BASh: Bourne Again Shell
	- ZSh: Z Shell
	- FISh: Friendly Interactive Shell
- Shell Scripting
	- Should start with shebang `#!`
```
#!/bin/bash
echo "Hey! What's your name?"
read name
echo "Welcome, $name"
```
- Give executable permissions to run the script.
	- `chmod +x first_script.sh`
- We can define loops.
	- For loop
```
	#!/bin/bash
	for i in {1..10};
	do
	echo $i
	done
```
- Conditional Statements
```
#!/bin/bash
echo "Please enter your first name: "
read name
if [ "$name" = "Hamza" ]; then
	echo "Welcome Hamza! Here is the secret: THM_Script"
else
	echo "Sorry! You are not authorized to access the secret."
fi
```
- We can do **comments** using #.

**Example Scripts**
```
#!/bin/bash
username=""
companyname=""
pin=""

for i in {1..3}
	if [ "$i" -eq 1 ]; then
		echo "Enter your username: "
		read username
	elif [ "$i" -eq 2 ]; then
		echo "Enter your company name: "
		read companyname
	else
		echo "Enter your pin: "
		read pin
	fi
done

if [ "$username" = "Hamza" ] && [ "$companyname" = "RSI" ] && [ "$pin" = "9876" ]; then
	echo "Authentication successful! You can now access your locker, Hamza."
else
	echo "Authentication failed!"
fi
```
