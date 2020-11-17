---
# required metadata

title: Create a job in Attract
description: This topic describes the elements of a job in Attract. It also explains how to create a job.
author: hasrivas
manager: AnnBe
ms.date: 07/18/2019
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
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: hasrivas
ms.search.validFrom: 2018-10-24
ms.dyn365.ops.version: Talent October 2018 update

---

# Create a job in Attract

[!include [banner](includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes the elements of a job in Microsoft Dynamics 365 Talent: Attract. It also explains how to create a job.

## Job creation

Admins, recruiters, and hiring managers can create jobs. When you create a job, you're prompted to select your role in the process: hiring manager or recruiter. After you select a role, you're prompted to select a process template. If you select **Skip**, the default template is used. For more information about process templates, see [Create a process template in Attract](./process-templates-attract.md).

A job in Attract has job details, a hiring team, a hiring process, job postings, and analytics.

## Job details

The **Job details** tab contains details about the job's responsibilities and attributes. The fields for the job title, job description, and job location are required. The other fields are optional.

By default, the **Number of openings** field is set to **1**. However, you can change the value. When an offer has been prepared for a job, the value of the **Number of openings available** field is decremented.

If position management has been turned on in the Admin Center, the **Update positions** lookup is available. This lookup reads the JobPosition entity in Common Data Service and returns a list of positions that can be selected for the job. If the number of positions that you select exceeds the number of open positions, you receive a warning. You also receive a warning if a position is used on multiple jobs.

> [!NOTE]
> Position management is available with the Comprehensive Hiring Add-on.

Depending on the settings in the Offer activity of the hiring process, a position number can be used twice in an offer. For more information, see [Activities in hiring processes](./activities-attract.md).

Attract includes a default set of **Skills**. These skills appear as suggestions as you type. You can add more skills by entering the new skill text in the field and then pressing Enter.

Attract includes a default set of **Job functions**. You can add up to three more job functions by entering the new job function in the field and then pressing Enter.

Attract includes a default set of **Company industry**. You can add up to three more company industries by entering the new company industry in the field and then pressing Enter.

## Hiring team

The **Hiring team** tab contains the list of individuals who will be involved in the job. When users are added to a hiring team, they must be assigned a role on the hiring team. The role determines the data that the users have access to and the notifications that they receive. The roles that can be selected are **Recruiter**, **Hiring manager**, **Delegate**, and **Interviewer**. For more information about role privileges, see the "Role management" document. Recruiters and hiring managers can appoint one or more delegates to work on their behalf. For more information about delegates, see [Security and role management in Attract](./security-attract.md).

The hiring team can be updated after the job is activated.

## Process

Default information about the hiring process is based on the process template that was selected when the job was created. If a specific template wasn't selected at that time, the default template is used. When you define the hiring process, you can add or remove various stages, except the Prospect, Application, and Offer stages. Although the Prospect stage can't be removed, it can be turned off. Within each stage, you can add or remove one or more predefined activities.

For more information about activities that can be added to the hiring process, see [Activities in hiring processes](./activities-attract.md).

> [!NOTE]
> The process hiring can't be updated after a job is activated.

## Postings

After a job is activated, it can be posted. Only recruiters and admins can post jobs. The job can be posted to either Talent Careers (a Dynamics 365 Talent career site) or LinkedIn. The Attract team is continually working to partner with job board aggregators. This list will expand over time. When a job is posted as internal only, candidates need an AAD account to view and apply for the job. If the job is listed as public, candidates can view and apply for jobs using all authentication options. 

For more information about job postings, see [Set up your career site in Microsoft Dynamics 365 Talent - Attract](career-site.md).

> [!NOTE]
> The job posting functionality is available only with the Comprehensive Hiring Add-on for Attract.

## Activate

After a job is activated, it can be posted, and prospects and applicants can be added to it. The option to add prospects to a job is set in the Prospect activity in the hiring process.

> [!NOTE]
> The process hiring can't be updated after a job is activated.

## Prospects and applicants

The option to add prospects to a job is set in the [Activities in hiring processes](./activities-attract.md#prospect-activity) in the hiring process. This option should be set before you activate the job. After a job is activated, prospects and applicants can be added to it.

## Approvals

Attract jobs can be submitted for approval. Not all jobs require approval. The requirement is set at the template level. By default, approvals are turned off on the template. To set up approvals, go to a process template, and set the **Approval** field to Default. Then select that template when you create the job.

After a job is saved, it can be submitted for approval. The following table lists the statuses of a document that uses approvals.

| Status   | State                                                               |
|----------|---------------------------------------------------------------------|
| Draft    | The job has been saved, but it hasn't been submitted to a workflow. |
| Pending  | The job has been submitted to approvers.                            |
| Approved | The job has been approved, but it hasn't been activated.            |
| Rejected | The job has been rejected, and it can't be activated.               |
| Active   | The job has been approved and activated.                            |

In the job list, you can filter on the job statuses.

Approvals can be sent to any Microsoft Azure Active Directory (Azure AD) user in the company. The approvals are sent in parallel to all the people who are listed as approvers. All approvers must approve the job before it can move forward. If a single approver rejects the job, the job will display a **Rejected** status. After a job is approved, it can be activated.

If a user edits the job after it is approved, but not activated, the job status will be reset to **Draft**, and the job must be re-submitted for approval. After an approved job has been activated, you can't edit it.

The people who are listed as approvers will receive a notification in Attract and an email to inform them they have an item to approve.  In the email, approvers can click the link to open the job, review the details, and either approve or reject. After the job's status is set to **Approved** or **Rejected**, the submitter will be notified in Attract and they will receive an email. Also, the approvers will receive a reminder email if they have not responded to the approval request within 24 hours.

> [!NOTE]
> You can create custom email templates for Approval emails. For more information, see [Creating and managing email templates](https://docs.microsoft.com/dynamics365/unified-operations/talent/email-templates).

## Create a job

Follow these steps to create a job.

1. Go to **Jobs**.
2. Select **New**.
3. In the **Job title** field, enter the job title. In the **Role** field, enter your role.
4. In the **Template** field, select a template. Alternatively, select **Skip**. If you select **Skip**, the template that is marked as the default template is used.

    If the document should go through an approval process, select a template where the **Approval process** field is set to **Default**.

5. On the **Details** tab, enter the details of the job. The **Title**, **Job description**, and **Location** fields are required.
6. Select **Save**.
7. On the **Hiring team** tab, add a hiring manager, recruiter, or interviewer.
8. Select **Save**.
9. On the **Process** tab, add or remove stages as you require:

    - To add a stage, select **+ New Stage**.
    - To remove a stage, hover the pointer over the stage to remove, and then select the trash can button that appears.

        > [!NOTE]
        > The Prospect, Application, and Offer stages can't be removed.

10. Add or remove activities as you require:

    - To add an activity, drag it from the list on the right to the appropriate stage. Alternatively, double-click the activity, and then select the stage to add it to.
    - To remove an activity, expand the activity, and then select the trash can button on the activity header.

11. Select **Save**.
12. If you selected to use an approval process, follow these steps:

    1. Select **+ Add approver**, and then enter a user who has an Azure AD account. You can add multiple approvers.
    2. Select **Send to approvers**.

    The **Job status** field of the job is set to **Pending**. After the value of the **Job status** field changes to **Approved**, the job can be activated.

13. To activate the job, select **Activate**.
14. To post the job, go to **Postings**, and then select **Post Now** under the Talent Careers site or LinkedIn.
