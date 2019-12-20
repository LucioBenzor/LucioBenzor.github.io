---
layout: post
title: "A Solution For Pervasive Local Admin Access"
date: 2019-12-18
---

I've seen this scenario play out a few times: Users complain that IT is unfairly constraining them and affecting their productivity by not
allowing them access to download the programs they need to run on their computers. Eventually security controls are rolled back and the
information technology department accedes to the users' wishes and everyone is granted local admin access over their computers.

You don't have to have a cybersecurity background to see what happens when folks are routinely granted this level of access. It's more than
everyone has Spotify running on their computers. Users in general tend to download programs without doing much due dilligence on their
source. So then a free program that promises to allow you to edit .PDFs a user downloads becomes ground zero for a pass-the-hash attack,
or a simple trojan infecting the computer.

What should an IT professional do when they inherit an environment where users enjoy local admin access over their computers?

# The Principle of Least Privilege #

As a principle, security measures only work when business justification is strong. That means the underlying IT perogative to safeguard
the companany's data assets take the form of measures that everyone understands do not affect productivity in a substantial way. When
too many users are annoyed with MFA, whether they were surprised by it's sudden activation or don't understand when they're prompted for
a 2nd token of authenitication, it gets rolled back.

The principle of least privilege should guide what level of access users enjoy. By default, users don't need access to download programs
on a day-to-day basis to complete the tasks their jobs require.

# LAPS #

So then, once the case is made and business leaders accept that security controls must be implemented to shore up their defences against
threats and be proactive, IT removes users having local admin access over their computers. When they want to install a driver or download
a program, and the ticket recieves approval from a manager with a business justification, someone from helpdesk would remote into the
computer and type their own password when they get the UAC prompt. The security issue with this method is passwords are cached by Windows
by default. 

Microsoft overcame this problem with a their Local Admin Password Solution (LAPS). As a Microsft [TechNet article](https://blogs.technet.microsoft.com/secguide/2018/12/10/remote-use-of-local-accounts-laps-changes-everything/) puts it: "LAPS is an elegant 
and lightweight mechanism for Active Directory domain-joined systems that periodically sets each computer’s admin account password to a new random
and unique value, storing the password in a secured confidential attribute on the corresponding computer object in Active Directory where only
specifically-authorized users can retrieve it."

Practically, this changes the old paradigm where helpdesk would enter in their domain admin password in the users computer for the UAC
prompt. Instead, they would get the password for the workstation and uses the LAPS-managed local admin account to login.








