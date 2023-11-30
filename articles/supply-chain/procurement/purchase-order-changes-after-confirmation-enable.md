---
title: Enable Copilot support to review and accept changes to confirmed purchase orders
description: This article describes how to enable Copilot support for the Confirmed purchase orders with changes workspace, where you can review and accept changes to confirmed purchase orders, based on their downstream impact.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchOrderInReview, PurchOrderApproved, PurchOrderInDraft, PurchOrderAssignedToMe, VendPurchOrderJournalListPage, PurchTableWorkflowDropDialog, VendPurchOrderJournal
ms.topic: how-to
ms.date: 07/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Enable Copilot support to review and accept changes to confirmed purchase orders

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The AI-powered and Copilot functionality that's described in this article is available as part of a preview release. All other functionality is generally available. The content and the functionality related to AI-powered and Copilot functionality are subject to change. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).
>
> **During this preview phase, the summaries of changes and downstream impacts are available only in environments that are hosted in the United States (US)**, and they are shown only in English. All other functionality is globally available.
>
> To learn about the capabilities and limitations of AI-powered and Copilot features in Microsoft Dynamics 365 Supply Chain Management, see [Responsible AI FAQs for Dynamics 365 Supply Chain Management](../responsible-ai-overview.md).

<!--KFM: Preview until further notice -->

This steps in this article are used by admins to enable capabilities that are part of the *Procurement with Copilot* feature set, which is a growing collection of features that use AI to help procurement managers with their daily procurement tasks.

## Steps to enable the feature for your system

This section describes the steps that you must complete to enable the **Confirmed purchase orders with changes** workspace and the related Copilot support.

- Steps 3 through 6 enable the support by Copilot for this workspace that provides, for example, natural-language change summaries and communication drafts. These steps require that your environment is enabled for Power Platform integration. For more information, see [Enable Power Platform integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md).


### <a name="enable-sql-key"></a>Step 3: Enable the SQL row version change tracking license key

Follow these steps to check the status of the **Sql row version change tracking (Preview)** license key and enable it if necessary. If the key isn't enabled, you'll get an error when you try to install the Copilot application in the Power Platform admin center.

1. Go to **System administration \> Setup \> License configuration**.
1. On the **Configuration keys** tab, scroll down the **Sql row version change tracking (Preview)** key. If the key is already enabled, then skip the rest of this procedure. If it isn't enabled, then continue to the next step.
1. Put your system into maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Return to the **License configuration** and enable the **Sql row version change tracking (Preview)** key.
1. Turn off maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

### Step 4: Upgrade the Finance and Operations Virtual Entity solution

Follow these steps to upgrade the *Finance and Operations Virtual Entity* solution.

1. Go to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select the Power Platform environment that's connected to your finance and operations app, and open the detail view.
1. In the **Resources** field, select **Dynamics 365 apps**.
1. Find the app that's named *Finance and Operations Virtual Entity*.
1. If the status is *Installed*, you're already running the latest version. If the status is *Update available*, you must update the solution by following these steps:

    1. Select the ellipsis button (**&hellip;**), and then select **Update**.
    1. Accept the terms of service, and then select **Update**.

You can follow the status of the update. During the update, the status is *Installing*. After the update is completed, the status changes to *Installed*.

### Step 5: Enable Supply Chain Management to access your Dataverse environment

Follow these steps to enable Supply Chain Management to access your Dataverse environment.

1. Go to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select the Dataverse environment that's connected to your Supply Chain Management environment, and open the detail view.
1. Select the **Settings** menu on the menu bar.
1. Go to **Product \> Features**.
1. Set the **Finance and Operations in Dataverse** option to *On*.

### Step 6: Install the Copilot application in Supply Chain Management

> [!NOTE]
> During this preview phase, the Copilot application can only be installed for environments that are hosted in the US.

Follow these steps to install the Copilot application in your Supply Chain Management environment.

1. Go to the [Copilot in Microsoft Dynamics 365 Supply Chain Management](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamicsscmai-preview?flightCodes=f42a7338c806438f8fca820c4ed82b7c&tab=Overview) page in the Microsoft commercial marketplace.
1. Select **Get it now**.
1. The deployment process opens [Power Platform admin center](https://admin.powerplatform.microsoft.com/). Select the Dataverse environment that's connected to your Supply Chain Management environment to install the Copilot application.

    > [!IMPORTANT]
    > **Troubleshooting:** You may see the following error message while installing the Copilot application in the Power Platform admin center: "Unable to complete updates to the Track changes option for table: 'EcoResProductTranslationAIEntity'. Exception details: This functionality requires enabling sql row version change tracking feature. Please enable SQL Row version configuration key." If you see this error, follow the instructions given in [Step 3: Enable the SQL row version change tracking license key](#enable-sql-key).

1. You can follow the status of the installation by opening the detail view of the environment. In the **Resources** field, select **Dynamics 365 apps**. The status of the Copilot application is **Installing**. After the installation is complete, the status changes to **Installed**. If an error occurs, the status changes to **Failed** and you can find details about the error in the **Notifications** field.

### Step 7: Enable the required security roles

Users who should have access to the functionality must be assigned the *AIB Roles* and *Finance and Operations AI* security roles in Dataverse.

In the detail view of the environment, in the **Access** field, select **Users** or **Teams**. Select the users or teams that should have access, and assign the *AIB Roles* and *Finance and Operations AI* security roles to them.

## Troubleshoot the Copilot configuration

The Copilot experience in the procureent workspace offers a trouble shooting capability that helps to identify missing configuration steps. If one of the configurtion steps is not complete the Copilot summarization tiles will offer a trouble shooting link.

[<img src="media/po-change-review-trouble-shooting.png" alt="Screenshot of the Confirmed purchase orders with changes workspace." title="Screenshot of the trouble shooter for Copilot configuration." width="720" />](media/po-change-review-trouble-shooting.png#lightbox)

The link offer opens the trouble shooting, which checks all installation and configuration requirements needed for Copilot to function. It marks the steps that need attention.

You can complete those configuration steps in a seperate Browser Tab and press Recheck to reevaluate the completeness of the configuration.  

## See also
- [How to use the Confirmed purchase orders with changes workspace](./purchase-order-changes-after-confirmation.md)
- [Responsible AI FAQ for the Confirmed purchase orders with changes workspace](../faq-confirmed-po-changes.md)
