---
# required metadata

title: Set up an email notification profile
description: This topic describes how to create an email notification profile in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8

---
# Set up an email notification profile

[!include [banner](includes/banner.md)]

This topic describes how to create an email notification profile in Microsoft Dynamics 365 Commerce.

When you create channels, you can set up an email notification profile. The email notification profile defines the events of a sales transaction (such as order created, order packed, and order invoiced events) for which you will send notifications to your customers. 

For additional email configuration information, see [Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json).

## Create an email notification profile

To create an email notification profile, follow these steps.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Headquarters setup \> Commerce email notification profile**.
1. On the action pane, click **New**.
1. In the **Email notification profile** field, enter a name to identify the profile.
1. In the **Description** field, enter a relevant description.
1. Set the **Active** switch to **Yes**.

### Create an email template

Before an email notification type can be enabled, you must create an organization email template in Commerce headquarters for each notification type you want to support. This template defines the email subject, sender, default language, and email body for each supported language.

To create an email template, follow these steps.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Headquarters setup \> Parameters \> Organization email templates**.
1. On the action pane, select **New**.
1. In the **Email ID** field, enter an ID to help identify this template.
1. In the **Sends name** field, enter the senders name.
1. In the **Email Description**, enter a meaningful description.
1. In the **Sender email**, enter the senders email address.
1. In the **General** section, select a default language for the email template. The default language will be used when no localized template exists for the specified language.
1. Expand the **Email message content** section and select **New** to create the template content. For each content item, select the language and provide the email subject line. If the email will have a body, ensure that the **Has body** box is checked.
1. On the action pane, select **Email message** to provide an email body template.

The following image shows some example email template settings.

![Email template settings.](media/email-template.png)

For more information about creating email templates, see [Create email templates for transactional events](email-templates-transactions.md). 

### Create an email event

To create an email event, follow these steps.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Headquarters setup \> Commerce email notification profile**.
1. In the list, find and select the desired record. 
1. Select the email template from the **Email ID** drop-down list.
1. Select the appropriate **Email notification type** from the drop-down list.
1. Select the **Active** check box.
1. On the action pane, select **Save**.

The following image shows some example event notification settings.

![Event notification settings.](media/email-notification-profile.png)

> [!NOTE]
> The customer created notification type requires a customization to be implemented before an email notification can be sent.

### Schedule a recurring email notification process job

To send out email notifications, you must have the **Process retail order email notification** job running.

To set up the **Process retail order email notification** job in Commerce headquarters if you haven't already done so, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Email and notifications \> Send email notification**.
1. In the **Process retail order email notification** dialog box, select **Recurrence**.
1. In the **Define recurrence** dialog box, select **No end date**.
1. Under **Recurrence pattern**, select **Minutes**, and then set the **Count** field to **1**. These settings will ensure that email notifications are processed as quickly as possible.
1. Select **OK** to return to the **Process retail order email notification** dialog box.
1. Select **OK** to complete the job setup.

### Next steps

Before you can send mails, you must configure your outgoing mail service and set up a batch job. For more information, see [Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json).

## Additional resources

[Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json)

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[Organizations and organizational hierarchies overview](../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md?toc=/dynamics365/commerce/toc.json)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
