---
title: Complete the Azure Resource Manager onboarding process
description: Learn how to complete the Azure Resource Manager onboarding process for your connectors, including known limitations. 
author: saurabhsurana
ms.author: sasurana
ms.topic: article
ms.date: 03/15/2022
ms.reviewer: johnmichalak
audience: IT Pro
ms.assetid: dcd23629-246d-4fbc-adf5-7245bb2121e4
ms.search.region: Global
ms.search.validFrom: 2016-08-30
ms.search.form: 
ms.dyn365.ops.version: Platform update 2
---

# Complete the Azure Resource Manager onboarding process

[!include [banner](../includes/banner.md)]

This article explains how to complete the Microsoft Azure Resource Manager onboarding process for your connectors. 

To deploy Azure Resource Manager topologies, you must complete the onboarding process for your connectors. To start the onboarding process, you must have the following items:

-   The Azure subscription ID that you're deploying to
-   Ownership of the Azure subscription, or access to the subscription owner, so that you can add contributor workflows, and the Upload Management certificate
-   The tenant administrator, to work through the admin consent workflow

## Azure Resource Manager onboarding process
You can consider Azure Resource Manager onboarding a two-step procedure, where each step has its own sub-procedures. You must complete all these procedures for every subscription that you add to the Microsoft Dynamics Lifecycle Services (LCS) project.

1.  Authorize the LCS deployment service to work on the Azure subscription.
    1.  Authorize the workflow.
    2.  Set the contributor workflow.

2.  Enable the Azure subscription to deploy Azure Resource Manager resources.
    1.  Enable the Azure connector, and add an LCS user.
    2.  Optional: Upload the Management certificate.
    3.  Configure deployment settings.

### Authorize the LCS deployment service to work on the Azure subscription

Complete the following procedures to authorize the LCS deployment service to work on the Azure subscription.

#### Authorize the workflow

The administrator of the tenant must complete the following procedure.

1.  In LCS, on the **Project** page, in the **Environments** section, select **Microsoft Azure settings**.
2.  On the **Project settings** page, on the **Azure connectors** tab, in the **Organization list** group, select **Authorize** to start the Azure Resource Manager Contributor workflow. This workflow sets up permissions for the deployment service, so that it can deploy to your subscription on your behalf.
3.  On the **Grant admin consent** page, select **Authorize**. Then sign in by using the administrator account of the Azure subscription that you must connect to, and select **Accept**. The authorization is now shown as completed.

#### Set the contributor workflow

Follow these steps to assign the **Contributor** role to the **Dynamics Deployment Services \[wsfed-enabled\]** application.

