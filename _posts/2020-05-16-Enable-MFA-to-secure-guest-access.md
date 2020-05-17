---
layout: post
title: "Enable MFA to secure guest access"
date: 2020-05-16
---

MFA is the gold standard control for information security. In this post, I'll show you step by step on configuring MFA to guest accounts
as well as a one big change you should consider making for this to take effect. I should note from the onset that this applies to all guests of the organization - even those without an O365 subscription (like a gmail accounts).

# Setting up SharePoint and OneDrive for guest access MFA

For some reason, SharePoint and OneDrive have their own sharing policies that go out of scope when locking down guest access. This means
users can share content from both services to external users without those users having to reply to an MFA prompt to view the content.

To remedy this: go to the SharePoint Admin Portal > Policies > Sharing and pull down the toggle to "Content can be shared with: Existing
guest"

<img src="{{ site.baseurl }}/assets/SharePointExternalSharing.png">

# MFA with a Conditional Access Policy

Onto the heavy lifting. We'll configure MFA with a conditional access policy. This will be available to you if you have an Azure AD P1/P2
license. Let's go ahead and give this CA policy an easy to remember name. Under assignments, select users and groups. From this panel
select "select users and groups" and toggle "All guests and external users"

<img src="{{ site.baseurl }}/assets/GuestAccess1.png">

From here, lets go down to Cloud Apps or Actions and select which applications you'd like the policy to apply to. Since we're making this change for all guests that have external access, we'll cast a wide net and shoot for all cloud apps

<img src="{{ site.baseurl }}/assets/GuestAccess2.png">

This next step is setting the enforcement mechanism we're triggering in order for the affected users accessing the resource

<img src="{{ site.baseurl }}/assets/GuestAccess3.png">


Take a hard look at that last frame. We're granting access to the external user provided the pass an MFA prompt. We can be a little flexible here and say, toggle "require device to be marked compliant" additionally and as long as the device meets your compliance policy, they can access the resource.

In a follow up post to this I'll show you using the Session pane with Conditional Access App Control through Microsoft's CASB, Microsoft Cloud App Security.

# What MFA methods are available to my users?

First, [here's the up-to-date list](https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-authentication-methods) with the authentications methods available to a company with Azure AD P1/P2.
To set MFA options for your users, lets go to to the Azure AD Dashboard > Security > "Additional cloud-based MFA settings"

<img src="{{ site.baseurl }}/assets/MFAMenu1.png">



