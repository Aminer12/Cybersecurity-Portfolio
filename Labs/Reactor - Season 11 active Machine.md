community rating - Easy
Machine - Linux

Goal:
User Flag:
Root Flag:

Target IP 10.129.19.247

Test Connection:
	command: ping 10.129.19.247 
	Result - Good Connection 

Scan Target:
	Command nmap -p- -sV -sC 10.129.19.247
	scan results:![](../assets/Pasted%20image%2020260626162728.png)

Look into OpenSSH 9.6pi results in a CVE-2025-26465 vulnerability, looks like a man in the middle attack 

Command: ssh - v 
	Result : OpenSSH 10.0p2 Debian-7+deb13ul, OpenSSL 3.5.5 /

Attempted some basic passwords - admin, administrator, root, nothing, 