---
title: Complete the Azure Resource Manager onboarding process for US government Lifecycle Services projects
description: Learn how to complete the Microsoft Azure Resource Manager onboarding process for your connectors. This article applies to Azure US government projects.
author: saurabhsurana
ms.author: sasurana
ms.topic: article
ms.date: 02/08/2024
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

You can consider Resource Manager onboarding a two-step procedure, where each step has its own subprocedures. You must complete all these subprocedures for every subscription that you add to the Lifecycle Services project.

1. Authorize the Lifecycle Services deployment service to work on the Azure subscription.

    1. Authorize the workflow.
    2. Set the contributor workflow.

2. Enable the Azure subscription to deploy Resource Manager resources.

    1. Enable the Azure connector.
    2. Configure the Azure subscription tag.
    3. Configure deployment settings.

### Authorize the Lifecycle Services deployment service to work on the Azure subscription

Complete the following procedures to authorize the Lifecycle Services deployment service to work on the Azure subscription.

#### Authorize the workflow

Be sure that you have Microsoft Entra ID PowerShell cmdlets installed. For more information, see [Install Microsoft Entra ID PowerShell for Graph](/powershell/azure/active-directory/install-adv2).

The following two app IDs must be authorized on the Microsoft Entra tenant:

- 68fdae24-7da6-4d2d-82b6-fd78a0f38eb7
- 913c6de4-2a4a-4a61-a9ce-945d2b2ce2e0

Follow these steps to authorize the app IDs on the tenant. Complete this procedure for each application.

1. Sign in via the Microsoft Entra PowerShell cmdlet. Use the tenant administrator account to sign in.

    ```powershell
    Connect-AzureAD 
    ```

2. Make sure that the service principal isn't already installed.

    ```powershell
    Get-AzureADServicePrincipal -Filter "AppId eq '<AppId>'"
    ```

3. Add the service principal.

    ```powershell
    New-AzureADServicePrincipal -AppId <AppId>
    ```

4. Verify that each application ID is added successfully.

    ```powershell
    $sp = Get-AzureADServicePrincipal -Filter "AppId eq '<AppId>'"
    ```

#### Set the contributor workflow

Follow these steps to assign the **Contributor** role to the **Dynamics Deployment Services \[wsfed-enabled\]** application.

1. In the [Azure Government portal](https://portal.azure.us), on the **Subscription** tab, select the Azure subscription, and then select the **Access Control (IAM)** item on the navigation menu.
2. Select **Add**, and then select **Add role assignment**.
3. In the **Add role assignment** dialog box, set the **Role** field to **Contributor**, and set the **Assign access to** field to **Microsoft Entra user, group, or service principal**. In the **Select** field, search for and select **Dynamics Deployment Services \[wsfed-enabled\]**. Then select **Save**.

    > [!NOTE]
    > Some Azure subscriptions have a **Users** item instead of an **Access control (IAM)** item on the navigation menu. In this case, in the **Add users** dialog box, in the **Select** field, enter **Dynamics Deployment Services \[wsfed-enabled\]**. Then select **Select**.

    [![Selecting Dynamics Deployment Services \[wsfed-enabled\] in the Add role assignment dialog box](./media/arm_redo_02.png)](./media/arm_redo_02.png)

3. On the **Role assignments** tab, the app is assigned as a contributor.

    > [!NOTE]
    > If **Dynamics Deployment Services \[wsfed-enabled\]** doesn't appear, the authorization process hasn't been completed, or it was completed on another Azure subscription.

### Enable the Azure subscription to deploy Resource Manager resources

Complete the following procedures to enable the Azure subscription to deploy Resource Manager resources.

#### Enable the Azure connector

Follow these steps to enable the Azure connector.

1. In Lifecycle Services, on the **Project** page, at the top of the page, select the hamburger icon, and then select **Project settings**.
2. On the **Project settings** page, select the **Azure connectors** tab.
3. On the **Azure connectors** tab, under **Azure connectors**, select **Add**.
4. Enter the **Name**, the **Azure subscription ID** to deploy to and set the **Configure to use Azure Resource manager (ARM)** option to **Yes**.
5. In the **Azure subscription Microsoft Entra ID Tenant Domain (or ID)** field, enter the domain name of the government Azure subscription account admin, and then select **Next**.
6. On the **Microsoft Azure setup** page, verify **Dynamics Deployment Services \[wsfed-enabled\]** has the contributor role and select **Next**.

    > [!NOTE]
    > If **Dynamics Deployment Services \[wsfed-enabled\]** doesn't appear, the authorization process hasn't been completed, or it was completed on another Azure subscription.

7. On the **Microsoft Azure setup** page, under **Apply a subscription tab**, select **Get a code**, and make a note of the information presented. You use this information to configure a tag on the Azure subscription.

#### Configure the Azure subscription tag


1. In the [Azure Government portal](https://portal.azure.us), go to your subscription. In the left pane, select **Tags**.
2. Enter the **Name** and **Value** from the information presented above and select **Apply**.


#### Configure deployment settings

1. In Lifecycle Services, on the **Microsoft Azure setup** page, select **Next**.
2. Select the **Azure region** and select **Connect**. The Resource Manager onboarding flow is now complete. You should now see that the subscription is added to the **Azure connectors** list. Additionally, a check mark should appear under **ARM Enabled**.

    > [!NOTE]
    > Azure connectors configured using an Azure subscription tag do not expire.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]