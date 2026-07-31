---
title: Configure Supplier Engagement elements in Power Platform (preview)
description: Configure portal URLs, email templates, mailboxes, cloud flows, and duplicate detection for Supplier Engagement.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Configure Supplier Engagement elements in Power Platform (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

After you install the Supplier Engagement components, align the Power Platform environment with your portal, communication, and automation requirements. This article covers the configuration tasks to complete before broad onboarding or production validation, including environment variables, email templates, mailbox activation, cloud flows, and duplicate detection rules. These tasks make sure that users receive the right links, cloud flows can run, and duplicate vendor data is detected before it causes problems.

## Prerequisites

Before you configure Supplier Engagement elements in Power Platform, complete the prerequisites listed in [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md).

## Configure supplier portal sign-in and onboarding URLs

To support seamless supplier onboarding and access, you need supplier portal sign-in and onboarding URLs. Configure these addresses in your Power Apps environment variables so they're consistent across environments (Dev, Test, Prod) and properly integrated with Supplier Engagement cloud flows.

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/) and select your environment.
1. On the navigation pane, select **Solutions**.
1. Find and open the solution that has a **Display name** of *Default solution*.
1. On the navigation pane, select **Objects** > **Environment variables**.
1. Open the environment variable named *Supplier Portal URL*.
1. Select **New Value** and enter the full supplier portal URL, such as `https://site-xyz.powerappsportals.com/`.
1. Select **Save**.

Validate the URL after you save it.

1. Confirm that the address uses HTTPS and doesn't contain trailing spaces.
1. Browse to the URL and make sure that the supplier portal opens.
1. Confirm that the URL matches the intended environment, such as Dev, Test, or Prod.

## Customize supplier invitation and notification emails

You can customize the email template text that Supplier Engagement sends to suppliers, including invitation and notification emails. This setup is useful when you want to align system-generated emails with your organization's tone, branding, and onboarding guidance. If you support multiple languages, you can maintain localized versions of each email template for each language.

> [!IMPORTANT]
> The Supplier Engagement invitation email template must include a link to your supplier portal. Update that link before you go live.

> [!TIP]
> Learn more in [Create templates for email](/power-apps/user/email-template-create).

To customize supplier invitation and notification emails, follow these steps.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as a system administrator and open your environment.
1. Select the link under **Environment URL** to open the environment in a new browser tab.
1. Do one of the following steps:
    - If a list of apps opens, select the **Power Platform Environment Settings** app.
    - If the environment opens directly to an app, select the app name on the app header bar at the top to open the list of published apps, and then select **Power Platform Environment Settings**.
1. On the navigation pane, go to **Templates** \> **Email Templates**.
1. Supplier Engagement uses the following templates. Open the template that you want to customize.
    - *Supplier Engagement contact portal access*
    - *Supplier Engagement invitation*
    - *Supplier Engagement registration status*

1. Make the following changes to the selected email template:
    - Update the subject and body text as needed.
    - If the message includes a portal action, verify that the link points to the correct supplier portal URL for your environment. By default, the *Supplier Engagement invitation* email template includes this URL and you must update it before going live with the solution.

1. Select **Save**.
1. Inspect and update the other templates as needed.

> [!NOTE]
> If you support multiple languages, review and update the localized versions of each template that you use.

## Enable a mailbox for cloud flow notifications

Cloud flows, which are part of Microsoft Power Automate, automate business processes and ensure timely communication across platforms such as Supply Chain Management and Microsoft Teams. To maximize the effectiveness of these flows—especially those that send notifications—you must enable a mailbox for the flow owner or service account. This setup allows the flow to send email notifications reliably, which ensures that users and stakeholders receive critical updates, alerts, and approvals directly in their inbox.

To enable a mailbox for cloud flow notifications, follow these steps.

1. Open the **Power Platform Environment Settings** app in the Power Platform admin center as described previously.
1. On the navigation pane, go to **Email Configuration** \> **Mailboxes**.
1. Select the mailbox to activate.
1. On the command bar, select **Activate**. In the **Confirm Mailbox Activation** dialog, select **Activate**.
1. On the command bar, select **Approve Email**. In the **Approve Primary Email** dialog, select **OK**.
1. On the command bar, select **Test and Enable Mailboxes**. In the **Test Email Configuration** dialog, select **OK**.

> [!NOTE]
> These mailboxes are used both for automated notifications and to send updates from cloud flows. Choose mailboxes for valid service accounts or non-personal accounts that are permanent and unaffected by organizational changes. This approach helps maintain stable, long-term automation and avoids unnecessary interruptions in workflow.

> [!NOTE]
> Power Automate can also work with on-premises Exchange through the appropriate connectors and gateway configuration. Learn more in [Manage an on-premises data gateway in Power Automate](/power-automate/gateway-manage).

## Enable supporting cloud flows

