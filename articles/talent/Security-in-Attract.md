Security and Role management in Attract
=======================================

This article provides an overview of the elements of role security in Microsoft Dynamics 365 for Talent: Attract.

Attract uses role-based security. In role-based security, access is not granted
to individual users, only to security roles. Users are assigned to roles. A user
who is assigned to a security role has access to the set of privileges that is
associated with that role. Attract provides five basic user roles that can be
used: Administrator, Hiring Manager, Recruiter, Interviewer, and Read only.

Administrators are the only role that can add other users. To add new users, navigate to
the **Admin Center** and select the **User Permissions** tab, select Assign user
and search for the user that you would like to add and assign their permissions.
To Edit existing privileges, you can choose assign user and search for the
existing user to edit their privileges OR you can find the user in the list and
select the ‘edit’ option. Deleting the permissions of the user does not remove
them from the system. However, it restricts the user’s permissions within
Attract. Example: Hilda has been assigned the Hiring manager security role.
Hilda is then added to a job as a hiring manager. If Hilda’s security role of a
hiring manager is later removed, she will remain as a hiring manager on the job she was added as a hiring manager earlier.
She will still have access to that job but will be unable to create any new
jobs.

Listed below is a high-level description of each role. See the table following
the role descriptions to see detailed access information. 

Note: Some features are only available with the purchase of the Comprehensive Hiring Add-on for
Attract.

Administrator role
------------------

The administrator role provides access to all data within Attract, this includes
the ability to create, read, update and delete. Also, this role includes access
to the Admin Center for configuring the Attract application as well as setting
up users. It is recommended that there be at least one individual who is
assigned to be an Administrator. By default, the Environment Administrator in
PowerApps will be set as an Administrator in Attract. If you have signed up for
the trial version of Attract you will automatically be granted the administrator
role. Currently, the Administrator role also requires the Recruiter or Hiring
manager role to create jobs.

Recruiter role
--------------

The recruiter role has full read, create, update and delete privileges for the
jobs that they have created. They also have full create, read, update and delete
privileges for the applications associated to the jobs that they own. Only users
that have a recruiter role can be added a hiring team as a recruiter.

Hiring manager role
-------------------

The hiring manager can create jobs and update the jobs that they have created.
Hiring managers have a limited set of actions that can be performed on a job and
the applications associated to a job. Only users that have a hiring manager role
can be added to a hiring team as a hiring manager.

Interviewer role
----------------

Any user with an AAD account within the organization can be added to a hiring
team as an interviewer. The interviewer can view the job details and applicant data
for the jobs in which they are part of the hiring team. In conext of those jobs,
interviewers can make hiring recommendations and provide feedback about candidates. They do not
have the ability to update job details or candidate information.

Read only role
--------------

Users with this role have read only access to all data within the Attract
environment but do not have the ability to create/edit any data.

Delegated roles
---------------

Recruiters and hiring managers can add one or more delegates for themselves for
each job where they are part of a hiring team. Delegates have the same
privileges as the person that designated them as a delegate. For example, if a
hiring manager sets a delegate for themselves, the delegate will have the same
privileges as the hiring manager for that job. (See the tables below for
detailed recruiter and hiring manager privileges.) Neither recruiters nor hiring
managers can assign delegates for other individuals on the hiring team.
Delegates do not have the ability to remove other delegates from the hiring
team, nor can they remove the individual that selected them as a delegate.

Job details and actions
-----------------------

New jobs can be created by the recruiter and hiring manager roles. The following
privileges apply to the job details and actions that can be taken on a job.

