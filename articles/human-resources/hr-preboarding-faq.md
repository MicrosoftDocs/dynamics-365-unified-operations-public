---
# required metadata

title: Preboarding FAQ (preview)
description: This article answers frequently asked questions about preboarding in Microsoft Dynamics 365 Human Resources.
author: ramagadu
ms.date: 10/23/2026
ms.topic: faq
ms.reviewer: twheeloc
# optional metadata

ms.search.form: 
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

# Preboarding FAQ (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article answers frequently asked questions about preboarding in Dynamics 365 Human Resources (preview).

## What is preboarding?

Preboarding lets new hires provide their personal details, contacts, dependents, identification, experience, education, skills, certifications, screenings, and documents on your careers site before their first day. HR reviews the information in Human Resources, where it's written to the candidate record, ready for hire.

### Do I need the HR Recruiting app to use preboarding?

You need to install it, but you don't need to use it. Preboarding ships in the HR Recruiting app (**Dynamics 365 Human Resource recruiting add-on**) and its careers site (**Dynamics 365 Human Resources careers**). After that, you can use preboarding in either of these ways:

- **Preboarding only** – Create candidates in Human Resources and run preboarding for them. Don't use any other Recruiting app or careers site features, such as job ads, applicants, or offer management. Use this option if you use a third-party recruiting solution.
- **Preboarding with the Recruiting app** – Applicants move from the Recruiting app into Human Resources, and preboarding and the offer are managed as one candidate lifecycle.

The candidate lifecycle settings need the Recruiting app. These settings are **Integration to new recruiting app**, **Offer timing type** (**Preboarding first** or **Offer first**), the offer phase, offer management, and **Sync**. When you use preboarding only, preboarding always comes first, and candidates go straight from preboarding to **Ready to onboard**.

### Can candidates complete preboarding before they get their offer?

Yes, if you use preboarding with the Recruiting app. Set **Offer timing type** to **Preboarding first** for the legal entity. To run preboarding after the offer, select **Offer first**. Both options need **Integration to new recruiting app**. Each candidate keeps the order that you set when you create the candidate.

> [!NOTE]
> Offer management in the Recruiting app isn't released yet. Until it's released, the offer phase is completed automatically, whichever option you choose.

#### Which steps do candidates see?

The portal always shows **Personal details** and **Review and finish**. You choose which other steps to show and which steps are mandatory under **Data collection steps** on the **Preboarding (preview)** tab of the **Human resources parameters** page. For more information, see [Configure preboarding](hr-preboarding-configuration.md).

#### Can I add my own fields?

Yes. You can add fields to every step except **Documentation** and **Review and finish**, and write their values to Human Resources. For more information, see [Add custom fields to preboarding](hr-preboarding-custom-fields.md).

#### How do candidates sign in?

It depends on whether the candidate already has an account on your careers site:

- **The candidate already has an account** - For example, because they applied for a job on the careers site. They don't receive an invitation. Their email has a link to the careers site sign-in page. They sign in with their existing account, and then select **Preboarding (preview)** in the menu.
- **The candidate doesn't have an account** - Their email has an invitation link. They open it and create an account on the careers site, with the email address that the invitation was sent to. They then see **Preboarding (Preview)** in the menu.

