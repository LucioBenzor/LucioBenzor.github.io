---
layout: post
title: "Identity And Access Management And Its Role In Cloud Security"
date: 2020-11-05
---

More companies than ever before are realizing the shortcomings of having applications hosted on on-premises datacenters. They're fickle to manage and update. A userbase to
support, servers to patch, ever-growing storage to keep an eye out for, and redundant controls to implement -- all on a likely shoestring budget. Security is "nice-to-have." At least that's the narrative
that SAAS vendors have been telling. But through the narrative there's truth behind the murky state of on-prem app hosting and more business are making use of software as a 
service applications that offer per-user licensing costs which makes resource planning easier and promises to take the strain off application management and security
off our beleaguered admins.

You've likely seen this chart illustrating the distinctions between IaaS, PaaS and SaaS

<a href="{{ site.baseurl }}/assets/saas-vs-paas-vs-iaas.png">
<img src="{{ site.baseurl }}/assets/saas-vs-paas-vs-iaas.png">
<a/>

It looks like with SaaS applications we're absolved of some major responsibilities and headaches - really all of them. So what's left for us as admins to configure? Likely just creating users and assigning them licenses and doing some training on how the interface works (lightly) right? On the security front we're not responsible
for ensuring the front-end side of the application is secure from script kiddies testing the input validation with drop table statements.

Instead, what we're chiefly responsible is data access security. If we incorrectly configure storage permissions, have lax admin access and data loss prevention controls, we're at a liability for data leakage and inappropriate handling by our users. Okay fine, so we'll have the vendor or a consultancy help us set up the service, you might think. Especially since it's a one-time setup. Which is fine to do. They'll likely do a pretty good job.

More urgently for us as admins to deploy to control data access is multi-factor authentication for our user logins. That way, if a malicious user attempts to access our 
employee's resources, they won't be able to meet the challenge prompt to gain access. 

But simply having MFA doesn't exactly absolve us our security duties. If you're an enterprise with a sprawling user-base with roles to dole out and Role-Based Access Controls to noodle on, you would do well to have an Identity and Access Management lifecycle like the one illustrated below (from O'Reilly's Practical Cloud Security)


<a href="{{ site.baseurl }}/assets/IAM_lifecycle.jpg">
<img src="{{ site.baseurl }}/assets/IAM_lifecycle.jpg">
<a/>



