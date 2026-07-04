Difficulty - Easy
OS - Linux 
Date: 2026-07-04
Completed in Guided Mode 
Target IP: 10.129.29.176
## Task Questions:

How many TCP ports are open? 3 

After running a "Security Snapshot", the browser is redirected to a path of the format /something/id, where id represents the id number of the scan. What is the something?  - data 

Are you able to get to other users' scans? 
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

## HTTP investigation
Following the HTTP open server we get a security dashboard with a username - Nathan. The dashboard shows security events, failed login attempts, port scans 
![](../assets/Pasted%20image%2020260704143536.png)

The security Snapshot page:
![](../assets/Pasted%20image%2020260704143645.png)

We can see that the url has the /data/1 