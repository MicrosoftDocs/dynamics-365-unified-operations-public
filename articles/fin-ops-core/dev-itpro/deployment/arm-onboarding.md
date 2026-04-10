---
title: Complete the Azure Resource Manager onboarding process
description: Learn how to complete the Azure Resource Manager onboarding process for your connectors, including known limitations. 
author: saurabhsurana
ms.author: sasurana
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/02/2026
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

To deploy Azure Resource Manager topologies, you must complete the onboarding process for your connectors. To start the onboarding process, you need the following items:

- The Azure subscription ID that you're deploying to
- Ownership of the Azure subscription, or access to the subscription owner, so that you can add contributor workflows, and the Upload Management certificate
- The tenant administrator, to work through the admin consent workflow

## Azure Resource Manager onboarding process

Consider Azure Resource Manager onboarding as a two-step procedure, where each step has its own sub-procedures. You must complete all these procedures for every subscription that you add to the Microsoft Dynamics Lifecycle Services project.

1. Authorize the Lifecycle Services deployment service to work on the Azure subscription.
    1. Authorize the workflow.
    1. Set the contributor workflow.

1. Enable the Azure subscription to deploy Azure Resource Manager resources.
    1. Enable the Azure connector, and add an Lifecycle Services user.
    1. Optional: Upload the Management certificate.
    1. Configure deployment settings.

### Authorize the Lifecycle Services deployment service to work on the Azure subscription

Complete the following procedures to authorize the Lifecycle Services deployment service to work on the Azure subscription.

#### Authorize the workflow

The administrator of the tenant must complete the following procedure.

1. In Lifecycle Services, on the **Project** page, in the **Environments** section, select **Microsoft Azure settings**.
1. On the **Project settings** page, on the **Azure connectors** tab, in the **Organization list** group, select **Authorize** to start the Azure Resource Manager Contributor workflow. This workflow sets up permissions for the deployment service, so that it can deploy to your subscription on your behalf.
1. On the **Grant admin consent** page, select **Authorize**. Then sign in by using the administrator account of the Azure subscription that you must connect to, and select **Accept**. The authorization is now shown as completed.

#### Set the contributor workflow

Follow these steps to assign the **Contributor** role to the **Dynamics Deployment Services \[wsfed-enabled\]** application.

1. In the [Azure portal](https://portal.azure.com), on the **Subscription** tab, select the Azure subscription, and then select the **Access Control (IAM)** line item.
1. Select **Add**, select **Add role assignment**. In the dialog box, set **Role** to **Contributor** and set **Assign access to** to **Microsoft Entra user, group, or service principal**. In the **Select** field, search for and select **Dynamics Deployment Services \[wsfed-enabled\]**. Select **Save**.

    > [!NOTE]
    > Some Azure subscriptions have a **Users** section instead of an **Access control (IAM)** section. In this case, in the **Add users** dialog box, in the **Select** field, enter **Dynamics Deployment Services \[wsfed-enabled\]**, and then select **Select**.

:::image type="content" source="./media/arm_redo_02.png" alt-text="Screenshot of the Dynamics Deployment Services wsfed-enabled role assignment in the Azure portal.":::

1. On the **Role assignments** tab, the app is assigned as a **Contributor**.

    > [!NOTE]
    > If Dynamics Deployment Services \[wsfed-enabled\] doesn't appear, the authorize process isn't complete, or it was completed on another Azure subscription.

### Enable the Azure subscription to deploy Azure Resource Manager resources

Complete the following procedures to enable the Azure subscription to deploy Azure Resource Manager resources.

#### Enable the Azure connector and add an Lifecycle Services user

Follow these steps to enable the Azure Connector and, as required, add an Lifecycle Services user.

1. In Lifecycle Services, on the **Project** page, in the **Environments** section, select **Microsoft Azure settings**.
1. On the **Project settings** page, on the **Azure connectors** tab, under **Azure connectors**, select **Add**.

    > [!NOTE]
    > If you're enabling Azure Resource Manager for an existing connector, select **Edit**.

1. Enter the connector name, enter the Azure subscription ID to deploy to, and set the **Configure to use Azure Resource manager** option to **Yes**.
1. In the **Azure subscription Microsoft Entra Tenant domain** field, enter the domain name of the Azure subscription account admin, and then select **Next**.
1. Authorize access to the subscription, either by adding the Lifecycle Services user to the Azure subscription or by using the management certificate.

    > [!IMPORTANT]
    > If you're adding an Lifecycle Services user, continue with step 6. If you must upload a management certificate, don't complete steps 6 through 8 of this procedure. Instead, complete the next procedure, [Upload the management certificate](#upload-the-management-certificate).

1. In the [Azure portal](https://portal.azure.com), on the **Subscription** tab, select the Azure subscription, and then select the **Access Control (IAM)** line item.
1. In the **Access Control (IAM)** dialog box, select **Add**, select **Contributor**, and then select **OK**.
1. In the **Add users** dialog box, in the **Select** field, enter the Lifecycle Services user, and then press Enter.

    > [!NOTE]
    > You must specifically enter a user. You can't just add a group that the user is a member of. When the **Users** page opens, you can see that the user is assigned as a **Contributor**.

#### Upload the management certificate

Complete this procedure only if you didn't complete steps 6 through 8 of the previous procedure, "Enable the Azure connector and add an Lifecycle Services user."

1. In Lifecycle Services, on the **Microsoft Azure setup** page, select **Download**. Make a note of the location of the certificate file that is downloaded. You use this information to upload the certificate to the Azure subscription.
1. In the [Azure classic portal](https://ms.portal.azure.com), in the left pane, select **Settings**.
1. Filter to the Azure subscription that you use, and then, on the **Management certificates** tab, select **Upload**.
1. Select the management certificate that you downloaded in step 1, and then select **OK**.

#### Configure deployment settings

1. In Lifecycle Services, on the **Project** page, in the **Environments** section, select **Microsoft Azure settings**.
1. On the **Microsoft Azure setup** page, select the region to deploy to, and then select **Connect**. The Azure Resource Manager onboarding flow is now completed. You should now see that the subscription is added to the **Azure connectors** list. Additionally, a check mark appears under **ARM Enabled**.

## Expired connectors

Azure connectors that you create by using management certificates have an expiration date. After the expiration date passes, the certificate is no longer valid. Therefore, you can't use the Azure connector or manage any resources that the connector deployed from Lifecycle Services. To renew the connector and reset the expiration date, follow the steps in [Enable the Azure connector and add an Lifecycle Services user](./arm-onboarding.md#enable-the-azure-connector-and-add-an-lifecycle-services-user) to edit the connector. This process generates a new certificate for download and resets the expiration date.

An expiration date appears only for connectors that use management certificates. If you created the connector by using an Lifecycle Services user, as described earlier in this article, no expiration date appears. Instead, the Azure connector is valid as long as the Lifecycle Services user has access to the subscription.

## Known limitations

When you set up or manage Azure connectors in Lifecycle Services, be aware of the following limitations:

- Because prospect organizations don't purchase a license for a finance and operations app, they can't deploy the software and aren't allowed to set up Azure connectors. To determine your organization type, select your name in the upper-right corner of the page while you're signed in to Lifecycle Services.
- You can create an Azure connector only for a unique combination of an Lifecycle Services project ID, an Azure subscription ID, and an Azure region. You can't create multiple connectors for the same subscription and region. If you must delete an Azure connector for a given combination of a subscription and a region, you must first delete all environments that the connector created.
- You can't reuse a management certificate in the same project for the same Azure subscription ID, regardless of the region.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
