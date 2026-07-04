Lessons:
	Lets Defend: Phishing Email Analysis

Phishing emails fall into the delivery phase of the Cyber Kill Chain. Designed to trick user into clicking on malicious links or downloading malicious files to steal information from the user. 

Spoofing Techniques - pretending to be someone else, by using their email address. 
	Protocols designed to counter spoofing 
		SPF - Sender Policy Framework
		DKIM - DomainKeys Identified Mail
		DMARC

Tools
	Mxtoolbox

To check if an email is spoofed look at the SMTP address - it should match the company ip profile. But its important to know this does not guarantee the email is safe. 

# Email Header
Contains information - sender, recipient, and date. Alongside - Return-path, reply-to, received. 

# Field Breakdown

From - name and email address of the sender 
To - recipient of the email, including name and email address 
Date - Timestamp of the email 
Subject - topic of email 
Return-path or Reply-to - this is the return address if you reply to the email 
Domain Key / DKIM signature - email signatures as part of protocols to make your email more secure 
Message-ID - A unique combination of letter and number for each specific email 
MIME (Multipurpose Internet Mail Extension) version - internet coding standard
Received - list each mail server the email passed through before arriving - listed in reverse chronological order - the first server is really the last - 
X-Spam Status - a score on the likelihood the email is spam 

