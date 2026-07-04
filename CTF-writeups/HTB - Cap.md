Difficulty - Easy
OS - Linux 
Date: 2026-07-04
Completed in Guided Mode 
Target IP: 10.129.29.176
## Task Questions:

How many TCP ports are open? 3 

After running a "Security Snapshot", the browser is redirected to a path of the format /something/id, where id represents the id number of the scan. What is the something?  - data 

Are you able to get to other users' scans?  - yes

What is the ID of the PCAP file that contains sensitive data - 0 

Which application layer protocol in the pcap file can the sensitive data be found in? - ftp 

We've managed to collect nathan's FTP password, On what other services does this password work? - SSH

What is the full path to the binary on this machine has special capabilities that can be abused to obtain root privileges? 

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

We can see that the url has the /data/1 - connecting it to Nathan. We can download the information on the page, which produces a pcap (packet capture file) which can be examined in Wireshark. But currently there is no data being shown. 

The question ask if we can switch between user, I attempted this by changing the Id to a different number. After messing around the /data/0 produces a dashboard with packet data. 

After download the packet data and opening the file in Wireshark we can see that within the packet data is the username and password for connecting to the FTP server: 

![](../assets/Pasted%20image%2020260704150558.png)
This is because the data is being transfer unencrypted 

Username: nathan
Password: Buck3tH4TF0RM3!

### FTP 
Using the username and password I connected to the FTP server. Once connected I used the ls command to see what was available. There was only one text file (user.txt) which we transferred using get. In an additional terminal I opened the user.txt file, which had the user flag. 

![](../assets/Pasted%20image%2020260704151505.png)

### SSH
Using the same username and password I was also able to access the SSH server running. It also contains the same user.txt file as seen in the FTP server 

