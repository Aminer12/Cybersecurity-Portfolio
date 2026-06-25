Lessons:
	HTB - Network Foundations 

Definitions:
	ISP - Internet Service Provider 

Network - a collection of interconnected devices 
	Nodes being the end points of a network (like person computers)

Local Area Networks (LANs):
	Small area 
	small organization or single person
	high data transfer speeds 
	using a combination of wired and wireless connections
	comply with RFC 1918 standards 

Wide Area Networks (WANs):
	Large area, multiple cities, countries 
	a collection of owners 
	lower speed because of distance 
	a combination of fiber optics or satellites, telecommunication lines 
	often using the BGP routing protocol 

Often LANs are connected to WANs expanding their reach and communication.

Virtual Private Networks (VPN):
	Site-to-Site VPN - Both clients are Networking devices like Firewalls or Routers, this is often used to connect different company networks over the internet 
	Remote Access VPN - creating a virtual interface that the behaves as part of the network. 
		Important to look at the routing numbers used 
		If route is only for specific networks like 10.10.101.0/24 then its called Split-Tunnel VPN - meaning the internet connection is not going out the VPN 
	SSL VPN - a web-browser based VPN 

Global Area Networks (GAN):
	Things like the internet 
	often utilizing fiber optics and undersea cables or satellites 

Metropolitan Area Networks (MAN):
	a broadband network servicing other LANs within a geographic range 

Personal Area Network (PAN) and Wireless Personal Area Network (WPAN):
	a temp Network made up of smartphones connected together, allowing for exchange of data 


Open Systems Interconnection (OSI) Model:
	A framework that standardizes interconnection into 7 layers 
	Physical Layer (Layer 1):
		physical connection between devices. The hardware like Ethernet cables, hubs, and repeaters 
	Data Link Layers (Layer 2):
		This layer represents node to node transfer. It ensures the data being transferred is synchronized, looks for error detection and correction. Devices like switches operate on this layer using Media Access Control (MAC) addresses to identify network devices. 
	Network Layer (Layer 3):
		Devices - Routers 
		Protocol - internet protocol (IP) addresses for device identification and for determining the most efficient path for data
		Layer 3 handles packet forwarding, across routers. Responsible for logical addressing and path determination, ensuring the fastest route 
	Transport Layer (Layer 4):
		 Protocols - 
			 Transmission Control Protocol (TCP) - reliable, connection-oriented transmission with error correction 
			 User Datagram Protocol (UDP) - faster, connectionless communication, no guarantee of delivery 
		This layer provides end to end communication services for application using one of these protocols 
	Session Layer (Layer 5):
		Application Programming Interfaces (APIs) operate on this layer 
		This layer manages sessions between applications. Establishing, maintaining and terminating connections 
	Presentation Layer (Layer 6):
		Data Encryptions and compression protocols operate at this layer 
		This layer acts as a translator between the application layer and network formats. Handling data representation, ensuring readability of data between the layers 
	Application Layer (Layer 7):
		Protocols:
			Hypertext Transfer Protocol (HTTPS(Secure)) - web browsing 
			File Transfer Protocol (FTP) - files
			Simple Mail Transfer Protocol (SMTP) - email
			DNS ( Domain Name System) - domain names to IP addresses
		This layer is the end-sure interaction layer, enabling basic operations 

The Transmission Control Protocol / Internet Protocol (TCP / IP ) Model:
	Link Layer: Made of of layers 1/2 of the OSI
	Internet Layer - Network Layer OSI // operate Internet Control Message Protocol ( ICMP )
	Transport Layer - Transport Layer OSI
	Application Layer - 5,6,7 Layers of OSI

The TCP / IP models is the backbone of network communications, while the OSI is more of a way of understanding the TCP / IP model better 

Transmission:
	digital - the most common -using bits to transfer data cover the network
	Modes:
		Simplex - one way communication - keyboard to computer 
		Half-plex - two ways but one at a time - walkie-talkies 
		Full-plex - two way communication - phones 


# Components of a Network

End Devices - computers, smartphones, printers 

Intermediary Devices - Switches, Routers, Modems, Wireless access points
	Routers protocols - Open Shortest Path first (OSPF) or Border Gateway Protocol (BGP) different ways of finding the fastest / efficient path

Network Media - Cables, protocols, firewall 

Servers - Web Servers, File Servers, Mail Servers, Database Servers 

