---
# required metadata

title: Benefits email notification
description: This article provides an overview of the Benefits management email notification feature in Microsoft Dynamics 365 Human Resources.
author: twheeloc  
ms.date: 08/01/2022
ms.topic: overview
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

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]
[!include [banner](../includes/preview-banner.md)]

The email notification feature enables email notifications and reminders to be sent to employees in the following scenarios:

- New hire enrollment
- Open enrollment
- Qualifying life events

You can create and set multiple email templates, and send the notifications by using the **Benefits management** workspace and the **Worker benefits** page. You can also track the notifications/reminders history.

## Set up Human resources shared parameters

On the **Human resources shared parameters** page, you can create benefit email templates for different types of communication that are sent to employees or employee groups.

## Create a new email ID template

To create a new email ID template, follow these steps.

1. Go to **System email templates**.
2. Select **New**.
3. In the **Email ID** field, enter a name.
4. Set the other fields as required.
5. Select **Email message** to upload the template.
6. On the **Human resources shared parameters** page, select the new template under **System templates**, and move it under **Templates for benefits**.

## Send email to employees

To send an email to a new hire who hasn't started yet, follow these steps.

1. Open the **Benefits management** workspace.
2. Select the tile for the group of employees that you want to send the email to.
3. Select **Send email**.
4. Select the employees that you want to send the email to.
5. Select **Send email**.
6. Select the template that you want to use.
7. Select **OK** to send the email.

    You can review the email message and status from the employee's **Worker benefit** page or by selecting **Benefits email history** in the **Links** section of the **Benefits management** workspace. You can also send the email from the **Worker benefit plan** page.

8. To view the benefits email history, in the **Benefits management** workspace, in the **Links** section, select **Benefits email history**.
9. View the complete email history for benefits emails that have been sent. To review the content of the email, select **Show message**.
10. Select **Worker**.
11. On the **Worker benefit plan** page, you can send email and view the benefits email history.

The **Benefits management** workspace includes different tiles. You can send emails by selecting the related template. If the new hire enrollment emails have been sent, select the **New hire not started** tile, and then select the **Send reminder** link. You can select a reminder template and set the title of the notification as a first, second, or third reminder.
