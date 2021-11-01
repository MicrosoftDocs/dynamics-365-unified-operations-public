---
# required metadata

title: Configuration for Finance insights
description: This topic explains the configuration steps that will enable your system to use the capabilities that are available in Finance insights.
author: ShivamPandey-msft
ms.date: 07/21/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.13

---
# Configuration for Finance insights

[!include [banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Finance insights combines functionality from Microsoft Dynamics 365 Finance with Microsoft Dataverse, Azure, and AI Builder to provide powerful forecasting tools for your organization. This topic explains the configuration steps that will enable your system to use the capabilities that are available in Finance insights. You will need System administrator and System Customizer access in [Power Portal admin center](https://admin.powerplatform.microsoft.com/), System Administrator access for Dynamics 365 Finance and Operations and access to create LCS environemnts to sucessfully complete the steps below.

> [!NOTE]
> The following procedures for setting up Finance insights are valid for Microsoft Dynamics 365 Finance before version 10.0.21, and later.

## Deploy Dynamics 365 Finance

Deploy the environments by completing the following steps.

1. In Microsoft Dynamics Lifecycle Services (LCS), create or update a Dynamics 365 Finance environment. The environment requires app version 10.0.21 or later.
2. The environment must be a high-availability (HA) environment. (This type of environment is also known as a Tier-2 environment.) For more information, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md).
3. If you are configuring Finance insights in a sandbox environment, you might need to copy production data to that environment for predictions to work. The prediction model uses multiple years of data to build predictions. The Contoso demo data doesn’t contain enough historical data to train the prediction model adequately. 

## Configure Dataverse

Follow these steps to configure Dataverse for Finance insights.

In LCS, open the environment page, and verify that the **Power Platform Integration** section is already set up.
- If it's already set up, the Dataverse environment name that is linked to the Finance environment should be listed.
- If it isn't yet set up, follow these steps:

    1. In the **Power Platform Integration** section, select **Setup**. Setup of the environment might take up to an hour.
    2. If the Dataverse environment is successfully set up, the Dataverse environment name that is linked to the Finance environment should be listed.

## Configure the Get insights add-in

If you previously installed the Get insights add-in, uninstall it before you complete the following procedure.

> [!NOTE]
> If you have installed data lake add-in in LCS already, Finance insights will use it save data needed for predictions. If data lake add-in in LCS not already set up, Get insights add-in will create a mandaged data lake for you.

Complete the following steps to install the Finance insights add-in.

1. Sign in to LCS, and then, under the environment name on the right side of the page, select **Full Details**.
2. In the **Environment add-ins** section, select **Install a new add-in**.
3. Select the **Get insights** add-in.
4. Agree to the terms and conditions, and then select **Install**.

The add-in might take several minutes to install.

## Once last thing...
Once add-in has been successfully installed, it may take up to an hour before Finance insights features can be enabled in Dynamics 365 Finance.

To expedite enabling the Finance insights features in the **Feature management** workspace, you can execute the **Insights provisioning status check** manually. 

1. In Dynamics 365 Finance, navigate to (**System administration \> Setup \> Process automation**).

2. On the **Background processes** tab, find **Insights provisioning status check** and click **Edit**.

3. Set the **Next execution** time to 30 minutes before the current time.

   This should force the **Insights provisioning status check** process to run immediately.

   After the **Insights provisioning status check** has run successfully, you can proceed enabling finance insights features in **Feature management** workspace.

## Feedback and support

If you're interested in providing feedback, or if you need support, send email to [Finance insights (Preview)](mailto:fiap@microsoft.com).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
