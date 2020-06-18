---
# required metadata

title: Configure export to Azure Data Lake
description: This topic provides information about configuring the export to Azure Data Lake.
author: MilindaV2
manager: AnnBe
ms.date: 05/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations

# ms.tgt_pltfrm: 
ms.custom: 96283
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2020-03-03
ms.dyn365.ops.version: Platform Update 33

---

# Configure export to Azure Data Lake

[!include [banner](../includes/banner.md)]

> [!NOTE]
> The **Export to Azure Data Lake** feature may not be available in all regions and environments supported by Microsoft Dynamics 365 Finance and Operations apps. If you are not able to find the **Export to Azure Data Lake** functionality in Life cycle services (LCS) or your Finance and Operations apps, this feature is not currently available in your environment. If you would like access to this feature, send an email to the feature team at **FnODataLakePreview@service.microsoft.com**. We will try and make this feature available soon. At this time, the **Export to Azure Data Lake** feature is not available in Tier-1 (developer) environments. You need a cloud based Tier-2 or higher environment to enable this feature.
> To make aggregate measurements available in a data lake, continue to use the feature in the manner that is described in the topic, [Make entity store available as a Data Lake](entity-store-data-lake.md).

To configure the export to Data Lake, you must create a storage account in your own Azure subscription. This storage account will be used to store data. Next, you must create an Azure Active Directory (Azure AD) application ID that grants access to the root of your storage account. Your Dynamics 365 Finance or Operations app will use the Azure AD application to gain access to storage, create the folder structure, and write data. Create a key vault in your subscription and store the names of the storage account, application ID, and the application secrets. If you don't have permission to create resources in Azure portal, you will need assistance from someone in your organization with required permissions.

The steps, which take place in the Azure portal, are as follows: 

