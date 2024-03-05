---
title: Configure Azure resources for Electronic invoicing (preview)
description: This article provides an overview of the process for setting up Microsoft Azure resources for Electronic invoicing (preview).
author: ilikond
ms.date: 01/21/2022
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ikondratenko
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Configure Azure resources for Electronic invoicing (preview)

[!INCLUDE[banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The process of setting up Microsoft Azure resources for Electronic invoicing has three steps. The first two steps, "Create an Azure key vault in the Azure portal" and "Create an Azure storage account in the Azure portal," are mandatory. The third step, "Configure a SharePoint connection," is optional.

## Create an Azure key vault in the Azure portal

Create a key vault in your Azure subscription. We recommend that you create a separate key vault for Electronic invoicing, and that you don't combine secrets with other applications. Create as many secrets and certificates as you require for your scenarios for electronic documents. You must create at least one secret to store the shared access signature (SAS) token of the Azure storage account that you create in the next step.

For information about how to complete this step, see [Create an Azure key vault in the Azure portal](gs-e-invoicing-create-azure-key-vault-azure-portal.md).

## Create an Azure storage account in the Azure portal

You own all the electronic documents and files that the Electronic Invoicing service generates or that enter the service. Those documents and files are stored in an Azure storage account that you create in your Azure subscription. The service will access your storage account by using the SAS token that's taken from your Key Vault secret.

For information about how to complete this step, see [Create an Azure storage account in the Azure portal](gs-e-invoicing-create-azure-storage-account-azure-portal.md).

## Configure a SharePoint connection

In some scenarios, you might have to save electronic files to SharePoint and retrieve them from SharePoint. To ensure that the Electronic Invoicing service can access your SharePoint folders, configure access to SharePoint.

For information about how to complete this step, see [Configure a SharePoint connection](gs-e-invoicing-create-sharepoint-connection.md).
