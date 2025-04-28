---
title: Windows Task Scheduler  Scripting  batch
date: 2021-10-21 20:14 +0300
categories: [Blogging, windows, SriLanka]
tags: [blog, security, taskscheduler,IT, industry]
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
        <a href="https://learn.microsoft.com/copilot/?WT.mc_id=studentamb_465942" target="_blank" style="text-decoration: none; color: inherit;">
          <strong style="font-size: 16px; color: #333; font-weight: bold;">Free Microsoft Courses</strong><br><br>
          <span style="font-size: 12px; color: #666;">Access free Microsoft learning resources.</span>
        </a>
      </div>
  
      <!-- Free Certifications -->
      <div style="padding: 15px; border: 2px solid #ccc; border-radius: 12px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
        <a href="https://events.microsoft.com/allevents/?WT.mc_id=studentamb_465942" target="_blank" style="text-decoration: none; color: inherit;">
          <strong style="font-size: 16px; color: #333; font-weight: bold;">Free Certifications</strong><br><br>
          <span style="font-size: 12px; color: #666;">Find and earn free certifications to boost your career.</span>
        </a>
      </div>
  
    </div>

  </div>

</div>

<!-- Space between Posts -->
<div style="height: 50px;"></div> <!-- This creates space -->


![Desktop View](https://i.stack.imgur.com/FTZrw.png)


I have come across a scenario where there is batch script need to be run daily, recurring in every 15 min without any human interaction using the windows task scheduler.

  
  
  
  

a typical script , path has been pointed to correct location.  
  
as per the requirement script has been been added to the task scheduler and all the settings been configured correctly. but in the #1 attempt script run with out any errors and complete it's intended tasks but when it's come to it's #2 attempt in next 15 min script run and finished without any errors , but it's not completing it's expected tasks on the script it self.

  
  
  
  

![](https://cybertuxlk.files.wordpress.com/2020/02/2020-02-11_13-26-21-2.png?w=1024)

  
  
  
  

I tried to go through task sheduler events , but there's no any faliures , warning events or anything to isolate this issue , so tried to manuelly run this script , and noticed.

  
  
  
  

*   running the script manually , it execute it's all tasks successfully , but when it's come to run the script with task scheduler only, script start to fail in it's second attempt and continued.

  
  
  
  

After spending some time on troubleshooting , I noticed the root cause for script to fail and the resolution to fix.

  
  
  
  

The primary problem was, ones the task started it's #1 attempt and finished , it should be mentioned the object residing place to for next scheduler task occurrence to find the path. if it's not mentioned on " Start in(Optional)" the script won't execute , but task scheduler will mark as that task has been performed successfully .

  
  
  
  

so the resolution is :

  
  
  
  

*   Select the action as "Start Program".
*   Brows the path to script ( "path\\file to script with in quotation mark " )
*   mention the folder path ( C:\\Folder\\script\\ )

  
  
  
  

![](https://cybertuxlk.files.wordpress.com/2020/02/2020-02-11_14-08-51.png?w=1024)

  
  
  
  

After configuring above setting , the script and scheduler started working the was it expected.

  
  
  
  

I hope this will save some ones Day or time :) !

