---
# required metadata

title: Service environments
description: This topic provides description of Service environments setup for Electronic invoicing.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]


**Service environments** are logical partitions that are created to support execution of the Globalization features and corresponding documents processing in Electronic invoicing service. The security secrets and digital certificates, and the governance (that is, access permissions), must be configured at the **Service environment** level.

You can create as many service environments as you need. All the service environments that you create are independent of each other. As the best practice, Microsoft recommends you to create at least two service environments:
- For main development and validation purposes (usually it is UAT environment)
- For production processes (usually it is PROD environment)

Such partitioning will help you to make sure that e-invoicing processes are validated and customized in the sandbox before they go to production.

Service environments must be created and maintained in RCS. When the service environments are ready, they must be published to Electronic invoicing service. Publishing process assumes sending service environment parameters from RCS instance to Electronic invoicing service.

If you don't complete the publishing step when you create a new service environment, or adjust an existing service environment, that includes adding or removing users, or Key Vault secrets, the changes will not be effective. Only published environments can be accessed by Finance and Supply Chain Management.

You can check the status of the environments publishing status in the Service environments list


### Service environment status
Service environments can be managed through status. The possible options are:
- Not published: The environment has been created, but it hasn't yet been published.
- Published: The environment has been published to Electronic invoicing.
- Changed: The attributes of a published environment have been changed, but the changes haven't yet been published.

### Users
Each **Service environment** must list the users who can connect from Finance and Supply Chain Management to Electronic invoicing.

### Applications
In some scenarios it can be required that other applications than Finance and  Supply Chain Management should connect to Electronic Invoicing service to submit electronic documents for further processing, or retrieve information like documents submission status.
In this case such application should be defined in the list of applications, thus providing an access to Electronic Invoicing service.

This application must be registered in Azure AD as an application, and Object ID must be used for identification of the application. 
As Microsoft requires to keep high level of security control over applications that can connect to Electronic Invoicing service, you should also contact Microsoft DGXRegulatoryservicesengineering@service.microsoft.com and provide the following parameters of your application:
- AAD TenantID
- LCS Environment ID
- Application ID (Client ID)
- Object ID
- Justification and a high level description of the application

Microsoft will evaluate the request and register the application in the security register to make sure it can operate with Electronic invoice.

### Number sequences
In case your scenarios require any number sequences, like in file name, you can use number sequences that is defined for the particular environment, but can be used across Globalization features, or per Globalization feature. As soon as it is defined, you can use it in **Variables** and **Processing pipelines**.
![e-inv_tut-setup-electronic-invoicing_setup-env_service-env-2](https://user-images.githubusercontent.com/78973132/146502109-fcb66f5a-93d8-4050-b92c-f2ddc7511ae1.jpg)


You can watch its usage by parameter **In use** and **Current** value.


To create and setup Service environments and corresponding parameters, follow the instruction below.
1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing** tile.
3. On the **Environment setup** page, on the Action Pane, select **Service environments**.

## Create Key Vault references
1. Select **Key Vault parameters**.
2. Select **New** to create a Key Vault reference.
3. In the **Name** field, enter the name of the Key Vault reference. In the **Description** field, enter a description.
4. In the **Key Vault URI** field, paste the Key Vault URI (`https://<<yourkeyvault>>.vault.azure.net/`) from Azure Key Vault. For more information, see [Create Azure Key Vault in Azure portal](e-inv_tut-setup-electronic-invoicing_azure_create-keyvault.md).
5. Select **Save**.
	
## Create secret for Storage account signature (SAS) token
1. Select a Key Vault reference created in the previous steps and in the **Certificates** section, select **Add**.
2. In the **Name** field, enter the name of the storage account secret. This name should be the same as the Azure Key Vault Secret name with SAS token. For more information, see [Create Azure storage account in Azure portal](e-inv_tut-setup-electronic-invoicing_azure_create-storage.md). 
3. In the **Description** field, enter a description.
4. In the **Type** field, select **Secret**.
5. Select **Save**.
	
## Create a service environment
1. Select **New** to create a new Service environment.
2. In the **Name** field, enter the name of the Electronic Invoicing environment. In the **Description** field, enter a description.
3. In the **Storage SAS token secret** field, select the name of the storage account secret that must be used to authenticate access to the storage account.
4. In the **Users** section, select **Add** to add a user who is allowed to submit electronic invoices through the environment and also connect to the storage account.
5. In the **User ID** field, enter the alias of the user. In the **Email** field, enter the user's email address.
6. Select **Save**.
7. On the Action Pane, select **Publish** to publish the environment to the Electronic invoicing service. Check that the value of the Status field is changed to Published.

## Work with Number sequences
Select **New** button to create a new Number sequence, provide **Name** and **Description**. 
Select **Delete** button to delete Number sequence, if it is not used.
You dot need to select **Publish** on the Action Pane to publish the changes of Number sequences, as the update is done automatically.
