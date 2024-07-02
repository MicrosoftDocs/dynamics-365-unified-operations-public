---
# required metadata

title: Set up job ads in the Recruiting app 
description: This article describes how to set up the job ads in the Recruiting app in Dynamics 365 Human Resources.
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

# Set up job ads in the Recruiting app 

[This article is prerelease documentation and is subject to change.]

This article describes how to set up the job ads in the Recruiting app in Dynamics 365 Human Resources.

Job ads are an essential part of the hiring process. This is used to advertise one or more job openings within a company. These ads are published on various platforms, such as job boards, company websites, social media, and other related channels. 

In the Recruiting app, job ads are a section where recruiters create job ads. Job ads contain a Job ID, number of openings, estimated start date, compensation, currency, company (legal entity), job location, skills, position type, and job description.

To create a job ad, fill in the following fields:
 - **Job title** - Clearly stating the position's title helps candidates quickly understand the role.
 - **Description** - This section provides a detailed overview of the responsibilities, duties, and qualifications associated with the job. It outlines what the role entails and the skills or experience required.
 - **Estimated start** - Highlighting the essential qualifications, such as education, experience, skills, and any specific certifications, helps candidates assess their suitability for the position.
 - **Company** - Including information about the company's values, culture, and mission can help attract candidates who align with the organization's goals.
 - **Job location** - Specifying the job's location is crucial for candidates to determine if the position is geographically suitable for them.
 - **Skills** - Clear instructions on how to apply, including details about submitting a resume, cover letter, or any other required documents, are essential.
 - **Compensation** - Providing information about the salary range, benefits, and any perks associated with the position can be attractive to potential candidates.
 - **Currency** - Gives an option to select the currency of the compensation.
 - **Position type** - Allows an option to create job ads for Full-time, part-time contract employees.

### Recruiting request
A recruiting request is a document that is used to create the requirement for job openings by the hiring managers in Dynamics 365 Finance. To publish the recruiting request, it must be in a active status. After the recruiting request is published, the recruiting request can't be updated. For more information, see [Recruit job candidates](/hr-personnel-recruit). 

### Job ad status
There are five different job ad statuses:
 - **Draft** - The job ad isn't saved.
 - **In progress** - The job ad is saved and the process of adding hiring team member or hiring template or approval is in progress.
 - **Active** - The job ad is posted to the job Careers site. The job ad details can't be changed after the job is posted.
 - **Inactive** - The job ad is deactivated after posting to job boards.
 - **Complete** - The job ad is completed after clicking **Complete**. Activities can't be added after the job is completed.

### Hiring team
The hiring team is a group of team members responsible for the hiring activities of a particular job ad. There can be multiple recruiters, hiring managers and interviewers. One recruiter and one hiring manager need to be selected as primary. Only hiring team members can take part in interview processes. 
To select hiring team member, follow these steps:
1.	Select **Hiring team** tab.
2.	Click **+New**. A pop-up opens.
3.	Search for **Name** and select the name from drop down or enter the name. 
4.	Select the role.
5.	Click **Save** and **Close**.

 
### Primary recruiter
There can be many recruiters in a job ad but there should be at least one primary recruiter. To select a Primary recruiter, select the **Set as primary** checkbox.
 
### Primary hiring manager
A job ad can have multiple hiring managers as members of the hiring team, but it must have one Primary hiring manager. To choose the Primary hiring manager, select **Set as primary** checkbox.

### Interviewer
A job ad might have several interviewers who are part of the hiring team.

### Hiring process
A recruiter can add a hiring template to the job ad. By adding the hiring template, the recruiter indicates the steps required for the hiring activities.
1. Go to **Hiring process** tab in a draft job ad.
2. Click the search field for hiring template.  
3. Select the hiring template from the list.
 
### Job ads approval

If job ads need approval from higher management, approvers can be added to accept or decline the job ad. When a recruiter assigns the approver and changes the stage to the approval stage, approvers 
receive a notification through these channels:
 - Outlook
 - Teams
 - In Recruiting add-on app

To add the approval list, follow these steps:
1.	Select **Approval required**. 
2.	Click **+New**. A pop-up opens with an input box for approval and email.
3.	Click the search icon in the input box of approver to see a list of all the approvers.
4.	Select the approvers.
5.	Click **Save** and **Create new** to add more approvers or click **Save** and **Close**.
6.	The next stage is **Approval**, the status of the approval changes to **Pending approval**.
7.	When the stage changes to approval, approvers receive notifications on Teams, Outlook and Recruiting add-on app. Approvers can use any of these channels to approve the Job ad.
8.	Click **Job ad approvals** to see the list of Job ads that require their action.
9.	Click **Approval id** for the Job ad that to give input.
10.	Click **Approve** or **Reject** to approve or reject the job Ad accordingly.
11.	Recruiters see provided input in the job ad.
12.	After the job ad is approved or rejected by the approvers for the job ad, Recruiters can move the job ad to next stage.

>[!Note]
> All approvers must provide input before the recruiter can move the job ad to next stage.

#### Business process flow

The business process flow stages of a job ad are:
 - **Draft** - the default stage of the business process flow where recruiters can make the changes in job ad. In the **Draft** stage, recruiters can provide job ad details like external title, skills, educational requirement, description, and compensation. They can also add hiring team members and the hiring template required for hiring process. They can also enable approval if it's required for the job ad.
 - **Approval** (optional) - this stage only shows up if job ad approval is required. Approvers receive notification on Teams or Outlook only when the stage changes from **Draft** to **Approval**. This stage
is hidden if approval isn't required. Recruiters can advance the stage to the next one after all the approvers give their consent to the job ad.
 - **Post** - the final stage of business process flow. If the job ad is ready to post the job ad to the career site, click **Finish**.
 - **Finished** - After the job is finished, the job ad is posted to the career site and available for internal and external candidates to apply.
 
#### Posting a new job ad

To post a new job ad, follow these steps:
1. In the Recruiting app, select **Job ads**.
2. Click **+New**.
3. Fill in the required fields.
4. Click **Save**.
5. Go to **Hiring team** tab, add hiring team members.
6. Go to **Hiring process** tab, pick a hiring template.
7. Go to **Approvals** tab, select **Approval required** tab if needed and add approvers.
8. Go to **Business process flow** and move the job ad from **Draft** to the next stage.



