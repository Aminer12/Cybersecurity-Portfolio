
describes how data is organized, transmitted, and managed across networks 

Peer to Peer (P2P) Architecture:
	Every node acts as both a client and a server. 
	No need for a central server 
	Example is like google docs were multiple people can access the same files when shared 

Client-Server Architecture:
	widely used across the internet 
	Client (end-users) send request to servers and get responses 
	Single-Tier Architecture:
		 the client, server, and database are all on the same machine 
	Two-Tier Architecture:
		split between clients and servers 
			client manage the presentation layer while servers manage the data layer
	Three-Tier Architecture:
		an application layer between the client and server, adding additional flexibility and scalability 
	N-Tier Architecture:
		N refers to a number above three, a multi level architecture. 

Hybrid Architecture:
	Combining the two above. Where servers facilitate coordination and authentication while the data is transferred between peers.  
	Example is like video call software like Zoom, were Zoom coordinates and authenticates. But once the call begins its peer to peer. 

Cloud Architecture:
	computing infrastructure hosted and operated by a third-party 

Software-Defined Architecture (SDN):
	a modern network that separates the control plane from the data plane. Instead of relying on hardware to operate both planes. Software is used to control the control plan creating a programmable network environment.


# Wireless Networks 

a connection of devices using signals instead of wires

wireless router - both provides connection within a range and directs data between devices 

Mobile Hotspot:
	a sharing of cellular data between devices 

Cell Tower:
	a structure holding antennas and other electronic communication equipment that creates a cellular network 
	Linked through Base Station Controllers (BSC) 
	And connected to the core network over fiber optic cables 

Frequency bands:
	2.4 Ghz : older Wi-Fi standards (802.11b/g/n) better at getting through objects but more prone to interference 
	5 Ghz - newer Wi-Fi (802.11a /n/ ac/ ax) faster speed shorter range
	Cellular bands (4g / 5g) (700 Mhz - 2.6 Ghz // up to 28 Ghz and beyond )

# Network Security 

CIA Triad:
	Confidentiality - only authorized user see the correct data
	Integrity - data remains accurate and unaltered 
	Availability - Network resources are accessible when needed 

Firewalls:
	a hardware or software component that tracks and blocks incoming and outgoing data based on a access control list (based on IP addresses, ports or protocols) in a process known as traffic filtering 
	Packet Filtering Firewall - operate lv 3/4, uses access control list 
	Stateful Inspection Firewall - tracks the state of network connections // more advanced than Filtering Firewalls / matching inbound and outbound data before authorization 
	Application Layer Firewall (proxy firewall) - Layer 7 // inspects content in traffic and block malicious request 
	Next-Generation Firewall (NGFW) combination of stateful inspection and proxy firewall 

Intrusion Detection and Prevention Systems (IDS / )

