
HTB Labs: foundational labs selection: 
Lab: Meow
	Target IP : 10.129.1.17
	Test Communication 
	ping Ip address: ping successful 
	Next we are going to see if there are any open ports using nmap (Network Mapper) utilizing -sV for service detection 
	command: nmap -sV 10.129.1.17
		results port 23/tcp is open state, running a telnet service 
	command: telnet 10.129.1.17:
		result: requires login information 
		Important to test basic authorized usernames like admin / administrator / root 
		root allows
	Command: ls 
		find the flag
	Command cat flag.txt 
		result show flag in terminal 

Learned Commands:
	ls - lists files and directories in Linux 
	cat - is used to read, concatenate and write file contents 

# lab: Fawn 
[Hack The Box :: Fawn Machine](https://app.hackthebox.com/machines/Fawn?sort_by=created_at&sort_type=desc)

Target IP: 10.129.1.14

Check connection: 
	Command ping 10.129.1.14 // good connection

Scan for open ports:
	Command: nmap -sV
	result:
	![](../assets/Pasted%20image%2020260625164914.png)
	We can see port 21 is open running a file transfer protocol // Version vsftpd 3.0.3 
quick google search shows their is an DoS exploit - CVE-2021-30047

Connecting to FTP Server:
	command ftp 10.129.1.14 
		connection established need a user name
		Made attempts was successful with : User anonymous - Password anything 

Looking around:
	command: ls
	![](../assets/Pasted%20image%2020260625165006.png)
	see the flag.txt file need to transfer it 

Transfer document:
	Commands: get flag.txt // quite // cat flag.txt C
	![](../assets/Pasted%20image%2020260625165030.png)

Takeaway Notes:
	Try username anonymous first with no password when connecting 
	Commands to remember for FTP: help - to understand command options // ls -  to look around // quit - to get off the FTP server // get - to transfer a file // ftp -? for client help menu 
	Linux command: cat - to read document on terminal 

Remedial action:
	Set up a better username for the FTP server, and a password. 

# LAB: Dancing 
[Hack The Box :: Dancing Machine](https://app.hackthebox.com/machines/Dancing?sort_by=created_at&sort_type=desc)

Machine - Windows 
Target IP: 10.129.1.12

Test Connection:
	Command ping 10.129.1.12
	Result: Good connection 

Scan:
	Command: nmap -p- -sV - sC 10.129.1.12
		-p- : all ports 
		-sV : determine service/version info
		-sC : running default scripts
		![](../assets/Pasted%20image%2020260626133744.png)
		port 445 shows Microsoft-ds is open. Research show this is a Server message Block (SMB protocol ) used in file sharing 

Connecting to SMB Server:
	Command: smbclient -L 10.129.1.12:
		-L : list 
		There was no password when requested 
		This command represent the correct command sequence after many failed attempts 
		![](../assets/Pasted%20image%2020260626135834.png)
		smbclient -? : for help option

Connecting to WorkShares Disk:
	Command: smbclient //10.129.1.12/WorkShares:
		![](../assets/Pasted%20image%2020260626140447.png)
		First on the list is Amy.J which is a directory 

Accessing Amy.J directory:
	Command: cd Amy.J // ls to look around // get worknotes.txt file
	![](../assets/Pasted%20image%2020260626140538.png)
	opened up the worknotes.txt file - does not seem important just text information
	![](../assets/Pasted%20image%2020260626140808.png)

Accessing James.P Directory:
	Commands: cd James.P // ls // get flag.txt 
	![](../assets/Pasted%20image%2020260626141050.png)

Flag:
	![](../assets/Pasted%20image%2020260626141211.png)

Overview:
	Combining Linux terminal commands with windows commands. 
	Important to look at the examples when using the help command dealing with SMB server and connecting to it. 
	Did require looking at the worksheet to solve. Got stuck on how to access the SMB server on my own. 

Additional information - Studying Walkthrough:
	SMB runs at the Application or Presentation Layer of the OSI model - relying on NetBIOS over TCP/IP (NBT) at the transport layer. Which is why you will often see both operating at the same time 
	SMB-enabled storage on a network is called a - Share 
	SMB connections always require a username for authentication - if no username is given then the local account username will be given instead 
	--------
	ADMIN$ - Administrative shares are hidden networks shares created by the Windows NT family of operating systems. They can be disabled but not deleted 
	C$ - Administrative shares - where the operating system is hosted 
	IPC$ - The inter-process communication share. Used for inter-process communication via named pipes and is not part of the file system.
	WorkShares - custom share 

# Lab: Redeemer:
https://app.hackthebox.com/machines/Redeemer?tab=play_machine
community rating - very easy 
Machine - Linux
Date: 2026-07-02