|                   | Recruiter                                                                        | Hiring Manager                                                                                                | Interviewer |
|-------------------|----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|-------------|
| Job details       | Create, read, update, and delete for jobs where they are on the hiring team      | Create, read, update, and delete for jobs where they are on the hiring team                                   | Read only   |
| Hiring team       | Create, read, update, and delete for jobs where they are on the hiring team      | Create, read, update, and delete for jobs where they are on the hiring team                                   | Read only   |
| Job Posting       | Create, read, update, and delete for jobs where they are on the hiring team      | Read only                                                                                                     | Read only   |
| Process           | Create, read, update, and delete for jobs where they are part of the hiring team | Create, read, update, and delete for jobs where they are part of the hiring team                              | Read only   |
| Add Applicants    | Can add applicants for jobs where they are part of the hiring team               | Can add applicants for jobs where they are part of the hiring team                                            | Not allowed |
| Add Prospects     | Can add prospects for jobs where they are part of the hiring team                | There is a configuration option within the [prospect activity setup](./activities-in-Attract.md#prospect-activity) that controls access to adding and viewing | Not allowed |
| Activate job      | Can activate jobs where they are a part of the hiring team                       | Can activate jobs where they are a part of the hiring team                                                    | Not allowed |
| Close job         | Can close jobs where they are a part of the hiring team                          | Not allowed                                                                                                   | Not allowed |
| Delete job        | Can delete jobs where they are a part of the hiring team                         | Only if no applicants on job                                                                                  | Not allowed |
| Delete applicants | Can delete applicants where they are part of the hiring team                     | Not allowed                                                                                                   | Not allowed |

Application details and actions
-------------------------------

The following privileges apply to the job specific data for an applicant
(application) and the actions that can be taken on an application.

|                         | Recruiter                                                                        | Hiring Manager                                                                   | Interviewer           |
|-------------------------|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------|-----------------------|
| Application documents   | Create, read, update, and delete for jobs where they are part of the hiring team | Create, read, update, and delete for jobs where they are part of the hiring team | Read only             |
| Application Notes       | Create, read, update, and delete for jobs where they are part of the hiring team | Create, read, update, and delete for jobs where they are on the hiring team      | Create                |
| Application Activity    | Can view where they are part of the hiring team                                  | Can view where they are part of the hiring teams                                 | Read only             |
| Application feedback    | Can add feedback and view all feedback where they are part of the hiring team    | Can add feedback and view all feedback where they are part of the hiring team    | Can add feedback\*\* |
| Reject application      | Can reject where they are part of the hiring team                                | Not allowed                                                                      | Not allowed           |
| Advance stage           | Can reject where they are part of the hiring team                                | Can advance where they are part of the hiring team                               | Not allowed           |
| Launch offer management | Can launch offer management.                                                     | Configuration option on the offer activity                                       | No allowed            |

\*\*There is a configuration option within the [feedback activity setup](./activities-in-Attract.md#feedback-activity) that
controls if interviewers can see each other’s feedback

Process templates
-----------------

The following privileges apply to the hiring process templates. The ability to
allow team members to create and edit templates is configured in Template
management in the Admin center. If template management is turned on recruiters
and hiring managers can create and manage their own process templates. If
template management is turned off only the admin can create and edit process
templates. The table below assumes that template management has been turned on.

| Data              | Recruiter                                      | Hiring Manager                                     | Interviewer |
|-------------------|------------------------------------------------|----------------------------------------------------|-------------|
| Process templates | Full privileges on templates that they create. | Full privileges on templates that they can create. | No access   |

Email and email templates 
--------------------------

The following privileges apply to email templates. Email templates can only be
created and updated by an administrator. The table below discusses the actions
that can be taken with emails.

| Data               | Recruiter              | Hiring Manager         | Interviewer |
|--------------------|------------------------|------------------------|-------------|
| Email templates    | Read only access       | Read only access       | No access   |
| Send email         | Send per activity      | Send per activity      | No access   |
| Edit email content | Can edit email content | Can edit email content | No access   |

Talent pools
------------

The following privileges apply to Talent pools. Talent pools are only visible to
the creator unless the creator chooses to share the pool. Candidates that do not
exist in a named pool can be searched via the candidate search.

|                  | Recruiter                            | Hiring Manager                       | Interviewer |
|------------------|--------------------------------------|--------------------------------------|-------------|
| Named pool       | Full privileges on pools they create | Full privileges on pools they create | No access   |
| Share pool       | On pools they have created           | On pools they have created           | No access   |
| Candidate search | Full search capabilities             | Full search capabilities             | No access   |

Candidates
----------

Candidates are individuals who exist in a Talent pool and are not associated to
a job.

|                             | Recruiter                            | Hiring Manager                       | Interviewer |
|-----------------------------|--------------------------------------|--------------------------------------|-------------|
| Profile – candidate details | Can create, read, update, and delete | Can create, read, update, and delete | No access   |
| Documents                   | Can create, read, update, and delete | Can create, read, update, and delete | No access   |
