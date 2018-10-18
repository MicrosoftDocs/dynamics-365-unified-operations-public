---
# required metadata

title: Security and role management in Attract
description: This topic provides information about role security in Microsoft Dynamics 365 for Talent - Attract.
author: 
manager: AnnBe
ms.date: 10/18/2018
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
ms.author: 
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Security and role management in Attract

[!include[banner](../includes/banner.md)]

Attract uses role-based security which means that access is not granted to individual users, but instead to security roles. Users are assigned to roles. A user who is assigned to a security role has access to the set of privileges that are associated with that role. Attract provides five basic user roles that can be used: 

- Administrator 
- Hiring Manager
- Recruiter
- Interviewer
- Read-only

The Administrator role is the only role with permissions to add other users and modify their permissions.

- **Add** - In the **Admin Center**, select the **User Permissions** tab, select **Assign user**, search for the user that you would like to add, and then assign their permissions.
- **Edit** - Search for or find the user in the list and click **Edit** to make changes to their permissions. 
- **Delete** - Deleting the permissions of the user does not remove them from the system but it does restrict the user’s permissions within Attract. For example, Hilda has been assigned the Hiring manager security role and is added to a job as a hiring manager. If Hilda’s security role of a hiring manager is later removed, she will remain as a hiring manager on the job for which she was added as a hiring manager earlier. She will still have access to that job but will be unable to create any new jobs.

The following sections provide a high-level description of each role. The table later in the topic provides more detailed information. 

> [!NOTE]
> Some features are only available with the Comprehensive Hiring Add-on for Attract.

## Administrator 

The Administrator role provides can access and modify all data within Attract. This includes the ability to create, read, update, and delete data. This role also has access to the Admin Center where they can configure the Attract application and set up user information. It is recommended that there be at least one individual who is assigned to the Administrator role. By default, the Environment administrator in PowerApps will be set as an Administrator in Attract. If you have signed up for the trial version of Attract, you will automatically be granted the Administrator role. Currently, the Administrator role also requires the Recruiter or Hiring manager role to create jobs.

## Hiring manager 

The Hiring manager can create new jobs and update the jobs that they have previously created. Hiring managers have a limited set of actions that can be performed on a job and the applications associated to a job. Only users that are assigned to the Hiring manager role can be added to a hiring team as a hiring manager.

## Recruiter role

The Recruiter role has full read, create, update, and delete privileges for the jobs that they have created. They also have full create, read, update, and delete privileges for the applications associated to the jobs that they own. Only users that are assigned to the Recruiter role can be added a hiring team as a recruiter.

## Interviewer 

Any user with an AAD account in the organization can be added to a hiring team as an interviewer. The interviewer can view the job details and applicant data for the jobs where they are part of the hiring team. In conext of those jobs, interviewers can make hiring recommendations and provide feedback about candidates. They do not have the ability to update job details or candidate information.

## Read-only 

Users with this role have read-only access to all data within the Attract environment but do not have the ability to create or edit any data.

## Delegated roles

Recruiters and hiring managers can add one or more delegates for themselves for each job where they are part of a hiring team. Delegates have the same privileges as the person that designated them. For example, if a hiring manager sets a delegate for themselves, the delegate will have the same privileges as the hiring manager for that job. Neither recruiters or hiring managers can assign delegates for other individuals on the hiring team. Delegates do not have the ability to remove other delegates from the hiring team or remove the individual that selected them as a delegate.

## Job details and actions

New jobs can be created by the Recruiter and Hiring manager roles. The following privileges apply to the job details and actions that can be taken on a job.

