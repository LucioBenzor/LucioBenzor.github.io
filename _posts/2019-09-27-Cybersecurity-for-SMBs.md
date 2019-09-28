---
layout: post
title: "Cybersecurity tips for Small & Medium Businessess"
date: 2019-09-27
---

With the recent headlines about ransomware, data breaches, and hacks, you might believe these threat actors only target large
corporations like Verizon and Equifax. Or maybe large cities, like the ransomware that hit the city of Atlanta or more recently, the 20-odd
Texan towns hit simultanously. But ransomware, and malware in general, can be blasted to hundreds of thousands of business email
addresses. And if you're a small business and feel the need to safeguard your data consider taking these proactive steps.

1. **Disable powershell** : While a handy tool for any sysadmin, the use of malicious powershell scripts increased 1000% since last year,
again according to that Symantec report. Even if users aren't local admins over their computers, chances are they are allowed to run powershell.

2. **Have off-site backups**: The most popular vendor in this field is Veeam. Their communuity edition allows you to try out their product 
for free, forever, in a limited capacity. It allows you to back up 10 Virtual Machines and On-Premise Servers. On an added note to this:
conduct Disaster Recovery testing as part of a larger business continuity strategy to confirm backups are suffienct to replicate the production environment

3. **ENABLE MFA ON EVERYTHING**: Even with good training, an employee that fell victim to a spearfishing attack might give up a username and password without realizing it.
A threat actor would normally have everything they need but with MFA, they'll be hit with a challenge prompt (say a 6 digit PIN) before 
they can really do serious damage. For an added layer of security,
and to prevent employees from making their PINs 123456, employ a dictionary that prevents most commonly guessed password and PINs. 

4. **Enable Geo fencing**: This especially holds true for SMBs where employees would not frequently have to leave the country. Azure AD has a very intuitive 
geo-fencing configuration to prevent international threat actors from employing 

5. **Block outbound network traffic to Pastebin** A popular code-hosting site, Pastebin has been used since the early 2000's in hosting
malicious code and making it essentially a remote-execution server.

6. **Block emails that fail SPF**: Sender Policy Framework is part of the triad of email authentication. Next to DMARC (Domain-based Message Authentication, Reporting & Conformance) 
and DKIM (Domain Keys Identified Mail), SPF allows the owner of the domain to specify which IP addresses are permitted to send mail. Basically, creating
this rule means emails coming from untrustworthy sources trashed. For various technical reasons, this is not a magic bullet against all phishing emails,
not even just considering the fact that this authentication method sometimes tends not to be maintained by some embarrassingly large companies.
To truly butress your cyber efforts, create a DMARC record which would block bad actors from spoofing *your* company email address to your own employees.

7. **Patch everything**: Back in 2017, Equifax was hit by an exploit in Apache Struts, a popular open-source web server software that had a 
patch available for months. Patching your operating systems is important but rember to patch the other software your business critical infrastructure runs on.

Here's a link to the Symantic [report](https://www.symantec.com/content/dam/symantec/docs/reports/istr-24-2019-en.pdf)
