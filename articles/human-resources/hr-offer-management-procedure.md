---
title: Candidate Offer management in recruiting
description: Learn how Offer management guides candidate offers through Draft, Approval, Communication, and Close stages. Discover roles, rules, and lifecycle steps.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 11/12/2026
ms.topic: article
---

# Offer management concepts

Offer management is a capability in the Recruiting Add-On that provides a controlled process for creating, approving, sending, tracking, and closing candidate offers. It defines a structured lifecycle that guides an offer from initial preparation through final outcome, giving recruiters, approvers, and candidates a clear path for each stage of the offer process.

The capability is organized into four lifecycle stages: **Draft**, **Approval**, **Communication**, and **Close**. Recruiters prepare the offer, manage documents, configure approvals, dispatch the offer package, and complete the lifecycle. Approvers review offer details and documents before the offer is sent to the candidate. Candidates receive the offer package and can sign, accept, or decline the offer. Final outcomes are recorded as **Offer accepted** or **Offer rejected**.

You can dispatch offers through a configured **eSign provider** or through a manual, non-eSign path where the recruiter records the signed offer directly.

## Prerequisites

- Enable the feature - An administrator must turn on Offer management for the organization before it can be used. When the feature is turned off, users can't create or open offers. The administrator enables the feature from the Recruiting configuration settings.

- Communication method - Organizations can onboard any eSign provider by creating the required Power Automate flows and integrating the provider with the offer dispatch and response process. If you don't use an eSign provider, the manual non-eSign path is available.

- Provider licensing - ESign usage requires the applicable provider license and configuration before the provider can be used for offer dispatch.  


### Lifecycle overview

Offer management follows an end-to-end lifecycle: Create Offer → Documents → Approval → Communication → Close. If approval isn't required, the recruiter can move directly from **Draft** to **Communication**. If approval is required, **Communication** becomes available only after all approvers approve the offer.

:::image type="content" source="media/hr-offer-management-procedure/offer-management-lifecycle-diagram.png" alt-text="Screenshot of a diagram showing the Offer management lifecycle stages from Draft through Approval, Communication, and Close.":::

### Roles and responsibilities

Offer management defines distinct roles with different levels of access and responsibility throughout the offer lifecycle.

| Role | Responsibility |
|----|----|
| Recruiter | Creates and manages the offer, prepares documents, configures approvals, dispatches the offer package, withdraws the offer when applicable, and closes the offer. |
| Recruiting admin | Receives full control access through the offer owning team. |
| Job recruiter | Receives full control access through the offer owning team. |
| Hiring manager | Receives read-only visibility through the offer access team. |
| Approver | Reviews offer details and documents, approves or rejects the offer, and provides feedback. |
| Candidate | Receives the offer package and signs, accepts, or declines the offer. |

### Draft stage

Use the **Draft** stage to create and prepare an offer. Create new offers with **Offer status = Draft**.

You can create offers on the following pages:

- **Candidate offers workspace** - The recruiter opens **Candidate offers** from the **Hiring** area, selects **New**, chooses either an applicant or a job ad first, provides the **Offer title**, and saves the record.
- **Job Ad offers view** - From an active job ad, the recruiter opens the **Offers** tab, selects **New**, confirms the pre-filled job ad, selects the applicant, enters the **Offer title**, and saves the record.
- **Applicant record action** - From an applicant linked to a job ad, the recruiter selects **Create offer**. The system opens the offer form with the job ad and applicant already populated.

You can only create one offer per applicant. The system prevents you from creating a second offer for the same applicant.

### Initial security setup

- The system automatically creates an **Offer owning team** for every offer. The default owning team members are the **Offer creator, Recruiter, and Recruiting admin**. The team provides full lifecycle control over the offer.
- The system also automatically creates an **Offer access team** to support read-only visibility. The hiring manager (from the associated job ad) is added to this team automatically.

### Document management

Recruiters manage offer files from the **Documents** tab, which separates current files from historical versions using **Active documents** and **Archived documents**.

| Category | Notes |
|----|----|
| Offer letter | One active document per offer |
| Employment agreement | One active document per offer |
| Non-Disclosure agreement | One active document per offer |
| Other | Used when a custom document category is required; one active document per unique custom category name |
| Signed document | System-managed; can only be added, edited, or deleted in the Close stage |

