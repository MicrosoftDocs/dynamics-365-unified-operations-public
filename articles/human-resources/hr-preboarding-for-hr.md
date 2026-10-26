---
# required metadata

title: Manage preboarding as HR (preview)
description: Learn how HR professionals use preboarding in Microsoft Dynamics 365 Human Resources to invite candidates, review submissions, request rework, record the pre-employment check, and track progress.
author: ramagadu
ms.date: 10/23/2026
ms.topic: how-to
ms.reviewer: twheeloc
# optional metadata

ms.search.form: HcmPreJoiningCandidateHub, HRAdminOnboardingWorkspaceOverviewPage
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ramagadu
ms.search.validFrom: 2026-10-23
ms.dyn365.ops.version: Human Resources

---

# Manage preboarding as HR (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article describes how HR professionals use preboarding in Dynamics 365 Human Resources (preview).
You can manage each candidate from the **Candidates (preview)** page:

- Invite candidates
- Review what candidates submit
- Ask for corrections
- Record the pre-employment check
- Message candidates
- Hire candidates

The **Preboarding (preview)** tab of the **Onboarding** workspace shows what needs your attention across all candidates.

## Prerequisites

- Preboarding is set up and configured for your legal entity. For more information, see [Install and set up preboarding](hr-preboarding-setup.md) and [Configure preboarding](hr-preboarding-configuration.md).
- You have the **Human resource manager**, **Human resource assistant**, or **Recruiter** security role.
- The candidate has a valid email address in their contact information. The invitation is sent to this address.

### Candidates page

To view the candidates, follow these steps:

1. Go to **Human resources** > **Recruitment** > **Candidates (preview)**. You can also find the page under **Personnel management** > **Recruiting** > **Candidates (preview)**. It's available only when the **Enhanced recruiting candidate experience (preview)** feature is enabled.

The list shows each candidate's **Candidate status** and **Preboarding status**. Use the **Candidate status** and **Preboarding status** filters to find candidates, and select **Clear filters** to show all candidates.

The **Preboarding** tab on the Action Pane has the following actions. An action is available only when it applies to the candidate's current status. When no preboarding action is possible, the page explains why. For example, "Preboarding isn't available because this candidate's status is **Ready for offer**. Actions become available when the status is **Ready for preboarding**.
Select **Next action** in the header to see the next step for the candidate.

| Group | Action | Use it to | Available when |
| --- | --- | --- | --- |
| Preboarding | **Initiate** | Invite the candidate to preboarding. | The candidate status is **Ready for preboarding**, and the candidate isn't invited yet. |
| Preboarding | **Reinitiate** | Start preboarding again with a new invitation. | The preboarding status is **Initiated**, **In progress**, or **Failed**. |
| Review | **Request rework** | Ask the candidate to update specific sections. | The preboarding status is **Submitted**. |
| Review | **Approve** | Approve the candidate's submission. | The preboarding status is **Submitted**. |
| Review | **Disqualify** | Stop preboarding, and move the candidate to **Not hired**. | Preboarding is active. |
| Pre-employment check | **Initiate** | Start the pre-employment check with a vendor. | The preboarding status is **Approved**. |
| Pre-employment check | **Update status** | Record the outcome of the pre-employment check. | The check started. |
| Pre-employment check | **Skip** | Skip the pre-employment check, with a reason. | The preboarding status is **Approved**, and the check didn't start. |
| Communication | **Email candidate** | Send the candidate a message. | A candidate is selected. |

### The candidate record

To view a candidate's details, follow these steps:

1. Go to **Human resources** > **Recruitment** > **Candidates (preview)**.
1. On the **Overview** tab:

