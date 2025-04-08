---
# required metadata

title: Set up panel members in the HR Recruiting app (preview)
description: This article explains how to set up panel members in the HR Recruiting app in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/01/2024
ms.topic: article
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-12-03
ms.dyn365.ops.version: Human Resources

---

# Set up panel members in the HR Recruiting app (preview)

[This article is prerelease documentation and is subject to change.]

This article explains how to set up panel members in the HR Recruiting app in Microsoft Dynamics 365 Human Resources.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Assign panel members to applicants

Recruiters can assign one or more panel members to each stage and set of steps. 

To assign panel members, follow these steps.

1. In the Recruiting app, select **Activity**.
1. Select the stage or steps where you want to add a panel member.
1. Select **New panel member**.
1. Select the hiring team member.
1. Select **Save**.
1. Change the value of the **Hiring activity status** field to **Scheduled**.

> [!NOTE]
> After the **Hiring activity status** field is set to **Scheduled**, interviewers can access the feedback page.
 
## Provide feedback

Panel members or interviewers provide feedback when a candidate is or isn't recommended. They can save their feedback and then return later to edit it. However, after interviewers select **Submit**, they can't change their feedback.

To provide feedback, follow these steps.

1. Select **Feedback**.
1. To provide details, select the feedback.
1. In the **Recommendation** field, select **Yes** or **No**.
1. In the **Interview feedback** field, enter feedback about the candidate. 

## View feedback

Recruiters and the hiring manager can view the feedback that an interviewer provided. However, they can't change it. 

To view feedback, go to the activity, and select the stage or steps.

## Reject applicants

Recruiters can reject one or more applicants at a time. Applicants who are rejected receive a notification by email if the email template is set. 

To reject an applicant, follow these steps.

1. Go to **Job ads** \> **Applicants** \> **Applicant**.
1. Select **Reject**.

The status of the application is changed to **Rejected**.

## Reopen applications

If a candidate's application is reconsidered after it was rejected, the application can be reopened.

To reopen an application, follow these steps.

1. Go to **Job ads** \> **Applicants** \> **Applicant**.
1. Select **Reopen**.

The status of the application is changed to **In progress**.

## Set applicants to Ready to hire

When a recruiter wants to hire a candidate, they can set the applicant to **Ready to hire**. The applicant's information is then transferred to Dynamics 365 Human Resources, and the system administrator can create the worker (employee) record.

To set an applicant to **Ready to hire**, follow these steps.

1. Go to **Job ad** \> **Applicants**.
1. Select the applicant.
1. Select **Ready to hire**.
1. In the confirmation message, select **OK**.

The status of the application is changed to **Ready to hire**.

## Hire candidates 

After a candidate is transferred from the Recruiting add-on to Dynamics 365 Human Resources, the system administrator can view the candidate details in the **Candidates** workspace.

To view the candidate details and create an employee record for the candidate, follow these steps.

1. On the **Candidate** page, select **Hire**.
1. On the **Hire new worker** page, select **Details**.
1. Fill in all the fields.
1. Under **Position details**, verify the information. Make any necessary changes.
1. Under **Onboarding checklists**, select the relevant onboarding checklists for the employee.
1. Select **Continue** to create the employee record.

## Limitations and known issues

- If a level isn't specified in the recruiting request in Dynamics 365 Human Resources, the education details from the recruiting request aren't shown in the job ads.
- In the email template, the user is the category.
- There's no limit on the number of times that the same candidate can be set to **Ready to hire**.
- When candidate data is moved from the Recruiting Add-on to the Dynamics 365 finance and operations environment, only the name is transferred. Other details, such as the educational background, skills, and positions, aren't transferred.
- Localization isn't done.
- When candidates enter personal details in their profile on the careers site, they must select **Save as draft** to enable the **Next** button. They can then select **Next** to provide their educational background and work history, and upload a resume.
- When candidates create a profile on the careers site and want to upload a resume, they must select **Upload** after they select the file.
- If the administrator deletes a candidate's profile, the candidate can still access the careers site, but they can't create a profile. To create a profile, the candidate must remove their existing account and then create a new one. 
