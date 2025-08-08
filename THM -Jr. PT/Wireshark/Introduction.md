- An open-source, cross-platform network packet analyzer tool
- Capable of sniffing and investigating live traffic and inspecting packet captures (PCAP).
- Use cases:
	- Detect and troubleshoot network problems such as network load failure points and congestion.
	- Detecting security anomalies
		- Rogue hosts
		- abnormal port usage
		- Suspicious traffic, etc.
	- Investigating and learning protocol details such as response codes and payload data.
- It is not an intrusion detection software (IDS).
	- Allows analysts to discover and analyze the packets in depth.
	- Detecting anamoly or network problem and their causes are purely based on analyst's knowledge.
- Wireshark GUI

|   |   |
|---|---|
|**Toolbar**|The main toolbar contains multiple menus and shortcuts for packet sniffing and processing, including filtering, sorting, summarising, exporting and merging.|
|**Display Filter Bar**|The main query and filtering section.|
|**Recent Files**|List of the recently investigated files. You can recall listed files with a double-click.|
|**Capture Filter and Interfaces**|Capture filters and available sniffing points (network interfaces).  The network interface is the connection point between a computer and a network. The software connection (e.g., lo, eth0 and ens33) enables networking hardware.|
|**Status Bar**|Tool status, profile and numeric packet information.|

![[Pasted image 20250705174212.png]]
- After loading a file: 
![[Pasted image 20250705174239.png]]
- We can see the processed filename, detailed number of packets and details of the packets.
- Packet details are shown in three different panes, which allow us to discover them in different formats.

|                     |                                                                                                                                                                                                                                      |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Packet List Pane    | Summary of each packet (source and destination addresses, protocol, and packet info). You can click on the list to choose a packet for further investigation. Once you select a packet, the details will appear in the other panels. |
| Packet Details Pane | Detailed protocol breakdown of the selected packet.                                                                                                                                                                                  |
| Packet Bytes Pane   | Hex and decoded ASCII representation of the selected packet. It highlights the packet field depending on the clicked section in the details pane.                                                                                    |
- **Coloring Packets**
	- Packets are colored based on various conditions and protocols.
	- Two packet coloring methods:
		- Temporary rules only available during current sessions.
		- Permanent rules under preferences which are available for future program sessions.
	- The default permanent coloring is show below:
	- ![[Pasted image 20250705180445.png]]
- **Packet Sniffing**
	- ![[Pasted image 20250705180605.png]]
	- First shark button to capture traffic and start sniffing.
	- Red button to stop sniffing.
	- Third (green) button to restart sniffing.
	- Status bar provides the sniffing interface and number of collected packets.
- **Merge PCAP files**
	- Wireshark can combine two pcap files into one single file.
	- Menu path: File --> Merge
	- Choosing the second file, Wireshark will show the total number of packets in the selected file.
	- Once you click "open", it will merge the existing pcap file with the chosen one and create a new pcap file.
	- Note that you need to save the "merged" pcap file before working on it.
	- ![[Pasted image 20250705181013.png]]
- **View File Details**
	- Knowing the file details if a PCAP file is helpful.
	- When working with multiple PCAP files, recalling the file details to identify the file, classify and prioritise it. 
	- File details:
		- File hash
		- Capture time
		- Capture file comments
		- Interface and statistics
	- To view the details (2 methods):
		- Statistics --> Capture File Properties
		- Click the **"pcap icon located on the left bottom"** of the window.
		- ![[Pasted image 20250705181321.png]]
