---
# required metadata

title: Set up job ads in the HR Recruiting app (preview)
description: This article explains how to set up job ads in the HR Recruiting app in Microsoft Dynamics 365 Human Resources.
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

# Set up job ads in the HR Recruiting app (preview)

[This article is prerelease documentation and is subject to change.]

This article explains how to set up job ads in the HR Recruiting app in Microsoft Dynamics 365 Human Resources.

*Job ads* are an essential part of the hiring process. They're used to advertise one or more job openings in a company. Job ads are published on various platforms, such as job boards, company websites, social media, and other related channels. 

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Create a job ad

The Recruiting app has a **Job ads** section where recruiters create job ads. Each job ad includes the following information: job ID, number of openings, estimated start date, compensation, currency, company (legal entity), job location, skills, position type, and job description.

To create a job ad, fill in the following fields:

- **Job title** – Enter the title of the position. A clear job title helps candidates quickly understand the role.
- **Description** – Provide a detailed overview of the responsibilities, duties, and qualifications that are associated with the job. Outline what the role entails, and what skills or experience is required.
- **Estimated start** – Specify the estimated start date of the job requirement activities.
- **Company** – By including information about the company's values, culture, and mission, you can help attract candidates who are aligned with the organization's goals.
- **Job location** – It's important that you specify the job's location, so that candidates can determine whether the position is geographically suitable for them.
- **Skills** – Specify the skill set required for the job position.
- **Compensation** – By including information about the salary range, benefits, and any perks that are associated with the position, you can help make the job ad attractive to potential candidates.
- **Currency** – Select the currency of the compensation.
- **Position type** – You can create job ads for full-time or part-time contract employees.
- **Recruiting request** – Select **Recruiting request** to view details about the job ad such as compensation, job description, and external title in the recruiting request.

## Recruiting requests

A *recruiting request* is a document that hiring managers in Dynamics 365 Finance use to create the requirement for job openings. A recruiting request can be published only if it's in an active status. After a recruiting request is published, it can't be updated. For more information, see [Recruit job candidates](hr-personnel-recruit.md). 

## Job ad statuses

There are five job ad statuses:

- **Draft** – The job ad isn't saved.
- **In progress** – The job ad was saved, and the process of adding hiring team members, adding a hiring template, or gaining approval is in progress.
- **Active** – The job ad was posted to the careers site. After a job ad is posted, its details can't be changed.
- **Inactive** – The job ad was deactivated after it was posted to job boards.
- **Complete** – The job ad was completed by selecting **Complete**. After a job ad is completed, activities can't be added.

## Add members to the hiring team

A *hiring team* is a group of team members who are responsible for the hiring activities of a specific job ad. Each hiring team can include multiple recruiters, hiring managers, and interviewers. However, one hiring manager and at least one recruiter must be selected as primary. Only members of the hiring team can participate in interview processes.

To add a member to the hiring team, follow these steps.

1. In the Recruiting app, on the **Hiring team** tab, select **New**.
1. In the dialog box, search for **Name**, and either select the name in the dropdown list or enter it. 
1. Select the role.
1. Select **Save** and then **Close**.

### Primary recruiters

Although the hiring team for a job can include many recruiters, it should have at least one primary recruiter. To select a primary recruiter, select the **Set as primary** checkbox.
 
### Primary hiring manager

Although the hiring team for a job ad can include multiple hiring managers, it must have one primary hiring manager. To select the primary hiring manager, select the **Set as primary** checkbox.

### Interviewers

The hiring team for a job ad can include several interviewers.

## Add a hiring template

A recruiter can add a hiring template to a job ad to define the steps that are required for the hiring activities.

To add a hiring template to a job ad, follow these steps.

1. Open a job ad that's in **Draft** status.
1. On the **Hiring process** tab, select the search field for the hiring template.
1. Select the hiring template in the list.


### Screening questions
Recruiters can add a set of questions related to specific job ads. Candidates answer these questions during the application process. The responses provided by applicants can be used by recruiters to filter through applicants for job vacancies. Recruiters can tailor these questions to suit the needs of the job opening, such as years of experience or willingness to relocate. For instance, if a recruiter is looking for candidates with a minimum of 5 years’ experience, they could swiftly eliminate applicants who have less experience.

To add screening questions, follow these steps. (optional)
1. Go to **Screening questions** tab in a draft job ad.
2. Click **Search** for the **Screening** template. This displays the **Screening** templates.
3. Select the **Screening** template from the list. Multiple templates can be selected.
4. All the questions on the selected templates will be displayed.

 
## Job ad approval

If job ads require approval from higher management, recruiters can assign approvers who must either accept or reject the job ads. When a recruiter assigns approvers and changes the stage to the **Approval** stage, approvers receive a notification through the following channels:

- Outlook
- Teams
- The Recruiting add-on app

### Define the approval list

To add approvers to the approval list, follow these steps.

1. Select **Approval required**. 
1. Select **New**.
1. In the dialog box, select the search button in the field for the approver to view a list of all the approvers.
1. Select the approvers.
1. If you want to add more approvers, select **Save** and then **Create new**. Otherwise, select **Save** and then **Close**.

The next stage is **Approval**. The status of the approval is changed to **Pending approval**.

### Approve or reject a job ad

When the stage is changed to **Approval**, approvers receive notifications in Teams, Outlook, and the Recruiting add-on app. They can use any of these channels to approve or reject the job ad.

To approve or reject a job ad, an approver follows these steps.

1. Select **Job ad approvals** to view the list of job ads that require your action.
1. Select the **Approval id** value of the job ad that you want to give input for.
1. Select **Approve** or **Reject** to approve or reject the job ad.

In the job ad, recruiters can view the input that the approver provided.

After the job ad is approved by the assigned approvers, recruiters can move it to the next stage.

> [!NOTE]
> All thee assigned approvers must provide input before recruiters can move the job ad to the next stage.

### Business process flow

The business process flow of a job ad has the following stages:

1. **Draft** – During this default stage of the business process flow, recruiters can make changes to the job ad. They can provide job ad details such as an external title, skills, an educational requirement, a description, and compensation information. They can also add hiring team members and the hiring template that is required for the hiring process. Finally, they can enable approval if it's required for the job ad.
1. **Approval** (optional) – This stage is shown only if approval is required for the job ad. Otherwise, it's hidden. Approvers receive notification in Teams or Outlook only when the stage is changed from **Draft** to **Approval**. Recruiters can move the job ad to the next stage only after all the approvers approve it.
1. **Post** – This stage is the final stage of the business process flow. If the job ad is ready to be posted to the careers site, select **Finish**.
1. **Finished** – After the job ad is finished, it's posted to the careers site, and internal and external candidates can apply for the job.
 
## Post a new job ad

To post a new job ad, follow these steps.

1. Select **Job ads**.
1. Select **New**.
1. Fill in the required fields.
1. Select **Save**.
1. On the **Hiring team** tab, add hiring team members.
1. On the **Hiring process** tab, select a hiring template.
1.  If approval is required, on the **Approvals** tab, select **Approval required**, and add approvers.
1. Go to **Business process flow**, and move the job ad from the **Draft** stage to the next stage.
