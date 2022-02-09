---
# required metadata

title: Service environments
description: This topic provides information about how to set up service environments for Electronic invoicing.
author: dkalyuzh
ms.date: 02/07/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Service environments
[!include [banner](../includes/banner.md)]


Service environments are logical partitions that are created to support the Globalization features and corresponding documents processed in the Electronic invoicing service. The security secrets and digital certificates, and the governance, or access permissions, must be configured at the service environment level.

You can create as many service environments as necessary. All the service environments that you create are independent of each other. As a best practice, we recommend that you create at least two service environments. One environment for main development and validation purposes. This environment is typically a UAT environment. The second environment is for production purposes and is usually a PROD environment.

Such partitioning helps ensure that the e-invoicing processes are validated and customized in the sandbox before they go to production.

Service environments must be created and maintained in RCS. When the service environments are ready, they must be published to Electronic invoicing service. The publishing process sends the service environment parameters from the RCS instance to the Electronic invoicing service.

If you don't complete the publishing step when you create a new service environment, or adjust an existing service environment, including adding or removing users or Key Vault secrets, the changes will not be effective. Only published environments can be accessed by Finance or Supply Chain Management.

Check the status of the environments publishing status in the **Service environments** list.


## Service environment status
Service environments can be managed through status. The possible options are:
    
  - **Not published**: The environment has been created, but it hasn't been published.
  - **Published**: The environment has been published to Electronic invoicing.
  - **Changed**: The attributes of a published environment have been changed, but the changes haven't been published.

## Users
Each service environment must list the users who can connect from Finance or Supply Chain Management to Electronic invoicing.

## Applications
In some scenarios, it's required that applications other than Finance or Supply Chain Management connect to the Electronic Invoicing service to submit electronic documents for further processing, or to retrieve information such as the submission status of a document.
In this situation, the application should be defined in the list of applications, providing an access to the Electronic Invoicing service.

This application must also be registered in Azure AD as an application, and the Object ID must be used to identify the application. 
Because Microsoft requires a high-level of security control over applications that can connect to the Electronic Invoicing service, contact Microsoft at  DGXRegulatoryservicesengineering@service.microsoft.com and provide the following parameters of your application:

- AAD TenantID
- LCS Environment ID
- Application ID (Client ID)
- Object ID
- Justification and a high-level description of the application

Microsoft will evaluate the request and register the application in the security register to make sure it can operate with Electronic invoices.

## Number sequences
If your scenarios require number sequences, use number sequences that not only defined for the particular environment, but can be used across Globalization features, or per Globalization feature. After the number sequence is defined, you can use it in **Variables** and **Processing pipelines**.

You can watch its usage by parameter **In use** and **Current** value.

To create and set up service environments and the corresponding parameters, complete the following steps.

1. Sign in to your RCS account and in the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing** tile.
2. On the **Environment setup** page, on the Action Pane, select **Service environments**.
3. Select **Key Vault parameters** and then select **New** to create a Key Vault reference.
4. In the **Name** field, enter the name of the Key Vault reference and in the **Description** field, enter a description.
5. In the **Key Vault URI** field, paste the Key Vault URI (`https://<<yourkeyvault>>.vault.azure.net/`) from the Azure Key Vault. For more information, see [Create Azure Key Vault in Azure portal](e-invoicing-create-azure-key-vault-azure-portal.md).
6. Select **Save**.
	
## Create secret for Storage account signature (SAS) token
1. Select a Key Vault reference and in the **Certificates** section, select **Add**.
2. In the **Name** field, enter the name of the storage account secret. This name should be the same as the Azure Key Vault Secret name with SAS token. For more information, see [Create Azure storage account in Azure portal](e-inv_tut-setup-electronic-invoicing_azure_create-storage.md). 
3. In the **Description** field, enter a description.
4. In the **Type** field, select **Secret**.
5. Select **Save**.
	
## Create a service environment
1. Select **New** to create a new service environment.
2. In the **Name** field, enter the name of the Electronic Invoicing environment and in the **Description** field, enter a description.
3. In the **Storage SAS token secret** field, select the name of the storage account secret that must be used to authenticate access to the storage account.
4. In the **Users** section, select **Add** to add a user who is allowed to submit electronic invoices through the environment and also connect to the storage account.
5. In the **User ID** field, enter the alias of the user. 
6. In the **Email** field, enter the user's email address and then select **Save**.
7. On the Action Pane, select **Publish** to publish the environment to the Electronic invoicing service. Verify that the value of the **Status** field is changed to **Published**.

## Work with number sequences
- Select **New** to create a new number sequence and enter a name and description. 
- Select **Delete** to delete a number sequence if it's no longer being used.
- You don't need to select **Publish** on the Action Pane to publish the changes to a number sequence. The update is done automatically.
