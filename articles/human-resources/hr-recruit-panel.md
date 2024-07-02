---
# required metadata

title: Set up panel members in the HR recruiting app
description: This article describes how to set up panel members in the HR recruiting app in Dynamics 365 Human Resources.
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

# Set up panel members in the HR recruiting app

[This article is prerelease documentation and is subject to change.]

This article describes how to set up panel members in the HR recruiting app in Dynamics 365 Human Resources.

## Panel members and feedback
Recruiters can assign one or more panel members to each stage and steps. 

### Assign panel members to applicants

To assign panel members, follow these steps:
1. Go to **Activity**.
2. Select the stage or steps where you want to add panel member.
3. Click **+New panel member**.
4. Select the hiring team member.
5. Click **Save**.
6. Change the **Hiring activity status** to **Scheduled**.

>[!Note]
> Interviewers access the feedback page after the **Hiring activity status** is **Scheduled**.
 

### Provide feedback
Panel members or interviewers provide feedback when a candidate is or isn't recommended and adding feedback. They can save their feedback and return later to edit their feedback. After clicking **Submit**, interviewers can't modify their feedback.

To provide feedback, follow these steps: 
1. Log in to the Recruiting app, select **Feedback**.
2. To provide details, click on the feedback.
3. Select **Yes** or **No** in **Recommendation**.
4. In **Interview feedback**, enter feedback about the candidate. 

 
### View feedback
Recruiters or the hiring manager aren't allowed to change the feedback given by interviewer. They can only view the feedback provided by interviewer. 
To see feedback, go to the activity and select the stage or steps.

### Reject
Recruiters can reject one or multiple applicants at a time. On the rejection of applicants, applicants get a notification in their email if the email template is set. 
To reject the applicant, follow these steps:
1. Go to **Job ads** > **Applicants** > **Applicant**.
2. Click **Reject**.
The status of the application is changed **Rejected**.


### Reopen
When a candidate application is reconsidered after rejection, the application can be reopened. 
To reopen the application, follow these steps:
1. Go to **Job ads** > **Applicants** > **Applicant**.
2. Click **Reopen**. The status of the application changes to **In progress**.

### Ready to hire
Recruiter can set the applicant to hire when the recruiter wants to hire the candidate. Setting the applicant as ready to hire, sends the applicant information to Dynamics 365 Human Resources. The System 
administrator can create the worker.
To set the applicant to ready to hire, follow these steps: 
1. Go to **Job ad** > **Applicants**.
2. Select the applicant.
3. Click **Ready to hire**, a confirmation message is displayed.
4. Click **OK**. The application status changes to **Ready to hire**.

### Hire 

When the candidate is transferred from Recruiting add-on, the system administrator can view the candidate details in the **Candidates** workspace.
To view candidate details, follow these steps:
1. On the **Candidate** page, select **Hire**.
2. On the **Hire new worker** page, > **Details**. Complete all the fields.
3. Under **Position details**, verify and change information as necessary.
4. Under **Onboarding checklists**, select the relevant onboarding checklists for this employee.
5. Select **Continue** to create the employee record.

#### Limitations and known issues

•	If a level isn't specified in the **Recruiting request** in Dynamics 365 Human Resources, the education details from the recruiting request won't display in the Job ads.
•	In the Email template, the user is the Category.
•	There's no limit on how many times the same candidate can be sent as **Ready to hire**.
•	Only the name is getting transferred to Dynamics 365 finance and operations environment when candidate data is moved from Recruiting Add-on to Dynamics 365 finance and operations environment. Other details 
like **education background**, **Skills**, **Positions** aren't transferred.
•	Localization isn't complete.
•	Candidates need to click **Save as draft** to enable **Next**.
•	Candidates need to click **Upload** after selecting the file while creating the profile in career site.
•	If the administrator deletes a candidate's profile, candidates can still access the careers site, but they can't make a profile. To create a profile, candidates need to remove their account and make a new one. 











