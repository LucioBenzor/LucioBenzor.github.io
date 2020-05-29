---
layout: post
title: "How Defender ATP Thwarts Emerging Attacks"
date: 2020-05-28
---

I've had the good fortune recently to do a few Proof Of Concepts on different security software with some clients who've recovered from ransomeware. Though they had sophisticed
Intrusion Prevetion systems in place and ACLs locked down like Fort Knox, these were grueling events that passed through all sorts of web
filters and AI-powered and deep packet checks that were delivered to a user who unknowlingly opened the payload.

Most of these Ransomeware attacks don't enact their encryption protocol right away. As other security professionals can tell you, they tend
to live off the land a bit and move latterally.

There's a whole range of products and services that exists specifically to combat this scenario, but the one I'd like to show off a bit is
Microsoft's own Endpoint Detection and Response solution. You can rightfully think of it as a host-based intrusion prevention/detection system.
Below is how Microsoft envisions all their services tie together to combat the lifecycle of a typical web-based attack

<img src="{{ site.baseurl }}/assets/DefenderATP1.png">

Anyway, one of the core copetencies it brings to the table and distiguishes itself from other major players in the field like Carbon Black,
CrowdStrike, Cylance, and PaloAlto is Microsoft's device hardening measures - Attack Surface Reduction. Another major advantage is that
it's Agentless. Sneaky Microsoft built the sensor right into the Operating System inexorably.

# What is Attack Surface Reduction?

Microsoft's Attack Surface Reduction rules (reproduced below) are efforts to overcome the common vulnerabilities sophisticated attacks use to compromise a
individual computer. These rules though are only a subset of the Attack Surface Reduction capabilities Defender ATP offers and are the most compelling proactive feature of the service.


<img src="{{ site.baseurl }}/assets/DefenderATP2.png">

|     Rule name                                                                                             |
|-----------------------------------------------------------------------------------------------------------|
|    [Block executable content from email client and webmail](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail)                                                 |
|    [Block all Office applications from creating child   processes](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)                                          |
|    [Block Office applications from creating executable content](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content)                                             |
|    [Block Office applications from injecting code into other   processes](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes)                                   |
|    [Block JavaScript or VBScript from launching downloaded   executable content](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content)                            |
|    [Block execution of potentially obfuscated scripts](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts)                                                      |
|    [Block Win32 API calls from Office macros](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros)                                                               |
|    [Block executable files from running unless they meet a   prevalence, age, or trusted list criterion](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)    |
|    [Use advanced protection against ransomware](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware)                                                             |
|    [Block credential stealing from the Windows local security   authority subsystem (lsass.exe)](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem)            |
|    [Block process creations originating from PSExec and WMI   commands](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)                                     |
|    [Block untrusted and unsigned processes that run from USB](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb)                                               |
|    [Block Office communication application from creating child   processes](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)                                 |
|    [Block Adobe Reader from creating child processes](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)                                                       |
|    [Block persistence through WMI event subscription](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-persistence-through-wmi-event-subscription)                                                       |

# What Are These Emerging Threats?
Why are these rules compelling and cumulatively, how do they coalesce to thwart emerging threats?
According to Symantec's last [Internet Security Threat Report](https://docs.broadcom.com/doc/istr-24-2019-en), 48% of Malicious email attachments are office files. This is up from 5% in 2017.
<img src="{{ site.baseurl }}/assets/DefenderATP3.png">

As the report goes on to note: 
> Use of malicious PowerShell scripts increased by 1,000 percent in 2018, as attackers continued the movement towards living off the land techniques. A common attack scenario uses Office macros to call a PowerShell script, which in turn downloads the malicious payload. Office macro downloaders accounted for the majority of downloader detections, while VBS.Downloader and JS.Downloader threats declined.

Looking back at our Attack Surface Reduction Rules, can you spot which ones would go into effect with these attacks?


# How Can I Test My Defenses?
As part of a POC, we run a series of tests against the newly established environment and Microsoft has a [site](https://demo.wd.microsoft.com/) to run evaluation scenarios to put Defender ATP through its paces. This means running scenarios to test 
each ASR rule.
