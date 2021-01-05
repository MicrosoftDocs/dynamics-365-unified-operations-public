---
# required metadata

title: Add activities to a hiring process 
description: This topic provides information about the various types of activities you can add to a hiring process in Microsoft Dynamics 365 Talent - Attract.
author: hasrivas
manager: AnnBe
ms.date: 05/28/2019
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
# ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: shielas
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Add activities to a hiring process

[!include [banner](includes/banner.md)]

Activities can be added as a part of the hiring process in Microsoft Dynamics 365 Talent: Attract. Activities can be added to a process template, or they can be added directly to the hiring process in the job. When a job is defined, a process template is selected, and the activities that are included in the template are applied to the job. If a template isn't selected, the default template is used. The hiring process can also be modified on the job after the template is applied.

> [!NOTE] 
> Process templates are available with the Comprehensive hiring add-on. For more information, see [Which version of Microsoft Dynamics 365 Talent - Attract](./attract-comprehensive-hiring.md).

## Prospect activity

The Prospect activity controls whether prospects can be added to a job. By default, prospects can be added to a job. To turn off the Prospect activity, set the **Enable prospects** option to **Off**. When the Prospect activity is turned on, hiring managers can add and view prospects, and the **Prospect** tab is shown on the job.

> [!NOTE]
> To allow candidates to be added to a job from LinkedIn, you must set the **Enable prospects** option to **On**.

## Application activity

The Application activity is required in the hiring process template. To send email to candidates when they submit their application or are added to the Application stage, set the **Send mail to candidate** option to **On**.

## Interview schedule and feedback activity

This activity has three components: Candidate availability request, Schedule, and Feedback. Use the interview activity in the job template if you want to include the candidate’s availability request, schedule, and feedback as part of the process instead of using them individually as part of the hiring process. For more information, see [Interview scheduling and feedback](interview-scheduling-feedback.md).

## Power Apps activity

The Power Apps activity lets you embed a Microsoft Power Apps app in your hiring process. The app can be required for all applicants, internal applicants only, external applicants only, or no applicants. If the app is marked as required, it must be completed before the stage can be advanced. To be considered complete, the **JobApplicationStatus** field must be set to **Complete**. This field is located in the JobApplicationActivity entity, so the Power Apps app will need to update this field before the stage can be advanced. If the app isn't marked as required, the activity is an optional step, and the stage can be advanced even if the app isn't completed.

To save the Power Apps activity to the hiring process, you must enter a Power Apps ID. To find the Power Apps ID, go to [Power Apps](https://web.powerapps.com), select **Apps**, and then select **Details**.

By default, the Power Apps activity is available to the Hiring Manager, Recruiter, and their delegates. If you select the **Allow adding participants for this activity** option, additional participants from the hiring team can be added for an application that uses the Power Apps activity. For example, an organization has created a Power Apps app that is a library of interview questions for technical roles. The organization is now hiring a new software developer and has added the Power Apps activity to the hiring process for the Software Developer role. If the **Allow adding participants for this activity** option is selected, a recruiter or hiring manager who is viewing an applicant for the Software Developer role can add interviewers to the Power Apps activity. Those people can then view the app that has the interview questions.

> [!NOTE]
> The Power Apps activity is available only with the Comprehensive hiring add-on. For more information, see [Which version of Microsoft Dynamics 365 Talent - Attract](./attract-comprehensive-hiring.md).

## YouTube activity

The YouTube activity lets you share a YouTube video as part of your hiring process. To save the YouTube activity to the hiring process, you must specify the URL of the YouTube video. You can choose to display the content to the **Hiring Team**, **Internal Candidates only**, **External Candidates only**, or **All Candidates**. Like the Power Apps activity, you can allow hiring team participants to be added to the activity. If you choose to show the content to candidates, the video is shown only as part of the candidate experience and not in the hiring process.

> [!NOTE]
> The YouTube activity is available only with the Comprehensive hiring add-on. For more information, see [Which version of Microsoft Dynamics 365 Talent - Attract](./attract-comprehensive-hiring.md).

## Web content activity

The Web content activity lets you embed online content in your hiring process. To save the Web content activity to the hiring process, you must specify the URL of the content. You can choose to display the content to the **Hiring Team**, **Internal Candidates only**, **External Candidates only**, or **All Candidates**. Like the Power Apps and YouTube activities, you can allow hiring team participants to be added to the activity. If you choose to show the content to candidates, the Web content is shown only as part of the candidate experience and not in the hiring process. You can choose the size of the content that is shown.

> [!NOTE]
> The Web content activity is available only with the Comprehensive hiring add-on. For more information, see [Which version of Microsoft Dynamics 365 Talent - Attract](./attract-comprehensive-hiring.md).

## Microsoft Forms activity

The Microsoft Forms activity lets you embed a Microsoft Forms activity in your hiring process. Microsoft Forms lets you create quizzes, surveys, and polls. To save the Microsoft Forms activity to the hiring process, you must specify the URL of the form. You can choose to display the content to the **Hiring Team**, **Internal Candidates only**, **External Candidates only**, or **All Candidates**. Like the Power Apps, YouTube, and Web content activities, you can allow hiring team participants to be added to the activity. If you choose to show the content to candidates, the form is shown only as part of the candidate experience and not in the hiring process.

In Microsoft Forms, authors can change their settings to let users outside their organization respond to their survey or quiz. In this case, users submit responses anonymously. If you want to see who has filled out your survey or quiz, you can require that respondents enter their names as part of the survey or quiz.

> [!NOTE]
> The Microsoft Forms activity is available only with the Comprehensive hiring add-on. For more information, see [Which version of Microsoft Dynamics 365 Talent - Attract](./attract-comprehensive-hiring.md).

## Offer activity

The hiring process template requires the Offer activity. To use the integrated offer management app, set **Launch Offer Management App on Prepare Offer** to **On**. If this setting is off, the candidate won't appear in the Offer app, so you'll have to track updates to a candidate's offer activity manually. To define whether hiring managers can prepare the offer for the candidate in the Offer app, set **Hiring Managers can prepare offer** to **On**. If the job has multiple positions associated with it, you can decide whether you want to prepare multiple offers against the same position number. If you want to allow only one offer per position per job, set **Allow Positions to be reused within job** to **Off**.

> [!NOTE]
> The integrated Offer Management App is available only with the Comprehensive hiring add-on. For more information, see [Which version of Microsoft Dynamics 365 Talent - Attract](./attract-comprehensive-hiring.md).