The following rules apply to documents:

- Only one active document per category can exist. For the **Other** category, one active document per unique custom name.
- When you update a document, the previous version moves to **Archived documents**.
- You can add, change, or remove documents only while the offer is in **Draft**. Once the offer moves to **Approval** or **Communication**, documents are locked. They unlock again in **Close** for signed documents only.
- Recruiters can preview and download files by selecting the file name.
- File format guidance - Allowed formats are PDF and DOCX. PDF files shouldn't be protected, and DOCX files should use the **Public** sensitivity label. These checks are performed when a file is uploaded through the offer; documents added through other means should meet the same standards.

#### Approval stage

The **Approval** stage allows offers to be reviewed before they reach the candidate. Complete approval configuration from the **Approvals** tab.

:::image type="content" source="media/hr-offer-management-procedure/offer-approval-process-flow-diagram.png" alt-text="Screenshot of a diagram illustrating the offer approval process flow.":::

#### Approval configuration

- If **Approval required = No**, the offer can move from **Draft** directly to **Communication**.
- If **Approval required = Yes**, the recruiter selects either **Sequential approval** or **Concurrent approval**.

| Approval mode | How it works |
|----|----|
| Sequential approval | Approvers review the offer in a defined order. The next approver is notified only after the previous approver approves. |
| Concurrent approval | All approvers receive the approval request at the same time. |

### Approver management

- Recruiters add approvers from the approval grid and can specify a role for each approver.
- Sequential approvers are assigned an order starting from one. Use **Move up** and **Move down** to adjust the order while the offer is still in **Draft**. The system automatically re-compacts sequence numbers when you remove an approver.
- Add approvers to the **Offer access team** with read-only access limited to **Offer details** and **Offer documents**.

### Approval processing

- Start the approval process by selecting **Submit for approvals** or by moving the lifecycle stage to **Approval**. Both actions behave identically.
- After approval starts, **Offer status** changes to **Approval pending**.
- If all approvers approve, **Offer status** changes to **Approved**.
- If any approver rejects, **Offer status** changes to **Approval rejected** and the offer can't proceed until you move it back to a supported previous stage.
- **Pause Approvals** allows approver changes during the approval stage. Newly added approvers are appended to the sequence, and only those new approvers receive notifications on resubmission.
- Changing the approver sequence after approval starts requires moving the offer back to **Draft**, which resets the approval process.

### Approval statuses (per approver)

| Approval status | Meaning |
|----|----|
| Draft | Approver is configured, but approval isn't started. |
| Pending approval | Approval request is sent and the system is waiting for a response. |
| Approved | Approver approved the request. |
| Rejected | Approver rejected the request. |

> [!NOTE]
> Pausing or resetting approvals is tracked at the offer level. The offer can be in a draft, in-progress, or paused approval state, not as a status for each individual approver.

#### Communication stage

The **Communication** stage delivers the offer package to the candidate. When an offer enters **Communication**, **Offer status** becomes **Communication preparation started**.

:::image type="content" source="media/hr-offer-management-procedure/offer-communication-process-flow.png" alt-text="Screenshot of a diagram illustrating the offer communication process flow.":::

### Entry criteria

- If approval isn't required, recruiters can move from **Draft** directly to **Communication**.
- If approval is required, Communication is available only after all approvers approve.

### Preparing the offer package

- Select **Send offer** to open a side panel for package preparation.
- The candidate email address is populated automatically.
- Select an email template. The subject and body are populated and you can edit them before sending.
- Only **Active documents** are available for the package. You can't include archived documents.
- You can remove documents from the package list without deleting them from the offer. **Undo** restores removed documents in reverse order.

### Delivery methods

| Method | Description |
|----|----|
| eSign delivery | The configured eSign provider prepares and dispatches the package. The candidate signs electronically, and the signed package is returned automatically. |
| Manual (non-eSign) delivery | The offer is sent without an eSign provider. The recruiter records the signed offer manually once the candidate returns it. |

### Email template configuration

Offer management supports configurable email templates to standardize candidate communications during the offer dispatch process.

