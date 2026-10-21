---
title: Configure Agency management 
description: Set up Agency management in the Recruiting Add-on. Configure agency users, share Job Ads, and validate candidate submissions.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 07/26/2026
ms.topic: article
---

# Configure Agency management

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes how to set up Agency management in a nonproduction environment before enabling real agency users.

## Enable Agency management settings

1. Open the Recruiting add-on model-driven app.
1. In the left sitemap, find **Setup**.
1. Select **Agency management**.
1. On the **Agency management** page, set the **Status** field to **Enabled**.

The **Agency management** feature is enabled for the environment.

### Add the recruiter candidate creation flow to the Career portal

1. Go to <https://make.powerpages.microsoft.com/>.
1. Select the target environment.
1. Edit the Career portal site.
1. Go to **Set up** > **Cloud flows**.
1. Select **Add existing flow**.
1. Add **Recruiter candidate creation** flow.
1. Assign the Agency recruiter role to the flow.
1. Select **Sync**.

The **Recruiter candidate creation** flow appears under **Cloud flows** with the Agency recruiter role, and the Career portal is synced.

### Create a test agency

To create a test agency, follow these steps:

1. Sign in to the internal recruiting app as a recruiting administrator.
1. Create a new agency record.
1. Save the agency record.

You can assign users to the agency record.

### Add agency users

To add an agency user, follow these steps:

1. Open the test agency record.
1. Add one agency manager.
1. Add one agency recruiter.
1. Confirm that each user has the correct agency role.
1. Send the agency-user invitations.

The system sends invitation emails to both agency users.

### Confirm agency registration

To confirm agency registration, follow these steps:

1. Open each invitation email.
1. Complete registration for the agency manager and agency recruiter by using a configured Career portal identity provider, such as Microsoft, Microsoft Entra ID, or another provider supported by Power Pages.
1. Sign in to the Career portal with each account.

When agency users sign in, they see only their agency workspace.

> [!NOTE]
> Local username and password sign-in is disabled for agency users.

### Share a job ad with the agency

After confirming the agency registration, you can share a job ad.

To share a job ad, follow these steps:

1. Sign in to the internal recruiting app as an internal recruiter.
1. Open the test job ad.
1. Enable external-agency sharing for the job ad.
1. Select the test agency.
1. Save or publish the sharing update.

The test job ad appears in the Career portal for the selected agency.

### Acknowledge the job ad

1. Sign in to the Career portal as the agency recruiter.
1. Open the shared job ad.
1. Select **Acknowledge**.

Candidate submission is available for the acknowledged job ad.

### Submit a test candidate

1. Open the acknowledged job ad.
1. Select **Submit candidate**.
1. Enter the candidate's first name, last name, email address, and phone number.
1. Upload the candidate resume as a PDF.
1. Submit the candidate.

The system accepts the submission or starts the candidate consent process if approval is required.

### Validate candidate consent

If candidate approval is required, follow these steps:

1. Open the candidate approval email.
1. Select **Approve** or **Deny**.
1. Return to the Career portal and review the submission status.

Submissions that are approved continue the flow. Submissions that are denied don't complete the flow and the agency isn't credited for the candidate.

### Validate tracking and notifications

1. Confirm that the application appears in the **Agency application tracking** view.
1. Confirm that the **Application status** is correct.
1. Test an agency-initiated withdrawal and confirm that the candidate is notified.
1. Test a candidate-initiated withdrawal and confirm that the submitting recruiter and agency managers are notified.

### Common tasks

Some common tasks that you perform in Agency management include:

- Register an agency - After you register an agency, set up users and share the job ad.
- Add or update agency users - The user receives an invitation and access based on the assigned agency role.
- Share a job ad with agencies - Selected agencies can see the shared job ad.
- Acknowledge or deny a job ad - Candidate submission is available only for acknowledged job ads.
- Submit a candidate - Candidate and application records are created unless duplicate checks block the submission.
- Offboard an agency - The agency no longer has active Career portal access. Historical records remain available for audit.

To register an agency, follow these steps:

1. Sign in to the internal recruiting app as a recruiting administrator.
1. Go to **Agency management**.
1. Select **New agency**.
1. Enter the required agency information.
1. Save the record.

To add or update agency users, follow these steps:

1. Open the agency record.
1. Add or update the agency user's name and email address.
1. Assign the user as Agency manager or Agency recruiter.
1. Save the user record.
1. Send or resend the invitation if the user isn't registered.

To share a job ad with agencies, follow these steps:

1. Sign in as an internal recruiter.
1. Open the job ad.
1. Enable external-agency sharing.
1. Select the agencies that can work on the job ad.
1. Save or publish the update.

To acknowledge or deny a job ad, follow these steps:

1. Sign in to the Career portal as an agency manager or recruiter.
1. Open the shared job ad.
1. Select **Acknowledge** to work on the job ad, or select **Deny** to decline it.

To submit a candidate for a job, follow these steps:

1. Open an acknowledged job ad in the Career portal.
1. Select **Submit candidate**.
1. Enter the required candidate details.
1. Upload a PDF resume.
1. Submit the candidate.

To offboard an agency, follow these steps:

1. Sign in as a recruiting administrator.
1. Open the agency record.
1. Retire or deactivate the agency.
1. Confirm that agency users can no longer access the agency experience in the Career portal.

### Application statuses

|Status| Meaning |
|-------|-----------|
|Submitted |The application is sent to the internal recruiting team.|
|In Progress| The candidate is actively being considered.|
|Rejected| The candidate isn't selected for the role.|
|Hired| The candidate is hired.|
|Withdrawn| The candidate or the agency withdraws the application.|

### Notifications

|Event| Recipient|
|-------|----------|
|Agency user invitation is created| Invited agency user|
|Candidate consent is required| Candidate|
|Agency withdraws a candidate| Candidate|
|Candidate withdraws directly| Submitting agency recruiter and agency managers|
