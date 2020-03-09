---
# required metadata

title: Set up an email notification profile
description: This topic describes how to create an email notification profile in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 01/27/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8

---
# Set up an email notification profile


[!include [banner](includes/banner.md)]

This topic describes how to create an email notification profile in Microsoft Dynamics 365 Commerce.

## Overview

Before creating channels, you'll want to set up a profile to ensure that email notifications can be sent out for various events, such as order creation, order shipping status, and payment failure.

For additional email configuration information, see [Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json).

## Create an email notification profile

To create an email notification profile, follow these steps.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Headquarters setup \> Commerce email notification profile**.
1. On the action pane, click **New**.
1. In the **Email notification profile** field, enter a name to identify the profile.
1. In the **Description** field, enter a relevant description.
1. Set the **Active** switch to **Yes**.

### Create an email template

Before an email notification can be created, you must create an organization email template which contains the senders email information and the email template.

To create an email template, follow these steps.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Headquarters setup \> Parameters \> Organization email templates**.
1. On the action pane, select **New**.
1. In the **Email ID** field, enter an ID to help identify this template.
1. In the **Sends name** field, enter the senders name.
1. In the **Email Description**, enter a meaningful description.
1. In the **Sender email**, enter the senders email address.
1. In the **General** section, fill out any optional information needed (such as the email priority).
1. Expand the **Email message content** section and select **New** to create the template content. For each content item, select the language and provide the email subject line. If the email will have a body, ensure that the **Has body** box is checked.
1. On the action pane, select **Email message** to provide an email body template.

The following image shows some example email template settings.

![Email template settings](media/email-template.png)

### Create an email event

To create an email event, follow these steps.

1. In the navigation pane, go to **Modules \> Retail and commerce \> Headquarters setup \> Commerce email notification profile**.
1. In the list, find and select the desired record. 
1. Select the email template from the **Email ID** drop-down list.
1. Select the appropriate **Email notification type** from the drop-down list.
1. Select the **Active** check box.
1. On the action pane, select **Save**.

The following image shows some example event notification settings.

![Event notification settings](media/email-notification-profile.png)

## Additional resources

[Configure and send email](../fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json)

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[Organizations and organizational hierarchies overview](../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md?toc=/dynamics365/commerce/toc.json)
