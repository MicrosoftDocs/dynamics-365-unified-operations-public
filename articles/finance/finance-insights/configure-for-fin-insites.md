---
# required metadata

title: Configuration for Finance insights
description: This topic explains the configuration steps that will enable your system to use the capabilities that are available in Finance insights.
author: ShivamPandey-msft
ms.date: 1/08/2021
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
[!include [preview banner](../includes/preview-banner.md)]

Finance insights combines functionality from Microsoft Dynamics 365 Finance with Dataverse, Azure, and AI Builder to provide powerful forecasting tools for your organization. This topic explains the configuration steps that will enable your system to use the capabilities that are available in Finance insights. To successfully complete the procedures in this topic, you must have System administrator and System Customizer access in the [Power Portal admin center](https://admin.powerplatform.microsoft.com/), System Administrator access in Dynamics 365 Finance, and access to create environments in Microsoft Dynamics Lifecycle Services (LCS).

> [!NOTE]
> The following procedures for setting up Finance insights are valid for versions of Dynamics 365 Finance version 10.0.21, and later.

## Deploy Dynamics 365 Finance

Follow these steps to deploy the environments.

1. In LCS, create or update a Dynamics 365 Finance environment. The environment requires app version 10.0.21 or later.

    > [!NOTE]
    > The environment must be a high-availability (HA) environment. (This type of environment is also known as a Tier-2 environment.) For more information, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md).

2. If you're configuring Finance insights in a sandbox environment, you might have to copy production data to that environment before predictions will work. The prediction model uses multiple years of data to build predictions. The Contoso demo data doesn't contain enough historical data to adequately train the prediction model. 

## Configure Dataverse

Follow these steps to configure Dataverse for Finance insights.

- In LCS, open the environment page, and verify that the **Power Platform Integration** section is already set up.

    - If it's already set up, the Dataverse environment name that is linked to the Finance environment should be listed.
    - If it isn't yet set up, select **Setup**. Setup of the Dataverse environment might take up to an hour. When the setup is successfully completed, the Dataverse environment name that is linked to the Finance environment should be listed.

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

## Feedback and support

If you're interested in providing feedback, or if you need support, send email to [Finance insights (Preview)](mailto:fiap@microsoft.com).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
