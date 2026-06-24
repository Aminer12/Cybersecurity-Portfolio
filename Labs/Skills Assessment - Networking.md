
Lessons:
	HTB Network Foundations 

Step 1 - open bash script terminal

Command: ifconfig -a 
	ifconfig is used to configure network interfaces and display their current status 
	-a allows us to see all interfaces, including those down 

The command shows us the Lo or loopback address which is always associated with 127.0.0.1. This address is used when a device needs to send information to its self, for things likes test, \

Command: netstat -tulnp4
	netstat displays network connections, routing tables, and interface statistics 
	IP:PORT - shows all open or listening TCP UDP ports for IPv4  

Command: netstat - tulp4
	by removing the n option our output now displays hostname:service rather than IP:Port 

Command: ip route get <target ip> (10.129.59.132)
	response - 10.129.59.132 via 10.10.14.1 dev tun0 src 10.10.15.176 uid 1002 
	This shows that we are connected to the target device through the tun0 vpn 

command: ping -c 4 <target ip> 
	ping helps determine the reachability of a host network, operating on level 3 
	the -c 4 represent the count (number of pings ) if not specified Linux will try until Ctrl + C is used to terminate it. 
	TTL or Time to live is the number of hops it took to reach the destination 
	time - tells us how much latency there is on the network 

command nmap <target ip>:
	shows use the open ports on a target machine
	result show open ports on the machine 
	Port 21 used for File Transfer Protocol 
	Port 80 for HTTP is going to be our focus 

command nmap -p21,80 -sC -sV 10.129.59.132
	This scan operates at level 4  by adding -sV (version scan) and -sC (default scripts), nmap uses protocols on level 7 
	The lack of information on port 80 shows their may be a request filtering in place 
	shows data about port 21 
	showing that anonymous ftp is enabled - meaning anyone can connect 