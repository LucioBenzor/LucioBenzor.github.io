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

