---
title: Configuration for Finance insights
description: Learn about the configuration steps that enable your system to use the capabilities that are available in Finance insights.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 12/12/2025
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.13
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
---

# Configuration for Finance insights

[!include [banner](../includes/banner.md)]

[!include [finance-insights-update-banner](includes/finance-insights-update-banner.md)]

Finance insights combines functionality from Microsoft Dynamics 365 Finance with Dataverse, Azure, and AI Builder to provide powerful forecasting tools for your organization. This article explains the configuration steps that enable your system to use the capabilities that are available in Finance insights. To successfully complete the procedures in this article, you must have System administrator and System customizer access in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), System administrator access in Dynamics 365 Finance, and access to create environments in Microsoft Dynamics 365 Lifecycle Services.

## Deploy Dynamics 365 Finance

To deploy the environments, follow these steps.

1. In Lifecycle Services, create or update a Dynamics 365 Finance environment.
   
    > [!NOTE]
    > The environment must be a high-availability (HA) environment. (This type of environment is also known as a Tier-2 environment.) Learn more in [Environment planning](../../fin-ops-core/dev-itpro/organization-administration/environment-planning.md).

2. If you're configuring Finance insights in a sandbox environment, you might have to copy production data to that environment before predictions work. The prediction model uses multiple years of data to build predictions. The Contoso demo data doesn't contain enough historical data to adequately train the prediction model. 

## Configure your Microsoft Entra tenant

Microsoft Entra must be configured so that it can be used with Dataverse and the Microsoft Power Platform applications. This configuration requires that either the **Project Owner** role or the **Environment Manager** role is assigned to the user in the **Project security role** field in Lifecycle Services.

Verify that the following setup is completed:

- You have **System administrator** and **System customizer** access in the Power Platform admin center.
- A Dynamics 365 Finance or equivalent license is applied to the user who is installing the Finance insights add-in.
- The following Microsoft Entra apps are registered in Microsoft Entra ID.

    | Application                              | App ID                               |
    |------------------------------------------|--------------------------------------|
    | Microsoft Dynamics ERP Microservices CDS | 703e2651-d3fc-48f5-942c-74274233dba8 |

    To verify the application is registered in Microsoft Entra ID, check the **All Applications** list. Learn more in [View enterprise applications](/azure/active-directory/manage-apps/view-applications-portal).
  
    If the application isn't registered in Microsoft Entra ID, contact support.
  
## Configure Dataverse

To configure Dataverse for Finance insights, follow these steps.

- In Lifecycle Services, open the environment page, and verify that the **Power Platform Integration** section is already set up.

    - If Dataverse has already been set up, the Dataverse environment name that is linked to the Finance environment should be listed.
    - If Dataverse hasn't yet been set up, select **Setup**. Setup of the Dataverse environment can take up to an hour. When the setup has been successfully completed, the Dataverse environment name that is linked to in the Finance environment should be listed.
    - If this integration was set up with an existing Microsoft Power Platform environment, contact your administrator to make sure that the linked environment isn't in the disabled state.

        Learn more in [Enabling the Power Platform integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md). 

        To access the Microsoft Power Platform admin site, go to <https://admin.powerplatform.microsoft.com/environments>.

## Configure the Finance insights add-in

Installation of the Finance insights add-in automatically enables all Finance Insights features in Dynamics 365 Finance.
If you previously installed the Finance insights add-in, uninstall it before you complete the following procedure.

> [!NOTE]
> If you previously installed the Export to Data Lake add-in in Lifecycle Services, uninstall it before you install the Finance Insights add-in, because the Export to Data Lake add-in has been deprecated. Learn more in [Export to Data Lake in finance and operations apps](../../fin-ops-core/dev-itpro/data-entities/finance-data-azure-data-lake.md).

To install the Finance insights add-in, follow these steps.

1. Sign in to Lifecycle Services, and then, under the environment name on the right side of the page, select **Full Details**.
2. In the **Environment add-ins** section, select **Install a new add-in**.
3. Select the **Finance insights** add-in.
4. Agree to the terms and conditions, and then select **Install**.

The add-in might take several minutes to install.

## One last thing

After the add-in is successfully installed, it might take up to an hour for the Finance insights feature to be enabled in Dynamics 365 Finance. If you don't want to wait that long, you can manually run the **Insights provisioning status check** process. 

1. In Dynamics 365 Finance, go to **System administration \> Setup \> Process automation**.
2. On the **Background processes** tab, find **Insights provisioning status check**, and select **Edit**.
3. Set the **Next execution** field to 30 minutes before the current time.

   This change should force the **Insights provisioning status check** process to run immediately.

   After the **Insights provisioning status check** process is successfully run, you can view the enabled Finance insights features in the relevant workspaces.

> [!NOTE]
> If the **Insights provisioning status check** process doesn't run, go to **System administration** > **Inquiries** > **Batch jobs**. In the **Process automation background process system job** field, change the value to **Waiting** to initiate the process. 
 
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
