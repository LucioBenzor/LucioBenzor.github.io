---
layout: post
title: "Restricting Sign Ins with Azure Active Directory"
date: 2020-05-17
---

A customer I was working with told me: "We're an international organization and most of our users travel around their native country. We
have execitives that sometimes travel internationally. We've had some users succumb to phishing attempts from overseas so we'd like to
restrict sign-ins from outside the country. How can we do this with the Microsoft stack?"

This is a simple enough request that Microsoft created [step-by-step guidance](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-location)
on creating this Policy. An Azure AD P1/P2 license is required to configure this policy and can be found in the Enterprise Mobility + Security suite or M365 Business, E3 or E5.

I'd like to use today's post though, to add a visual layer to Microsoft's guidance.

First, we'll go to our Azure Active Directory Admin Center. Then to the Azure AD Conditional Access Pane, and from there Named Locations.
As you can tell, I already have two locations created. Our Atlanta Office and Our outpost in Haiti. You can create named locations to point to Specific IP address ranges (and mark
those addresses as a trusted location" or a single or multiple countries or regions.

<img src="{{ site.baseurl }}/assets/TrustedLocationCA1.png">

From here we worked on splitting users up into country-specific groups so the Conditional Access Policy can apply to users in a single country for ease of use. E.G., our Atlanta-based CA policy affects only users in the Atlanta Office group, while the Peru-based CA policy affects our users in Peru.

Let's go ahead and navigate to the Conditional Access pane and create a new Conditional Access Policy. I'm calling this one Trusted Locations Sign in only - Atlanta and as you can see I've added our Atlanta users there. 

<img src="{{ site.baseurl }}/assets/TrustedLocationCA2.png">

Stop here and decide if there's some C-level executives you'd like to exclude if they're the type to travel on a moment's notice. We wouldn't want to block their access. Just head on over to that Exclude pane and shoot them over in the exclusion group (best practice here is to exclude groups and not individual members).

Select all cloud apps in the "Cloud Apps or Actions" panel

<img src="{{ site.baseurl }}/assets/TrustedLocationCA3.png">

Lets go to the Conditions Panel and go to Locations and configure it to include "Any Location".

<img src="{{ site.baseurl }}/assets/TrustedLocationCA4.png">

Immediately after, lets go to exclude and select the Atlanta Office

<img src="{{ site.baseurl }}/assets/TrustedLocationCA5.png">

Let's finish this up by going to the Grant panel at the bottom and selecting "Block Access".

<img src="{{ site.baseurl }}/assets/TrustedLocationCA6.png">

Enabling this policy will block any users in the Atlanta Office Group from accessing cloud resources from anywhere in the world except the Atlanta Office (really just anywhere in the US)