- **Lifecycle** shows the **Lifecycle phase order** (**Preboarding only**, **Offer only**, **Preboarding first**, or **Offer first**), the state of the **Preboarding**, **Pre-employment check**, **Offer**, and **Onboarding** phases, and the **Next step**. A phase that doesn't apply to the candidate shows **Not applicable**.
- **Recruiting** shows the recruiting request, the hiring manager, and the **Assigned HR**, the HR worker who receives the notifications about this candidate.
- **Preboarding** shows the **Status**, **Submitted date**, **Reviewed date**, and **Role confirmed**, and the **Reason for disqualification** if the candidate was disqualified.
- **Pre-employment check** shows the **Check status**, **Initiated date**, **Vendor**, and **Comments**.

The **Profile**, **Address and identification**, **Competencies**, and **Personal contacts** tabs show the information that the candidate entered. You can edit it. A dependent's date of birth can't be later than today. The **Documents** tab shows the files that the candidate uploaded. You can open, remove, and download them, and upload more.

The **Audit history** tab has four sections:

- **Rework history** – Each rework request, with the instructions and when it was resolved.
- **Preboarding history** – Each preboarding status change, who made it, and why.
- **Lifecycle history** – Each candidate status change, the system it came from, and why.
- **Message history** – Each message sent to the candidate. For more information, see [Send a message to a candidate](#send-a-message-to-a-candidate).

#### Create a candidate in Human Resources

When you use the **Dynamics 365 Human Resource recruiting add-on**, Human Resources creates candidates when a recruiter moves an applicant to **Ready to hire**. If you use preboarding without the Recruiting app, for example by using a third-party recruiting solution, create the candidate yourself:

1. On the **Candidates (preview)** page, on the **Candidate** tab, select **New**.
1. On the details page, enter the candidate's name and personal details, and a primary email address. Preboarding sends the invitation to this address.
1. On the **Overview** tab, enter the recruiting request and the **Availability date**, which the candidate sees as their start date, and select the **Assigned HR**.
1. Save the candidate.

The candidate's status depends on the preboarding setup of the legal entity. For example, when preboarding is enabled, the candidate is **Ready for preboarding**, and you can invite them.

#### Invite a candidate

To invite a candidate to preboard, follow these steps:

1. On the **Candidates (preview)** page, select the candidate.
1. On the **Preboarding** tab, in the **Preboarding** group, select **Initiate**.
1. When prompted, select **Yes** to initiate preboarding for the candidate.

The preboarding status changes to **Initiated**, and the candidate receives an invitation email with a link to the careers site. The careers site prepopulates information that's already on the candidate, such as their name, email address, education, experience, and skills, for them to review.

> [!TIP]
> Before you initiate, check the candidate's name, email address, and recruiting request. They appear in the invitation and on the careers site.

When the candidate saves on the careers site for the first time, the preboarding status changes to **In progress**. When they submit, it changes to **Submitted**. The candidate's **Assigned HR** and the notification recipients of the legal entity receive Teams notifications for these events, depending on the notifications that are turned on.

> [!TIP]
> To make sure the right HR person is notified about this candidate, in the **Recruiting** section, select them in **Assigned HR** on the **Overview** tab. For more information, see [Notifications](hr-preboarding-configuration.md#notifications).

If a candidate doesn't start, they're listed in a daily reminder in Teams, and in the **Pending preboarding invitations** insight.

#### Correct the candidate's details or send the email again

If you find something wrong about the candidate when you initiated preboarding, or if the candidate needs the email again, select **Reinitiate**. For example, the start date, the role, or the hiring manager that the candidate sees on the careers site is wrong.

1. Correct the information in Human Resources:

   - **Start date** – The candidate's **Availability date**, on the **Overview** tab of the candidate.
   - **Role** and **Hiring manager** – The job and the hiring manager of the candidate's recruiting request.
   - **Name** and **email address** – On the candidate record.
1. Select the candidate. On the **Preboarding** tab, in the **Preboarding** group, select **Reinitiate**, and confirm.

The careers site is updated with the corrected start date, role, hiring manager, legal entity, name, and email address. The information that the candidate already entered is kept. The candidate receives an email containing a sign-in link if they already have an account on the careers site, or their invitation link if they haven't created an account yet.

You can reinitiate when the preboarding status is **Initiated**, **In progress**, or **Failed**. After the candidate submits, their details are no longer updated this way. To correct them then, request rework, or edit the candidate record directly.

If an invitation fails, the preboarding status is **Failed**, and a **Preboarding failed** message bar offers **Reinitiate preboarding**.

#### Review a submission

When a candidate submits, their information is written to the candidate record. Review it on the candidate's tabs, and then do one of the following:

> [!NOTE]
> Phone numbers and email addresses keep the description the candidate entered. Their purpose is written as **Business**, **Home**, or **Other**, matching **Business**, **Personal**, or **Other** on the careers site. These purposes must exist under **Organization administration** > **Global address book** > **Address and contact information purpose**. If a purpose can't be found, the contact is saved with the default purpose instead.

- To accept the submission, select **Approve**, and confirm. The preboarding status changes to **Approved**, and the candidate receives an email.
- To ask for changes, request rework.
- To stop preboarding, disqualify the candidate.

#### Request rework

To request rework, follow these steps:

1. Select the candidate. On the **Preboarding** tab, in the **Review** group, select **Request rework**.
1. In the **Request rework** dialog, select each section that the candidate must update, such as **Rework address** or **Rework documents**.
1. In **Instructions to candidate**, describe what to change.
1. Select **OK**.

You must select at least one section or enter instructions. The preboarding status changes to **Rework requested**, and the candidate receives an email with your instructions. On the careers site, only the selected sections are open for editing. When the candidate resubmits, the status changes back to **Submitted**.

#### Disqualify a candidate

To disqualify a candidate, follow these steps:

1. Select the candidate. On the **Preboarding** tab, in the **Review** group, select **Disqualify**.
1. Enter the **Reason for disqualification**, and select **OK**.
1. Confirm. The candidate moves to **Not hired**.

The preboarding status changes to **Rejected**, the careers site shows that the application is closed, and the candidate receives an email. If the pre-employment check is already completed, you're warned that disqualifying discards its outcome.

About 10 minutes after the candidate is sent the email, their preboarding information is deleted from Dataverse, and they can no longer open the preboarding pages on the careers site. The candidate information that already was transferred to Human Resources stays. For more information, see [What happens to a candidate's information if they don't join?](hr-preboarding-faq.md#what-happens-to-a-candidates-information-if-they-dont-join)

#### Record the pre-employment check

After you approve the submission, record the pre-employment check. Preboarding records the vendor and the outcome. It doesn't send a request to the vendor.

#### Start the check

1. Select the candidate. On the **Preboarding** tab, in the **Pre-employment check** group, select **Initiate**.
1. In the **Initiate pre-employment check** dialog, select the **Vendor**. The default vendor for the legal entity is preselected.
1. Select **OK**.

The preboarding status changes to **Pre-employment check started**, and the candidate receives an email.

#### Record the outcome

1. Select the candidate, and then select **Update status**.
1. In the **Update pre-employment check status** dialog, select the **Pre-employment check outcome**: **Completed** or **Rejected**. Add **Comments** if needed.
1. Select **OK**.

If you select **Rejected**, you're asked to confirm, and the candidate moves to **Not hired** and their preboarding closes. You can't undo it. The candidate receives an email with the outcome.

#### Skip the check

If the candidate doesn't need a pre-employment check, select **Skip** while the status is **Approved**, enter the **Reason**, and confirm. The candidate moves to the next stage without a check result. After a check starts, you can't skip it. Record its outcome instead.

When the check is completed or skipped, preboarding is complete, and the candidate moves on. With **Preboarding first**, the candidate is **Ready for offer**. With **Offer first**, or when there's no offer phase, the candidate is **Ready to onboard**. A candidate who wasn't created from an applicant in the Recruiting app has no offer to wait for, so after a few seconds they move from **Ready for offer** to **Ready to onboard**. If they don't, select **Sync**.

#### Send a message to a candidate

1. Select the candidate. On the **Preboarding** tab, in the **Communication** group, select **Email candidate**.
1. Enter the **Subject** and the **Message**, and then select **Send**.

The message goes to the email address on the candidate's record. You must provide both the subject and the message.

> [!NOTE]
> The message isn't sent from your own mailbox. It's sent from the **Sender email address** that's set up for preboarding, such as a shared careers mailbox. If you don't set up a sender email address, the message is sent from the account that owns the Outlook connection that preboarding uses. The candidate can't reply to you directly, so include how they can contact you in the message if needed. For more information, see [Send candidate emails from a shared mailbox](hr-preboarding-configuration.md#send-candidate-emails-from-a-shared-mailbox).

On the **Audit history** tab, **Message history** shows each message with its **Sent on** date, **Subject**, **Delivery status** (**Pending**, **Sent**, or **Failed**), and **Sent by**. If a message wasn't sent, the reason appears in the **Delivery error** column in plain text. To show the column, add it to the grid by using **Insert columns**.

#### Hire the candidate

When the candidate status is **Ready to onboard**, select the candidate. On the **Candidate** tab, select **Hire**. Complete the **Hire new worker** dialog, including the employment start date. If the candidate is already a worker in your organization, select **Transfer** instead.

**Hire** and **Transfer** are unavailable until the candidate is ready to onboard, after every required phase is complete.

When you hire the candidate, the emergency contacts, dependents, and documents from preboarding are copied to the new worker.

To stop hiring a candidate whose hiring is still in progress, use **Do not hire**, which moves them to **Not hired**, or **Dismiss candidate**, which moves them to **Dismissed**. These actions aren't available for candidates who are already **Hired**, **Not hired**, or **Dismissed**. Both actions withdraw the candidate's open preboarding. About 10 minutes later, their preboarding information is deleted from Dataverse and their access to the preboarding pages is removed. You can't undo these actions from the **Candidates (preview)** page.

#### Keep the candidate and the applicant in sync

When you use the Recruiting app, each candidate exists in two places: the candidate in Human Resources, and the applicant in the Recruiting app. They're kept in snyc automatically:

- The offer outcome in the Recruiting app (sent, accepted, declined, or withdrawn) is reported to Human Resources, which moves the candidate on.
- The candidate status in Human Resources is copied to the applicant. While the candidate is in preboarding, the applicant's status in the Recruiting app is **Ready for preboarding** or **Preboarding in progress**.

Sometimes they can get out of sync, for example if an update failed during a service outage, or if a change was made while the recruiting integration was off. You might see that:

- The offer was accepted in the Recruiting app, but the candidate is still **Offer in progress** in Human Resources.
- The applicant shows a different status from the candidate.
- A candidate doesn't move on after the offer or preboarding is complete.

**Sync** fixes this without any manual edits.

1. Select the candidate. On the **Candidate** tab, select **Sync**.

   "A sync has been requested. The result will appear on this candidate once the recruiting integration has responded." message appears.
1. Wait a minute or two, and then refresh the candidate.

Sync reads the applicant's current offer status in the Recruiting app and reports it to Human Resources. Human Resources then works out the correct candidate status from the offer status and the preboarding status, and that status is copied back to the applicant. The result appears on the candidate, and any status change is recorded under **Lifecycle history** on the **Audit history** tab.

Things to know:

- Sync is safe to use at any time. If the candidate and the applicant are already in step, nothing changes.
- Every sync records its result on the candidate. For a candidate who wasn't created from an applicant in the Recruiting app, the result is **No change was needed. This candidate has no applicant in the Recruiting app, there was nothing to sync.** If that candidate is waiting for an offer, Sync completes the offer phase instead.
- **Sync** is available only when **Integration to new recruiting app** is on.
- Sync doesn't reopen a candidate who is **Hired**, **Not hired**, or **Dismissed**. The only change it makes to such a candidate is when the Recruiting app shows the offer as declined or the application as withdrawn: then the candidate is set to **Not hired**.
- If Sync doesn't fix the status, check that the preboarding flows are turned on, and check the run history of **Preboarding Flow U - Lifecycle Sync On Demand** and **Preboarding Flow Q - Lifecycle Status**.

#### Track preboarding in the Onboarding workspace

Go to **Human resources** > **Onboarding**, and select the **Preboarding (preview)** tab. It shows preboarding candidates for the selected legal entity and period.

**Insights** lists the candidates who need action today:

| Insight | Candidates |
| --- | --- |
| **Pending preboarding invitations** | Invited, but didn't start for longer than the pending action threshold. |
| **HR review overdue** | Submitted longer ago than the pending action threshold, and not yet reviewed. |
| **Rework requested** | Asked to rework their submission. |
| **Joining date approaching or passed, details incomplete** | Didn't submit, and their estimated start date is within the joining nearing threshold or has passed. |

**Candidate pipeline** shows each candidate as a card in a lane:

| Lane | Candidates |
| --- | --- |
| **Preboarding not initiated** | Ready for preboarding, and not invited yet. |
| **Preboarding process** | Invited, in progress, submitted, or failed. |
| **HR review** | Approved, disqualified, or asked to rework. |
| **Background checks** | Pre-employment check started or rejected. |
| **Offer phase** | Ready for offer, or with an offer in progress. |
| **Ready for worker creation** | Pre-employment check completed or skipped. |

Select a card or an insight to open the candidate.

Insights are shown even when no candidate falls in the selected period. If there are insights but no pipeline cards, the page reads "No preboarding activity for *legal entity* in last *period*".

## Statuses

### Candidate status

| Candidate status | Meaning |
| --- | --- |
| **Not processed** | The candidate was created before the hiring lifecycle was set up. Run **Process candidate statuses**. |
| **Ready for preboarding** | You can invite the candidate. |
| **Preboarding in progress** | The candidate is completing preboarding, or you're reviewing it or running the pre-employment check. |
| **Ready for offer** | The offer is the next step. |
| **Offer in progress** | An offer was sent. |
| **Ready to onboard** | Every required phase is complete. You can hire the candidate. |
| **Hired** | The candidate is hired. |
| **Not hired** | The candidate was disqualified, failed the pre-employment check, declined the offer, or was marked **Do not hire**. |
| **Dismissed** | The candidate was dismissed. |

The order of the phases depends on the **Offer timing type** that you set when you create the candidate:

- **Preboarding first** – Ready for preboarding > Preboarding in progress > Ready for offer > Offer in progress > Ready to onboard.
- **Offer first** – Ready for offer > Offer in progress > Ready for preboarding > Preboarding in progress > Ready to onboard.

If only one phase applies, for example when there's no offer phase, the candidate skips the other phase.

### Preboarding status

| Preboarding status | Meaning |
| --- | --- |
| **Not initiated** | You didn't invite the candidate. |
| **Initiated** | You invited the candidate, but they didn't start. |
| **In progress** | The candidate started on the careers site. |
| **Submitted** | The candidate submitted. Review the submission. |
| **Rework requested** | You asked the candidate to update some sections. |
| **Approved** | You approved the submission. |
| **Pre-employment check started** | The pre-employment check is in progress. |
| **Pre-employment check completed** | The check was completed. Preboarding is complete. |
| **Pre-employment check skipped** | The check was skipped. Preboarding is complete. |
| **Pre-employment check rejected** | The check was rejected. The candidate is **Not hired**. |
| **Rejected** | The candidate was disqualified. |
| **Withdrawn** | The candidate was dismissed. |
| **Failed** | The invitation couldn't be completed. Select **Reinitiate**. |

## Related information

- [Preboarding in Dynamics 365 Human Resources](hr-preboarding-overview.md)
- [Configure preboarding](hr-preboarding-configuration.md)
- [Complete preboarding as a candidate](hr-preboarding-for-candidates.md)
- [Preboarding FAQ](hr-preboarding-faq.md)
