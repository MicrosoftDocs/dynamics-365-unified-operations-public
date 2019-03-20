---
# required metadata

title: Activities in the processes
description: This topic provides information about the various types of activities that can be used in the hiring process.
author: andreabichsel
manager: AnnBe
ms.date: 02/04/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
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

## Interview schedule and feedback activity

This activity has three components: Candidate availability request, Schedule, and Feedback. Use the interview activity in the job template if you want to include the candidate’s availability request, schedule, and feedback as part of the process instead of using them individually as part of the hiring process. For more information, see [Interview scheduling and feedback](interview-scheduling-feedback.md).

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
