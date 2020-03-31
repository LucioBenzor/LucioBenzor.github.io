---
layout: post
title: "Modern Device Management with Intune - Part 1"
date: 2020-03-24
---

Disclaimer: As a Microsoft employee, the below opinions are mine alone and do not necessarily reflect the opinions of Microsoft.

Part of an exciting development professionally is being able to speak and show more broadly to an engaged audience cybersecurity
best practices and demonstrate how Microsoft is taking steps to address these gaps as more and more workers are working remotely.

Chief among their concerns are protecting devices that are not joined to the corporate network and therefore can't recieve Group Policy
updates. The traditional strategy here is to have users connect to the corporate VPN in order to gain access to company software, which also
extends the Infrastructure security umbrella of Proxy Services, Web Filtering, and sometimes EDR to that device. 

Intune steps in here to offer Mobile Device Management and Mobile Application Management to devices the same if they were joined to Active
Directory and bound to Group Policy. Mobile Application Management refers to rules and measures that rest on the application no matter what device they're being accessed
on. Practically, this means a company can extend access to their O365 and internal applications to smartphones, tablets, and Win 10 devices
without having to compromise data integrity policies or device security policies. A company may make a MAM policy forbidding accessing
the company sharepoint site from a device that's jailbroken, for example. A more aggressive policy might be restricting copy/paste and print
functionality for Outlook on any device that doesn't pass an MFA prompt, and isn't Hybrid-Joined.

Mobile Device Management steps this up by requiring a company portal application to be installed on the device. Found in the Windows store,
App Store, and Google Play Store, the company portal application functions as a constant tether to the corporate network and allows Admins
some of the great functions they enjoy with SCCM, and Group Policy. They can deploy applications to the company portal app for users to download.
In place of a standard Win 10 .iso image that gets manually input for each device, the user can login to their Work account on any Win 10 device
and the intune device policies and applications get added to that Win 10 computer.



In the coming posts, I will be doing walking through some of the best features of intune with step-by-step guidance for new admins.

Stay tuned.
