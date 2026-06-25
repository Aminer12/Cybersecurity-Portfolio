
HTB Labs:

Lab: Meow
	Target IP : 10.129.1.17
	Test Communication 
	ping Ip address: ping successful 
	Next we are going to see if there are any open ports using nmap (Network Mapper) utilizing -sV for service detection 
	command: nmap -sV 10.129.1.17
		results port 23/tcp is open state, running a telnet service 
	