We recommend that candidates sign up with a trusted identity provider that you set up for the careers site. For more information, see [Set up how candidates sign in](hr-preboarding-setup.md#candidate-sign-in).

#### Can candidates change their information after they submit?

No. After a candidate submits, their information is read-only on the careers site. If something needs to change, HR requests rework on the sections that need changes. The candidate can then edit only those sections, and submit again. HR can also edit the information on the candidate record in Human Resources.

#### Can a candidate change their status on the careers site?

No. On the careers site, a candidate can only start preboarding and submit it. The server checks every change that a candidate makes, and it refuses status changes that only HR can make, such as approval.

#### What happens to the candidate's documents?

When the candidate submits, their documents are attached to the candidate in Human Resources, on the **Documents** tab. When you hire the candidate, the documents, emergency contacts, and dependents are copied to the new worker.

#### What happens to a candidate's information if they don't join?

When HR withdraws a candidate's preboarding or disqualifies the candidate, preboarding waits about 10 minutes and then:

- Deletes the candidate's preboarding information from Dataverse, including the documents they uploaded and the status history.
- Removes the candidate's access to the preboarding pages on the careers site, and deletes any invitation they didn't use. If the candidate has preboarding open in another legal entity, they keep their access.

Preboarding is withdrawn when HR dismisses the candidate or marks them **Do not hire**, and when the candidate declines the offer or withdraws their application in the Recruiting app. A disqualified candidate's information is deleted only after they're sent the decision email.

The candidate's careers site account isn't deleted, because they can use it to apply for other jobs. The information that already reached Human Resources stays on the candidate there, together with the full preboarding status history. Manage it with your organization's retention policies for candidates in Human Resources.

Information isn't deleted for candidates whose preboarding was approved, or whose pre-employment check was completed, skipped, or rejected. It also isn't deleted for candidates whose preboarding ended before this cleanup was installed.

#### Does preboarding run the pre-employment check?

No. Preboarding records the vendor and the outcome of the pre-employment check. You run the check with your vendor, and then record the outcome on the **Candidates (preview)** page. You can also skip the check when it isn't needed.

#### Who receives HR notifications?

The **Assigned HR** worker on the candidate receives the notifications about that candidate in Microsoft Teams. In addition, the workers under **Notification recipients** on the **Human resources parameters** page receive the notifications about every candidate. So you can notify only the HR person who looks after each candidate, a central HR team, or both. Notifications are sent only for the events that are turned on. For more information, see [Notifications](hr-preboarding-configuration.md#notifications).

#### Which address do candidate emails come from?

On the **Human resources parameters** page > **Preboarding (preview)** > **Sender email address**. Otherwise, from the account that owns the **Recruiting office 365 outlook connection**. For more information, see [Send candidate emails from a shared mailbox](hr-preboarding-configuration.md#send-candidate-emails-from-a-shared-mailbox).

#### How do I find out why an email to a candidate failed?

For messages that HR sends with **Email candidate**, the **Message history** on the candidate shows the **Delivery status**, and the reason in the **Delivery error** column. For other emails, HR receives a Teams notification when an email can't be sent. Check the run history of the flow and the **Recruiting office 365 outlook connection**. Candidate information is hidden in the flow run history, so read the error on the failed step.

#### What happens to candidates if I turn off preboarding?

Candidates you create while preboarding is on continue with it. New candidates skip preboarding. To move candidates who are waiting for preboarding and didn't start it, on the **Human resources parameters** page >  **Recruitment**. Select **Recover candidates stuck by disabled preboarding**.

#### What are the known limitations?

- File size - The largest file that a candidate can upload is 10 MB, or less if you set a lower **Maximum document file size**.
- Blocked file types - For security, the careers site refuses web page, SVG, XML, and script files, such as **html**, **svg**, **xml**, and **js**, even if a document requirement accepts them. For the full list, see [Set up documents](hr-preboarding-configuration.md#set-up-documents).
- Public site - Candidates can't reach a private site. Make the careers site public.
- Updates overwrite site changes - Updating the careers app overwrites changes to the content snippets and site settings that ship with it.
- Custom fields need a site setting - For each custom field, add its column to the **Webapi/**_table_**/fields** site setting. Changes can take a few minutes to appear.
- Save your work - A step is saved when the candidate selects **Next**, **Save and close**, or **Save details**. Candidates are asked before they leave a form with unsaved changes.
- Email outages delay submissions - If the Outlook connection fails, flows that send candidate emails retry the email before they fail, and the next submission waits for them. Check the connection if submissions are slow to reach Human Resources.

#### Related information

- [Preboarding in Dynamics 365 Human Resources](hr-preboarding-overview.md)
- [Install and set up preboarding](hr-preboarding-setup.md)
- [Configure preboarding](hr-preboarding-configuration.md)
- [Manage preboarding as HR](hr-preboarding-for-hr.md)
- [Complete preboarding as a candidate](hr-preboarding-for-candidates.md)
