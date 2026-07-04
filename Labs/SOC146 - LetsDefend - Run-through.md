
Link: [Monitoring - LetsDefend](https://app.letsdefend.io/monitoring?channel=investigation&event_id=93)

Type: Phishing Mail Detected 

Taking ownership and starting Case Report 
![](../assets/Pasted%20image%2020260703210256.png)

# Playbook Questions:

- When was it sent? - Jun,13,2021, 02:13 PM
- What is the Emails SMTP Address? - 24.213.228.54
- What is the sender Address? - trenton@tritowncomputers.com
- What is the recipient Address? - lars@letsdefend.io
- Is the mail content suspicious? - 
- Are there any attachements? - yes 

# Scanning file 

![](../assets/Pasted%20image%2020260703212901.png)

We downloaded the zip file attached to the suspicious email, and had virustotal inspect its contents. 

The image shown above shows that the zip folder contained three documents:
	iroto.dll - Malicious 
	Research-numbers.xls - Malicious 
	iroto1.dll - malicious


Was the device-action allowed - yes 

# check if anyone opened the malicious file