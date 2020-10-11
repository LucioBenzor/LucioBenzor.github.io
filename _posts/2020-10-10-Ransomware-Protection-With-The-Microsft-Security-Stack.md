---
layout: post
title: "Ransomware Protection with the Microsoft Security Stack"
date: 2020-10-10
---

Some time ago, I wrote a post on Defender ATP (now called Microsoft Defender for Endpoint) and the OS hardening measures it offers under attack surface reduction rules that
are useful for crafting a client that's resiliant against next gen attacks.

But seeing as most admins have projects with certain outcomes in mind, I wanted to briefly outline the M365 platforms that will aid in a project
with total ransomware proection as it's outcome. 

After setting expectations and a sucess criteria likely with a OS build to test actual ransomware against, let's talk about the platforms we'll be using. This assumes you have full
M365 E5 or the E5 security license.

Here's the platforms we'll make use of:

* Microsoft Cloud App Security
* Azure Active Directory P2
* Defender for Endpoint/ Micorosft Enterprise E5
* Office 365 Adavanced Threat Protection P2

***What, exactly are we being protected from?***

Bad actors can affect our systems and users a whole lot of different ways. Ransomeware, specifically, is a type of attack that encrypts files, folders, or the whole hard drive with the intent to extract
a ransom from the user or organization. To combat this, we'll need to find a way to make our files and folders resiliant. Because ransomeware is mainly spread via email, we'll need 
some strong controls in place to interrogate the content being displayed to our users and the senders themselves. And we need to accomplish this with a series of controls that
balances security without compromising the productivity of the user base.

***How to accomplish this***

Let's first start by configuring our **Email Security** with O365 by running the Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA) Powershell module to get the current setting for O365 ATP
and recommended settings. The module can be downloaded [here](https://www.powershellgallery.com/packages/ORCA/). Email security is already likely something you have in the form of
Exchange Online Protection configured or maybe the Premium 1 license of O365 Advanced Threat Protection.

Or if you want to skip all that, jump over to the Microsoft site [here](https://docs.microsoft.com/en-us/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp?view=o365-worldwide#office-365-advanced-threat-protection-security)
for a list of the various settings under a *Default, Standard* and *Strict* matrix. The full P2 license offers not only the helpful Safe Links and Safe Attachments policies to
protect users from malicious links directing them to low-reputation sites and from downloading unsafe attachments, but for Enterprise users, the newly revamped Threat Simulator
(think controlled spoofing scenarios to test your users) and the Automated Investigation and Response playbooks allows AI to take the rote work email security admins might take.
**If you're a new admin and need additional guidance on email security, Microsoft has a good primer [here](https://docs.microsoft.com/en-us/microsoft-365/security/office-365-security/protect-against-threats?view=o365-worldwide)**.


Lets next deploy the whole suite of **Attack Surface Reduction rules** offered by Defender for Endpoint. Taking special attention that we know ahead of time we're blocking Macro's. Excel powerusers should be kept in mind for this deployment.

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
|    [Block persistence through WMI event subscription](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-persistence-through-wmi-event-subscription)  

These rules will comprise our 2nd line of defense after email security.

On top of that, our third pillar meant to capture other stray variable is deploying [Application Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) offered with Windows Enterprise E5. Basically, it's add-on that
allows users to acces sites that are untrusted (I.E not explictly whitelisted, or not seen a great deal across the network) but in a hyper-V-based browser container. If our employee
recieves a link that redirects them to a webpage that O365 ATP allows them to access, and Smart Screen allows them to access, they'll be able to access the webpage, but in an 
isolated environment. And from there, we can make further restrictions, like blocking copy/paste functionalities etc.

For our fourth wheel, we'll configure [Controlled Folder Access](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview)
that was specifically designed to thwart Ransomware. Basically, this blocks untrusted applications from accessing protected folders. These protected folders are specified when
controlled folder access is configured.
