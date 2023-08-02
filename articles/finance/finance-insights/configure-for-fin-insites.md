---
# required metadata

title: Configuration for Finance insights
description: This article explains the configuration steps that will enable your system to use the capabilities that are available in Finance insights.
author: ShivamPandey-msft
ms.date: 09/16/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.13

---
# Configuration for Finance insights

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Finance insights combines functionality from Microsoft Dynamics 365 Finance with Dataverse, Azure, and AI Builder to provide powerful forecasting tools for your organization. This article explains the configuration steps that will enable your system to use the capabilities that are available in Finance insights. To successfully complete the procedures in this article, you must have System administrator and System Customizer access in the [Power Portal admin center](https://admin.powerplatform.microsoft.com/), System Administrator access in Dynamics 365 Finance, and access to create environments in Microsoft Dynamics Lifecycle Services (LCS).

> [!NOTE]
> The following procedures for setting up Finance insights are valid for versions of Dynamics 365 Finance version 10.0.21, and later.

## Deploy Dynamics 365 Finance

Follow these steps to deploy the environments.

1. In LCS, create or update a Dynamics 365 Finance environment. The environment requires app version 10.0.21 or later.

    > [!NOTE]
    > The environment must be a high-availability (HA) environment. (This type of environment is also known as a Tier-2 environment.) For more information, see [Environment planning](/fin-ops-core/fin-ops/imp-lifecycle/environment-planning).

2. If you're configuring Finance insights in a sandbox environment, you might have to copy production data to that environment before predictions will work. The prediction model uses multiple years of data to build predictions. The Contoso demo data doesn't contain enough historical data to adequately train the prediction model. 

## Configure your Azure AD tenant

Azure Active Directory (Azure AD) must be configured so that it can be used with Dataverse and the Microsoft Power Platform applications. This configuration requires that either the **Project Owner** role or the **Environment Manager** role be assigned to the user in the **Project security role** field in LCS.

Verify that the following setup is completed:

- You have **System administrator** and **System Customizer** access in the Power Portal admin center.
- A Dynamics 365 Finance or equivalent license is applied to the user who is installing the Finance insights add-in.
- The following Azure AD apps are registered in Azure AD.

    |  Application                             | App ID                               |
    |------------------------------------------|--------------------------------------|
    | Microsoft Dynamics ERP Microservices CDS | 703e2651-d3fc-48f5-942c-74274233dba8 |

    To verify the application is registered in Azure AD, check the **All Applications** list. For more details, see [View enterprise applications](/azure/active-directory/manage-apps/view-applications-portal).
  
    If the application isn't registered in Azure AD, contact support.
  
## Configure Dataverse

Follow these steps to configure Dataverse for Finance insights.

- In LCS, open the environment page, and verify that the **Power Platform Integration** section is already set up.

    - If Dataverse has already been set up, the Dataverse environment name that is linked to the Finance environment should be listed.
    - If Dataverse hasn't yet been set up, select **Setup**. Setup of the Dataverse environment can take up to an hour. When the setup has been successfully completed, the Dataverse environment name that is linked to in the Finance environment should be listed.
    - If this integration was set up with an existing Microsoft Power Platform environment, contact your administrator to make sure that the linked environment isn't in the disabled state.

        For more information, see [Enabling the Power Platform integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md). 

        To access the Microsoft Power Platform admin site, go to <https://admin.powerplatform.microsoft.com/environments>.

## Configure the Finance insights add-in

If you previously installed the Finance insights add-in, uninstall it before you complete the following procedure.

> [!NOTE]
> If you've already installed the data lake add-in in LCS, Finance insights will use it to save data that is required for predictions. If you haven't yet installed the data lake add-in in LCS, the Finance insights add-in will create a managed data lake for you.

Follow these steps to install the Finance insights add-in.

1. Sign in to LCS, and then, under the environment name on the right side of the page, select **Full Details**.
2. In the **Environment add-ins** section, select **Install a new add-in**.
3. Select the **Finance insights** add-in.
4. Agree to the terms and conditions, and then select **Install**.

The add-in might take several minutes to install.

## One last thing...

After the add-in is successfully installed, it might take up to an hour before you can enable Finance insights features in the **Feature management** workspace in Dynamics 365 Finance. If you don't want to wait that long, you can manually run the **Insights provisioning status check** process. 

1. In Dynamics 365 Finance, go to **System administration \> Setup \> Process automation**.
2. On the **Background processes** tab, find **Insights provisioning status check**, and select **Edit**.
3. Set the **Next execution** field to 30 minutes before the current time.

   This change should force the **Insights provisioning status check** process to run immediately.

   After the **Insights provisioning status check** process is successfully run, you can enable Finance insights features in the **Feature management** workspace.

> [!NOTE]
> If the **Insights provisioning status check** process doesn't run, go to **System administration** > **Inquiries** > **Batch jobs**. In the **Process automation polling system** field, change the value to **Waiting** to initiate the process. 
> 
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