- The offer dispatch email template serves as the default template. Organizations can create additional templates to address business-specific communication requirements.
- To be available within Offer management, include custom templates in the **Email templates for recruiting** view. You can only select templates in this view during offer dispatch.

Recruiters select from the available recruiting templates. The subject and body are automatically populated, and recruiters can review and edit them before dispatch. The final edited content is used when generating and sending the package.

Templates support dynamic content through placeholders:

| Supported placeholder | Source |
|---------------------------|----------------------------|
| Candidate name | Candidate profile |
| Company name | Organization configuration |
| Job title | Associated job ad |

During dispatch, the service retrieves the latest values from the associated recruiting records and replaces the configured placeholders before delivery. The following validation rules apply:

- You can only select templates in the **Email templates for recruiting** view.
- Placeholder replacement occurs during offer package generation.
- Recruiters can modify the generated content before dispatch.
- Changes to a template don't affect communications that are already sent.

### Dispatch and communication records

- When you select **Send offer**, the chosen delivery method prepares and sends the package by using the selected files and email content.
- The system creates a communication record for both successful and failed dispatch attempts.
- A successful dispatch creates an **Active** communication and sets **Offer status = Offer sent**. A failed dispatch creates a **Communication error** record with failure details. The **Offer status** remains **Communication preparation started**.
- Only one active communication can exist at a time. You can send a new offer package only after the active communication concludes.

### Completion paths

| Path | Result |
|----|----|
| Candidate signs | The signed package is attached under the **Signed document** category, the communication is completed, and **Offer status** is set to **Offer accepted**. The recruiter then moves the offer to **Close** to finalize it. |
| Candidate declines | Communication is completed with **Status reason** = **Offer declined**. **Offer status** becomes **Offer declined**. On **Close**, the outcome is **Offer rejected**. |
| Recruiter withdraws | The active communication is voided after a withdrawal reason is provided. On success, **Offer status** becomes **Offer withdrawn**. On failure, a **Communication error** record is created. On **Close**, the outcome is **Offer rejected**. |
| Reminder / resend | When supported by the selected provider, the recruiter can send a reminder for the active communication. |

### Deactivation before dispatch

- If the offer is in **Communication** with **Offer status** set to **Communication preparation Started** and the recruiter decides not to send the package, they can deactivate the offer.
- The recruiter can reactivate the offer later and continue the communication preparation process.

#### Close stage

The **Close** stage is available once the candidate responds - that is, when **Offer status** is **Offer accepted (signed)**, **Offer declined**, or **Offer withdrawn**.

| Before close | After close | Outcome |
|----|----|----|
| Offer accepted (candidate signed) | **Offer accepted** | The candidate signed the offer; **Close** keeps it as accepted and finalizes the lifecycle. |
| Offer declined | **Offer rejected** | The candidate declined the offer and it is finalized as rejected. |
| Offer withdrawn | **Offer rejected** | The recruiter withdrew the offer and it is finalized as rejected. |

In the **Close** stage, you can add, edit, or delete only **Signed document** files; all other document categories are locked. Recruiters can move back to earlier stages when a supported business process needs to be restarted, and stage-specific rules continue to apply.

> [!NOTE]
> Due to a platform limitation, you can upload only a signed file smaller than 1 MB to Dynamics 365 finance and operations apps. Signed documents at or above 1 MB don't sync to Dynamics 365 finance and operations apps.

#### Access control

Offer management uses two dedicated teams to manage access for each offer.

### Offer owning team

Each offer has a dedicated owning team that provides full control for users responsible for managing the offer lifecycle.

- The owning team is created when the offer is created.
- Default members are **Offer creator, Recruiter, and Recruiting admin**.
- Grants full create, read, update, and delete access across the offer and its approvals, documents, and communications.

Manage owning team members through the following steps:

1. Open the offer and select the **Owner** field shown above the business process flow.
1. The owning team record opens. In the **User associated view** grid, select **Add existing user**.
1. Use the side panel to search for the required user and select **Add**.
1. To remove a member, select the user in the grid and choose **Remove**.

> [!NOTE]
> The team page might take a moment to finish loading. Refresh the page if **Add existing user** isn't visible.

