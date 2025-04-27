---
title: Azure Shared Access Signature (SAS)
date: 2025-04-24 20:14 +0300
categories: [Blogging, Azure, Storage]
tags: [blog,security, Azure,Cloud,Storage]
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


### **How a Shared Access Signature (SAS) Works**

A Shared Access Signature (SAS) is a token added to the URI of an Azure Storage resource. This token includes query parameters, such as permissions and expiry time, with a signature generated using a key. Azure uses this signature to validate access requests.

* * * * *

### **Types of SAS and Their Authorization Methods**

| Type | Authorization Method |
| --- | --- |
| **User Delegation SAS** | Microsoft Entra ID |
| **Service SAS** | Shared Key |
| **Account SAS** | Shared Key |

Microsoft recommends using **User Delegation SAS** for enhanced security.

* * * * *

### **User Delegation SAS**

This SAS type uses Microsoft Entra credentials and permission settings for access. It supports **Blob Storage** and **Data Lake Storage**, allowing access to blob and dfs endpoints. It's not available for **Queue**, **Table Storage**, or **Azure Files**.

* * * * *

### **Service SAS**

A **Service SAS** is secured with the storage account key and provides access to a single storage service like Blob, Queue, Table, or Azure Files. It is suitable for resource-level access.

* * * * *

### **Account SAS**

Also secured with the account key, an **Account SAS** can grant access across multiple services and includes broader capabilities such as service-level operations and advanced permissions not available with a Service SAS.

* * * * *

### **Best Practices When Using SAS**

To minimize security and functionality risks, follow these practices:

-   **Always Use HTTPS**: Prevents interception during token transmission.

-   **Prefer User Delegation SAS**: Offers better security as it avoids exposing account keys.

-   **Have a Revocation Plan**: Be prepared to invalidate compromised SAS tokens.

-   **Set SAS Expiration Policies**: Limits token lifetime and helps detect over-permissive configurations.

-   **Use Stored Access Policies**: Enables revocation and management without rotating keys (max 5 per container).

-   **Short Expiry for Ad-hoc SAS**: Reduces exposure if leaked.

-   **Auto-renew SAS in Clients**: Especially important for long-lived applications.

-   **Avoid Immediate Start Times**: Allow 15 minutes of skew or avoid setting the start time.

-   **Use Correct Date Formats**: Use ISO 8601 (e.g., `2023-08-15T10:00:00Z`) for compatibility with tools.

-   **Grant Minimum Privileges**: Follow the principle of least privilege.

-   **Track Access via SAS Fields**: Use `sip`, `st`, and `se` parameters for logging and tracing.

-   **Understand Billing Implications**: All SAS usage is billable to your account, including excessive reads or writes.

-   **Validate Written Data**: Prevent harmful data from affecting your app by validating post-upload.

-   **Know When Not to Use SAS**: For sensitive operations, consider using a secure middle-tier service.

-   **Use Monitoring Tools**: Leverage Azure Monitor and Storage logs to detect authorization issues.

-   **Set Expiration Policies Again**: Reinforces best practices by enforcing shorter lifespan for SAS tokens.