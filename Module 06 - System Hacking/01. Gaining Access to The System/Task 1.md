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

### TASK 02 - Gain Access to a Remote System using Reverse Shell Generator
#### Lab Objectives
Gain access to a remote system using Reverse Shell Generator

#### Step by Step
 1. Open Parrot
 2. Run **docker run -d -p 80:80 reverse_shell_generator**
    <img url="https://github.com/user-attachments/assets/34083a8e-3b78-43f4-8303-d69a032e56a6" heigth=50%>
    notes:
    If you receive an error run **service apache2 stop** command and perform Step#2 again
 3. launch browser localhost, Type IP **10.10.1.14** Port **4444**, **MSFVenom**
    <img src="https://github.com/user-attachments/assets/88d7375a-96cb-4743-b448-5473117f7f68" height=50%>
    notes:
    Here, we are selecting Windows Meterpreter Staged Reverse TCP (x64) from MSFVenom section to generate payload.
 5. Enter Payload
    <img src="https://github.com/user-attachments/assets/2a03255a-c3cd-47e8-ba61-43a4edd6d7d0" height=50%>
 6. Copy listener msfconsole as Type from the drop-down under Listener
    <img src="https://github.com/user-attachments/assets/135923b2-e9a3-479d-82c1-66ed94b16e88" height=50%>
 7. Click **Place** to attacker and copy **reverse.exe**
   <img src="https://github.com/user-attachments/assets/4f09e974-34c3-47f8-aa84-3c7a5f5706f5" height=50%>
8. Click the Places menu present at the top of the Desktop and select Network.
9. type smb://10.10.1.11 and press Enter to access Windows 11 shared folders.
10. The security pop-up appears; enter the Windows 11 machine credentials (Admin/Pa$$w0rd) and click Connect.
11. The Windows shares on 10.10.1.11 window appears; double-click the CEH-Tools folder.
     <img src="https://github.com/user-attachments/assets/fe56999f-187c-4282-adfc-25a4cf083d12" height=50%>
12. Paste **reverse.exe**
13. Open Windows and navigate to E:\CEH-Tools\CEHv13 Module 06 System Hacking, copy **reverse.exe** to dekstop
     <img src="https://github.com/user-attachments/assets/8d44f245-40ca-414b-8f20-9f8bc80c7e00" height=50%>
15. Double click **reverse.exe**
16. Open Parrot, session has been created
     <img src="https://github.com/user-attachments/assets/dc8a61eb-964c-438a-92f0-a4169c8e49b6" height=50%>
17. type **getuid**
     <img src="https://github.com/user-attachments/assets/49fce01f-a059-4361-9967-21cbf30b1fc4" height=50%>
18. open browser and select HoaxShell and PowerShell IEX used Port 444
     <img src="https://github.com/user-attachments/assets/9bfaa79e-95c5-474a-a9da-aee9bc8e34e9" height=50%>
19. Open terminal **pluma shell.ps1**, copy payload and save
20. Listen Hoaxshell
     <img src="https://github.com/user-attachments/assets/2ede358e-6403-429a-b757-668227a82d4c" height=50%>    
21. click **place** attacker, copy to ceh module 06
     <img src="https://github.com/user-attachments/assets/255ace07-4c40-4a8c-a6fc-9fbfe1a7ab20" height=50%>
22. Open windows 11, Copy from CEH-Tools Module 06 **shell.ps1** to desktop
     ![image](https://github.com/user-attachments/assets/b7133d2e-0a7e-4db0-8caa-f21b4efd5773)
24. run powershell as administrator
25. run cd C:\Users\Admin\Desktop\
26. execute ./shell.ps1
    ![image](https://github.com/user-attachments/assets/6a7786ed-d086-4fb2-ac5c-485122ea35a8)

27. open parrot terminal listener
28. Enter whoami
     ![image](https://github.com/user-attachments/assets/c386858c-7176-436e-8b04-abdbe5243747)


##### Question 6.1.2.1
In Parrot Security machine, use Reverse Shell Generator to create payload and set up listener to gain access to Windows 11 machine. Enter the type of payload that is selected under HoaxShell tab to generate a PowerShell script  that is used to compromise Windows 11 machine.
**Answer: Powershell IEX**
Perform buffer overflow attack to gain access to a remote system

