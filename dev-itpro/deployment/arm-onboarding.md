---
# required metadata

title: Azure Resource Manager onboarding
description: This topic explains how to complete the Azure Resource Manager (ARM) onboarding process for your connectors. 
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 141093
ms.assetid: dcd23629-246d-4fbc-adf5-7245bb2121e4
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Azure Resource Manager onboarding

[!include[banner](../includes/banner.md)]


This topic explains how to complete the Azure Resource Manager (ARM) onboarding process for your connectors. 

To deploy Microsoft Azure Resource Manager (ARM) topologies, which include Microsoft Dynamics 365 for Operations Platform update 2 (August 2016), you must complete the ARM onboarding process for your connectors. To start the onboarding process, you must have the following items:

-   The Azure subscription ID that you're deploying to
-   Ownership of the Azure subscription, or access to the subscription owner, so that you can add contributor workflows, and the Upload Management certificate
-   The tenant administrator, to work through the admin consent workflow

## ARM onboarding process
You can consider ARM onboarding a two-step procedure, where each step has its own sub-procedures. You must complete all these procedures for every subscription that you add to the Microsoft Dynamics Lifecycle Services (LCS) project.

1.  Authorize the LCS Deployment Service (DSU) to work on the Azure subscription.
    1.  Authorize the workflow.
    2.  Set the contributor workflow.

2.  Enable the Azure subscription to deploy ARM resources.
    1.  Enable the Azure connector, and add an LCS user.
    2.  Optional: Upload the Management certificate.
    3.  Configure deployment settings.

### Authorize the LCS DSU to work on the Azure subscription

Complete the following procedures to authorize the LCS DSU to work on the Azure subscription.

#### Authorize the workflow

The administrator of the tenant must complete the following procedure.

1.  In LCS, on the **Project** page, in the **Environments** section, click **Microsoft Azure settings**.
2.  On the **Project settings** page, on the **Azure connectors** tab, in the **Organization list** group, click **Authorize** to start the ARM Contributor workflow. This workflow sets up permissions for the DSU, so that it can deploy to your subscription on your behalf.
3.  On the **Grant admin consent** page, click **Authorize**. Then sign in by using the administrator account of the Azure subscription that you must connect to, and click **Accept**. The authorization is now shown as completed.

#### Set the contributor workflow

Follow these steps to assign the **Contributor** role to the **Dynamics Deployment Services \[wsfed-enabled\]** application.

1.  In the [Azure portal](https://portal.azure.com), on the **Subscription** tab, select the Azure subscription, and then click the **Access Control (IAM)** line item.
2.  Click **Add**, select **Contributor**, and then click **OK**. **Note:** Some Azure subscriptions have a **Users** section instead of an **Access control (IAM)** section. In this case, in the **Add users** dialog box, in the **Select** field, enter **Dynamics Deployment Services \[wsfed-enabled\]**, and then click **Select**.
3.  On the **Add access** page, click **OK**. The **Users** page opens, and you can see that the user is assigned as a **Contributor**. **Note:** If Dynamics Deployment Services \[wsfed-enabled\] doesn't appear, the Authorize process hasn't been completed, or it was completed on another Azure subscription. [![Dynamics Deployment Services \[wsfed-enabled\]](./media/arm_redo_01-1024x407.png)](./media/arm_redo_01.png)

### Enable the Azure subscription to deploy ARM resources

Complete the following procedures to enable the Azure subscription to deploy ARM resources.

#### Enable the Azure connector and add an LCS user

Follow these steps to enable the Azure Connector and, as required, add an LCS user.

1.  In LCS, on the **Project** page, in the **Environments** section, click **Microsoft Azure settings**.
2.  On the **Project settings** page, on the **Azure connectors** tab, under **Azure connectors**, click **Add**. **Note:** If you're enabling ARM for an existing connector, click **Edit**.
3.  Enter the connector name, enter the Azure subscription ID to deploy to, and set the **Configure to use Azure Resource manager** option to **Yes**.
4.  In the **Azure subscription AAD Tenant domain** field, enter the domain name of the Azure subscription account admin, and then click **Next**.
5.  Authorize access to the subscription, either by adding the LCS user to the Azure subscription or by using the Management certificate. **Important:** If you're adding an LCS user, continue with step 6. If you must upload a Management certificate, don't complete steps 6 through 8 of this procedure. Instead, complete the next procedure, "Upload the Management certificate."
6.  In the [Azure portal](https://portal.azure.com), on the **Subscription** tab, select the Azure subscription, and then click the **Access Control (IAM)** line item.
7.  In the **Access Control (IAM)** dialog box, click **Add**, select **Contributor**, and then click **OK**.
8.  In the **Add users** dialog box, in the **Select** field, enter the LCS user, and then press Enter. **Note:** You must specifically enter a user. You can't just add a group that the user is a member of. When the **Users** page opens, you can see that the user is assigned as a **Contributor**.

#### Upload the Management certificate

Complete this procedure only if you didn't complete steps 6 through 8 of the previous procedure, "Enable the Azure Connector and add an LCS user."

1.  In LCS, on the **Microsoft Azure setup** page, click **Download**. Make a note of the location of the certificate file that is downloaded. You will use this information to upload the certificate to the Azure subscription.
2.  In the [Azure classic portal](https://manage.windowsazure.com/), in the left pane, click **Settings**.
3.  Filter to the Azure subscription that is used, and then, on the **Management certificates** tab, click **Upload**.
4.  Select the Management certificate that you downloaded in step 1, and then click **OK**.

#### Configure deployment settings

1.  In LCS, on the **Project** page, in the **Environments** section, click **Microsoft Azure settings**.
2.  On the **Microsoft Azure setup** page, select the region to deploy to, and then click **Connect**. The ARM onboarding flow is now completed. You should now see that the subscription has been added to the **Azure connectors** list. Additionally, a check mark should appear under **ARM Enabled**.




