---
# required metadata

title: Email notification profile
description: This topic presents an overview of Microsoft Dynamics 365 Commerce email notification profile.
author: samjarawan
manager: annbe
ms.date: 01/20/2020
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
# Email notification profile

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic presents an overview of Microsoft Dynamics 365 Commerce email notification profile.

## Overview

Before creating channels you'll want to ensure you have set up an email notification profile to ensure email notifications can be sent out for various activities such as order creation, order shipped and payment failure.

For additional email configuration information see [configure and send email](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/configure-email).

## Create an email notification profile

To create an email notification profile, follow these steps.

1. Go to **Navigation pane** > **Modules** > **Retail** > **Headquearters setup** > **Retail Email notification profile**.
1. On the **Action pane**, click **New**.
1. In the **Email notification profile** field, provide a name to identify the profile.
1. In the **Description** field, provide a relevant description.
1. Set the **Active** switch to Yes.

## Create email events

Before an email notification can be created it will require an organization email template which contains the senders email information and the email template.  Follow the below steps to create one.

### Create an email template

To create an email template, follow these steps.

1. Go to **Navigation pane** > **Modules** > **Retail** > **Headquearters setup** > **Parameters** > **Organization email templates**.
1. On the **Action pane**, click **New**.
1. In the **Email ID** field, provide an ID to help identify this template.
1. In the **Sends name** field, provide the senders name.
1. In the **Email Description**, provide a meaningful description.
1. In the **Sender email**, provide the senders email address.
1. Fill out any optional information in the **General** section as needed such as the email priority.
1. Expand the **Email message content** section and click **New** to create the content.  For each content select the **Language** and provid eht email **Subject** line.  If the email will have a body ensure **Has body** is checked.
1. On the **Action pane**, click "Email message** to provide an email body template.

The following image shows an example email template.

![Email template](media/email-template.png)

### Create an email event
To create an email event, follow these steps.

1. Go to **Navigation pane** > **Modules** > **Retail** > **Headquearters setup** > **Retail Email notification profile**.
1. In the list, find and select the desired record. 
1. Select the email template created in the previous step from the **Email ID** drop down
1. Select the appropriate **Email notification type** from the drop down.
1. Select the **Active** check box.
1. Click **Save**.

The following image shows example email notification profiles.

![Email template](media/email-notification-profile.png)

## Additional resources

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[Organizations and organizational hierarchies overview](../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md?toc=/dynamics365/commerce/toc.json)
