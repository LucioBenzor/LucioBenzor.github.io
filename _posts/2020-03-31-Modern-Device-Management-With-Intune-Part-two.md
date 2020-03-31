---
layout: post
title: "Modern Device Management with Intune - Part 2"
date: 2020-03-31
---

Disclaimer: As a Microsoft employee, the below opinions are mine alone and do not necessarily reflect the opinions of Microsoft.

**Enabling a Bring-your-own-device Policy with Intune**

Here's the scenario: A user broke their device and they're hundred of miles away huddled in their apartment. You're huddled away as well in your own house a 1/2 hour away from the office. Instead of going to the office, imaging a computer or worse -- waiting for a computer to arrive from a vendor, you think of what you can do. The user offers to use their personal device in the meantime. Can you grant the user access to the applications and resources they have access to? What are the security implications?

In this overhyped scenario, you can grant a user this functionality, provided a few requirements have been met:
* All Line of Business Applications are off-premises and hosted by a 3rd party or on the cloud
* These applications have been registered in Azure AD and have SSO enabled
* Intune is setup and Device Configuration Profiles are created
* The company portal app is configured with the applications you want available to users
 
