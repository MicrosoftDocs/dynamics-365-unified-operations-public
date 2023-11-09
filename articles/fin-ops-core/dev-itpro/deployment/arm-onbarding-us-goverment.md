---
# required metadata

title: Complete the Azure Resource Manager onboarding process for US government Lifecycle Services projects
description: This article explains how to complete the Microsoft Azure Resource Manager onboarding process for your connectors. This article applies to Azure US government projects.
author: saurabhsurana
ms.date: 08/12/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sasurana
ms.search.validFrom: 2021-07-31
---

# Complete the Azure Resource Manager onboarding process for US government Lifecycle Services projects

[!include [banner](../includes/banner.md)]

This article explains how to complete the Microsoft Azure Resource Manager onboarding process for your connectors.

To deploy Azure Resource Manager topologies, you must complete the Resource Manager onboarding process for your connectors. To start the onboarding process, you must have the following items:

- The Azure subscription ID that you're deploying to

    > [!NOTE]
    > For US government Microsoft Dynamics Lifecycle Services (LCS) projects, 
    > 1. Only Azure Government–specific Azure subscriptions are supported.
    > 2. Azure Government Subscriptions where management certificate support is not available, for example CSP Azure subscriptions are **not** supported currently.


- Ownership of the Azure subscription, or access to the subscription owner, so that you can add contributor workflows and upload the management certificate
- The tenant administrator, so that you can work through the admin consent workflow

## Resource Manager onboarding process

You can consider Resource Manager onboarding a two-step procedure, where each step has its own sub-procedures. You must complete all these sub-procedures for every subscription that you add to the LCS project.

1. Authorize the LCS deployment service to work on the Azure subscription.

    1. Authorize the workflow.
    2. Set the contributor workflow.

2. Enable the Azure subscription to deploy Resource Manager resources.

    1. Enable the Azure connector, and add an LCS user.
    2. Upload the management certificate.
    3. Configure deployment settings.

### Authorize the LCS deployment service to work on the Azure subscription

Complete the following procedures to authorize the LCS deployment service to work on the Azure subscription.

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

#### Enable the Azure connector and add an LCS user

Follow these steps to enable the Azure connector and, as required, add an LCS user.

1. In LCS, on the **Project** page, at the top of the page, select the hamburger icon, and then select **Project settings**.
2. On the **Project settings** page, select the **Azure connectors** tab.
3. On the **Project settings** page, on the **Azure connectors** tab, under **Azure connectors**, select **Add**.

    > [!NOTE]
    > If you're enabling Resource Manager for an existing connector, select **Edit** instead of **Add**.

4. Enter the connector name, enter the Azure subscription ID to deploy to, and set the **Configure to use Azure Resource manager (ARM)** option to **Yes**.
5. In the **Azure subscription Microsoft Entra Tenant domain** field, enter the domain name of the Azure subscription account admin, and then select **Next**.
6. On the **Microsoft Azure setup** page, select **Download**. Make a note of the location of the certificate file that is downloaded. You will use this information to upload the certificate to the Azure subscription.
7. In the [Azure Government portal](https://portal.azure.us), go to your subscription. In the left pane, select **Management Certificates**.
8. Filter to the Azure subscription that is used, and then, on the **Management certificates** tab, select **Upload**.
9. Select the Management certificate that you downloaded in step 5, and then select **OK**.

#### Configure deployment settings

1. In LCS, on the **Project** page, at the top of the page, select the hamburger icon, and then select **Project settings**.
2. On the **Project settings** page, select the **Azure connectors** tab.
3. On the **Project settings** page, on the **Azure connectors** tab, under **Azure connectors**, select **Add**.
4. On the **Microsoft Azure setup** page, select the region to deploy to, and then select **Connect**. The Resource Manager onboarding flow is now completed. You should now see that the subscription has been added to the **Azure connectors** list. Additionally, a check mark should appear under **ARM Enabled**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]