1. [Create a Data Lake Storage (Gen2 account) in your subscription](#createsubscription)
2. [Create a key vault and a secret that contain the storage account](#createkeyvault)
3. [Create an application in Azure Active Directory](#createapplication) 
4. [Add secrets to the key vault](#addsecrets)
5. [Authorize the application to read secrets in the key vault](#authorize)
6. [Grant access control roles to applications](#grantaccess)

    > [!NOTE]
    > When you are working in the Azure portal, you will be instructed to save several values for subsequent steps. You will also provide some of these values to your Finance and Operations apps by using Lifecycle Services (LCS). You will need Administrator access to LCS in order to do this.

7. [Install the Export to Data Lake add-in in LCS](#installaddin)

## <a name="createsubscription"></a>Create a Data Lake Storage (Gen2) account in your subscription

The Data Lake Storage account will be used to store data from your Finance and Operations apps. To manually create a storage account, you must have administrative rights to your organization's Azure subscription. To create a storage account, complete the following steps.

1. In the Azure portal, select **Create new resource**, and then search for and select **Storage account – blob, file, table, queue**.
2. In the **Create storage account** dialog box, provide values for the following parameter fields:

    - **Location:** Select the data center where your environment is located. If the data center that you select is in a different Azure region, you may incur additional data movement costs. If your Microsoft Power BI or your data warehouse is in a different region, you can use replication to move storage between regions.
    - **Performance**: We recommend you select **Standard**.
    - **Account kind**: You must select **StorageV2**. In the **Advanced options** dialog box, you will see the option, **Data Lake storage Gen2**.

3. On the **Advanced tab**, select **Data Lake storage Gen2** \> **Hierarchical namespaces**, and then select **Enabled**. If you disable this option, you may not be able to consume data that is written by Finance and Operations apps with services such as Power BI data flows and AI builder.
4. Select **Review and create**. When the deployment is complete, the new resource will be shown in the Azure portal.
5. Copy and keep the following information from the storage account that you created:

    i. In the Azure portal, select the storage account you created. Copy and save the <a name="storageaccount"></a>storage account name.
    
    ii. On the left navigation pane, select **Settings** \> **Access keys**, and copy the **Connection string** from Key 1 or Key 2.
        

## <a name="createkeyvault"></a>Create a key vault and a secret that contains the storage account

A key vault is a secure way to share details such as storage account name to your Finance and Operations apps. Complete the following steps to create a key vault and a secret.

1. In the Azure portal, select **Create a new resource** and then search for and select, **Key Vault**.
2. In the **Create key vault** dialog box, in the **Location** field, select the datacenter where your environment is located.
3. After the key vault is created, select it from the list, and on the left navigation pane, select **Overview**. 
4. Save the value in the <a name="dnsname"></a>**DNS name** field. You will need this value later.
5. In the left navigation pane, select **Secrets** > **Generate/Import**.
6. In the **Create a secret** dialog box, in the **Upload options** field, select **Manual**.
7. Enter a name for the secret, for example **storage-account-name**. Make a note of the name because you will have to provide it later.
8. In the **Value** field, enter the storage account name that you obtained in the previous procedure.
9. Select **Enabled**, and then select **Create**. The secret is created and added to the key vault.

## <a name="createapplication"></a>Create an application in Azure Active Directory

1. In the Azure portal, select **Azure Active Directory**, and then select **App registrations**.
2. Select **New registration**, and enter the following information: 

    -  **Name:** Enter a name for the app.
    -   **Supported Account types**: Choose the appropriate option.

3. After the application is created, select it and then copy and save the <a name="appid"></a>Application (client) ID at the top of the page. You will need this later.
4. On the left navigation pane, select **API permissions**.
5. Select **Add a permission**, and in the **Request API permissions** dialog box, select **Azure Key vault**.
6. Select **Delegated permissions**, select **user_impersonation**, and then select **Add permissions**.
7. On the left navigation pane, select **Certificates & secrets**, and then select **New client secret**. 
8. In the **Description** field, enter a name.
9. In the **Expires** field, select an option, and then select **Add**. The system will generate a secret. Immediately copy the secret to the clipboard, as it will disappear within one or two minutes. You will have to <a name="secret"></a>provide this secret value when you set up the key vault later.

## <a name="addsecrets"></a>Add secrets to the key vault

You are going to create three secrets in the Key vault and then add the values saved from previous steps. For each of the secrets, you will need to provide a secret name and provide the value you saved from earlier steps.

| <a name="suggest"></a>**Suggested secret name** | **Secret value (what you saved earlier)**                                |
|---------------------------|---------------------------------------------------------------------------|
| app-id                    | The ID of the application [created earlier](#appid).                             |
| app-secret                | The [client secret](#secret) specified earlier.                                 |
| storage-account-name      | The name of the [storage account](#storageaccount) created earlier. |

You will need to complete the following steps three times, once for each secret.

1. In the Azure portal, go to the key vault you created earlier and on the left navigation pane, select **Secrets**.
2. Select **Generate/Import**, and in the **Create a secret** dialog box, in the **Upload options** field, select **Manual**.
3. Enter a name for the secret. See the table in the introduction of this section for suggested names.
4. Copy and paste the corresponding secret value in the **Value** field.
6. Select **Enabled**, and then select **Create**. 

You will notice the secret created in the list of secrets.

## <a name="authorize"></a>Authorize the application to read secrets in the key vault

1. In **Azure portal**, open the key vault that you created earlier.
2. On the left navigation page, select **Access policies > Add Access Policy** to create a new policy. 
3. On the **Add access policy** dialog, in the **Select principal** field, search for the [name of the application](#appid) you created earlier.
4. When you find your application in the list of principals, select the application, and then click **Select**.
5. In the **Key permissions** and **Secret permissions** fields, select **Get** and **List**.  
6. In the **Add access policy** dialog box, select **Add**.
7. On the left navigation pane, select **Access policies > Add Access Policy** to create a new policy. 
8. On the **Add access policy** dialog, in the **Select principal** field, locate and select the application, **Microsoft Dynamics ERP Microservices**, and then click **Select**. 

> [!NOTE]
> If you can't find **Microsoft Dynamics ERP Microservices**, see the [troubleshooting section](#troubleshooting) at the end of this document.

9. In the **Key permissions**  and **Secret permissions** fields, select **Get** and **List**.  
10. In the **Access policy** dialog, select **Add**.

You should see two applications with access to your key vault as shown below.

| Application                                                   | Key permissions | Secret permissions |
|---------------------------------------------------------------|-----------------|--------------------|
| Display name of the [new application](#appid) you created  | Get, List       | Get, List          |
| Microsoft Dynamics ERP Microservices                          | Get, List       | Get, List          |

11.  Select **Save**.

## <a name="grantaccess"></a>Grant access control roles to applications 

You need to grant your application permissions to read and write to the storage account. These permissions are granted by using Roles in Azure AD.

1. In **Azure portal**, open the storage account that you created earlier.
2. Select **Access Control (IAM)** in the left navigation. 
3. On the **Access control** page, select the **Role assignments** tab.
4. Select **Add** at the top of the page, and then select **Add role assignment**.
5. In the **Add role assignment** dialog, select the **Role** field, and then select **Owner**.

> [!NOTE]
> Don't make any changes to the fields, **Assign access to** and **Azure AD user, group, or service principal**.

6. In the **Select** field, select the application that you registered earlier.
7. Select **Save**
8. Add the remaining roles shown in the following table by repeating steps 4 - 7.

|   Application to be selected     |     Role to be assigned     |
|----------------------------------|-----------------------------|
| [Your application](#appid) you created earlier | Owner                       |
| [Your application](#appid) you created earlier | Contributor                 |
| [Your application](#appid) you created earlier | Storage account contributor |
| [Your application](#appid) you created earlier | Storage blob data owner     |
| AI builder authorization service | Storage blob data reader    |

## <a name="installaddin"></a>Install the Export to Data Lake add-in in LCS 

Before you can export data to your Data lake from your Finance and Operations apps, you must install the **Export to Data Lake** add-in in LCS. To complete this task, you must be an environment administrator in LCS for the environment that you want to use.

You need the following information before you start. Keep the information handy before you begin.

| **Information you need for Export to Data lake add-in**   | **Where can you find it**                                                                                                                                                                                                |
|-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Your environment Azure AD Tenant ID                            | Your Azure AD tenant ID in the Azure portal. Sign in to the **Azure portal** and open the **Azure Active Directory** service. Open the **Properties** page and copy the value in the **Directory ID** field. |
| DNS name of your key vault                                | This name should have been previously saved. Enter the [DNS name](#dnsname) of your key vault                                                                                                               |
| The secret that contains the name of your storage account |  If you used the suggested name, enter **storage-account-name**. If not, enter the [secret name](#suggest) you defined.                                                                                                                                                                                                                         |
| Secret that contains the Application ID                   |  If you used the suggested name, enter **app-id**. If not, enter the [secret name](#suggest) you defined.                                                                                       |
| Secret that contains the Application secret               |  If you used the suggested name, enter **app-secret**. If not, enter the [secret name](#suggest) you defined.                                                                                             |

1.  Sign in to [LCS](https://lcs.dynamics.com) and navigate to your environment.
2.  On the **Environment** page, select the **Environment add-ins** tab. If **Export Data Lake** appears in the list, the Data Lake add-in is already installed, and you can skip the rest of this procedure. Otherwise, complete the remaining steps.
3.  Select **Install a new add-in**, and in the dialog box, select **Export to Data lake** in the list. If **Export to data lake** isn't listed, the feature might not be available for your environment at this time.
4.  In the **Setup add-in** dialog box, provide the required information. To answer the questions, you must already have a storage account. If you don't already have a storage account, create one, or ask your admin to create one on your behalf.
5.  Accept the terms of the offer by selecting the check box, and then select **Install**.

The system installs and configures the data lake for the environment. After installation and configuration are complete, you should see **Azure Data Lake** listed on the **Environment** page.

## <a name="troubleshooting"></a>Troubleshooting tips

### Can’t find Microsoft Dynamics ERP Microservices or AI Builder Authorization Service

You will need **Azure Active Directory tenant administrator** rights to perform these steps.

1. Launch the Azure portal and go to the Azure Active Directory.
2. On the left menu bar, select **Manage** \> **Enterprise Applications** and search for the following applications.

| **Application**                          | **App ID**                           |
|------------------------------------------|--------------------------------------|
| Microsoft Dynamics ERP Microservices     | 0cdb527f-a8d1-4bf8-9436-b352c68682b2 |
| Microsoft Dynamics ERP Microservices CDS | 703e2651-d3fc-48f5-942c-74274233dba8 |
| AI Builder Authorization Service         | ad40333e-9910-4b61-b281-e3aeeb8c3ef3 |


If you are unable to find any of the above applications, complete steps 3 - 7:

3. On your local machine, open the Start menu and search for **PowerShell**.
4. Right-click **Windows PowerShell** and select **Run as administrator**.
5. Run the following command to install **AzureAD** module:

     >   *Install-Module -Name AzureAD*

  - If NuGet provider is required to continue, select **Y** to install it.
  - If an **Untrusted repository** message appears, select **Y** to continue.

6. For each application that needs to be added, run the following commands to add the application to the Azure Active Directory.

    > Connect-AzureAD
    > New-AzureADServicePrincipal –AppId \<AppId\>

7. Sign in as the Azure Active Directory administrator when prompted.
