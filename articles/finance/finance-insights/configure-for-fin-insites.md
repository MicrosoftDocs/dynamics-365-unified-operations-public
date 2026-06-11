---
title: Configuration for Finance insights
description: Learn about the configuration steps that enable your system to use the capabilities that are available in Finance insights.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 06/01/2026
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.13
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
---

# Configuration for Finance insights

[!include [banner](../includes/banner.md)]
[!INCLUDE [lcs-freeze-banner](../../includes/lcs-freeze-banner.md)]
[!include [finance-insights-update-banner](includes/finance-insights-update-banner.md)]


Finance insights combines functionality from Microsoft Dynamics 365 Finance with Dataverse, Azure, and AI Builder to provide powerful forecasting tools for your organization. This article explains the configuration steps that enable your system to use the capabilities that are available in Finance insights. To successfully complete the procedures in this article, you must have System administrator and System customizer access in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), System administrator access in Dynamics 365 Finance, and access to create environments in Microsoft Dynamics 365 Lifecycle Services.

## Deploy Dynamics 365 Finance

To deploy the environments, follow these steps:

1. In Lifecycle Services, create or update a Dynamics 365 Finance environment.
   
    > [!NOTE]
    > The environment must be a high-availability (HA) environment. (This type of environment is also known as a Tier-2 environment.) Learn more in [Environment planning](../../fin-ops-core/dev-itpro/organization-administration/environment-planning.md).

1. If you're configuring Finance insights in a sandbox environment, you might have to copy production data to that environment before predictions work. The prediction model uses multiple years of data to build predictions. The Contoso demo data doesn't contain enough historical data to adequately train the prediction model. 

## Configure your Microsoft Entra tenant

You must configure Microsoft Entra to use it with Dataverse and the Microsoft Power Platform applications. This configuration requires that you assign either the **Project Owner** role or the **Environment Manager** role to the user in the **Project security role** field in Lifecycle Services.

Verify that the following setup is completed:

- You have **System administrator** and **System customizer** access in the Power Platform admin center.
- A Dynamics 365 Finance or equivalent license is applied to the user who is installing the Finance insights add-in.
- The following Microsoft Entra apps are registered in Microsoft Entra ID.

    | Application                              | App ID                               |
    |------------------------------------------|--------------------------------------|
    | Microsoft Dynamics ERP Microservices CDS | 703e2651-d3fc-48f5-942c-74274233dba8 |

    To verify the application is registered in Microsoft Entra ID, check the **All Applications** list. For more information, see [View enterprise applications](/azure/active-directory/manage-apps/view-applications-portal).
  
    If the application isn't registered in Microsoft Entra ID, contact support.
  
## Configure Dataverse

To configure Dataverse for Finance insights, follow these steps:

- In Lifecycle Services, open the environment page, and verify that the **Power Platform Integration** section is already set up.

    - If Dataverse is already set up, the Dataverse environment name that is linked to the Finance environment appears.
    - If Dataverse hasn't yet been set up, select **Setup**. Setup of the Dataverse environment can take up to an hour. When the setup has been successfully completed, the Dataverse environment name that is linked to in the Finance environment should be listed.
    - If this integration was set up with an existing Microsoft Power Platform environment, contact your administrator to make sure that the linked environment isn't in the disabled state.

        Learn more in [Enabling the Power Platform integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md). 

        To access the Microsoft Power Platform admin site, go to <https://admin.powerplatform.microsoft.com/environments>.

## Configure the Finance insights add-in

When you install the Finance insights add-in, it automatically enables all Finance Insights features in Dynamics 365 Finance.
If you previously installed the Finance insights add-in, uninstall it before you complete the following procedure.

> [!NOTE]
> If you previously installed the Export to Data Lake add-in in Lifecycle Services, uninstall it before you install the Finance Insights add-in. The Export to Data Lake add-in is deprecated. For more information, see [Export to Data Lake in finance and operations apps](../../fin-ops-core/dev-itpro/data-entities/finance-data-azure-data-lake.md).

To install the Finance insights add-in, follow these steps:

1. Go to the Power Platform Admin Center (PPAC). Open the Power Platform Admin Center and sign in with an account that has admin permissions.
1. Under **Environments**, choose the Dataverse environment that pairs with your Dynamics 365 finance and operations instance.
1. In the left navigation, select **Resources > Dynamics 365 apps**.
1. Select **Install app** (or **Add app** depending on UI).
   - Find **Finance Insights** in the list.
   - Choose **Install**.
1. Confirm the terms and conditions, and begin installation.
1. It might take several minutes before the add-in becomes active and available in Dynamics 365 finance and operations.

## One last thing

After you install the add-in, it might take up to an hour for the Finance insights feature to be enabled in Dynamics 365 Finance. If you don't want to wait, you can manually run the **Insights provisioning status check** process. 

1. In Dynamics 365 Finance, go to **System administration \> Setup \> Process automation**.
1. On the **Background processes** tab, find **Insights provisioning status check**, and select **Edit**.
1. Set the **Next execution** field to 30 minutes before the current time.

   This change forces the **Insights provisioning status check** process to run immediately.

   After the **Insights provisioning status check** process is successfully run, you can view the enabled Finance insights features in the relevant workspaces.

> [!NOTE]
> If the **Insights provisioning status check** process doesn't run, go to **System administration** > **Inquiries** > **Batch jobs**. In the **Process automation background process system job** field, change the value to **Waiting** to initiate the process. 
 
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