#### Packet Dissection
- Also called **protocol dissection** 
- Investigates packet details by decoding available protocols and fields.
- Wireshark supports a long list of protocols for dissection.
- We can also write our own dissection scripts.
- More details on dissection [**here**](https://github.com/boundary/wireshark/blob/master/doc/README.dissector).

- Click on the packet to open its details.
- Packet consist of 5 to 7 layers based on the OSI model.
- ![[Pasted image 20250705183215.png]]
- Each time you click a detail, it will highlight the corresponding part in the packet bytes pane.
- ![[Pasted image 20250705183232.png]]
- If we see the detail pane, we can see that there are 7 layers:
	- frame/packet
	- Source MAC
	- Source IP
	- Protocol
		- Protocol errors
	- Application protocol
	- Application data.
	- ![[Pasted image 20250705183312.png]]
- **The Frame (Layer 1):** This will show you what frame/packet you are looking at and details specific to the Physical layer of the OSI model.
	- ![[Pasted image 20250705183550.png]]
- **Source MAC (Layer 2):** This will show you the source and destination MAC Addresses; from the Data Link layer of the OSI model.
	- ![[Pasted image 20250705183611.png]]
- **Source IP (Layer 3):** This will show you the source and destination IPv4 Addresses; from the Network layer of the OSI model.
	- ![[Pasted image 20250705183648.png]]
- **Protocol (Layer 4):** This will show you details of the protocol used (UDP/TCP) and source and destination ports; from the Transport layer of the OSI model.
	- ![[Pasted image 20250705183715.png]]
- **Protocol Errors:** This continuation of the 4th layer shows specific segments from TCP that needed to be reassembled.
	- ![[Pasted image 20250705183738.png]]
- **Application Protocol (Layer 5):** This will show details specific to the protocol used, such as HTTP, FTP,  and SMB. From the Application layer of the OSI model.
	- ![[Pasted image 20250705183822.png]]
- **Application Data:** This extension of the 5th layer can show the application-specific data.
	- ![[Pasted image 20250705183845.png]]
#### Packet Navigation
- **Packet Number**
	- Wireshark calculates the number of investigated packets and assigns a unique number for each packet.
	- This helps the analysis process for big captures and makes it easy to go back to a specific point of an event.
	- ![[Pasted image 20250705184416.png]]
- **Go to Packet**
	- Packet numbers do not only help to count the total number of packets or make it easier to find/investigate specific packets.
	- This feature not only navigates between packets up and down; it also provides in-frame packet tracking and finds the next packet in the particular part of the conversation.
	- We can use the **"Go"** menu and toolbar to view specific packets.
	- ![[Pasted image 20250705184555.png]]
- **Find Packets**
	- Packets can also be found based on packet contents.
	- Edit -> Find Packet
	- This helps analysts and administrators to find specific intrusion patterns or failure traces.
	- Two crucial points at finding packets:
		- Know the input type.
			- Four types of inputs
				- Display filter
				- Hex
				- String
				- Regex
			- String and Regex are most commonly used search types.
			- Searches are case insensitive but we can search case sensitive by clicking the radio button.
		- Know the search field.
			- Searches can be conducted in the three panes.
				- Packet list 
				- Packet details 
				- Packet bytes
			- It is important to know the available information in each pane to find the event of interest.
			- For example, if we try to find the information available in the packet details pane and conduct the search in the packet list pane, Wireshark won't find it even if it exists.
	- ![[Pasted image 20250705185507.png]]
- **Mark Packets**
	- Marking packets is another helpful functionality for analysts.
	- Marking a packet would find/point to a specific packet for further investigation
	- Helps analysts point to an event of interest or export particular packets from the capture. 
	- Edit tab or right-click menu to mark/unmark packets.
	- Marked packets will be shown in black regardless of the original colour representing the connection type. 
	- Note that marked packet information is renewed every file session, so marked packets will be lost after closing the capture file.
	- ![[Pasted image 20250705185807.png]]
- **Packet Comments**
	- Similar to marking, we can comment on particular packets.
	- Helps further investigation or remind and point out important/suspicious points for other layer analysts.
	- Unlike packet marking, the comments can stay within the capture file until the operator removes them.
	- ![[Pasted image 20250705185917.png]]
- **Export Packets**
	- Capture files can contain thousands of packets in a single file.
	- Sometimes, it is necessary to separate specific packages from the file and dig deeper to resolve an incident.
	- This functionality helps analysts share the only suspicious packages (decided scope).
	- Redundant information is not included in the analysis process.
	- Use the **"File"** menu to export packets.
	- ![[Pasted image 20250705190032.png]]
- **Export Objects (Files)**
	- Wireshark can extract files transferred through the wire.
	- For a security analyst, it is vital to discover shared files and save them for further investigation.
	- Exporting objects are available only for selected protocol's streams including:
		- DICOM
		- HTTP
		- IMF
		- SMB
		- TFTP
	- ![[Pasted image 20250705190300.png]]
- **Time Display Format**
	- Wireshark lists the packets as they are captured, so investigating the default flow is not always the best option.
	- By default, Wireshark shows the time in "Seconds Since Beginning of Capture".
	- The common usage is using the UTC Time Display Format for a better view.
	- View --> Time Display Format
	- ![[Pasted image 20250705190418.png]]
	- ![[Pasted image 20250705190429.png]]
- **Expert Info**
	- Wireshark also detects specific states of protocols to help analysts easily spot possible anomalies and problems.
	- Note that these are only suggestions, and there is always a chance of having false positives/negatives.
	- Expert info can provide a group of categories in three different severities.

|              |            |                                                          |
| ------------ | ---------- | -------------------------------------------------------- |
| **Severity** | **Colour** | **Info**                                                 |
| **Chat**     | **Blue**   | Information on usual workflow.                           |
| **Note**     | **Cyan**   | Notable events like application error codes.             |
| **Warn**     | **Yellow** | Warnings like unusual error codes or problem statements. |
| **Error**    | **Red**    | Problems like malformed packets.                         |
- 
	- Frequently encountered information groups are listed in the table below.

|              |                           |                |                             |
| ------------ | ------------------------- | -------------- | --------------------------- |
| **Group**    | **Info**                  | **Group**      | **Info**                    |
| **Checksum** | Checksum errors.          | **Deprecated** | Deprecated protocol usage.  |
| **Comment**  | Packet comment detection. | **Malformed**  | Malformed packet detection. |
- 
	- **lower left bottom section** in the status bar or **Analyse --> Expert Information** menu to view all available information entries via a dialogue box.
	- It will show the packet number, summary, group protocol and total occurrence.
	- ![[Pasted image 20250705190909.png]]
#### Packet Filtering
- **Packet Filtering**
	- Wireshark has a powerful filter engine that helps analysts to narrow down the traffic and focus on the event of interest.
	- Filters are specific queries designed for protocols available in Wireshark's official protocol reference.
	- Two types of filtering approaches: 
		- Capture filters: Used for capturing only the packets valid for the used filter.
		- Display filters: Used for viewing the packets valid for the used filter.
	- There are two different ways to filter traffic and remove the noise from the capture file.
		- The first one uses queries
		- The second uses the right-click menu. 
	- Wireshark provides a powerful GUI, and there is a golden rule for analysts who don't want to write queries for basic tasks: **"If you can click on it, you can filter and copy it"**.
- **Apply as Filter**
	- Most basic way of filtering traffic.
	- While investigating a capture file, you can click on the field you want to filter and use the "right-click menu" or **Analyse --> Apply as Filter** menu to filter the specific value.
	- Once the filter is applied, Wireshark will generate the required filter query, apply it, show the packets according to our choice.
	- It will hide the unselected packets from the packet list pane.
	- Note that the number of total and displayed packets are always shown on the status bar.
	- ![[Pasted image 20250705193825.png]]
- **Conversation Filter**
	- When we use the "Apply as a Filter" option, we will filter only a single entity of the packet.
	- This option is a good way of investigating a particular value in packets.
	- However, suppose we want to investigate a specific packet number and all linked packets by focusing on IP addresses and port numbers.
	- In that case, the "Conversation Filter" option helps us view only the related packets and hide the rest of the packets easily.
	- We can use the"right-click menu" or "**Analyse --> Conversation Filter**" menu to filter conversations.
	- ![[Pasted image 20250705193950.png]]
- **Colorize Conversation**
	- This option is similar to the "Conversation Filter" with one difference.
	- It highlights the linked packets without applying a display filter and decreasing the number of viewed packets.
	- This option works with the "Colouring Rules" option ad changes the packet colours without considering the previously applied colour rule.
	- We can use: 
		- right-click menu
		- View --> Colourise Conversation
	- Note that you can use the **View --> Colourise Conversation --> Reset Colourisation** menu to undo this operation.
	- ![[Pasted image 20250705194215.png]]
- **Prepare as Filter**
	- This model doesn't apply the filters after the choice.
	- It adds the required query to the pane and waits for the execution command (enter) or another chosen filtering option by using the **".. and/or.."** from the "right-click menu".
	- ![[Pasted image 20250705194311.png]]
- **Apply as Column**
	- By default, the packet list pane provides basic information about each packet.
	- Use the **right-click menu** or **Analyse --> Apply as Column** menu to add columns to the packet list pane.
	- The value will be visible on the packet list pane by clicking on a value and applying it as a column.
	- This function helps analysts examine the appearance of a specific value/field across the available packets in the capture file.
	- The columns can be enabled/disabled by clicking on the top of the packet list pane.
	- ![[Pasted image 20250705194634.png]]
- **Follow Stream**
	- Wireshark displays everything in packet portion size.
	- It is possible to reconstruct the streams and view the raw traffic as it is presented at the application level.
	- Following the protocol, streams help analysts recreate the application-level data and understand the event of interest.
	- It is also possible to view the unencrypted protocol data like usernames, passwords and other transferred data.
	- Use 
		- right-click menu
		- Analyse --> Follow TCP/UDP/HTTP Stream menu
		- Shown in a separate dialogue box
			- Packets originating from the server are highlighted with blue.
			- Packets originating from the client are highlighted with red.
	- ![[Pasted image 20250705195117.png]]
	- Once a stream is followed:
		- Wireshark automatically creates and applies the required filter to view the specific stream.
		- Remember, once a filter is applied, the number of the viewed packets will change. You will need to use the "**X** **button**" located on the right upper side of the display filter bar to remove the display filter and view all available packets in the capture file.