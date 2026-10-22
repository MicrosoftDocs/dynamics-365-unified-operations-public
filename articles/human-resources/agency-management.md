---
title: Agency management overview
description: Agency management enables internal recruiters to share job ads with selected agencies in Dynamics 365 Human Resources. 
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 10/22/2026
ms.topic: article
---

# Agency management overview

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Agency management is a Dynamics 365 Human Resources feature that your recruiting team can use to work with approved third-party agencies through the agency experience in the Career portal. Internal users decide which agencies can work on which job ads. Agency users can view shared job ads, acknowledge or deny work, submit candidates, and track the status of their submissions.

This article explains how the feature works and how to complete the setup before agency users start using Career Portal.

Agency management provides a complete workflow for collaborating with third-party agencies, from registration through candidate tracking.

- Agency registration and agency-user invitation.
- Agency-user registration and sign-in through configured Career portal identity providers, such as Microsoft, Microsoft Entra ID, or another identity provider supported by Power Pages.
- Job ad sharing from the internal recruiting app to selected agencies.
- Agency acknowledgment or denial of shared job ads.
- Candidate submission from the Career portal.
- Candidate consent when an agency relationship must be approved.
- Duplicate checks to help prevent repeated candidate or application records.
- Application tracking for agency-submitted candidates.
- Withdrawal notifications for agency-initiated and candidate-initiated withdrawals.
- Agency offboarding and job ad closure handling.

### How the process works

The typical Agency management scenario follows a defined sequence from agency creation to application tracking.

1. A recruiting administrator creates an agency record.
1. The administrator adds agency users and assigns each user an agency role.
1. The system sends invitation emails to agency users.
1. Agency users register and sign in to the Career portal.
1. An internal recruiter shares a job ad with one or more selected agencies.
1. An agency user acknowledges or denies the shared job ad.
1. If the job ad is acknowledged, the agency can submit candidates.
1. If candidate consent is required, the candidate receives an approval email.
1. Approved submissions create or update the appropriate candidate and application records.
1. Agency users track submitted applications in the Career portal.

### Roles and responsibilities

Each role in Agency management has distinct responsibilities across the internal recruiting app and the Career portal.

| Role | Responsibilities |
|----|----|
| Recruiting administrator | Creates agencies, adds agency users, assigns agency roles, and retires agencies when needed. |
| Internal recruiter | Shares job ads with agencies and reviews candidates submitted by agencies. |
| Agency manager | Manages work for their agency and can work with shared job ads and submissions. |
| Agency recruiter | Reviews shared job ads, acknowledges, or denies job ads, submits candidates, and tracks applications. |
| Candidate | Approves or denies agency representation when consent is required. |

### Data isolation and privacy

Agency management ensures each agency works in its own isolated space.

- Agency users can only view job ads, candidates, and applications associated with their own agency.
- Agencies can't view data that belongs to another agency.
- The system records candidate consent when approval is required.
- If a candidate deletes their Career portal account, active links to agency records are removed. The system retains historical records in an anonymized state for audit purposes.

### Prerequisites

 Set up the following prerequisites before you invite agency users or share job ads with agencies.

#### Required access

| Setup area | Required access |
|----|----|
| Agency setup | Recruiting administrator access in the internal recruiting app. |
| Job ad sharing | Internal recruiter access for the job ads that you share. |
| Career portal agency testing | Test agency manager and agency recruiter accounts. |
| Power Automate setup | Permission to view, turn on, and repair required flows and connections. |
| Email validation | Access to test inboxes for agency users and candidates. |
| Power Platform admin center package installation | Permission to install the Recruiting add-on package and Career portal package in the target environment. |

### Environment requirements

Before going live, confirm that you have:

- Deployed and made available the internal recruiting app.
- Installed the Recruiting add-on package from Power Platform Admin Center (PPAC).
- Installed the Career portal package from PPAC.
- Deployed the Career portal and made it reachable by Agency management users.
- Enabled Agency management on the **Agency management settings** page in the Recruiting add-on app.
- Added the Recruiter candidate creation flow to the Career portal cloud flows with the Agency recruiter role.
- Synced the Career portal after adding the cloud flow.
- Configured at least one standard identity provider for agency-user registration and sign-in on the Career portal, such as Microsoft, Microsoft Entra ID, or another identity provider supported by Power Pages.
- Disabled local username and password sign-in for agency users.
- Set up outbound email delivery for invitation, approval, and notification emails.
- Created at least one test job ad for agency sharing.
- Created at least one test agency manager, one test agency recruiter, and one test candidate.

### Install required packages from Power Platform Admin Center (PPAC)

Before configuring Agency management, install both required packages in the target environment from Power Platform admin center:

1. Open Power Platform admin center.
1. Select the target environment.
1. Install the Recruiting Add-on package.
1. Install the Career portal package.
1. Confirm both package installations complete successfully.

### Required Power Automate flows

Turn on the following flows before agency users begin using the feature.

Add the Recruiter candidate creation flow to the Career portal cloud flows with the Agency recruiter role. This step is a one-time Career portal configuration before turning on the flow.

| # | Flow name | Required for | What happens if it's off |
|----|----|----|----|
| 1 | Send agency user invitation email | Agency user onboarding | Agency users are created but don't receive invitation emails. They can't register or sign in. |
| 2 | Recruiter candidate creation flow | Candidate submission from the Career portal | Candidate submission fails and records aren't created. |
| 3 | Send approval email For agency candidate creation | Candidate consent | Candidates don't receive approval emails. Consent-required submissions remain pending. |
| 4 | Agency - candidate withdraw notification | Agency withdrawal notification to candidate | Candidates aren't notified when an agency withdraws their application. |
| 5 | Candidate withdrawal - notify recruiter and agency manager | Candidate withdrawal notification to agency | The submitting agency recruiter and agency managers aren't notified when a candidate withdraws. |

### Validate flow setup

To validate your flow setup, follow these steps:

1. Go to **Power Automate** > **My flows**.
1. Find each flow listed in the required flows table.
1. Confirm that each flow is turned on.
1. Open each flow and check its connections.
1. Repair any invalid or expired connection.
1. Review recent flow run history if the flow already ran.
