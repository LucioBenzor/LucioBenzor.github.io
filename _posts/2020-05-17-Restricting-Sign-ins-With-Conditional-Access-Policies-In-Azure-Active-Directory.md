---
layout: post
title: "Restricting Sign Ins with Azure Active Directory"
date: 2020-05-17
---

A customer I was working with told me: "We're an international organization and most of our users travel around their native country. We
have execitives that sometimes travel internationally. We've had some users succumb to phishing attempts from overseas so we'd like to
restrict sign-ins from outside the country. How can we do this with the Microsoft stack?"

This is a simple enough request that Microsoft created [step-by-step guidance](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-location)
on creating this Policy.

I'd like to use today's post though, to add a visual layer to Microsoft's guidance.

First, we'll go to our Azure Active Directory Admin Center. Then to the Azure AD Conditional Access Pane, and from there Named Locations.
As you can tell, I already have two locations created. You can created named locations to point to Specific IP address ranges (and mark
those addresses as a trusted location" or a single or multiple country or region.

<img src="{{ site.baseurl }}/assets/TrustedLocationCA1.png">

From here
