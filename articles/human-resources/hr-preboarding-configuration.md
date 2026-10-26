---
# required metadata

title: Configure preboarding in Dynamics 365 Human Resources (preview)
description: This article explains how to configure preboarding in Microsoft Dynamics 365 Human Resources, including the portal steps, documents, pre-employment check vendors, notifications, sender address, and email templates.
author: ramagadu
ms.date: 10/23/2026
ms.topic: how-to
ms.reviewer: twheeloc
# optional metadata

ms.search.form: HRMParameters
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

# Configure preboarding in Dynamics 365 Human Resources (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to configure preboarding in Dynamics 365 Human Resources (preview) for a legal entity. Most settings are on the **Preboarding (preview)** tab of the **Human resources parameters** page. Changes that you make there are copied to the careers site automatically, usually within a few minutes.

Before you begin, install and set up preboarding. For more information, see [Install and set up preboarding](hr-preboarding-setup.md).

## Set the preboarding parameters

Set preboarding parameters for each legal entity. Repeat these steps in each legal entity that uses preboarding.

1. Go to **Human resources** > **Setup** > **Human resources parameters**.
1. Select the **Preboarding (preview)** tab.
1. Set the fields that are described in the following sections, and then select **Save**.

> [!NOTE]
> Each candidate keeps the **Enable preboarding** and **Offer timing type** values that were in effect when the candidate was created. Changes apply to new candidates.

### Enable preboarding

When you set **Enable preboarding** to **Yes** in the legal entity, new candidates go through preboarding before they're ready to onboard, and HR can invite them to the careers site.

When it's **No**, new candidates skip preboarding, and you can't change the other preboarding settings.

In the **Offer timing type** field, select:
**Preboarding first** - if you want candidates to complete preboarding and the pre-employment check before the offer.
**Offer first** - if you want candidates to complete the offer before preboarding.
You can select **Offer first** only when **Integration to new recruiting app** is set to **Yes** on the **Recruitment** tab. Without the integration, there's no offer phase, so preboarding always comes first. |

### Candidate portal

On the **Candidate portal**, the following options are available:

