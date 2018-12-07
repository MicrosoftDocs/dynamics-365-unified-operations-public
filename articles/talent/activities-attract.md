---
# required metadata

title: Activities in the processes
description: This topic provides information about the various types of activities that can be used in the hiring process.
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

# Activities in the hiring processes

[!include[banner](../includes/banner.md)]

Activities can be added as a part of the hiring process in Microsoft Dynamics 365 for Talent: Attract. Activities can be added to a process template, or they can be added directly to the hiring process in the job. When a job is defined, a process template is selected, and the activities that are included in the template are applied to the job. If a template isn't selected, the default template is used. The hiring process can also be modified on the job after the template is applied.

> [!NOTE] 
> Process templates are available with the Comprehensive hiring add-on.

## Prospect activity

The Prospect activity controls whether prospects can be added to a job. By default, prospects can be added to a job. To turn off the Prospect activity, set the **Enable prospects** option to **Off**. When the Prospect activity is turned on, hiring managers can add and view prospects, and the **Prospect** tab is shown on the job.

## Application activity

The Application activity is required in the hiring process template. To send email to candidates when they submit their application or are added to the Application stage, set the **Send mail to candidate** option to **On**.

## Scheduler activity

The Scheduler activity is optional. This activity has two components: Candidate availability and Schedule. The Candidate availability component lets you use email to request a candidate's availability. The Schedule component provides the ability to schedule interviews with the candidate and the hiring team. In the Scheduler activity, the following options can be configured: **Request candidate availability**, **Online meeting**, and **Send mail to candidate**.

- To send email to candidates to request their availability, set the **Request candidate availability** option to **On**. If you set the option to **Off**, this step won't be shown in the hiring process on the job.
- To live-stream or have a conference call by using Skype for Business, set the **Online meeting** field to **Skype for Business**. The correct **Join Skype Meeting** link will then be added in the interview meeting request that is sent to interviewers.
- To send email to candidates to finalize the schedule, set the **Send mail to candidate** option to **On**. If you set the option to **Off**, candidates will receive the interview schedule only when they sign in to the Candidate portal.

## Feedback activity

The Feedback activity is optional. This activity lets interview participants enter recommendations for an applicant. They can also enter any feedback comments that they have. If you turn on the **Inherit feedback participants from Hiring Team** option, the recruiter, hiring manager, and interviewers are automatically entered in the Feedback activity. Organizations can allow interviewers to view the feedback of other people before they submit their own feedback. Organizations can also allow interviewers to edit their feedback after they submit it.

## Interview activity

The Interview activity is optional. This activity has three components: Candidate availability, Schedule, and Feedback. The Candidate availability component lets you use email to request a candidate's availability. The Schedule component provides the ability to schedule interviews with the candidate and the hiring team. In the Scheduler activity, the following options can be configured: **Request candidate availability**, **Online meeting**, and **Send mail to candidate**.

- To send email to candidates to request their availability, set the **Request candidate availability** option to **On**. If you set the option to **Off**, this step won't be shown in the hiring process on the job.
- To live-stream or have a conference call by using Skype for Business, set the **Online meeting** field to **Skype for Business**. The correct **Join Skype Meeting** link will then be added in the interview meeting request.
- To send email to candidates to finalize the schedule, set the **Send mail to candidate** option to **On**. If you set the option to **Off**, candidates will receive the interview schedule only when they sign in to the Candidate portal.

>[!NOTE]
> - For all 1:1 interviews, reminders are sent to the interviewers every 24 hours if the interviewer has not responded (accepted or declined) to the interview request.
> - For all panel interviews, there are no automated reminders to respond to interview request. To trigger a reminder manually, edit the interview and use the **Update & Send** option to send the request back to the interviewers.

The Feedback component lets people enter recommendations for an applicant. They can also enter any feedback comments that they have. If you turn on the **Inherit feedback participants from Hiring Team** option, the recruiter, hiring manager, and interviewers are automatically entered in the Feedback component. Organizations can allow interviewers to view the feedback of other people before they submit their own feedback. Organizations can also allow interviewers to edit their feedback after they submit it.

## PowerApps activity

The PowerApps activity lets you embed a Microsoft PowerApps app in your hiring process. The app can be required for all applicants, internal applicants only, external applicants only, or no applicants. If the app is marked as required, it must be completed before the stage can be advanced. If the app isn't marked as required, the activity is an optional step, and the stage can be advanced even if the app isn't completed.

To save the PowerApps activity to the hiring process, you must enter a PowerApps ID. To find the PowerApps ID, go to [PowerApps](https://web.powerapps.com), select **Apps**, and then select **Details**.

If you select the **Allow adding participants for this activity** option, additional contributors can be added for an application that uses the PowerApps activity. For example, an organization has created a PowerApps app that is a library of interview questions for technical roles. The organization is now hiring a new software developer and has added the PowerApps activity to the hiring process for the Software Developer role. If the **Allow adding participants for this activity** option is selected, a recruiter or hiring manager who is viewing an applicant for the Software Developer role can add people to the PowerApps activity. Those people can then view the app that has the interview questions.

> [!NOTE]
> The PowerApps activity is available only with the Comprehensive hiring add-on.

## YouTube activity

The YouTube activity lets you share a YouTube video as part of your hiring process. To save the YouTube activity to the hiring process, you must specify the URL of the YouTube video. As for the PowerApps activity, you can allow participants to be added to the activity. If you select the **Show only to candidate** option, the video is shown only as part of the candidate experience. It isn't shown in the hiring process in Attract.

> [!NOTE]
> The YouTube activity is available only with the Comprehensive hiring add-on.

## Web content activity

The Web content activity lets you embed online content in your hiring process. To save the Web content activity to the hiring process, you must specify the URL of the content. As for the PowerApps and YouTube activities, you can allow participants to be added to the activity. If you select the **Show only to candidate** option, the content is shown only as part of the candidate experience. It isn't shown in the hiring process in Attract. You can select the size of the content that is shown.

> [!NOTE]
> The Web content activity is available only with the Comprehensive hiring add-on.

## Microsoft Forms activity

The Microsoft Forms activity lets you embed a Microsoft Forms form in your hiring process. Microsoft Forms lets you create quizzes, surveys, and polls. To save the Microsoft Forms activity to the hiring process, you must specify of the URL of the form. As for the PowerApps, YouTube, and Web content activities, you can allow participants to be added to the activity. If you select the **Show only to candidate** option, the form is shown only as part of the candidate experience. It isn't shown in the hiring process in Attract.

In Microsoft Forms, authors can change their settings to let users outside their organization respond to their survey or quiz. In this case, users submit responses anonymously. If you want to see who has filled out your survey or quiz, you can require that respondents enter their names as part of the survey or quiz.

> [!NOTE]
> The Microsoft Forms activity is available only with the Comprehensive hiring add-on.
