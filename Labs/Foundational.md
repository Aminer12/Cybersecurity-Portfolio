
HTB Labs: foundational labs selection: Each lab was completed by following a write-up guide following along with the guide. 

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

