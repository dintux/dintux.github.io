---
title: SMB Signing not required
date: 2020-02-02 20:14 +0300
categories: [Blogging, Srilankan_IT_industry, SriLanka]
tags: [blog, smb, ssl,IT, security]
author: Dinusha Tharindu
---

<!-- Space between Posts -->
<div style="height: 50px;"></div> <!-- This creates space -->

<div style="margin: 20px auto; padding: 20px; max-width: 900px; background: #f4f4f9; border-radius: 10px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);">

  <div style="display: flex; justify-content: center; align-items: flex-start; text-align: center; gap: 25px; padding: 20px; border-radius: 12px; box-shadow: 0 8px 16px rgba(0,0,0,0.15);">
  
    <!-- First Column (LinkedIn Profile) -->
    <div style="flex: 1; max-width: 180px; padding: 15px; border: 2px solid #ccc; border-radius: 12px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
      <a href="https://www.linkedin.com/in/dinushatharindu/" target="_blank" style="text-decoration: none; color: inherit;">
        <strong style="font-size: 16px; color: #333; font-weight: bold;">Meet me on LinkedIn</strong><br><br>
        <img src="https://media.licdn.com/dms/image/v2/D5603AQEvsf5kX0_8jw/profile-displayphoto-shrink_100_100/profile-displayphoto-shrink_100_100/0/1696480058873?e=1751500800&v=beta&t=2beBrDxeX7DAhi0ICDUB89iNUG0z-WGCwOUcdeGDTkk" alt="Dinusha Tharindu" style="border-radius: 50%; width: 60px; height: 60px; margin-bottom: 15px;"><br>
        <span style="font-size: 12px; color: #666;">SME - Azure, DevOps, Citrix and Windows stack.<br>Enthusiast Of Cyber Security.</span>
      </a>
    </div>

    <!-- Second Column (Courses + Certifications) -->
    <div style="flex: 2; display: flex; flex-direction: column; gap: 20px;">
  
      <!-- Free Microsoft Courses -->
      <div style="padding: 15px; border: 2px solid #ccc; border-radius: 12px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
        <a href="https://learn.microsoft.com/copilot/?WT.mc_id=%3Fwt.mc_id%3Dstudentamb_465942" target="_blank" style="text-decoration: none; color: inherit;">
          <strong style="font-size: 16px; color: #333; font-weight: bold;">Free Microsoft Courses</strong><br><br>
          <span style="font-size: 12px; color: #666;">Access free Microsoft learning resources.</span>
        </a>
      </div>
  
      <!-- Free Certifications -->
      <div style="padding: 15px; border: 2px solid #ccc; border-radius: 12px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
        <a href="https://events.microsoft.com/allevents/?WT.mc_id=%3Fwt.mc_id%3Dstudentamb_465942" target="_blank" style="text-decoration: none; color: inherit;">
          <strong style="font-size: 16px; color: #333; font-weight: bold;">Free Certifications</strong><br><br>
          <span style="font-size: 12px; color: #666;">Find and earn free certifications to boost your career.</span>
        </a>
      </div>
  
    </div>

  </div>

</div>

<!-- Space between Posts -->
<div style="height: 50px;"></div> <!-- This creates space -->


you may have came across above statement specially when vulnerability scanning. nessus scanner identified above issue by the plugin ID 57608 as below

  
  
  
  

**Severity:** Medium.

  
  
  
  

**ID:** 57608

  
  
  
  

**File Name:** smb\_signing\_disabled.nasl

  
  
  
  

**Version:** 1.18

  
  
  
  

**Type:** remote

  
  
  
  

**Family:** [Misc.](https://www.tenable.com/plugins/nessus/families/Misc)

  
  
  
  

this issue occurred when SMB traffic or server is not signed so an unauthenticated remote attacker can exploit or launch a MIM or Man -in- Middle attack against the SMB server.

  
  
  
  

the vulnerability can be fixed by enforcing SMB signing from a Group policy for Clinet and server.

  
  
  
  

GPO Location : Computer Configuration\\Windows Settings\\Security Settings\\Local Policies\\Security Options

  
  
  
  

![](https://static.wixstatic.com/media/e54cd3_09013e640c9b46549acb4398cdd817db~mv2.jpg/v1/fill/w_740,h_262,al_c,q_90,usm_0.66_1.00_0.01/e54cd3_09013e640c9b46549acb4398cdd817db~mv2.webp)

  
  
  
  

Fore more Details read below.

  
  
  
  

[https://docs.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/smbv1-microsoft-network-server-digitally-sign-communications-always](https://docs.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/smbv1-microsoft-network-server-digitally-sign-communications-always)

  
  
  
  

[https://docs.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/microsoft-network-server-digitally-sign-communications-always](https://docs.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/microsoft-network-server-digitally-sign-communications-always)

  
  
  
  

Happy Fixing :)

 
