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

Wide Area Networks (WANs):
	Large area, multiple cities, countries 
	a collection of owners 
	lower speed because of distance 
	a combination of fiber optics or satellites, telecommunication lines 

Often LANs are connected to WANs expanding their reach and communication.



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

