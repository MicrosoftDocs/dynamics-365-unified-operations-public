---
# required metadata

title: Complete the Azure Resource Manager (ARM) onboarding process for US government Lifecycle Services projects
description: This topic explains how to complete the Azure Resource Manager (ARM) onboarding process for your connectors. This topic applies to Azure US Government projects.
author: sericks007
ms.date: 07/21/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sasurana
ms.search.validFrom: 2021-07-31
---

# Complete the Azure Resource Manager (ARM) onboarding process for US government Lifecycle Services projects

[!include [banner](../includes/banner.md)]

This topic explains how to complete the Azure Resource Manager (ARM) onboarding process for your connectors. 

To deploy ARM topologies, you must complete the ARM onboarding process for your connectors. To start the onboarding process, you must have the following items:

-   The Azure subscription ID that you're deploying to
    > [!Note]
    > For US Government Lifecycle Services (LCS) projects, only Azure US Government specific Azure subscriptions will be supported.
-   Ownership of the Azure subscription, or access to the subscription owner, so that you can add contributor workflows, and the Upload Management certificate
-   The tenant administrator, to work through the admin consent workflow

## ARM onboarding process
You can consider ARM onboarding a two-step procedure, where each step has its own sub-procedures. You must complete all these procedures for every subscription that you add to the Microsoft Dynamics Lifecycle Services (LCS) project.

1.  Authorize the LCS Deployment Service (DSU) to work on the Azure subscription.
    1.  Authorize the workflow.
    2.  Set the contributor workflow.

2.  Enable the Azure subscription to deploy ARM resources.
    1.  Enable the Azure connector, and add an LCS user.
    2.  Upload the Management certificate.
    3.  Configure deployment settings.

### Authorize the LCS DSU to work on the Azure subscription

Complete the following procedures to authorize the LCS DSU to work on the Azure subscription.

#### Authorize the workflow

Be sure that you have Azure Active Directory PowerShell cmdlets installed. For more information, see [Install Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).  

The following two AppIds need to be authorized on the AAD tenant: 

- 68fdae24-7da6-4d2d-82b6-fd78a0f38eb7 
- 913c6de4-2a4a-4a61-a9ce-945d2b2ce2e0 

Follow these steps to authorize the AppIds on the tenant (repeat the steps for both the applications). 

1. Login via AuzreAD powershell cmdlet using the tenant administrator account.

    ```powershell
    Connect-AzureAD 
    ```

2. Check if Service Principal is not already installed.  

    ```powershell
    Get-AzureADServicePrincipal -Filter "AppId eq '<AppId>'"  
    ```

3. Add Service Principal  

    ```powershell
    New-AzureADServicePrincipal -AppId <AppId>  
    ```

4. Verify 

    ```powershell
    $sp = Get-AzureADServicePrincipal -Filter "AppId eq '<AppId>'"  
    ```

#### Set the contributor workflow

Follow these steps to assign the **Contributor** role to the **Dynamics Deployment Services \[wsfed-enabled\]** application.

1.  In the [Azure portal](https://portal.azure.com), on the **Subscription** tab, select the Azure subscription, and then click the **Access Control (IAM)** line item.
2.  Click **Add**, select **Add role assignment**. In the dialog box, set **Role** to **Contributor** and set **Assign access to** to **Azure AD user, group, or service principal**. In the **Select** field, search for and select **Dynamics Deployment Services \[wsfed-enabled\]**. Select **Save**. 
    > [!NOTE]
    > Some Azure subscriptions have a **Users** section instead of an **Access control (IAM)** section. In this case, in the **Add users** dialog box, in the **Select** field, enter **Dynamics Deployment Services \[wsfed-enabled\]**, and then select **Select**.
    
[![Dynamics Deployment Services \[wsfed-enabled\.]](./media/arm_redo_02.png)](./media/arm_redo_02.png)

3.  On the **Role assignments** tab, the App is assigned as a **Contributor**. 
    > [!NOTE]
    > If Dynamics Deployment Services \[wsfed-enabled\] doesn't appear, the authorize process hasn't been completed, or it was completed on another Azure subscription. 

### Enable the Azure subscription to deploy ARM resources

Complete the following procedures to enable the Azure subscription to deploy ARM resources.

#### Enable the Azure connector and add an LCS user

Follow these steps to enable the Azure Connector and, as required, add an LCS user.

1. In LCS, on the **Project** page, in the **Environments** section, click **Microsoft Azure settings**.
2. On the **Project settings** page, on the **Azure connectors** tab, under **Azure connectors**, click **Add**. 
    > [!NOTE]
    > If you're enabling ARM for an existing connector, click **Edit**.
3. Enter the connector name, enter the Azure subscription ID to deploy to, and set the **Configure to use Azure Resource manager** option to **Yes**.
4. In the **Azure subscription AAD Tenant domain** field, enter the domain name of the Azure subscription account admin, and then click **Next**.
5. In LCS, on the **Microsoft Azure setup** page, click **Download**. Make a note of the location of the certificate file that is downloaded. You will use this information to upload the certificate to the Azure subscription. 
6. In the [Azure classic portal](https://manage.windowsazure.com), in the left pane, click **Settings**. 
7. Filter to the Azure subscription that is used, and then, on the **Management certificates** tab, click **Upload**. 
8. Select the Management certificate that you downloaded in step 1, and then click **OK**. 

#### Configure deployment settings

1.  In LCS, on the **Project** page, in the **Environments** section, click **Microsoft Azure settings**.
2.  On the **Microsoft Azure setup** page, select the region to deploy to, and then click **Connect**. The ARM onboarding flow is now completed. You should now see that the subscription has been added to the **Azure connectors** list. Additionally, a check mark should appear under **ARM Enabled**.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
