
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