1.  In the [Azure portal](https://portal.azure.com), on the **Subscription** tab, select the Azure subscription, and then select the **Access Control (IAM)** line item.
2.  Select **Add**, select **Add role assignment**. In the dialog box, set **Role** to **Contributor** and set **Assign access to** to **Microsoft Entra user, group, or service principal**. In the **Select** field, search for and select **Dynamics Deployment Services \[wsfed-enabled\]**. Select **Save**. 

    > [!NOTE]
    > Some Azure subscriptions have a **Users** section instead of an **Access control (IAM)** section. In this case, in the **Add users** dialog box, in the **Select** field, enter **Dynamics Deployment Services \[wsfed-enabled\]**, and then select **Select**.
    
[![Dynamics Deployment Services \[wsfed-enabled\.\]](./media/arm_redo_02.png)](./media/arm_redo_02.png)

3.  On the **Role assignments** tab, the App is assigned as a **Contributor**. 

    > [!NOTE]
    > If Dynamics Deployment Services \[wsfed-enabled\] doesn't appear, the authorize process hasn't been completed, or it was completed on another Azure subscription. 

### Enable the Azure subscription to deploy Azure Resource Manager resources

Complete the following procedures to enable the Azure subscription to deploy Azure Resource Manager resources.

#### Enable the Azure connector and add an LCS user

Follow these steps to enable the Azure Connector and, as required, add an LCS user.

1.  In LCS, on the **Project** page, in the **Environments** section, select **Microsoft Azure settings**.
2.  On the **Project settings** page, on the **Azure connectors** tab, under **Azure connectors**, select **Add**. 

    > [!NOTE]
    > If you're enabling Azure Resource Manager for an existing connector, select **Edit**.

3.  Enter the connector name, enter the Azure subscription ID to deploy to, and set the **Configure to use Azure Resource manager** option to **Yes**.
4.  In the **Azure subscription Microsoft Entra Tenant domain** field, enter the domain name of the Azure subscription account admin, and then select **Next**.
5.  Authorize access to the subscription, either by adding the LCS user to the Azure subscription or by using the management certificate. 

    > [!MPORTANT] 
    > If you're adding an LCS user, continue with step 6. If you must upload a management certificate, don't complete steps 6 through 8 of this procedure. Instead, complete the next procedure, [Upload the management certificate](#upload-the-management-certificate). 

6.  In the [Azure portal](https://portal.azure.com), on the **Subscription** tab, select the Azure subscription, and then select the **Access Control (IAM)** line item.
7.  In the **Access Control (IAM)** dialog box, select **Add**, select **Contributor**, and then select **OK**.
8.  In the **Add users** dialog box, in the **Select** field, enter the LCS user, and then press Enter. 

    > [!NOTE]
    > You must specifically enter a user. You can't just add a group that the user is a member of. When the **Users** page opens, you can see that the user is assigned as a **Contributor**.

#### Upload the management certificate

Complete this procedure only if you didn't complete steps 6 through 8 of the previous procedure, "Enable the Azure connector and add an LCS user." 

1.  In LCS, on the **Microsoft Azure setup** page, select **Download**. Make a note of the location of the certificate file that is downloaded. You will use this information to upload the certificate to the Azure subscription.
2.  In the [Azure classic portal](https://ms.portal.azure.com), in the left pane, select **Settings**.
3.  Filter to the Azure subscription that is used, and then, on the **Management certificates** tab, select **Upload**.
4.  Select the management certificate that you downloaded in step 1, and then select **OK**.

#### Configure deployment settings

1.  In LCS, on the **Project** page, in the **Environments** section, select **Microsoft Azure settings**.
2.  On the **Microsoft Azure setup** page, select the region to deploy to, and then select **Connect**. The Azure Resource Manager onboarding flow is now completed. You should now see that the subscription has been added to the **Azure connectors** list. Additionally, a check mark should appear under **ARM Enabled**.

## Expired connectors

Azure connectors that were created by using management certificates have an expiration date. After the expiration date has passed, the certificate will no longer be valid. Therefore, you won't be able to use the Azure connector or, in turn, manage any resources that have been deployed from LCS via that connector. To renew the connector and reset the expiration date, we recommend that you follow the steps in [Enable the Azure connector and add an LCS user](./arm-onboarding.md#enable-the-azure-connector-and-add-an-lcs-user) to edit the connector.  This will generate a new certificate for download, and reset the expiration date.

An expiration date is shown only for connectors that use management certificates. If you created the connector via an LCS user, as described earlier in this article, no expiration date will be shown. Instead, the Azure connector will be good for as long as the LCS user has access to the subscription.

## Known limitations

There are a few known limitations when you set up or manage Azure connectors in LCS:

- Because prospect organizations haven't purchased a license for a finance and operations app, and therefore can't deploy the software, they aren't allowed to set up Azure connectors. To determine your organization type, select your name in the upper-right corner of the page while you're signed in to LCS.
- An Azure connector can be created only for a unique combination of an LCS project ID, an Azure subscription ID, and an Azure region. You can't create multiple connectors for the same subscription and region. If you must delete an Azure connector for a given combination of a subscription and a region, you must first delete all environments that were created by that connector.
- A management certificate can't be reused in the same project for the same Azure subscription ID, regardless of the region.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]