|                   | Recruiter                                                                        | Hiring Manager                                                                                                | Interviewer |
|-------------------|----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|-------------|
| Job details       | Create, read, update, and delete for jobs when part of the hiring team      | Create, read, update, and delete for jobs when part of the hiring team                                   | Read-only   |
| Hiring team       | Create, read, update, and delete for jobs when part of the hiring team      | Create, read, update, and delete for jobs when part of the hiring team                                   | Read-only   |
| Job Posting       | Create, read, update, and delete for jobs when part of the hiring team      | Read-only                                                                                                     | Read-only   |
| Process           | Create, read, update, and delete for jobs when part of the hiring team | Create, read, update, and delete for jobs when part of the hiring team                              | Read-only   |
| Add Applicants    | Add applicants for jobs when part of the hiring team               | Add applicants for jobs where they are part of the hiring team.                                            | Not allowed |
| Add Prospects     | Add prospects for jobs when part of the hiring team               | There is a configuration option in the [prospect activity setup](./activities-attract.md#prospect-activity) that controls access to adding and viewing | Not allowed |
| Activate job      | Activate jobs when part of the hiring team                       | Activate jobs wwhen part of the hiring team                                                    | Not allowed |
| Close job         | Close jobs when part of the hiring team                          | Not allowed                                                                                                   | Not allowed |
| Delete job        | Delete jobs when part of the hiring team                         | Only if no applicants on job                                                                                  | Not allowed |
| Delete applicants | Delete applicants when part of the hiring team                     | Not allowed                                                                                                   | Not allowed |

## Application details and actions

The following privileges apply to the job-specific data for an applicant and the actions that can be taken on an application.

|                         | Recruiter                                                                        | Hiring Manager                                                                   | Interviewer           |
|-------------------------|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------|-----------------------|
| Application documents   | Create, read, update, and delete for jobs when they are part of the hiring team | Create, read, update, and delete for jobs when they are part of the hiring team | Read-only             |
| Application Notes       | Create, read, update, and delete for jobs when they are part of the hiring team. | Create, read, update, and delete for jobs when they are on the hiring team      | Create                |
| Application Activity    | View when they are part of the hiring team                                  | View when they are part of the hiring teams                                 | Read-only             |
| Application feedback    | Add and view all feedback when part of the hiring team.    | Add and view all feedback when part of the hiring team    | Can add feedback\*\* |
| Reject application      | Can reject when they are part of the hiring team                                | Not allowed                                                                      | Not allowed           |
| Advance stage           | Can reject when they are part of the hiring team                                | Can advance when they are part of the hiring team                               | Not allowed           |
| Launch offer management | Can launch offer management.                                                     | Configuration option on the offer activity                                       | Not allowed            |

\*\*There is a configuration option within the [feedback activity setup](./activities-attract.md#feedback-activity) that
controls whether interviewers can see each other’s feedback.

## Process templates

The following privileges apply to the hiring process templates. The ability to allow team members to create and edit templates is configured in **Template management** in the **Admin center**. If template management is turned on, recruiters and hiring managers can create and manage their own process templates. If template management is turned off, only the admin can create and edit process templates. The table below assumes that template management has been turned on.

| Data              | Recruiter                                      | Hiring Manager                                     | Interviewer |
|-------------------|------------------------------------------------|----------------------------------------------------|-------------|
| Process templates | Full privileges on templates that they create. | Full privileges on templates that they can create. | No access   |

## Email and email templates 

The following privileges apply to email templates. Email templates can only be created and updated by an administrator. The table below discusses the actions that can be taken with emails.

| Data               | Recruiter              | Hiring Manager         | Interviewer |
|--------------------|------------------------|------------------------|-------------|
| Email templates    | Read-only access       | Read-only access       | No access   |
| Send email         | Send per activity      | Send per activity      | No access   |
| Edit email content | Can edit email content | Can edit email content | No access   |

## Talent pools

The following privileges apply to Talent pools. Talent pools are only visible to the creator unless the creator chooses to share the pool. Candidates that have not been added to a named pool can be searched via the candidate search.

|                  | Recruiter                            | Hiring Manager                       | Interviewer |
|------------------|--------------------------------------|--------------------------------------|-------------|
| Named pool       | Full privileges on pools they create | Full privileges on pools they create | No access   |
| Share pool       | On pools they have created           | On pools they have created           | No access   |
| Candidate search | Full search capabilities             | Full search capabilities             | No access   |

## Candidates

Candidates are individuals who have been added to a Talent pool and are not associated to a job.

|                             | Recruiter                            | Hiring Manager                       | Interviewer |
|-----------------------------|--------------------------------------|--------------------------------------|-------------|
| Profile – candidate details | Create, read, update, and delete | Create, read, update, and delete | No access   |
| Documents                   | Create, read, update, and delete | Create, read, update, and delete | No access   |
