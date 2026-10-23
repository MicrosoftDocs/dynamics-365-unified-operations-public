---
title: Troubleshoot Agency management in Dynamics 365 Human Resources
description: Troubleshoot Agency management in Dynamics 365 Human Resources
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 10/22/2026
ms.topic: article
---

# Troubleshoot Agency management

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Agency management in the Career portal is a collaboration model that external recruiting agencies use to submit candidates for shared job ads. This article provides troubleshooting guidance for common issues.

## Troubleshooting

This section covers common symptoms that agencies and administrators encounter, along with the checks, resolutions, and validation steps for each symptom. The following table describes each scenario.

| Symptom | Check | Resolution | Validation |
| ---- | ---- | ---- | ---- |
| Agency user doesn't receive invitation email | Check the **Send agency user invitation email** flow and email connection. | Turn on the flow, repair the connection, and resend the invitation. | The user receives a valid invitation email. |
| Agency user can't sign in | Check the configured Career portal identity provider, invitation completion, and agency role assignment. | Correct the identity provider setup or role assignment, then ask the user to sign in again. Local username and password sign-in isn't supported for agency users. | The user can access only their agency workspace. |
| Shared job ad doesn't appear in the Career portal | Check that the job ad was shared with the correct agency. | Update the job ad sharing selection and save or publish the change. | The job ad appears for the selected agency only. |
| Candidate submission fails | Check the **Recruiter candidate creation** flow and required candidate fields. | Turn on or repair the flow, then verify required data and resume format. | The submission completes or enters the consent workflow. |
| Candidate approval email isn't received | Check the **Send approval email For Agency candidate creation** flow and candidate email address. | Turn on or repair the flow and correct the candidate's email if needed. | The candidate receives approval email. |
| Submission remains pending | Check whether candidate consent is waiting for a response. | Ask the candidate to approve or deny the request or regenerate the request if needed. | The submission status updates after candidate response. |
| Withdrawal notification is missing | Check the withdrawal notification flows. | Turn on or repair the related notification flow. | The expected recipients receive the notification email. |
| Agency sees incorrect data | Check agency-user role assignments and agency mapping. | Correct the user-to-agency mapping and security configuration. | The users can only see their agency data. |
| Duplicate candidate conflict appears | Check whether the candidate or application already exists. | Review the existing record and avoid creating a duplicate submission. | No duplicate candidate or application records are created. |

If an issue requires escalation, gather the following information and contact support:

- Agency name or identifier.
- Agency user's email address and role.
- Job ad identifier.
- Candidate email address used in the submission.
- Date, time, and time zone of the issue.
- Related Power Automate flow runs ID and error message, if available.
