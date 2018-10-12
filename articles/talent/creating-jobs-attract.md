Creating, approving and posting jobs in Attract
===============================================

This topic describes the elements that a job contains in Microsoft Dynamics 365 for Talent: Attract and provides a
guide on creating a job.

**Creating a job**
------------------

A job can be created by either an admin, recruiter or hiring manager. When
creating a job, the user will be prompted to select their role in the process;
hiring manager or recruiter. Once a role has been selected the user will be
prompted select a **Process template**. If the user selects ‘Skip’ the default
template will be used. To find out more information regarding templates refer to
the [Creating a Process Template in Attract](./process-templates-attract.md) topic.

A job in Attract contains **Job details**, a **Hiring team**, a **Hiring
process**, **Job posting(s)** and **Analytics**.

**Job details**
---------------

The **job details** contain the details regarding the job’s responsibilities and
attributes. The **job title**, **job description** and **job location** are
required fields. The remaining fields are optional.

The **number of openings** field will default with 1 and can be incremented. The
**number of openings available** will be decremented when an offer has been
prepared for a job.

If **Position Management** has been turned on in the Admin Center, the ‘Update
positions’ lookup will be available. This lookup will read the JobPosition
entity in CDS for Apps and return a list of positions to select on the job. If more
positions are selected than are open, a warning will be displayed. If a position
is used on multiple jobs, a warning will be displayed.

[!NOTE] Position management is available with the Comprehensive Hiring
Add-on.

Depending on settings in the **Offer activity** of the hiring process, a
position number may be used twice in an offer. Please see the hiring process
section for more details.

Attract ships with a default set of **Skills**. These will show up as suggestions as you type. You can add additional Skills by
entering the new skill text in the field and selecting Enter.

Attract ships with a default set of **Job functions**. You can add Job functions
by entering the function in the field and selecting Enter. You can add up to 3 job
functions.

Attract ships with a default set of **Company Industries**. You can add up to 3
company industries by entering the Company Industry in the field and selecting
enter.

**Hiring team**
---------------

The **Hiring team** contains the list of individuals who will be involved in the
job. When users are added to a hiring team they must be given a role on the
hiring team. The role determines what data they will have access to, as well as
what notifications they will receive. Roles that can be selected are recruiter,
hiring manager, delegate, and interviewer. To read more about role privileges
please refer to the **Role management** document. Recruiters and hiring managers
may appoint one or more delegates to work on their behalf. To read more about
delegates please refer to the [Security and Role management in Attract](./security-attract.md) topic.

The hiring team can be updated after the job is activated.

**Process**
---------------

The hiring process is defaulted based on the **Process template** that was
selected at the time the job was created. If a template was not selected at the
time of creation, the default template will be used. When defining the hiring
process various stages can be added or removed, except for the Prospect,
Application, and Offer stages. While the Prospect stage cannot be removed, it
can be turned off. Within each stage one or more pre-defined activities can be
added or removed.

To learn more about activities that can be added to the hiring process, review
the [Hiring Process Activities in Attract](./activities-attract.md) topic.

[!NOTE] The process cannot be updated after the job is activated.

**Postings**
---------------

Once a job has been activated it can be posted. Only recruiters or admins can
post the job. The job can be posted to Talent Careers (A Dynamics365 for Talent
career site) or to LinkedIn. The Attract team continually works to partner with
job board aggregators so this list will expand over time.

To learn more about job posting refer to the [Career Site functionality in Attract](./career-site.md) topic.

[!NOTE] Job Posting functionality is only available with the Comprehensive
Hiring Add-on for Attract.

**Activate**
-------------

Activating a job allows it to be posted and allows for prospects and applicants to be added
to the job. The ability to add prospects to a job is configured within the
Prospect activity within the hiring process. Once a job has been activated, the
hiring process cannot be edited.

**Prospects and applicants**
---------------

The option to add prospects to a job is set within the [Prospect activity](./activities-attract.md#prospect-activity) in the
Hiring process. This should be set before activating the job. Once a job has been activated, prospects and applicants can be added.

**Approvals**
---------------

Attract jobs can be submitted for approval. Whether a job will require
approval is set at the template level. By default, approvals are turned off on
the template. To setup approvals, navigate to a process template and set the
approval to ‘Default’ and select this template when creating the job.

Once the job is saved it can be submitted for approval. Listed below
are the statuses of a document using approvals.

| Status   | State                                         |
|----------|-----------------------------------------------|
| Draft    | Job is saved but not submitted to workflow    |
| Pending  | Job has been submitted to approvers           |
| Approved | Job has been approved but not activated       |
| Rejected | Job has been rejected and it cannot be activated |
| Active   | Job has been approved and has been activated. |

Within the job list you can filter on the job statuses above.

Approvals can be sent to any AAD user in the company. The approvals will be sent
in parallel to all approvers listed. Once the job is approved it can be
activated.

Individuals who are listed as approvers will receive a notification in Attract
indicating they have an item to approve and an approval item will show on the
dashboard in the ‘Assigned to you’ section. Once an individual accepts or
approves the job the hiring team will receive a notification informing them.
Lastly, when the job is approved, the hiring team will receive a notification.

To create a job:

1.  Navigate to **Jobs**

2.  Select **New**

3.  Enter in the **Job title** and your **Role**

4.  Select a **Template** or choose skip. Choosing ‘skip’ selects the template
    marked as ‘Default’. If you want the document to go through an approval
    process, select a template that has the **Approval process** set to
    **Default**

5.  Enter in the details in the details tab. Required fields are **Title**,
    **Job description**, and **Location.**

6.  Select **Save**

7.  Select the **Hiring team** tab

8.  Add a hiring manager, recruiter, or interviewer

9. Select **Save**

10. Navigate to the **Process tab**

11. Add a new stage, as needed, by selecting **‘+ New Stage’**

12. Remove a stage, as needed, by hovering on the **Stage** and selecting the trash can icon
    that appears. 
    
    [!NOTE] Prospect, Application and Offer stages cannot be removed

13. Add activities, as needed, by dragging the **Activity** on the right and dropping in the
    appropriate stage OR by double clicking the activity and selecting which
    stage to put it in.

15. Remove activities, as needed, by expanding the **Activity** and selecting the trash can
    icon on the activity header.

16. Select **Save**

17. If you have selected to use an approval process, select **‘+ Add approver’**
    and enter in a user with an AAD account. You can add multiple approvers.
    Otherwise, continue to step 21.

18. Select **Send to approvers**.

19. The job will display a **Job status** of **Pending**.

20. Once the **Job status** status changes to **Approved,** it can be activated.

21. To activate the job, select the **Activate** button.

22. Navigate to Postings. Select **Post Now** under the Talent Careers site or
    LinkedIn to post the job.
