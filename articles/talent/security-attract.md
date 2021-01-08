---
# required metadata

title: Set user permissions in Attract
description: This topic provides information about role security in Microsoft Dynamics 365 Talent - Attract.
author: andreabichsel
manager: AnnBe
ms.date: 03/08/2019
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
ms.author: anbichse
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Set user permissions in Attract

[!include [banner](includes/banner.md)]

Microsoft Dynamics 365 Talent: Attract uses role-based security. In other words, access isn't granted to individual users, but to the security roles that users are assigned to. A user who is assigned to a security role has access to the set of privileges that is associated with that role.

Attract provides five basic user roles:

- Administrator
- Hiring Manager
- Recruiter
- Interviewer
- Read-only

The Administrator role is the only role that has permission to add other users and change their permissions.

- **Add** – In the Admin center, on the **User permissions** tab, select **Assign roles**, search for the user to add, and then assign permissions to that user.
- **Edit** – Search for the user, or find the user in the list, and then select **Edit** to changes his or her permissions.
- **Delete** – If you delete a user's permissions, you don't remove the user from the system. However, you do limit the user's access and privleges in Attract. For example, Hilda has been assigned to the Hiring Manager role, and she is added to a job as a hiring manager. If Hilda is later removed from the Hiring Manager role, she remains a hiring manager on the job and still has access to that job. However, she can't create other jobs.

The following sections provide a high-level description of each role. The tables later in the topic provide more detailed information.

> [!NOTE]
> Some features are available only with the Comprehensive Hiring add-on for Attract.

## Administrator

Users who are assigned to the Administrator role can access and change all data in Attract. Admins can create, read, update, and delete data. They also have access to the Admin center, where they can configure Attract and set up user information. We recommend that at least one individual be assigned to the Administrator role. By default, the environment admin in Microsoft Power Apps is set as an admin in Attract. If you signed up for the trial version of Attract, the Administrator role is automatically assigned to you. Currently, to create jobs, users who have the Administrator role must also have either the Recruiter role or the Hiring Manager role.

## Hiring Manager

Users who are assigned to the Hiring Manager role can create jobs and update jobs that they previously created. Hiring managers can perform only a limited set of actions on a job and on the applications that are associated with that job. Only users who are assigned to the Hiring Manager role can be added to a hiring team as hiring managers.

## Recruiter role

Users who are assigned to the Recruiter role have full read, create, update, and delete privileges for the jobs that they have created. They also have full create, read, update, and delete privileges for the applications that are associated with jobs that they own. Only users who are assigned to the Recruiter role can be added to a hiring team as recruiters.

## Interviewer

Any user who has a Microsoft Azure Active Directory (Azure AD) account in the organization can be added to a hiring team as an interviewer. Users who are assigned to the Interviewer role can view the job details and applicant data for jobs that they are on the hiring team for. For those jobs, interviewers can also make hiring recommendations and provide feedback about candidates. However, they can't update the job details or applicant data.

## Read-only

Users who are assigned to the Read-only role have read-only access to all data in the Attract environment. However, they can't create or edit any data.

## Find out which roles you have

1.  In Attract, click the question mark (**?**) in the top right corner of the page.

2.  Click **About**.

    You will see which roles you have for Attract in the window that appears:

    ![View your Attract license type](media/attract-license-types.png)
    
## Delegated roles

For each job that they are on the hiring team for, recruiters and hiring managers can designate one or more delegates for themselves. However, they can't designate delegates for other people on the hiring team.

Delegates have the same privileges as the person who designated them. For example, if a hiring manager designates a delegate for herself for a job, the delegate will have the same privileges as that hiring manager for that job. Delegates can't remove other delegates from the hiring team. They also can't remove the people who designated them as delegates.

## Job details and actions

Users who have the Recruiter or Hiring Manager role can create jobs. The following privileges apply to the job details and the actions that can be taken on jobs.