Software Firewalls - installed on individual computers, ( host based firewalls) monitoring incoming and outgoing traffic and blocking any unwanted traffic 

Server - a computer that provides // or houses services that it provided over the network to other computers 

# Networking Topologies 

Point to Point:
	aa direct connection between two devices
Bus:
	A connecting median - a bus - that connects multiple devices together, but does not have a central network component 
Star:
	Has a central network component (router) that all the host are connected to. This central piece forwards packets 
Ring:
	A duel connection of wires between host of facilitate incoming and outgoing data. 
	Does not require a central component 
Mesh:
	Fully Meshed - host directly connected 
	Partially Meshed - only a single connection on endpoints to the main network 
Tree:
	

# Proxies:
When a device or service sits in the middle of a connection and acts as a mediator. 
	Without out the ability to inspect the traffic, the mediator is only a gateway (not a proxy)
	Operating at level 7 
Dedicated Proxy / Forward Proxy:
	client makes a request and the computer carries it out. 

Reverse Proxy:
	similar as a forward proxy but focuses on incoming traffic instead 

non - Transparent Proxy:
	
# Network Communication 

Media Access Control (MAC) Address
	unique identifier assigned to the Network Interface Card (NIC) device, allowing it to be recognized on the local network. 
	Used when operating at level 2 (Data link layer) to ensure data reaches the correct physical device 
	Mac Address is 48 bits long, in hexadecimals format // Example: 00:1A:2B:3C:4D:5E 
	The first 24 bits represent the Organizationally Unique Identifier (OUI) assigned by the manufacture the other 24 are specific to each device 

When sending frames over the network the Address Resolution Protocol (ARP) connects MAC address to IP address bridging the gap between hardware and the internet 

Internet Protocol (IP) Address:
	a unique label assigned to a device when utilizing an internet protocol for communication. 
	Functions at the Network Layer (layer 3) 
	Two version: IPv4 and IPv6 
		IPv4 consist of 32-bit address space, formatted as 4 digits separated by a space 192.168.12.1
		IPv6  developed to replace IPv4 has 128-bit address, formatted in eight groups of four hexadecimals - 2001:0db8:85e3:0000:8a2e:0370:7334
	Not permanently assigned to a device, they can change

Ports:
	A number assigned to a specific service on a network to help with traffic management. 
	Functions on the Transport layer (layer 4 ) working directly with TCP /UDP 
	Ports range from 0 - 65535
	Well Known ports 0 - 1023 are reserved for common or universal protocols and managed by the Internet Assigned Numbers Authority (IANA)
	Registered Ports 1024 - 49151 not as strictly regulated but still assigned, often associated with companies and software a user may install on their computer 
	Dynamic / Private Ports (49152 - 65535) - not fixed often used for temporary communication
	HTTP - port 80
	HTTPS - 443 
	

# Dynamic Host Configuration Protocol (DHCP)

A network management protocol that assigns IP address to devices automatically based on given parameters 

The work : DORA ( Discover, Offer, Request, Acknowledge)
	DHCP server - device operating and managing the protocol 
	DHCP client - device connected to the network requesting the IP address 
	1 (Discover): client broadcast a DHCP discover message to find the server 
	2 (Offer): Server receives request and responds with an offer 
	3(Request): client receives the offer and replies with a request message, indicating acceptation
	4(Acknowledge): Server send acknowledgement message, confirming client configuration 


# Network Address Translation (NAT)

Allows devices on a private network to share a single public IP address, this was implemented to solve the shortage problem within IPv4 addresses 

Private IP ranges:
	Under RFC 1918
	10.0.0.0 to 10.255.255.255
	172.16.0.0 to 172.31.255.255
	192.168.0.0 to 192.168.255.255

This is done often by a router and is done by modifying the header IP address as it passes through 

Types
Static NATs - one to one mapping, one private one public
Dynamic Nat - a pool of public address are shared between a pool of private addresses 
Port Address Translation (PAT)- most common form - single public address for multiple private address, utilizing ports to distinguish between the different devices 

# Domain Name Systems ( DNS)

Connects domain names like (google.com) to IP address 

DNS Hierarchy:
Root server 
Top-level Domains (TLDs) like : .com / .org / .net / .uk
Second level Domains like : google or amazon
Subdomains or Hostname like:  www or (account).google.com

https:// www.example.com./home.html

https - scheme
www - subdomain
.example- 2nd level domain
.com-  top level domain 
./ - root
home.html -  page name 

