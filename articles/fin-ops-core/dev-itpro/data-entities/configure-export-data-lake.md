---
title: Install Export to Azure Data Lake add-in
description: Learn about configuring the export to Azure Data Lake and configuring various add-ins and Azure resources, including how to create an application in Microsoft Entra ID.
author: MilindaV2
ms.author: johnmichalak
ms.topic: install-set-up-deploy
ms.date: 01/16/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-03-03
ms.search.form:
ms.dyn365.ops.version: Platform Update 33

---

# Install Export to Azure Data Lake add-in

[!include [banner](../includes/banner.md)]

> [!NOTE]
> Over the past 12 months, the product team worked to fill in gaps and add new features that members of the user community highlighted. [Azure Synapse Link for Dataverse service built into Power Apps](/power-apps/maker/data-platform/azure-synapse-link-select-fno-data), the successor to the **Export to Data Lake** feature in finance and operations apps, is generally available and ready for you. Azure Synapse Link provides one experience for working with data from all Microsoft Dynamics 365 apps.
>
> To benefit from the enhanced performance, flexibility, and improved user experience that Azure Synapse Link offers, the product team announced the deprecation of the **Export to Data Lake** feature, effective October 15, 2023. If you're already using the **Export to Data Lake** feature, you can continue to use it until November 1, 2024. If you're new to the **Export to Data Lake** feature or are planning to adopt this feature in the coming months, use Azure Synapse Link instead. 
>
> The transition might seem daunting, but the product team wants to provide a smoother experience and offer guidance. To get started, see the [Azure Synapse Link transition guide](https://aka.ms/TransitionToSynapseLink). The product team is listening closely to the community and is working on multiple features to help make the transition smoother. They announce these other improvements to the transition process as they bring new features online. If you want to stay in touch, join the community at [https://aka.ms/SynapseLinkforDynamics](https://aka.ms/SynapseLinkforDynamics).
>
> The **Export to Data Lake** feature isn't available in Tier-1 (developer) environments. You must have a cloud-based Tier-2 or higher sandbox environment to enable this feature. 

Before you can use the **Export to Data Lake** feature in finance and operations environments, your administrator must install the **Export to Data Lake** add-in and connect your environment with a data lake. You must install the **Export to Data Lake** add-in in your environment via Lifecycle Services. Contact your Lifecycle Services administrator to perform this operation.

The **Export to Data Lake** add-in requires connection information for your data lake. Therefore, before you install it, you must create a storage account (that is, an Azure data lake) if you haven't already created one. To create the required Azure resources, you might have to contact an administrator who can create Azure resources on your behalf. 

The following step-by-step instructions guide you through the process. 

## <a name="createServicePrincipal"></a> Create Service Principal for Microsoft Dynamics ERP Microservices

The **Export to Azure Data Lake** feature uses a microservice that exports finance and operations app data to Azure Data Lake and keeps the data fresh. The microservice uses the Azure service principal, **Microsoft Dynamics ERP Microservices**, to securely connect to your Azure resources. Before you configure the Export to Data Lake feature, add the **Microsoft Dynamics ERP Microservices** service principal to your Microsoft Entra. This step enables Microsoft Entra to authenticate the microservice. 

To add the service principal, complete the following steps.

1. Launch the Azure portal and go to the Microsoft Entra.
1. On the left menu, select **Manage** > **Enterprise Applications**, and search for the following applications.

    | Application                          | App ID |
    |--------------------------------------|--------|
    | Microsoft Dynamics ERP Microservices | 0cdb527f-a8d1-4bf8-9436-b352c68682b2 |

    If you can't find the above applications, complete the following steps.

1. On your local machine, open the **Start** menu, and search for **PowerShell**.
1. Right-click **Windows PowerShell**, and then select **Run as administrator**.
1. Run the following command to install **AzureAD** module:

    ```powershell
    Install-Module -Name AzureAD
    ```

    - If NuGet provider is required to continue, select **Y** to install it.
    - If an **Untrusted repository** message appears, select **Y** to continue.

1. Run the following commands to add the application to the Microsoft Entra.

    ```powershell
    Connect-AzureAD
    ```
    
    ```powershell
    New-AzureADServicePrincipal –AppId '0cdb527f-a8d1-4bf8-9436-b352c68682b2'
    ```

1. Sign in as the Microsoft Entra administrator when prompted.

## <a name="ConfigureAzureResources"></a>Configure Azure resources 

To configure the export to Data Lake, create a storage account in your own Azure subscription. Use this storage account to store data. Next, create a Microsoft Entra application ID that grants access to the root of your storage account. Your finance or operations apps use the Microsoft Entra application to gain access to storage, create the folder structure, and write data. Create a key vault in your subscription and store the name of the storage account, application ID, and the application secrets. If you don't have permission to create resources in Azure portal, you need assistance from someone in your organization with the required permissions.

The following steps take place in the Azure portal:

> [!NOTE]
> When you're working in the Azure portal, save several values for subsequent steps. You also provide some of these values to your finance and operations apps by using Lifecycle Services. You need Administrator access to Lifecycle Services in order to do this.

1. [Create an application in Microsoft Entra ID](#createapplication)
1. [Create a Data Lake Storage (Gen2 account) in your subscription](#createsubscription)
1. [Grant access control roles to applications](#grantaccess)
1. [Create a key vault](#createkeyvault)
1. [Add secrets to the key vault](#addsecrets)
1. [Authorize the application to read secrets in the key vault](#authorize)
1. [Power Platform integration](#powerplatformintegration)
1. [Install the Export to Data Lake add-in in Lifecycle Services](#installaddin)

## <a name="createapplication"></a>Create an application in Microsoft Entra ID

1. In the Azure portal, select **Microsoft Entra**, and then select **App registrations**.
1. Select **New registration**, and enter the following information: 

    - **Name:** Enter a name for the app.
    - **Supported Account types**: Choose the appropriate option.

1. After creating the application, select it, and then copy and save the <a name="appid"></a>Application (client) ID at the top of the page. You need this ID later.
1. In the left navigation pane, select **Certificates & secrets**, and then select **New client secret**. 
1. In the **Description** field, enter a name.
1. In the **Expires** field, select an option, and then select **Add**. The system generates a secret and displays it under the grid. 
1. Copy the secret **Value** to the clipboard. This is the <a name="secret"></a>value you need to provide when you set up the key vault later.

## <a name="createsubscription"></a>Create a Data Lake Storage (Gen2) account in your subscription

Use the Data Lake Storage account to store data from your finance and operations apps. To manually create a storage account, you must have administrative rights to your organization's Azure subscription. To create a storage account, complete the following steps.

1. In the Azure portal, select **Create new resource**, and then search for and select **Storage account – blob, file, table, queue**.
1. In the **Create storage account** dialog box, provide values for the following parameter fields:

    - **Location:** Select the data center where your environment is located. If the data center that you select is in a different Azure region, you might incur more data movement costs. If your Microsoft Power BI or your data warehouse is in a different region, you can use replication to move storage between regions.
    - **Performance**: Select **Standard**.
    - **Account kind**: Select **StorageV2**. In the **Advanced options** dialog box, you see the option, **Data Lake storage Gen2**.

1. On the **Advanced tab**, select **Data Lake storage Gen2** \> **Hierarchical namespaces**, and then select **Enabled**. If you disable this option, the **Export to Data lake** feature might fail with an error.
1. Select **Review and create**. When the deployment finishes, the new resource appears in the Azure portal.
1. In the Azure portal, select the storage account you created. Copy and save the <a name="storageaccount"></a>storage account name.

## <a name="grantaccess"></a>Grant access control roles to applications 

You need to grant your application permissions to read and write to the storage account. Grant these permissions by using Roles in Microsoft Entra ID.

1. In **Azure portal**, open the storage account that you created earlier.
1. Select **Access Control (IAM)** in the left navigation. 
1. On the **Access control** page, select the **Role assignments** tab.
1. Select **Add** at the top of the page, and then select **Add role assignment**.
1. In the **Add role assignment** dialog box, select the **Role** field, and then select **Storage blob data contributor**.
1. In the **Select** field, select the application that you registered earlier.

    > [!NOTE]
    > Don't change the fields **Assign access to** and **Microsoft Entra user, group, or service principal**.

1. Select **Save**.
1. Validate the storage account role assignment for [the application](#appid) you created earlier. 

    | Application                                   | Role |
    |-----------------------------------------------|------|
    | [The application](#appid) you created earlier | Storage blob data contributor |

## <a name="createkeyvault"></a>Create a key vault

A key vault is a secure way to share details such as storage account name to your finance and operations apps. Complete the following steps to create a key vault and a secret. Create a key vault for the use of the Export to Data lake feature. Don't use the same key vault to provide access to multiple services.

1. In the Azure portal, select **Create a new resource** and then search for and select **Key Vault**.
1. In the **Create key vault** dialog box, in the **Location** field, select the datacenter where your environment is located.
1. After the key vault is created, select it from the list, and on the left navigation pane, select **Overview**. 
1. Save the value in the <a name="dnsname"></a>**DNS name** field. You need this value later.

## <a name="addsecrets"></a>Add secrets to the key vault

Create three secrets in the key vault and add the values you saved from previous steps. For each secret, provide a secret name and enter the value you saved from earlier steps.

| <a name="suggest"></a>Suggested secret name | Secret value that you saved earlier | Example secret value |
|---------------------------------------------|-------------------------------------|----------------------|
| app-id                                      | The ID of the application [created earlier](#appid). | 8936e905-197b-xxx-xxxx-xxxxxxxxx |
| app-secret                                  | The [client secret](#secret) specified earlier. | NaeIxxxxxxx---xxxx7eixxx~1g- |
| storage-account-name                        | The name of the [storage account](#storageaccount) created earlier. | contosod365datalake |

Complete the following steps three times, once for each secret.

1. In the Azure portal, go to the key vault you created earlier. In the left navigation pane, select **Secrets**.
1. Select **Generate/Import**. In the **Create a secret** dialog box, in the **Upload options** field, select **Manual**.
1. Enter a name for the secret. See the table in the introduction of this section for suggested names.
1. Copy and paste the corresponding secret value in the **Value** field.
1. Select **Enabled**, and then select **Create**. 

You see the secret created in the list of secrets.

## <a name="authorize"></a>Authorize the application to read secrets in the key vault

1. In **Azure portal**, open the key vault that you created earlier.
1. In **Settings**, select **Access configuration**.
1. Then go to **access policies** and select **create** to create a new policy.
1. In the **Secret permissions** fields, select **Get** and **List**.
1. In the **Key permissions** fields, select **Get**.
1. In the **Select principal** field, locate and select the application, **Microsoft Dynamics ERP Microservices**, and then select **Select**. 

    > [!NOTE]
    > If you can't find **Microsoft Dynamics ERP Microservices**, see the [Create Service Principal](#createServicePrincipal) section in this document.
1. Select **Save**.

    You should see the application with access to your key vault, similar to the following example.

    | Application                          | Secret permissions |
    |--------------------------------------|--------------------|
    | Microsoft Dynamics ERP Microservices | Get, List          |
    
    

## <a name="powerplatformintegration"></a>Power Platform integration

If you're installing add-ins in this environment for the first time, you might need to enable the **Power Platform integration** for this environment. For more information, see [Microsoft Power Platform integration with finance and operations apps](../power-platform/overview.md).

## <a name="installaddin"></a>Install the Export to Data Lake add-in in Lifecycle Services 

Before you can export data to your data lake from your finance and operations apps, you must install the **Export to Data Lake** add-in in Lifecycle Services. To complete this task, you must be an environment administrator in Lifecycle Services for the environment that you want to use.

You need the following information before you start. Keep the information handy before you begin.

| Information you need for Export to Data lake add-in       | Where you can find it | Example |
|-----------------------------------------------------------|-----------------------|---------|
| Your environment Microsoft Entra Tenant ID                       | Your Microsoft Entra tenant ID in the Azure portal. Sign in to the **Azure portal** and open the **Microsoft Entra** service. Open the **Properties** page and copy the value in the **Directory ID** field. | 72f988bf-0000-0000-00000-2d7cd011db47 |
| DNS name of your key vault                                | This name should be previously saved. Enter the [DNS name](#dnsname) of your key vault | `https://contosod365datafeedpoc.vault.azure.net/` |
| The secret that contains the name of your storage account | If you used the suggested name, enter **storage-account-name**. If not, enter the [secret name](#suggest) you defined. | storage-account-name |
| Secret that contains the Application ID                   | If you used the suggested name, enter **app-id**. If not, enter the [secret name](#suggest) you defined. | app-id |
| Secret that contains the Application secret               | If you used the suggested name, enter **app-secret**. If not, enter the [secret name](#suggest) you defined. | app-secret |

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com) and go to your environment.
1. On the **Environment** page, select the **Environment add-ins** tab. If **Export Data Lake** appears in the list, the Data Lake add-in is already installed, and you can skip the rest of this procedure. Otherwise, complete the remaining steps.
1. Select **Install a new add-in**, and in the dialog box, select **Export to Data lake**. If **Export to data lake** isn't listed, the feature might not be available for your environment at this time.
1. In the **Setup add-in** dialog box, enter the required information. To answer the questions, you must already have a storage account. If you don't already have a storage account, create one, or ask your admin to create one on your behalf.
1. Accept the terms of the offer by selecting the check box, and then select **Install**.

The system installs and configures the data lake for the environment. This operation might take a few minutes. After installation and configuration are completed, **Export to Data Lake** appears on the **Environment** page, and the status is **Installed**. If a different status is shown, see the "Troubleshooting" section that follows.

## <a name="troubleshooting"></a> Troubleshooting

### Add-in installation isn't completed within a few minutes

In some cases, add-in installation might show a status of **Installing** or **Configuring** for more than 10 minutes. The cause of the delay might be a configuration issue or a missing parameter. In this case, select the **Abort** option, and then follow the steps to [install the add-in](#installaddin) again. 

### Add-in installation fails

In some cases, add-in installation might show a status of **Installation failed**. When installation fails, an error code and error message appear. The "Resolution" column in the following table provides suggestions that can help you correct the reason for the failure. To correct the issue, select the **Abort** option, and then follow steps to [install the add-in](#installaddin) again.

| Error code and message | Resolution |
|------------------------|------------|
| **AppidUserError**: Failed to find Application ID to access the data lake. Application ID provided is incorrect or can't be found. | The application ID (**app-id**) that you provide in the key vault can't be found in Microsoft Entra ID. Validate the application ID by following the steps in [Configure export to Azure Data Lake - Create Application](#createapplication). You might need to contact the system administrator or the administrator who configured Azure resources. |
| **AppSecretUserError**: Failed to access data lake with given Application ID and Application secret. | The application ID (**app-id**) and application secret (**app-secret**) that you provide can't be used to access the storage account. Validate the application ID and application secret by following the steps in [Configure export to Azure Data Lake - Create Application](#createapplication). Next, verify that the application has the required access to the storage account. For more information, see [Configure export to Azure Data Lake - Grant access](#grantaccess). You might need to contact the system administrator or the administrator who configured Azure resources. |
| **StorageNameUserError**: Failed to access the storage account using the storage name provided in the key vault. | The storage account that you provide in the key vault can't be found, or it isn't valid. Verify that the correct storage account name is entered in the key vault by following the steps in [Configure export to Azure Data Lake - Add secrets](#addsecrets). Verify that you provided the correct secret name for the storage account by following the steps in [Configure export to Azure Data Lake Add secrets](#addsecrets). |
| **KeyVaultUserError**: Failed to access the key vault or the key vault secrets. | The service can't access the key vault or the secrets in it. Verify that your Azure subscription hasn't expired. Verify that you created the service principal by following the steps in [Configure export to Azure Data Lake - Create service principal](#createServicePrincipal). Verify that the key vault contains all the required secrets by following the steps in [Configure export to Azure Data Lake - Add secrets](#addsecrets). Verify that you provided the correct key vault URI in the configuration steps in [Configure export to Azure Data Lake - Install add-in](#installaddin). Also ensure you have granted Get Key permissions as per [Authorize the application to read secrets in the key vault](#authorize).
| **TenantIdUserError**: Failed to locate the Azure Tenant ID for the environment. | Verify that you provided the correct Azure tenant ID by following the steps in [Configure export to Azure Data Lake - Install add-in](#installaddin). |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