| Data or action    | Recruiter | Hiring Manager | Interviewer |
|-------------------|-----------|----------------|-------------|
| Job details       | Create, read, update, and delete for jobs that the user is on the hiring team for | Create, read, update, and delete for jobs that the user is on the hiring team for | Read-only |
| Hiring team       | Create, read, update, and delete for jobs that the user is on the hiring team for | Create, read, update, and delete for jobs that the user is on the hiring team for | Read-only |
| Job Posting       | Create, read, update, and delete for jobs that the user is on the hiring team for | Read-only | Read-only |
| Process           | Create, read, update, and delete for jobs that the user is on the hiring team for | Create, read, update, and delete for jobs that the user is on the hiring team for | Read-only |
| Add Applicants    | Add applicants for jobs that the user is on the hiring team for | Add applicants for jobs that the user is on the hiring team for | Not allowed |
| Add Prospects     | Add prospects for jobs that the user is on the hiring team for | A configuration option in the [prospect activity setup](./activities-attract.md#prospect-activity) controls whether interviewers can add and view prospects. | Not allowed |
| Activate job      | Activate jobs that the user is on the hiring team for | Activate jobs that the user is on the hiring team for | Not allowed |
| Close job         | Close jobs that the user is on the hiring team for | Not allowed | Not allowed |
| Delete job        | Delete jobs that the user is on the hiring team for | Only if no applicants have been added to the job | Not allowed |
| Delete applicants | Delete applicants if the user is on the hiring team | Not allowed | Not allowed |

## Application details and actions

The following privileges apply to the job-specific data for applicants and the actions that can be taken on applications.

| Data or action          | Recruiter | Hiring Manager | Interviewer |
|-------------------------|-----------|----------------|-------------|
| Application documents   | Create, read, update, and delete for jobs that the user is on the hiring team for | Create, read, update, and delete for jobs that the user is on the hiring team for | Read-only |
| Application Notes       | Create, read, update, and delete for jobs that the user is on the hiring team for | Create, read, update, and delete for jobs that the user is on the hiring team for | Read-only|
| Application Activity    | View, if the user is on the hiring team | View, if the user is on the hiring team | Read-only |
| Application feedback    | Add and view all feedback if the user is on the hiring team | Add and view all feedback if the user is on the hiring team | Can add feedback\*\* |
| Reject application      | Can reject if the user is on the hiring team | Not allowed | Not allowed |
| Advance stage           | Can reject if the user is on the hiring team | Can advance if the user is on the hiring team | Not allowed |
| Launch offer management | Can start offer management | There is a configuration option on the offer activity. | Not allowed |


\*\* A configuration option in the [feedback activity setup](./activities-attract.md) controls whether interviewers can see each other's feedback.


## Process templates

The following privileges apply to hiring process templates. The ability of team members to create and edit templates is configured in **Template management** in the Admin center. If template management is turned on, recruiters and hiring managers can create and edit their own process templates. If template management is turned off, only admins can create and edit process templates. The following table assumes that template management has been turned on.

| Data              | Recruiter                                           | Hiring Manager                                      | Interviewer |
|-------------------|-----------------------------------------------------|-----------------------------------------------------|-------------|
| Process templates | Full privileges for templates that the user creates | Full privileges for templates that the user creates | No access   |

## Email and email templates

The following privileges apply to email templates and the actions that can be taken on emails. Only admins can create and edit email templates.

| Data or action     | Recruiter          | Hiring Manager     | Interviewer |
|--------------------|--------------------|--------------------|-------------|
| Email templates    | Read-only access   | Read-only access   | No access   |
| Send email         | Send per activity  | Send per activity  | No access   |
| Edit email content | Edit email content | Edit email content | No access   |

## Talent pools

The following privileges apply to talent pools. Talent pools are visible only to the person who created them, unless that person chooses to share them. Candidate search can be used to search for candidates who haven't been added to a named pool.

| Data or action   | Recruiter                                       | Hiring Manager                                  | Interviewer |
|------------------|-------------------------------------------------|-------------------------------------------------|-------------|
| Named pool       | Full privileges for pools that the user creates | Full privileges for pools that the user creates | No access   |
| Share pool       | Only pools that the user creates                | Only pools that the user creates                | No access   |
| Candidate search | Full search capabilities                        | Full search capabilities                        | No access   |

## Candidates

Candidates are people who have been added to a talent pool but aren't associated with a job.

| Data                        | Recruiter                        | Hiring Manager                   | Interviewer |
|-----------------------------|----------------------------------|----------------------------------|-------------|
| Profile – candidate details | Create, read, update, and delete | Create, read, update, and delete | No access   |
| Documents                   | Create, read, update, and delete | Create, read, update, and delete | No access   |