### Offer access team

The access team provides read-only access for users who need visibility into the offer without full lifecycle control.

- Each offer has a separate access team created with the offer.
- Owning team members can manage access team membership from the **Offer details** tab.
- Users added through the access team grid receive read-only access to the complete offer.
- **Approvers** are also added to the access team, but their read-only access is limited to **Offer details** and **Offer documents**.

#### Applicant status synchronization

Offer management keeps the associated applicant record in sync as the offer progresses. This gives recruiters visibility into offer progress directly from the applicant.

| Offer status | Applicant update |
|------------------|--------------------------------------------------|
| Approval pending | Applicant offer status → **Offer in progress** |
| Offer sent | Applicant external status → **Offer dispatched** |
| Offer accepted | Applicant offer status → **Offer accepted** |
| Offer rejected | Applicant offer status → **Offer rejected** |

#### State transition

The following table summarizes how offers move between states based on triggers and conditions.

| Trigger | Condition | Offer status | Approval status | Communication status | Next action |
|----|----|----|----|----|----|
| Offer created | Applicant and title provided | Draft | Not started | Not started | Attach documents and configure approvals |
| Move to Communication without approvals | **Approval required** = **No** | **Communication preparation started** | Not applicable | Not started | Prepare offer package |
| Submit for approval | **Approval required** = **Yes** | Approval pending | **Pending approval** | Not started | Approver review |
| All approvers approve | All approvals completed | Approved | Approved | Not started | Move to Communication |
| Any approver rejects | One or more approvals rejected | **Approval Rejected** | Rejected | Not started | Move back if rework is required |
| Offer dispatched | Dispatch succeeds | Offer sent | Completed / Not applicable | Active | Await candidate response |
| Dispatch fails | Dispatch fails | **Communication preparation started** | Completed / Not applicable | Communication error | Review failure details |
| Candidate signs | Provider completion event (or manual signed-offer receipt) | **Offer Accepted** | Completed / Not applicable | Completed | Move to close |
| Candidate declines | Provider rejection event | **Offer declined** | Completed / Not applicable | Completed / Offer declined | Move to Close |
| Recruiter withdraws | Active communication exists | **Offer withdrawn** | Completed / Not applicable | Completed / Offer withdrawn | Move to Close |
| Close signed offer | Offer already Offer accepted | **Offer accepted** (kept) | Completed / Not applicable | Completed | Lifecycle complete |
| Close declined or withdrawn offer | Offer declined or Offer withdrawn | **Offer rejected** | Completed / Not applicable | Completed | Lifecycle complete |

#### Status glossary

| Status | Meaning |
|----|----|
| Draft | The offer is being prepared. |
| Approval pending | Approval requests have been sent and responses are pending. |
| Approved | All required approvals are complete. |
| Approval rejected | An approver rejected the offer during the approval stage; the offer can be reworked. |
| Communication preparation started | The offer is ready for communication setup but hasn't been sent. |
| Offer sent | The offer package has been sent to the candidate (awaiting signature/response). |
| Offer accepted | Set when the candidate signs; retained as the final state after Close. |
| Offer withdrawn | The recruiter withdrew the offer. |
| Offer declined | The candidate declined the offer. |
| Offer rejected | Final closed state for declined or withdrawn offers. |

> [!NOTE]
> There isn't a separate **Offer signed** status. When a candidate signs, the signed document is stored under the **Signed document** category and the offer status is set directly to **Offer accepted**. Moving the offer to the Close stage keeps this status and completes the lifecycle.

#### Key business rules

- Only one offer is allowed per applicant.
- You can maintain only one active document per category at a time.
- You can modify documents only in **Draft** (unlocked) status. During **Approval** and **Communication** stages, documents are locked. You can modify only **Signed documents** in the Close stage.
- You can't include archived documents in the offer package.
- You can have only one active communication for an offer at a time.
- You can dispatch offers through a configured **eSign provider** or through the manual (non-eSign) path.
- Due to a platform limitation, you can upload to Dynamics 365 finance and operations apps only a signed file smaller than 1 MB.
- An administrator must enable the feature before you can create or open offers.
