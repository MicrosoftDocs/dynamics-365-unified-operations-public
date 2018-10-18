---
# required metadata

title: Hiring processes
description: This topic provides information about the various activity types that can be used in the hiring process.
author: 
manager: AnnBe
ms.date: 10/15/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Hiring processes

[!include[banner](../includes/banner.md)]

Activities can be added as a part of the hiring process in Attract. Activities can be added to a process template or can be added directly to the hiring process within the job. When a job is defined, a process template is selected and the activities included in the template are applied to the job. If a template is not selected, the default template will be used. The hiring process can also be modified on the job after the template is applied. 

> [!NOTE] 
> Process templates are available with the Comprehensive hiring add-on.

## Prospect activity

The Prospect activity controls whether prospects can be added to a job or not. By default, prospects can be added to a job. To turn this off, change the **Enable prospects** toggle to **Off**. When the Prospect activity is enabled, the
administrator can choose to allow hiring managers to add and view prospects. When this is on, the **Prospect** tab will be displayed within the job.

## Application activity

The Application activity is required in the hiring process template. If you want to send an email to a candidate when the candidate submits her or his application or is added to the application stage, set the **Send mail to candidate** toggle to **On**.

## Scheduler activity

The Scheduler activity is optional. This activity has two components, **Candidate availability** and **Schedule**. The **Candidate
availability** component provides the option to use email to request a candidate’s availability. The **Schedule** component provides the ability to schedule interviews with the candidate and the hiring team. Within the Scheduler
activity, the following options can be configured, **Request candidate availability**, **Online meeting** , and **Send mail to candidate**.

To send an email to the candidate to request their availability, set the **Request candidate availability** option to **On**. If this option is set to **Off**, this step will not display within the hiring process on the job.

To live stream or have a conference call by using Skype for Business set the **Online meeting** option to Skype for Business. This will insert the right **Join Skype Meeting** link in the interview meeting request that is sent to the interviewers.

To send an email to the candidate to finalize the schedule, set the **Send mail to candidate option** to **On**. If this is set to **Off**, the candidate will receive the interview schedule only when they log in to the Candidate portal.

## Feedback activity

The Feedback activity is optional. This activity provides an option for interview participants to enter a recommendation on an applicant as well as enter in any feedback comments that they have. If you turn on **Inherit feedback participants from Hiring Team**, the recruiter, hiring manager, and interviewers in the feedback activity will automatically default in. Organizations can choose to allow
interviewers to see the feedback of others individuals prior to submitting their own. Also, organizations can allow interviewers to edit their feedback after their first submission.

## Interview activity

The Interview activity is optional . This activity has three components, **Candidate availability**, **Schedule** and **Feedback**. The
**Candidate availability** component provides the option to use email to request a candidate’s availability. The **Schedule** component provides the ability to schedule interviews with the candidate and the hiring team. In the Scheduler activity, the following options can be configured, **Request candidate availability**, **Online meeting**, and **Send mail to candidate**.

To send an email to the candidate to request their availability, set the **Request candidate availability** option to **On**. If this is set to **Off** this option will not display within the hiring process on the job.

To live stream or have a conference call via Skype for Business set the **Online
meeting** option to Skype for Business. This will insert the ‘Join Skype
Meeting’ in the interview meeting request.

To send an email to the candidate to finalize the schedule, set the **Send mail to candidate option** to **On**. If this is set to **Off**, the candidate will get the interview schedule when they login to the Candidate portal.

The **feedback** component provides an option for individuals to enter a recommendation on an applicant as well as enter in any feedback comments that they have. If you turn on **Inherit feedback participants from Hiring Team**, the the recruiter, hiring manager, and interviewers in the feedback activity will automatically default in.
Organizations can choose to allow interviewers to see the feedback of others individuals prior to submitting their own. Also, organizations can allow interviewers to edit their feedback after their first submission.

## PowerApps activity

The PowerApps activity provides an option to embed a PowerApp in the hiring process. The PowerApp can be required for all applicants, internal applicants, external applicants, or none. If the PowerApp is marked as required, then the PowerApp must be completed before the stage can be advanced. If the activity is not required, the PowerApp is an optional step and the stage can be advanced without the PowerApp being completed.

A PowerApp ID is required to be able to save the activity to the hiring process. To find the PowerApps ID, go to [PowerApps](https://web.powerapps.com), select **Apps**, and then click **Details**.

If you select to **Allow adding participants for this activity**, additional contributors can be added for an application that is using this activity. For example, an organization created a PowerApp that is a library of interview questions for technical roles. The organization is hiring a new Software developer. They have added this PowerApp activity to their hiring process for
the Software developer role. When the **Allow adding participants** option is selected, the recruiter or hiring manager can view an applicant for the Software Developer role and choose to add individuals to view the PowerApp that they created with the library of interview questions.

> [!NOTE] 
> The PowerApps activity is only available with the Comprehensive hiring add-on.

## YouTube activity

The **YouTube** activity allows you to add the sharing of a video to your hiring process. The YouTube video URL is required to save the activity to the hiring process. Similar to the PowerApps activity, you can allow adding participants to this activity. If you select **Show only to candidate**, the video will only display in the candidate experience and will not show in the hiring process within Attract.

> [!NOTE] 
> The YouTube activity is only available with the Comprehensive hiring add-on.


## Web content activity

The **Web content** activity allows you to embed a URL with content into the hiring process. The URL is required to save the activity to the hiring process. Similar to the PowerApps activity, you can allow adding participants to this activity. If you select **Show only to
candidate**, the content will only display in the candidate experience and will not show in the hiring process within Attract. You can also select the content size to display.

> [!NOTE] 
> The Web content activity is only available with the ComprehensiveH hiring add-on


## Microsoft Forms activity

The **Microsoft Forms** activity allows you to embed a Microsoft Form into your hiring process. Microsoft Forms allow you to create quizzes, surveys and polls. The Microsoft forms URL is required to save the activity to the hiring process. Similar to the PowerApps activity, you can allow adding participants to this activity. If you select **Show only to candidate**, the content will only display in the candidate experience and will not show in the hiring process within Attract.

In Microsoft Forms, authors can toggle their settings to allow users outside of their organization to respond to their survey or quiz. In this case, users will be submitting responses anonymously. If you want to see who has filled out your survey or quiz, you can require respondents to fill in their names as part of your questionnaire.

> [!NOTE] 
> The Microsoft Forms activity is only available with the Comprehensive hiring add-on.
