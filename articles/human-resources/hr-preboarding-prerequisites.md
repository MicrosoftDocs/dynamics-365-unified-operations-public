---
# required metadata

title: Prerequisites for preboarding in Dynamics 365 Human Resources (preview)
description: Learn what prerequisites are needed before you install and set up preboarding in Microsoft Dynamics 365 Human Resources.
author: ramagadu
ms.date: 10/23/2026
ms.topic: how-to
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

# Prerequisites for preboarding in Dynamics 365 Human Resources (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article lists the prerequisites to complete before you install and set up preboarding in Microsoft Dynamics 365 Human Resources.
Before you set up preboarding in Dynamics 365 Human Resources (preview), ensure you meet the following prerequisites.

## Environment

- A Dynamics 365 Human Resources environment, Dynamics 365 Human Resources version 10.0.50 or later, with the latest quality update. For more information, see [Deploy a new environment](../fin-ops-core/dev-itpro/deployment/deployenvironment-newinfrastructure.md).
- The environment is linked to a Microsoft Dataverse environment. If it isn't linked yet, see [Connect finance and operations apps with a new Microsoft Dataverse instance](../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv.md) or [Connect finance and operations apps with an existing Microsoft Dataverse instance](../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv.md).
- The **Finance and Operations Virtual Entity** solution is installed in the Dataverse environment. Preboarding reads and writes candidate data in Human Resources through virtual tables.

### HR Recruiting app and careers site

Preboarding is part of the HR Recruiting app (**Dynamics 365 Human Resource recruiting add-on**), and candidates complete preboarding on the Recruiting careers site (**Dynamics 365 Human Resources careers**), so set up both. Setting up both is the first step in [Install and set up preboarding](hr-preboarding-setup.md#set-up-the-recruiting-app). After that, choose how to use them:

- Preboarding on its own - You create candidates in Human Resources and run preboarding for them, for example, because you use a third-party recruiting solution. You don't use any other feature of the Recruiting app or the careers site, such as job ads, applications, interviews, or Offer Management. The careers site is used only for preboarding, and preboarding always comes first.
- Preboarding with the Recruiting app - You use the Recruiting app and the careers site for recruiting as well. Applicants move from the Recruiting app into Human Resources, and the offer and preboarding create one candidate lifecycle. This option lets you choose whether preboarding comes before or after the offer.

If you use the Recruiting app for applicants and offers, turn on the integration between the Recruiting app and Human Resources in each legal entity:

To turn on the integration, follow these steps:

1. In Dynamics 365 Human Resources, go to **Human resources** > **Setup** > **Human resources parameters**.
1. Select the **Recruitment** tab.
1. Set **Integration to new recruiting app** to **Yes**.
1. Select **Save**.

Without the integration, preboarding works for candidates that you create in Human Resources, and there's no offer phase.

### Licenses

Preboarding and the HR Recruiting app are included in the Dynamics 365 Human Resources license. Customers who have that license don't pay anything extra for them. HR users and candidates don't need separate Power Apps or Power Pages licenses to use preboarding.

- **Dynamics 365 Human Resources** – A Dynamics 365 Human Resources license for the finance and operations environment.
- **Power Automate capacity** – Preboarding uses Power Automate cloud flows to sync data between the careers site, Dataverse, and Human Resources. The Dynamics 365 Human Resources license includes limited Power Automate capacity. If your usage goes beyond it, you might need to buy more Power Automate capacity. The same applies to Power Pages capacity for the careers site.
- **Administrators and IT** – Users who customize preboarding, for example by changing flows, tables, or careers site pages, need the Power Apps, Power Automate, or Power Pages licenses that those tasks require.
- **Email and Teams** – The accounts that own the Outlook and Teams connections need Microsoft 365 licenses that include Outlook and Teams.

For more information, see [HR recruiting app licensing overview](recruit-license.md).

#### Permissions

You need a user who has system administrator permissions for both Dynamics 365 Human Resources and the Dataverse environment to complete the setup.

#### Email, Teams, and connections

Preboarding sends candidate emails, sends HR notifications in Teams, and attaches documents in Human Resources through connections that the Recruiting app's flows use.

You need an account for each connection:

| Connection reference | Connector | Used by preboarding to | Where you set it up |
| --- | --- | --- | --- |
| Recruiting office 365 outlook connection | Office 365 Outlook | Send emails to candidates. The account needs a Microsoft 365 mailbox. | [Set up the HR Recruiting app](hr-recruit-setup.md#activate-connections-and-flows-for-the-recruiting-app) |
| Recruiting Teams connection | Microsoft Teams | Send notifications to HR. The account must be able to post in Teams. | [Set up the HR Recruiting app](hr-recruit-setup.md#activate-connections-and-flows-for-the-recruiting-app) |
| Recruiting FinOps connection | Fin & Ops Apps (Dynamics 365) | Attach the documents that candidates upload to the candidate in Human Resources. The account needs access to Human Resources. | [Install and set up preboarding](hr-preboarding-setup.md) |

By default, candidate emails come from the account that owns the **Recruiting office 365 outlook connection**. Optionally, to send emails from a shared mailbox, such as `careers@contoso.com`, you need a shared mailbox and **Send as** permission for that account. For more information, see [Send candidate emails from a shared mailbox](hr-preboarding-configuration.md#send-candidate-emails-from-a-shared-mailbox).

The recipient of the Teams notifications is set in Human Resources. For more information, see [Notifications](hr-preboarding-configuration.md#notifications).

> [!NOTE]
> Preboarding doesn't use the email accounts that are set up in the Recruiting app under **Setup** > **Email Accounts**. Those accounts send the Recruiting app's own emails.

## Related information

- [Preboarding in Dynamics 365 Human Resources](hr-preboarding-overview.md)
- [Install and set up preboarding](hr-preboarding-setup.md)
