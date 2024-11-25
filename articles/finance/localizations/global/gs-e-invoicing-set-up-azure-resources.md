---
title: Configure Azure resources for Electronic invoicing
description: Learn about the process for setting up Microsoft Azure resources for Electronic invoicing, including an overview on creating an Azure key vault.
author: ilikond
ms.author: ikondratenko
ms.topic: overview
ms.date: 03/13/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39 
---

# Configure Azure resources for Electronic invoicing

[!INCLUDE[banner](../../includes/banner.md)]

The process for setting up Microsoft Azure resources for Electronic invoicing has three steps. The first two steps, "Create an Azure key vault in the Azure portal" and "Create an Azure storage account in the Azure portal," are mandatory. The third step, "Configure a SharePoint connection," is optional. These steps can be completed by using any of the following methods:

- Use the Azure portal user interface (UI).
- Run an Azure PowerShell script.
- Deploy an Azure Resource Manager (ARM) template.

If you prefer to use the Azure portal UI, continue with this article. If you prefer to use the PowerShell script or an ARM template, see [Create Azure resources using Azure PowerShell or ARM templates](e-invoicing-set-up-azure-resources-automation.md).

## Create an Azure key vault in the Azure portal

Create a key vault in your Azure subscription. We recommend that you create a separate key vault for Electronic invoicing, and that you don't combine secrets with other applications. Create as many secrets and certificates as you require for your scenarios for electronic documents. You must create at least one secret to store the shared access signature (SAS) token of the Azure storage account that you create in the next step.

For information about how to complete this step, see [Create an Azure key vault in the Azure portal](gs-e-invoicing-create-azure-key-vault-azure-portal.md).

## Create an Azure storage account in the Azure portal

You own all the electronic documents and files that the Electronic Invoicing service generates or that enter the service. Those documents and files are stored in an Azure storage account that you create in your Azure subscription. The service will access your storage account by using the SAS token that's taken from your Key Vault secret.

For information about how to complete this step, see [Create an Azure storage account in the Azure portal](gs-e-invoicing-create-azure-storage-account-azure-portal.md).

## Configure a SharePoint connection

In some scenarios, you might have to save electronic files to SharePoint and retrieve them from SharePoint. To ensure that the Electronic Invoicing service can access your SharePoint folders, configure access to SharePoint.

For information about how to complete this step, see [Configure a SharePoint connection](gs-e-invoicing-create-sharepoint-connection.md).
