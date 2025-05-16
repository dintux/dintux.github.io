---
title: How Nerdio Automatically Updates FSLogix
date: 2025-05-15 20:14 +0300
categories: [Blogging, Azure, Nerdio, AVD]
tags: [blog,Nerdio, Azure,Cloud,AVD,EUC,FSlogix]
author: Dinusha Tharindu
---



If you've been managing Azure Virtual Desktop (AVD) environments for a while, you probably remember the days when updating FSLogix meant downloading the latest installer manually, pushing it to your image, and hoping no profile corruption followed. But those days are over — thanks to Nerdio’s built-in automation.

Let’s take a look at how Nerdio simplifies FSLogix updates, and what other time-saving magic it performs automatically in your environment.

---

##  FSLogix Now Automatically Updated by Nerdio

Nerdio Manager now **automatically updates FSLogix** to the latest stable version during the image optimization process. This means:

- No more manual downloads or version checks  
- Consistent FSLogix versions across all session hosts  
- Fewer profile-related support issues  
- One less thing to remember during image maintenance

This happens seamlessly during image creation or reimaging — as part of Nerdio’s optimization routine — so you’re always deploying the latest Microsoft-supported FSLogix version without lifting a finger.

---

##  How It Works

When you schedule a reimage or create a new desktop image in Nerdio:

1. Nerdio downloads the latest FSLogix release directly from Microsoft.  
2. It silently installs FSLogix into the image.  
3. It applies best-practice settings for performance and compatibility (Teams, OneDrive, Outlook, etc.).  
4. If needed, you can still layer on your own configuration using Nerdio’s Scripted Actions.



**The result:** Zero-touch FSLogix management, baked into your AVD lifecycle.

![Desktop View](https://nmmhelp.getnerdio.com/hc/article_attachments/27613223771405)