- **Preboarding portal name** - The name that's used in the emails that are sent to candidates, for example in the subject line and in the footer. For example, **Contoso careers**.
- **Career portal URL** - The web address of your careers site. It's used to build the links in candidate emails. If it's blank, the address in the **Preboarding Portal Url** environment variable is used. If that's blank too, the address of the Power Pages site in the environment is used, when the environment has only one site. Set this field.
- **Sender email address** - Optional. The address that candidate emails are sent from, for example a shared careers mailbox. The account that owns the Outlook connection must have **Send As** permission on it. Leave it blank to send from that account. For more information, see [Send candidate emails from a shared mailbox](#send-candidate-emails-from-a-shared-mailbox).
- **Maximum document file size** - The largest file, in MB, that a candidate can upload on the careers site. Enter a value from 1 through 10. If it's blank, the limit is 10 MB.

Under **Set up links for candidates**, add the links that candidates see on the **Preboarding** page of the careers site, such as your employee handbook or benefits site. Select **New link**, and enter:

- **Name** – The text that the candidate sees.
- **Internet address** – A full URL, such as `https://www.contoso.com`.
- **Group** – The heading that the link is listed under. To list several links under the same heading, add a link for each one, and enter the same **Group** for each.
- **Description** – The text that's shown under the group heading.

### Data collection steps

Choose which steps candidates see on the careers site, and which steps they must complete.

- Address details
- Contact information
- Dependents
- Emergency contact
- Identification / ID details
- Professional experience
- Education history
- Skills
- Certifications
- Screenings
- Documentation

- **Enabled** shows the step on the careers site and lets HR request rework on it. For the **Documentation** step, the option is named **Enable document collection**. When it's off, candidates don't upload documents.
- **Mandatory** requires the candidate to complete the step before they can submit. You can set **Mandatory** only while the step is enabled.

The **Personal details** and **Review and finish** steps are always shown.

### Pre-employment check

In **Default pre-employment check vendor**, select the vendor that's preselected when HR starts a pre-employment check. HR can select another vendor. The vendor must be set up for this legal entity. For more information, see [Set up pre-employment check vendors](#set-up-pre-employment-check-vendors).

### Notifications

Preboarding sends HR notifications in Microsoft Teams, for example when a candidate starts or submits, or when an email to a candidate can't be sent. You decide who receives them.

For each candidate, HR can select an **Assigned HR** worker, on the **Overview** tab, in the **Recruiting** section. The assigned HR worker receives the notifications about that candidate. You can select any worker whose security role gives access to candidates, and you can change it at any time. The notification goes to the worker's primary email address.

**Notification recipients** - add workers to receive notifications about every candidate in the legal entity, in addition to the candidate's **Assigned HR**.

If you want only the HR person who looks after each candidate to be notified, set **Assigned HR** on each candidate, leave **Notification recipients** and the **Preboarding Notify Email** environment variable empty. |
If you want a central HR team to be notified about every candidate, add the team members under **Notification recipients**. You can also set **Assigned HR** on candidates, so that the assigned person is notified too.

To add notification recipients:

1. Under **Notification recipients**, select **New**, select the **Worker** who receives the notifications, and check their **Email**.
1. Add a row for each person.

> [!NOTE]
> If a legal entity has no notification recipients, notifications go to the address in the **Preboarding notify email** environment variable. To notify only the **Assigned HR**, leave both empty. The daily **Stuck candidate reminder** covers several candidates, so it goes to the notification recipients of the legal entity, or to that address when there are none. It isn't sent to each candidate's **Assigned HR**. To set the address, in [Power Apps](https://make.powerapps.com/), select **Solutions** > **Default Solution** > **Environment variables**, open **Preboarding notify email**, and enter a **Current value**.

Under **Send a Teams notification for these events**, turn off any events that you don't want notifications for. All events are on by default.

| Event | Sent when |
| --- | --- |
| **Preboarding initiated** | HR initiates preboarding. |
| **Preboarding in progress** | The candidate saves on the careers site for the first time. |
| **Candidate submitted** | The candidate submits. |
| **Documents uploaded** | The candidate's documents are attached to the candidate. |
| **Approved / rejected** | HR approves the submission or disqualifies the candidate. |
| **Request rework** | HR requests rework. |
| **Pre-employment check status changed** | The pre-employment check is started, completed, rejected, or skipped. |

Under **Reminders**:

- **Stuck candidate reminder** – When it's on, recipients receive one Teams summary each day of candidates who were invited but didn't start.
- **Stuck candidate threshold (days)** – How many days after the invitation a candidate who didn't start is included in the reminder. The default is 3.

### Insights and monitoring

These thresholds control the insights on the **Preboarding (preview)** tab of the **Onboarding** workspace. For more information, see [Manage preboarding as HR](hr-preboarding-for-hr.md#track-preboarding-in-the-onboarding-workspace).

| Field | Description |
| --- | --- |
| **Pending action threshold (days)** | Candidates who you invited, or who submitted, longer ago than this number of days appear in **Pending preboarding invitations** and **HR review overdue**. The default is 7. |
| **Joining nearing threshold (days)** | Candidates whose start date is within this number of days, or has passed, and who didn't submit, appear in **Joining date approaching or passed, details incomplete**. The default is 7. |

#### Set up documents

To set up the documents that candidates upload, follow these steps:

1. On the **Human resources parameters** page, on the **Preboarding (preview)** tab.
1. On the **Set up preboarding**, select:

- **Document category** – To group document requirements. Enter a **Category name** and a **Description**, and set **Active** to **Yes**. Document categories belong to a legal entity. When you select a **Category** on a document requirement, you can select only the categories of the current legal entity.
- **Document requirements** – To add each document that candidates upload. Enter:

  - **Document name** – The name that the candidate sees.
  - **Description** – Help text that the candidate sees.
  - **Category** – The document category.
  - **Required** – **Yes** if the candidate must upload this document before they can submit.
  - **Accepted formats** – The file types that the candidate can upload for this document. Select at least one.
  - **Active** – Set to **No** to stop asking for the document.

The **Accepted formats** list shows every file type that's set up in Human Resources.

To set the file type, follow these steps:

1. Go to **Organization administration** > **Document management** > **Document management parameters**, on the **File types** tab.
1. To offer another file type, add it here. Removing a file type there doesn't change the document requirements that already use it.

> [!IMPORTANT]
> Accept only document and image formats, such as **pdf**, **docx**, **jpg**, **jpeg**, and **png**. Don't accept **html**, **htm**, **xhtml**, **mht**, **xml**, or **svg** files. These formats can contain content that runs in a browser, and Human Resources shows a preview of an attachment in the browser when HR selects it.

On the careers site, candidates can upload only the accepted formats for each document, up to the **Maximum document file size**.

For security, the careers site never accepts files that can contain content that runs in a browser, even if you add their format to **Accepted formats**. It refuses these file extensions: **html**, **htm**, **xhtml**, **mht**, **mhtml**, **xml**, **svg**, **svgz**, **shtml**, **xsl**, **xslt**, and **js**. It checks the last extension of the file name, so a file named *CV.pdf.html* is refused. It also refuses web page, SVG, XML, and script files that have no extension. These formats aren't shown to the candidate in the accepted formats or in the file picker. If a document requirement accepts only these formats, the candidate can't upload anything for it.

When a file is refused, the candidate sees this message: *"CV.pdf.html" can't be uploaded. This file type isn't allowed for security reasons.* To change it, edit the **PreJoin/Step12/BlockedType** content snippet. Use **{name}** where the file name goes.

Document requirements are set per legal entity. In the **Documentation** step, the candidate sees the active document requirements for their legal entity, and the active requirements that have no legal entity. Uploaded documents are attached to the candidate in Human Resources, and are copied to the worker when you hire the candidate.

#### Set up pre-employment check vendors

Preboarding records the vendor and the outcome of the check. It doesn't send requests to the vendor.

To set up a pre-employment check vendor, follow these steps:

1. Go to **Human resources parameters** > **Preboarding (preview)** tab.
1. Under **Set up preboarding**, select **Pre-employment check vendors**.
1. Add the vendors that run pre-employment checks for you.
1. Fill in the following:

- **Vendor name** - The vendor's name.
- **Vendor code** - A code for the vendor. This is required, and unique in the legal entity.
- **Contact email** - The vendor's contact email.
- **SLA days** - The number of days the vendor usually takes.
- **Status** - **Active** or **Inactive**. Only active vendors can be selected.
- **Notes** - Enter any relevant notes.

#### Update existing candidates

Candidates that you created before you turned on preboarding have the candidate status **Not Processed**. The **Process candidate statuses** job moves them into the hiring lifecycle: to **Ready for offer**, **Ready for preboarding**, or **Ready to onboard**.

> [!IMPORTANT]
> The job places each candidate according to the settings of the legal entity at the moment it runs. You can't move a candidate back to **Not Processed** afterwards. A candidate that you placed with the wrong settings stays on that path. For example, if **Integration to new recruiting app** is off when the job runs and candidates get no offer phase.

### Before you run the job

Ensure that everything is set up the way you want it for the legal entity:

- The **Enable recruitment add-on (preview)**, **Enhanced recruiting candidate experience (preview)**, and **Preboarding (preview)** features are enabled.
- **Integration to new recruiting app** on the **Recruitment** tab is set the way you use the HR Recruiting app (**Dynamics 365 Human Resource recruiting add-on**). It decides whether candidates get an offer phase.
- **Enable preboarding** on the **Preboarding (preview)** tab is set. It decides whether candidates get a preboarding phase.
- If you use the Recruiting app, Offer management is set up.
- The rest of the preboarding setup in this article is complete.

When the recruiting integration is on, existing candidates are always treated as **Offer first**, so their offer comes before preboarding, whatever the **Offer timing type** is. Without the integration, there's no offer phase.

### Test the job on one candidate

1. On the **Human resources parameters** > **Set up preboarding** > **Preboarding (preview)** tab, select **Process candidate statuses**.
1. Under **Records to include**, select **Filter**.
1. In the **Candidate** range, enter the ID of one test candidate. The **Candidate status** range is fixed to **Not Processed**.
1. Select **OK** to run the job.
1. Open the candidate on the **Candidates (preview)** page, and check that its **Candidate status** and **Lifecycle** are what you expect.

### Run the job for all candidates

1. Open **Process candidate statuses**.
1. Under **Records to include**, clear the **Candidate** range.
1. To run the job as a batch job, expand **Run in the background**, and set it up.
1. Select **OK**.

When the job finishes, a message shows how many candidates were initialized and how many were skipped. The job only changes candidates that are **Not Processed**, so you can run it again safely. Run it in each legal entity.

A candidate who already has a preboarding submission is skipped, unless their pre-employment check was completed or skipped. Set the status of a skipped candidate manually.

### Candidates waiting after you turn off preboarding

If you turn off preboarding for a legal entity, candidates who didn't start preboarding remain waiting. To move them on, on the **Recruitment** tab, select **Recover candidates stuck by disabled preboarding**. They move to **Ready for offer** or **Ready to onboard**, based on the current setup. This action is available to HR managers.

#### Send candidate emails from a shared mailbox

By default, candidate emails come from the account that owns the **Recruiting office 365 outlook connection**. To send them from a shared mailbox, such as `careers@contoso.com`, complete these steps once per environment.

### Create the shared mailbox

You need the Exchange administrator or Global administrator role.

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Teams & groups** > **Shared mailboxes**, and select **Add a shared mailbox**.
1. Enter a display name, for example **Preboarding**, and an email address, for example `preboarding@contoso.com`, and then select **Save changes**.

A shared mailbox that's smaller than 50 GB doesn't need a license.

### Give the connection account Send as permission

1. In the [Exchange admin center](https://admin.exchange.microsoft.com), go to **Recipients** > **Mailboxes**, and open the shared mailbox.
1. Select **Delegation** > **Send as** > **Edit** > **Add members**.
1. Add the account that owns the **Recruiting office 365 outlook connection**, and save.

Select **Send as**, not **Send on behalf**. With **Send on behalf**, candidates see "*user* on behalf of *mailbox*". The permission can take up to an hour to apply.

### Enter the sender address

1. In Human Resources, go to **Human resources** > **Setup** > **Human resources parameters**, and select the **Preboarding (preview)** tab.
1. Under **Candidate portal**, in **Sender email address**, enter the shared mailbox address.
1. Select **Save**.

Set the sender address for each legal entity. Set it in each legal entity that uses preboarding.

When you set the sender address, each candidate email is sent from that address. If a send from that address fails, for example, because the Send as permission isn't applied yet. The email is sent again from the connection account, so the candidate still receives it. When the sender address is blank, emails come from the connection account.

> [!NOTE]
> The sender address applies to preboarding emails only. HR notifications in Teams aren't affected. The Recruiting app's own emails are set up in the Recruiting app under **Setup** > **Email Accounts**.

#### Change the candidate email templates

Preboarding emails use email templates in Dataverse. You can change their wording and add translations. To find them, in the Recruiting app, go to **Templates** > **Email Template**. Their titles start with **Preboarding**.

| Email template | Sent when |
| --- | --- |
| Preboarding portal invitation | HR initiates preboarding. |
| Preboarding portal invitation Reminder | HR reinitiates preboarding for a candidate who didn't accept their invitation yet. |
| Preboarding ready to start | HR initiates preboarding for a candidate who already has an account on the careers site. |
| Preboarding submission received | The candidate submits. |
| Preboarding submission failed | The submission couldn't be saved in Human Resources. |
| Preboarding document upload failed | A document couldn't be attached in Human Resources. |
| Preboarding decision approved | HR approves the submission. |
| Preboarding decision rejected | HR disqualifies the candidate. |
| Preboarding rework requested | HR requests rework. |
| Preboarding background verification started | HR starts the pre-employment check. |
| Preboarding background verification sompleted | HR records a completed check. |
| Preboarding background verification rejected | HR records a rejected check. |
| Preboarding background verification skipped | HR skips the check. |
| Preboarding candidate message | HR sends a message from Human Resources. This template is the layout around HR's message. |

The templates contain placeholders in square brackets, such as `[CandidateName]` and `[PortalUrl]`, that are replaced when the email is sent. Each email supports only the placeholders that the template contains. When you change a template, keep its placeholders, and don't add placeholders from other templates, they aren't replaced and appear as text in the email.

To change an email, edit its template, and keep the template title unchanged. The flows find each template by its title and language.

To send an email in another language, create a copy of the template with the same title in that language. Candidates whose language is set to that language receive the translated email. Other candidates receive the English template. For **Preboarding Candidate Message**, only the layout around the message is translated; the message itself is the text that HR writes.

> [!IMPORTANT]
> Don't rename the templates or remove the **Preboarding rework section labels** template. It isn't an email; it holds the section names that are listed in the rework email.

#### Customize the preboarding pages on the careers site

The text on the preboarding pages comes from content snippets on the careers site. To change it, sign in to [Power Pages](https://make.powerpages.microsoft.com/), select your careers site, select the ellipsis (**...**), select **Power Pages management**, and then select **Content snippets**.

| What to change | Content snippet |
| --- | --- |
| Company name in the header | **Site name** |
| The **View terms** link and the consent dialog text | See [Configure the consent dialog, terms, and privacy link](#configure-the-consent-dialog-terms-and-privacy-link). |
| The message after the candidate submits | **PreJoin/Step8/SubmissionSuccessTitle** and **PreJoin/Step8/SubmissionSuccessMessage** |
| The **Preboarding** page text for each stage | **PreJoin/Welcome/Status/***stage***/**... |
| The **What's happening next** timeline | **PreJoin/Welcome/Timeline/**... |
| The **Preboarding (Preview)** menu link | **PreJoining/Nav/Label** |
| Field labels on each step | **PreJoin/Step***number***/**... |

The site theme and styles apply to the preboarding pages. Changes to the header and footer can take up to 15 minutes to appear.

The links under **Recommended resources** come from **Set up links for candidates** in Human Resources. You don't change them on the careers site.

#### Configure the consent dialog, terms, and privacy link

When the candidate selects **Submit** on the **Review and finish** step, a consent dialog asks them to consent to the pre-employment check. You can change all of its text, and add a link to your own consent terms, so that it matches your organization's hiring process and legal terms. There are no site settings for this feature. Change these content snippets in **Power Pages management** or in the Power Pages design studio:

| What to change | Content snippet | Shipped value |
| --- | --- | --- |
| The web address of your consent terms. The **View terms** link opens it in a new tab. | **PreJoin/Step8/ConsentTermsUrl** | Empty. The **View terms** link is shown only after you set it. |
| The text of the terms link | **PreJoin/Step8/ConsentTermsLabel** | View terms |
| The dialog title | **PreJoin/Step8/ConsentTitle** | Consent for pre-employment check |
| The consent message | **PreJoin/Step8/ConsentText** | As part of our hiring process, we require your consent to initiate a pre-employment check using the personal details, identification documents, and uploaded files you provide. This process typically takes about 15 to 30 days. |
| The question | **PreJoin/Step8/ConsentQuestion** | Do you provide your consent for the pre-employment check? |
| The buttons | **PreJoin/Step8/ConsentConfirm** and **PreJoin/Step8/ConsentDeny** | I consent, Deny |
| The message after the candidate selects **Deny** | **PreJoin/Step13/ConsentDenied** | You need to give consent before you can submit. You can come back and submit at any time. |
| The privacy link in the site footer | **Footer/PrivacyLink** for the web address, and **Footer/PrivacyLabel** for the text | Empty web address, and Privacy |
| The terms of use link in the site footer | **Footer/TermsOfUseLink** for the web address, and **Footer/TermsOfUseLabel** for the text | Empty web address, and Terms of use |

The values are plain text, and they apply to the whole careers site, not to each legal entity. Changes can take a few minutes to appear.

Set **PreJoin/Step8/ConsentTermsUrl**, **Footer/PrivacyLink**, and **Footer/TermsOfUseLink** before you invite candidates. The footer links show on every careers site page, including the **Preboarding** page. They aren't shown while the candidate completes the steps, where the site footer is hidden. We recommend that you set **PreJoin/Step8/ConsentTermsUrl** and review **PreJoin/Step8/ConsentText** before you go live, so that they match your own pre-employment check and privacy terms, including how long the check takes.

The careers site doesn't keep a record of which terms the candidate accepted, or when. If you need that record, keep your own versions of the terms.

> [!IMPORTANT]
> Updating the **Dynamics 365 Human Resources careers** app overwrites the content snippets that ship with it. Keep a copy of your changes, and reapply them after an update.

#### Add your own fields

You can add fields to the steps on the careers site and write their values to Human Resources. For more information, see [Add custom fields to preboarding](hr-preboarding-custom-fields.md).

#### Related information

- [Install and set up preboarding](hr-preboarding-setup.md)
- [Manage preboarding as HR](hr-preboarding-for-hr.md)
- [Add custom fields to preboarding](hr-preboarding-custom-fields.md)
