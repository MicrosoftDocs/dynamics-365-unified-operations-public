---
title: Complete the Azure Resource Manager onboarding process for US government Lifecycle Services projects
description: Learn how to complete the Microsoft Azure Resource Manager onboarding process for your connectors. This article applies to Azure US government projects.
author: saurabhsurana
ms.author: sasurana
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-07-31
---

# Complete the Azure Resource Manager onboarding process for US government Lifecycle Services projects

[!include [banner](../includes/banner.md)]

This article explains how to complete the Microsoft Azure Resource Manager onboarding process for your connectors.

To deploy Azure Resource Manager topologies, you must complete the Resource Manager onboarding process for your connectors. To start the onboarding process, you must have the following items:

- The Azure subscription ID that you're deploying to.

    > [!NOTE]
    > For US government Microsoft Dynamics Lifecycle Services projects, only Azure Government–specific Azure subscriptions are supported.

- Ownership of the Azure subscription, or access to the subscription owner, so that you can configure the  Azure subscription tag.
- The tenant administrator, so that you can work through the admin consent workflow.

## Resource Manager onboarding process

Resource Manager onboarding is a two-step procedure, where each step has its own subprocedures. You must complete all these subprocedures for every subscription that you add to the Lifecycle Services project.

1. Authorize the Lifecycle Services deployment service to work on the Azure subscription.

    1. Authorize the workflow.
    1. Set the contributor workflow.

1. Enable the Azure subscription to deploy Resource Manager resources.

    1. Enable the Azure connector.
    1. Configure the Azure subscription tag.
    1. Configure deployment settings.

### Authorize the Lifecycle Services deployment service to work on the Azure subscription

Complete the following procedures to authorize the Lifecycle Services deployment service to work on the Azure subscription.

#### Authorize the workflow

Make sure you have Microsoft Entra ID PowerShell cmdlets installed. For more information, see [Install Microsoft Entra ID PowerShell for Graph](/powershell/azure/active-directory/install-adv2).

Authorize the following two app IDs on the Microsoft Entra tenant:

- 68fdae24-7da6-4d2d-82b6-fd78a0f38eb7
- 913c6de4-2a4a-4a61-a9ce-945d2b2ce2e0

Follow these steps to authorize the app IDs on the tenant. Complete this procedure for each application.

1. Sign in by using the Microsoft Entra PowerShell cmdlet. Use the tenant administrator account to sign in.

    ```powershell
    Connect-AzureAD 
    ```

1. Make sure that the service principal isn't already installed.

    ```powershell
    Get-AzureADServicePrincipal -Filter "AppId eq '<AppId>'"
    ```

1. Add the service principal.

    ```powershell
    New-AzureADServicePrincipal -AppId <AppId>
    ```

1. Verify that each application ID is added successfully.

    ```powershell
    $sp = Get-AzureADServicePrincipal -Filter "AppId eq '<AppId>'"
    ```

#### Set the contributor workflow

Follow these steps to assign the **Contributor** role to the **Dynamics Deployment Services \[wsfed-enabled\]** application.

1. In the [Azure Government portal](https://portal.azure.us), on the **Subscription** tab, select the Azure subscription. Then select the **Access Control (IAM)** item on the navigation menu.
1. Select **Add**, and then select **Add role assignment**.
1. In the **Add role assignment** dialog box, set the **Role** field to **Contributor**, and set the **Assign access to** field to **Microsoft Entra user, group, or service principal**. In the **Select** field, search for and select **Dynamics Deployment Services \[wsfed-enabled\]**. Then select **Save**.

    > [!NOTE]
    > Some Azure subscriptions have a **Users** item instead of an **Access control (IAM)** item on the navigation menu. In this case, in the **Add users** dialog box, in the **Select** field, enter **Dynamics Deployment Services \[wsfed-enabled\]**. Then select **Select**.

    :::image type="content" source="./media/arm_redo_02.png" alt-text="Screenshot of the Add role assignment dialog box with Dynamics Deployment Services wsfed-enabled selected.":::

1. On the **Role assignments** tab, the app is assigned as a contributor.

    > [!NOTE]
    > If **Dynamics Deployment Services \[wsfed-enabled\]** doesn't appear, the authorization process isn't complete, or it was completed on another Azure subscription.

### Enable the Azure subscription to deploy Resource Manager resources

Complete the following procedures to enable the Azure subscription to deploy Resource Manager resources.

#### Enable the Azure connector

Follow these steps to enable the Azure connector.

1. In Lifecycle Services, on the **Project** page, at the top of the page, select the hamburger icon, and then select **Project settings**.
1. On the **Project settings** page, select the **Azure connectors** tab.
1. On the **Azure connectors** tab, under **Azure connectors**, select **Add**.
1. Enter the **Name**, the **Azure subscription ID** to deploy to, and set the **Configure to use Azure Resource manager (ARM)** option to **Yes**.
1. In the **Azure subscription Microsoft Entra ID Tenant Domain (or ID)** field, enter the domain name of the government Azure subscription account admin, and then select **Next**.
1. On the **Microsoft Azure setup** page, verify **Dynamics Deployment Services \[wsfed-enabled\]** has the contributor role and select **Next**.

    > [!NOTE]
    > If **Dynamics Deployment Services \[wsfed-enabled\]** doesn't appear, the authorization process isn't complete, or it was completed on another Azure subscription.

1. On the **Microsoft Azure setup** page, under **Apply a subscription tab**, select **Get a code**, and make a note of the information presented. You use this information to configure a tag on the Azure subscription.

#### Configure the Azure subscription tag


1. In the [Azure Government portal](https://portal.azure.us), go to your subscription. In the left pane, select **Tags**.
1. Enter the **Name** and **Value** from the information presented earlier and select **Apply**.


#### Configure deployment settings

1. In Lifecycle Services, on the **Microsoft Azure setup** page, select **Next**.
1. Select the **Azure region** and select **Connect**. The Resource Manager onboarding flow is now complete. You should now see that the subscription is added to the **Azure connectors** list. Additionally, a check mark appears under **ARM Enabled**.

    > [!NOTE]
    > Azure connectors configured by using an Azure subscription tag don't expire.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
