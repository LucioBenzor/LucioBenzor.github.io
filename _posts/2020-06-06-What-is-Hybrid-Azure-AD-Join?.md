---
layout: post
title: "What is Hybrid Azure AD Join?"
date: 2020-06-06
---

Let’s start this post by looking at the [Microsoft definition](https://docs.microsoft.com/en-us/azure/active-directory/devices/concept-azure-ad-join-hybrid)
of what a Hybrid Azure AD Joined device is
> Joined to on-premises AD and Azure AD requiring organizational account to sign into the device

Simple enough. It's a device that retains fealty to Active Directory while being joined to the Azure AD tenant. In what scenarios would this be a good idea to implement? Well, with a Hybrid Azure AD Joined device, you can continue to have Group Policy manage devices, WHILE also allowing Intune and conditional access policies govern other actions or take over parts of Group Policy. It's a way to have your cake and eat it too.

In my experience, businesses with a complicated AD structure, meaning RBAC is heavily scoped through security groups and access to applications relies on AD authentication, see Hybrid joining as a quick way to bridge the gap between the shortcomings of AD and to tap into the cloud-based security and management features offered by Azure AD conditional access policies and Intune. Alternatively, smaller orgs also try this approach when they're also planning to transition to a cloud-first model and are looking to retire AD or have an increasing amount of remote users and fewer resources that require a VPN connection to access.

For a device that's Hybrid Azure AD Joined, the user experience is the same. They'll still login with their AD credentials and be granted a Kerberos ticket to authenticate to AD resources, but now they'll also be granted a session cookie from  Azure AD that does the same for Azure AD resources, like email, Microsoft Teams, Box, Workday, etc.

# What Are The Requirements?
First, you must have Azure AD connected to the AD environment via Azure AD connect

Secondly, users from AD should be synched to Azure AD with the same (User Principal Name) UPNs

# What about a Cloud Management Gateway? Do I need to deploy that?
A good question. Cloud Management Gateway (CMG) refers to using Configuration Manager to continue to manage devices while also leveraging cloud-based management tooling. CMG is not related to Hybrid Azure AD joining a device, although it can be used in managing that device with Configuration Manager.

If you're currently managing devices via Group Policy and want to manage them with Intune or a mixture of both, CMG is not for you.

# I meet the requirements; how do I get started?

In the next post, I'll go over configuring Hybrid Azure AD Join. I'll be using this [documentation](https://docs.microsoft.com/en-us/azure/active-directory/devices/hybrid-azuread-join-managed-domains) to guide us along