*Cloud flows* automate key business processes and ensure integration between the Supplier Engagement app, supplier portal, and Supply Chain Management. These flows streamline notifications, synchronize data, and automate approvals to help reduce manual effort and minimize errors.

*Connection references* act as secure bridges between your Power Platform environment and external services such as Dataverse, Outlook, Teams, and Power Apps. By establishing these references, you ensure that cloud flows and integrations can authenticate and interact with the necessary data sources and applications. Proper configuration of connection references enables automated workflows that synchronize supplier data and support collaboration across the Supplier Engagement app, supplier portal, and Supply Chain Management.

Although the cloud flows are already present in the system after installation, they're inactive by default and don't run until you enable them. After you configure the necessary connection references, activate the cloud flows in your environment so that all related functionalities become operational.

To create the required connection references and activate the cloud flows, follow these steps:

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/) and select your environment.
1. On the navigation pane, select **More** \> **Connections**.
1. On the command bar, select **New connection**.
1. A list of services opens. Add connections for the **Microsoft Dataverse** service by using the **+** in the **Actions** column.
1. Add a second connection for the **Microsoft Teams** service.
1. On the navigation pane, select **Solutions**.
1. Find and open the solution that has a **Display name** of *Default solution*.
1. On the navigation pane, go to **Objects** \> **Connection References**.
1. Use your browser's on-page search function to find connection references that include the text *SupplierEngagement* (in other words, use Ctrl + F to do an on-page search, don't use the filter provided by the site). There should be three of them:
    - *Microsoft Dataverse MicrosoftSupplierEngagement-77aa1*
    - *Microsoft Dataverse msdyn_SupplierEngagementBase-abf2e*
    - *Microsoft Teams MicrosoftSupplierEngagement-0e21b*

1. For *Microsoft Dataverse MicrosoftSupplierEngagement-77aa1*, open the **Commands** (three dots) menu, select **Edit**, set **Connection** to the *Microsoft Dataverse* connection that you created, and then select **Save**.
1. For *Microsoft Dataverse msdyn_SupplierEngagementBase-abf2e*, open the **Commands** menu, select **Edit**, set **Connection** to the *Microsoft Dataverse* connection that you created, and then select **Save**.
1. For *Microsoft Teams MicrosoftSupplierEngagement-0e21b*, open the **Commands** menu, select **Edit**, set **Connection** to the *Microsoft Teams* connection that you created, and then select **Save**.
1. On the navigation pane, select **Back to solutions**.
1. On the **Solutions** page, open the **Managed** tab.
1. Find and open the solution that has a **Display name** of *Supplier Engagement Core*.
1. On the navigation pane, go to **Objects** \> **Cloud flows**.
1. Turn on each cloud flow that shows a **Status** of *Off*. To turn on a flow, select it and then select **Turn on** on the command bar.
1. Repeat the previous steps to turn on all the cloud flows in the *Supplier Engagement Portal* solution.

## Enable duplicate detection rules

Duplicate detection rules help maintain clean and consistent vendor data within the Supplier Engagement solution. These rules prevent the creation of duplicate global vendor records by automatically identifying potential matches based on key fields such as name, email address, phone number, and website. By configuring and activating duplicate detection, you ensure data integrity, streamline vendor management processes, and reduce the risk of errors caused by redundant or conflicting records.

Set up rules to detect duplicate global vendor records by making sure that none of the following fields have values that match those of an existing global vendor:

- **Primary phone number** – Use an exact match comparison and include blank values in the evaluation.
- **Email address** – Use an exact match comparison and ignore blank values.
- **Name** – Compare the first five characters by using a same-first-characters matching rule and ignore blank values.
- **Primary URL** – Use an exact match comparison and ignore blank values.

To enable the duplicate detection rules in the Supplier Engagement solution, follow these steps:

1. Open the **Power Platform Environment Settings** app in the Power Platform admin center as described previously.
1. On the navigation pane, go to **Data Management** \> **Duplicate Detection Rules**.
1. Select the check box for each of the following rules, and then select **Publish** on the command bar:
    - *Global vendor with same primary phone number*
    - *Global vendor with same email address*
    - *Global vendor with same name*
    - *Global vendor with same primary URL*

1. Confirm that each rule now shows a **Status Reason** of *Published*.

Learn more in [Set up duplicate detection rules to keep your data clean](/power-apps/developer/data-platform/detect-duplicate-data-with-code).

## Related information

- [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md)
- [Install the Supplier Engagement app and supplier portal on Power Platform](deploy-install-power-platform.md)
- [Onboard using the onboarding guide](deploy-onboarding-guide.md)
- [Configure Supplier Engagement features in Supply Chain Management](deploy-configure-scm.md)
- [Post-deployment validation checklist](deploy-validation-checklist.md)
- [Deployment FAQs](deploy-questions.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
