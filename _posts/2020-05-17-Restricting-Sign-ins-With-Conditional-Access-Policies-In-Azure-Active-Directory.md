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
