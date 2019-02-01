---
# required metadata

title: Client alert notifications by email
description: This topic provides information about how to set up rules that send email notifications when triggered by an event.
author: tjvass
manager: AnnBe
ms.date: 02/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EventCreateRule
# ROBOTS:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: tjvass
ms.search.validFrom: 2019-1-29
ms.dyn365.ops.version: Platform update 24
---

# Client alert notifications by email

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

You can create alert rules that automatically send email notifications when triggered by a pre-defined event. With Dynamics 365 for Finance & Operations, you can define custom alert rules to monitor filtered views of their data. The option to receive email notifications is available for all supported alert types and can be enabled for existing alert rules.  

You can use built-in controls to create alert rules that monitor the filtered views of System Batch jobs. By monitoring the value of the **Status** field, you can also configure alert rules that send email when a Batch job fails.  When these alert rules are created, you no longer have to check reports for changes to business data. Instead, you can let the Dynamics 365 for Finance & Operations intelligent change detection service monitor for you.

Client alerts depend on the email subsystem that is delivered through Microsoft Office integration. We recommend that the SMTP provider is used to enable the distribution of email without relying on a local mail client. To send notifications by email, customers must configure integrated email services. Email notifications are sent out to recipients on behalf of alert owners.

For more information on configuring email in Finance & Operations, see [Configure and send email](../organization-administration/configure-email.md).

The following screen shot shows the most recent **Create alert rule** page which now includes the **Send Email** option.

[![Alert rule form with the Send email option enabled](./media/Create-alert-rule-form.png)](./media/Create-alert-rule-form.png)<br>
> [!NOTE]
> Alert notifications will continue to be delivered from the Action Center when the **Send email** option is set to **Yes**.

## Alert notification email templates
The service dispatches email notifications by using pre-defined email templates that deliver the basic alert notification details. This includes a direct link page where the alert rule was defined.

The following graphics show the structure of the alert notifications when received via Email.

[![Email templates used for Client Alert notifications](./media/Alert-email-templates.png)](./media/Alert-email-templates.png)




