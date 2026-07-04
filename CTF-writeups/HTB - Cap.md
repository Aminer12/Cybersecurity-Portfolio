Difficulty - Easy
OS - Linux 
Date: 2026-07-04
Completed in Guided Mode 
Target IP: 10.129.29.176
## Task Questions:

How many TCP ports are open? 3 

After running a "Security Snapshot", the browser 
### Connection
command: ping 10.129.29.176 
![](../assets/Pasted%20image%2020260704142913.png)

## Scan:
Command: nmap -sC -sV 10.129.29.176 
![](../assets/Pasted%20image%2020260704143021.png)

scan shows we have:
21/tcp with FTP vsftpd 3.0.3 
22/TCP with ssh OpenSSH 8.2p1
80/TCP with HTTP - Gunicorn 

