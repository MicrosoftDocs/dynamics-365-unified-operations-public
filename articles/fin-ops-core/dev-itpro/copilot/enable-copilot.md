---
title: Enable Copilot capabilities in finance and operations apps (preview)
description: This article provides instructions for administrators on how to enable Copilot capabilities in finance and operations apps
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Enable Copilot capabilities in finance and operations apps (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

Copilot brings features that help users complete their tasks more efficiently. For example, one feature uses the power of generative AI to provide in-app help guidance.

This article describes how to enable Copilot capabilities in finance and operations apps.

[!INCLUDE [preview-note](../../../supply-chain/includes/preview-note.md)]

## Country/region and language availability

Please refer to the [Copilot international availability guide](https://dynamics.microsoft.com/availability-reports/copilotreport/) for details about which countries/regions and languages the Copilot capability in Supply Chain Management will be come available.

## Prerequisites

To enable Copilot capabilities in finance and operations apps, you must have the following prerequisites in place:

- You must be running version 10.0.38 or later of finance and operations apps. <!--KFM: Confirm minimum version. -->
- You must have enabled the Power Platform integration in Microsoft Dynamics Lifecycle Services. (However, you don't have to enable dual-write for this feature.)

> [!IMPORTANT]
> Depending on the availability of Copilot and generative AI back-office services in your region, your Dataverse environment may also need to be set up to support cross-region calls. For more information, see [Enable copilots and generative AI features](/power-platform/admin/geographical-availability-copilot)
>
> You don't need to set up support for cross-region calls if the required AI services are already available in your Dataverse environment.
>
> To learn about the capabilities and limitations of AI-powered Copilot features in Microsoft Dynamics 365 Supply Chain Management, see [Responsible AI FAQs for Dynamics 365 Supply Chain Management](../responsible-ai-overview.md).

## <a name="enable-sql-key"></a>Step 1: Enable the Sql row version change tracking license key

Follow these steps to check the status of the **Sql row version change tracking (Preview)** license key and enable it as required. If the key isn't enabled, you receive an error when you try to install the Copilot application in Power Platform admin center.

1. Go to **System administration \> Setup \> License configuration**.
1. On the **Configuration keys** tab, scroll down to the **Sql row version change tracking (Preview)** key. If the key is already enabled, skip the rest of this procedure. If it isn't enabled, move on to the next step.
1. Put your system into maintenance mode as described in [Maintenance mode](../sysadmin/maintenance-mode.md).
1. Return to the **License configuration** page, and enable the **Sql row version change tracking (Preview)** key.
1. Turn off maintenance mode as described in [Maintenance mode](../sysadmin/maintenance-mode.md).

## Step 2: Upgrade the Finance and Operations Virtual Entity solution

Follow these steps to upgrade the *Finance and Operations Virtual Entity* solution.

1. Go to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select the Power Platform environment that's connected to your finance and operations app, and open the detail view.
1. In the **Resources** field, select **Dynamics 365 apps**.
1. Find the app that's named *Finance and Operations Virtual Entity*.
1. If the status is *Installed*, you're already running the latest version. If the status is *Update available*, you must update the solution by following these steps:

    1. Select the ellipsis button (**&hellip;**), and then select **Update**.
    1. Accept the terms of service, and then select **Update**.

You can follow the status of the update. During the update, the status is *Installing*. After the update is completed, the status changes to *Installed*.

## Step 3: Enable your finance and operations apps to access your Dataverse environment

Follow these steps to enable your finance and operations apps to access your Dataverse environment.

1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select the Dataverse environment that's connected to your finance and operations apps environment, and open the detail view.
1. Select the **Settings** menu on the menu bar.
1. Go to **Product \> Features**.
1. Set **Finance and Operations in Dataverse** to *On*.

## Step 4: Install the Copilot application in your finance and operations apps environment

> [!NOTE]
> During the preview phase, the Copilot application can be installed only for environments on tenants that are hosted in the United States.

Follow these steps to install the Copilot application in your finance and operations apps environment.

1. Open the [Copilot in Microsoft Dynamics 365 Supply Chain Management](https://aka.ms/dynamicsfnocopilot_scmaiapp) page in the Microsoft commercial marketplace.
1. Select **Get it now**.
1. The deployment process opens [Power Platform admin center](https://admin.powerplatform.microsoft.com/). Select the Dataverse environment that's connected to your finance and operations apps environment to install the Copilot application.

    > [!IMPORTANT]
    > **Troubleshooting:** You might receive the following error message while you install the Copilot application in Power Platform admin center: "Unable to complete updates to the Track changes option for table: 'EcoResProductTranslationAIEntity'. Exception details: This functionality requires enabling sql row version change tracking feature. Please enable SQL Row version configuration key." If you receive this error, follow the instructions in the [Step 2: Enable the Sql row version change tracking license key](#enable-sql-key) section.

1. You can follow the status of the installation by opening the detail view of the environment. In the **Resources** field, select **Dynamics 365 apps**. During installation, the status of the Copilot application is *Installing*. After installation is completed, the status changes to *Installed*. If an error occurs, the status changes to *Failed*. In this case, you can find details about the error in the **Notifications** field.

## Step 5: Enable the required security roles

Users who should have access to the functionality must be assigned the *AIB Roles* and *Finance and Operations AI* security roles in Dataverse.

1. In the detail view of the environment, in the **Access** field, select *Users* or *Teams*.
2. Select the users or teams that should have access, and assign the *AIB Roles* and *Finance and Operations AI* security roles to them.
