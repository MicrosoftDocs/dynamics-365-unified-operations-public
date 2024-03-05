---
title: Create an Azure storage account in the Azure portal (preview)
description: This article explains how to create a Microsoft Azure storage account for Electronic invoicing (preview).
author: ilikond
ms.date: 01/29/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: 
ms.author: ikondratenko
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Create an Azure storage account in the Azure portal (preview)

[!INCLUDE[banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

All electronic files that the Electronic Invoicing service generates or that go to the service during processing are stored in containers in your Microsoft Azure storage account. To ensure that Electronic invoicing can access those containers, you must provide the shared access signature (SAS) token of the storage account to the Electronic Invoicing service. Additionally, to ensure that the token is securely stored, don't provide the SAS token directly. Instead, store it in an Azure key vault, and provide a Key Vault secret.

1. Open the storage account that you plan to use with the Electronic Invoicing service.
1. Go to **Settings** \> **Configuration**, and make sure that the **Allow Blob public access** parameter is set to **Enabled**.
1. Go to **Data storage** \> **Containers**, and create a container.
1. Enter a name for the container, and set the **Public access level** field to **Private (no anonymous access)**.
1. Open the new container, and go to **Settings** \> **Access policy**.
1. Select **Add policy** to add a stored access policy.
1. Set the **Identifier** field as appropriate.
1. In the **Permissions** field, select all permissions.

    ![Screenshot that shows all permissions selected in the Permissions field in the Add policy dialog box.](../media/e-invoicing-azure-1.png)

1. Enter the start and end dates. The end date should be in the future.
1. Select **OK** to save the policy, and then save your changes to the container.
1. Go to **Settings** \> **Shared access tokens**, and set the field values.
1. Enter the start and end dates. The end date should be in the future.
1. In the **Permissions** field, select the following permissions:

    - Read
    - Add
    - Create
    - Write
    - Delete
    - List

1. Select **Generate SAS token and URL**.
1. Copy and store the value of the **Blob SAS URL** field. This value will be used later in this procedure and will be referred to as the *shared access signature URI*.
1. Open the key vault that you intend to use with Electronic invoicing.
1. Go to **Settings** \> **Secrets**, and select **Generate/Import** to create a secret.
1. On the **Create a secret** page, in the **Upload options** field, select **Manual**.
1. Enter the name of the secret. This name will be used during the setup of the service in Regulatory Configuration Service (RCS) and will be referred to as the *key vault secret name*. For more information about how to set up RCS, see [Set up Regulatory Configuration Service (RCS)](e-invoicing-set-up-rcs.md).
1. In the **Value** field, enter the shared access signature URI that you copied earlier.
1. Select **Create**.
