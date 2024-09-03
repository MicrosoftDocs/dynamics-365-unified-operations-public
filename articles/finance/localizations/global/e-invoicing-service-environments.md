---
title: Service environments
description: Learn about service environments for Electronic invoicing and explains how to set them up, including an outline on service environment statuses.
author: ilikond
ms.author: ikondratenko
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 06/17/2024 
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version:
---

# Service environments

[!include [banner](../../includes/banner.md)]

Service environments are logical partitions that are created to support the Globalization features and the corresponding documents that are processed in the Electronic Invoicing service. The security secrets and digital certificates, and the access permissions (governance), must be configured at the service environment level.

You can create as many service environments as you require. All the service environments that you create are independent of each other. As a best practice, we recommend that you create at least two service environments:

- One environment for main development and validation purposes. This environment is typically a user acceptance testing (UAT) environment.
- One environment for production purposes. This environment is usually a production environment.

This type of partitioning helps ensure that the e-invoicing processes are validated and customized in the sandbox before they go to production.

Service environments must be created and maintained in Regulatory Configuration Service (RCS). Then, when they are ready, they must be published to the Electronic Invoicing service. The publishing process sends the parameters of the service environment from the RCS instance to the Electronic Invoicing service.

If you don't complete the publishing process after you create a new service environment or adjust an existing service environment (for example, by adding or removing users or Microsoft Azure Key Vault secrets), the changes won't be effective. Only published environments can be accessed by Dynamics 365 Finance or Dynamics 365 Supply Chain Management.

## Service environment statuses

Service environments can be managed through their status. You can view the status of an environment on the **Service environments** page. The following statuses are available:

- **Not published** – The environment has been created, but it hasn't yet been published.
- **Published** – The environment has been published to the Electronic Invoicing service.
- **Changed** – The attributes of a published environment have been changed, but the changes haven't yet been published.

## Users

Each service environment must list the users who can connect to Electronic invoicing from Finance or Supply Chain Management.

## Number sequences

If your scenarios require number sequences (for example, in file names), you can use number sequences that are defined for a specific environment, but that can be used either across Globalization features or for a specific Globalization feature. After a number sequence is defined, you can use it in variables and processing pipelines. To track its use, on the **Number sequences** page, look for a value of **Current** for the **In use** parameter.

### Working with number sequences
On the **Number sequences** page: 

- Select **New** to create a number sequence. Then enter a name and description. 
- Select **Delete** to delete a number sequence if it's no longer used.
- You don't have to select **Publish** on the Action Pane to publish the changes to a number sequence. The update is done automatically.

## Create a Key Vault reference

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing** tile.
3. On the **Environment setup** page, on the Action Pane, select **Service environments**.
4. On the **Service environments** page, on the Action Pane, select **Key Vault parameters**.
5. On the **Key Vault parameters** page, select **New** to create a Key Vault reference.
6. In the **Name** field, enter the name of the Key Vault reference.
7. In the **Description** field, enter a description.
8. In the **Key Vault URI** field, paste the Key Vault URI from the key vault (`https://<your key vault>.vault.azure.net/`). For more information, see [Create an Azure key vault in the Azure portal](e-invoicing-create-azure-key-vault-azure-portal.md).
9. Select **Save**.
	
## Create a secret for the storage account secret token

1. On the **Key Vault parameters** page, select the Key Vault reference that you created in the previous procedure, and then, in the **Certificates** section, select **Add**.
2. In the **Name** field, enter the name of the storage account secret. This name should match the name of the Key Vault secret that holds the storage shared access signature (SAS) token. For more information, see [Create an Azure storage account in the Azure portal](e-invoicing-create-azure-storage-account-azure-portal.md). 
3. In the **Description** field, enter a description.
4. In the **Type** field, select **Secret**.
5. Select **Save**.
	
## Create a service environment

1. On the **Service environments** page, select **New** to create a service environment.
2. In the **Name** field, enter the name of the Electronic invoicing environment.
3. In the **Description** field, enter a description.
4. In the **Storage SAS token secret** field, select the name of the storage account secret that must be used to authenticate access to the storage account.
5. In the **Users** section, select **Add** to add a user who is allowed to submit electronic invoices through the environment and connect to the storage account.
6. In the **User ID** field, enter the alias of the user. 
7. In the **Email** field, enter the user's email address.
8. Select **Save**.
9. On the Action Pane, select **Publish** to publish the environment to the Electronic Invoicing service. Verify that the value of the **Status** field is changed to **Published**.
