### TASK 01 - Perform Active Online Attack to Crack the System’s Password using Responder
LLMNR (link local multicast name resolution) and NBT-NS (netbios namer service) are used to performe name resolution on the local link.

Responder is LLMNR, NBT-NS, MDNS poisoner. By default the tool only responds to SMB.

#### Lab Objectives
Perform active online attack to crack the system’s password using Responder

#### Step by Step
 1. Open Parrot Security
 2. check the interfaces (if config)
    <img src="https://github.com/user-attachments/assets/9a25debd-1623-4ea5-b7a4-b8df621a32c4" height=50%>
 3. Run **sudo reponder -I eth0**
    <img src="https://github.com/user-attachments/assets/fe43d4de-01df-4d23-86c0-ce4d409a1690" height=50%>
    notes:
    -I: specifies the interface (here, eth0). However, the network interface might be different in your machine, to check the interface issue ifconfig command.
 4. Responder starts listening to the network interface for events, as shown in the screenshot.
    <img src="https://github.com/user-attachments/assets/9016fe73-c09e-48f6-b522-784735e06814" height=50%>
 5. Open Windows 11
 6. Click Windows and Run \\CEH-Tools
    <img src="https://github.com/user-attachments/assets/26328705-e4d1-4b4d-8649-aeb67420c103" height=50%>
 7. Open Parrot Security
 8. Responder Capture Windows 11 login user hash password
    <img src="https://github.com/user-attachments/assets/98d2f3b8-591b-47aa-b10c-be3c56e78f29" height=50%>
    notes:
    By default, Responder stores the logs in /usr/share/responder/logs
 9. Copy hash value
    <img src="https://github.com/user-attachments/assets/b21fae20-5cbe-4b3c-b487-49024d6d0094" height=50%>
10. Paste hash value and run **pluma hash.txt**
    <img src="https://github.com/user-attachments/assets/07c2a3a2-6277-4dd6-81c5-4f1ba0187d1f" height=50%> 
11. Run **john hash.txt**
    <img src="https://github.com/user-attachments/assets/137e76b2-b52f-401a-b815-ddabdd74b7f5" height=50%>

##### Question 6.1.1.1
Run the Responder tool on the Parrot Security machine and find the NTLM hash for the user Jason on Windows 11. Simulate the user Jason (user: Jason and password: qwerty) on the Windows 11 machine. Enter the option that specifies the interface while running the Responder tool.
**Answer: -I**

