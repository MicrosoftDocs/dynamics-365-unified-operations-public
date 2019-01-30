---
# required metadata

title: Alerts Email Notifications
description: Stay on top of your business data with integrated change tracking tools that allow users to create Alert Rules that automatically send email notifications when triggered by an event.
author: tjvass
manager: AnnBe
ms.date: 01/29/2019
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

# Alerts

[!include [banner](../includes/banner.md)]

## Overview
Stay on top of your business data with integrated change tracking tools.  With the latest Platform Update Release, users are able to create Alert Rules that automatically dispatch email notifications when triggered by a pre-defined event.  With Dynamics 365 for Finance & Operations, users are able to define custom Alert Rules to monitor filtered views of their data.  The option of receiving email notifications is available for all supported Alert types and can be enabled for existing Alert Rules.  

Supported scenarios include the ability to use built-in controls to create Alerts Rules that monitor filtered views of System Batch jobs.  Administrators are able to configure Alert rules that send email in cases where a Batch job fails by monitoring the value of the Status field.  Move beyond the burden of constantly checking reports for changes to business data and let the Dynamics 365 for Finance & Operations intelligent change detection service do the monitoring for you.

### What's important to know?
- Client Alerts depend on the Email subsystem delivered through Office Integration
- Recommend that the SMTP provider is used to enable distribution of email without relying on a local mail client
- Customers MUST configure integrated Email services to send notifications by email
- Email notifications are sent out to recipients on behalf of Alert owners

For more information on configuring email in Dynamics 365 for Finance & Operations, review the article [Configure and send email](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/organization-administration/configure-email).

Here's a screen shot of the latest **Create alert rule** form which now includes the **Send Email** option<br>
[![Alert rule form with the Send email option enabled](./media/Create-alert-rule-form.png)](./media/Create-alert-rule-form.png)<br>
**Note:** Alert notifications will continue to be delivered via the Action Center when **Send email** option is set to **Yes**

### Alert notification - Email templates
The service dispatches Email notifications using pre-defined email templates that deliver the basic alert notification details.  This includes a direct link into the Finance & Operations form where the Alert rule was defined.

The following illustrations showcases the structure of the Alert notifications when received via Email<br>
[![Email templates used for Client Alert notifications](./media/Alert-email-templates.png)](./media/Alert-email-templates.png)




