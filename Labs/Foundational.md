
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
	result:![[Pasted image 20260625160957.png]]
	We can see port 21 is open running a file transfer protocol // Version vsftpd 3.0.3 
quick google search shows their is an DoS exploit - CVE-2021-30047