---
layout: post
title: "Azure AD vs Active Directory and the difference"
date: 2019-10-30
---

Though the newest iteration of Microsoft's cloud identity service inherited the name of it's On-premises counterpart it preceded, there's very little resemblance between the two. This isn't necessarily bad -- there are important distinctions between the two-- but it's important to be aware of the nuances between the two and think critically of the use cases for Azure AD.


If you're looking for a carbon copy replacement of Active Directory, I exhort you to check out [Azure Active Directory Domain Services](https://azure.microsoft.com/en-us/services/active-directory-ds/).

# Active Directory #

The biggest commonality between Azure Active Directory and Active Directory is the function to centrally create, manage and secure Identities across a network. Traditionally, Sys Admins have approached this task by further securing these identities with Group policies, practicing role-based access control by lumping users into organizational units, and using Kerberos and NTLM for authentication. From here, administrators would tether on-premises applications (CRMs, ERPs, etc.) against OUs in AD to leverage the Identity and Access Rights  Management infrastructure to grant users access and authenticate against.

As more workloads are shifted to the cloud, On-premises Applications converted to Web Apps, or entirely shifted to SaaS offerings, the traditional Active Directory model is no longer the single viable Identity and Access Management solution.

# Azure Active Directory #

Microsoft introduced Azure AD to help manage those web-based services with the same principles behind AD. Specifically, Azure AD natively supports services that use REST API interfaces. This means it supports authentication through SAML, OAuth, OpenID Connect and WS-Federation protocols -- essentially users will only have to remember a single set of credentials to access Workday, ADP online, QuickBooks, Salesforce, JIRA, and of course Office 365. Similar in concept to a Kerberos ticket, authentication through Azure AD provides users with a token stored on the user's device. Admins can set Group Policy-like policies specifying token expirations, enforcing MFA, and self-service password reset options. 

## Key considerations ##

If you're a small to medium sized company with zero on-premises workloads that rely on AD or are in the process of migrating existing workloads to the cloud, you might wonder if Azure AD should be the sole Identity provider. This is actually a viable option. Before moving forward with that project, consider these nuances:

1. Because there are so many networking technologies (firewalls, Reverse Proxies, DMZ, VLANS) created to protect on-premises workloads, those safeguards don't exist for SaaS applications. In good conscience, when I recommend migrating from AD to Azure AD, I specify companies consider Microsoft's Enterprise Mobility and Security E3 licenses to implement information security measures with device management to keep all company data that's outside the organization's boundaries secure. A single EMS E3 license = 1 Azure AD P1 License, 1 Intune License, and 1 Azure Information Protection License.

2. Because Azure Active Directory doesn't support LDAP, Kerberos, or NTLM, any on-premises applications integrated with AD will no longer work. Migrate these workloads to SaaS applications and secure with Azure AD + MFA

3. Group policy as you once knew it, is no more. Now, you'll configure device policies with Intune. Intune is perfect for a Bring-Your-Own-Device-Policy and better, enforcing what data users can access, modify, and delete on their personal or corporate devices.


