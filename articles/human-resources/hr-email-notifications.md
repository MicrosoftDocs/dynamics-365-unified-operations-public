---
# required metadata

title: Benefits email notification
description: This article provides an overview of the Benefits management email notification feature in Dynamics 365 Human Resources. 
author: twheeloc  
ms.date: 08/01/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Benefits email notification


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

**Email notification** provides the ability to send email notifications and reminders to the employees in the following scenarios:
 - new hire enrollment 
 - open enrollment 
 - qualifying life events 

It allows users to create and set multiple email templates and send the notifications using the **Benefits management** workspace and the **Worker benefits** page. You can also track the notifications/reminders history. 

## Set up Human resources shared parameters

You can create **Benefit email templates** on the **Human resources shared parameters** page for different types of communication to send to employees or employee groups. 

## Create a new email ID template

To create a new email ID template:
1. Go to **System email templates**.
2. Click **New** and enter a name in the **Email ID** field.
3. Enter the other fields as needed.
4. Click **Email message** to upload the template. 
5. On the **Human resources shared parameters** page, select the newly created template from **System templates** and move it under **Templates for benefits**. 

## Send email to employees

To send an email to a new hire who hasn't started yet:
1. Go to **Benefits** workspace.
2. Select the tile for the group of employees to send email to.
3. Click **Send email**.
4. Select the employees that you want to email.
5. Click **Send email**.
6. Select the template that you want to use.
7. Click **Ok** to send the email.

You can check the email message and status through the employee’s **Worker benefit** page or using the **Benefits email history** button from the **Links** section. You can also send the email using the **Worker benefit plan** page.  
 
To see the **Benefits email history**, go to **Benefits** workspace, click on **Links** > **Benefits email history**.   
View the complete email history for **Benefits emails** sent. Click on **Show message** on the task bar to review the content of the email.  

8. Click **Worker**. 
9. Go to the **Worker benefit plan** page. From this page, you can **Send email** and **Benefits email history**. You can send email to this specific worker and check the email history for them.  
10. There are different tiles on the **Workspace**. You can send emails by selecting the related template. If the emails have been sent already, for example, if the new hire enrollment emails have been sent, select the **New hire not started** tile, and **Send reminder** link. Select a reminder template and set the title of the notification as a first, second or third reminder  
11. Click on the action center, you will see the alert on the success/failure status on emails sent.  
12. Click on **Benefits email history** from the **Benefit plan** page or **Links**. You can **Send emails** or reminders for **Life events** and **Open enrollment** through the **Workspace**. 



