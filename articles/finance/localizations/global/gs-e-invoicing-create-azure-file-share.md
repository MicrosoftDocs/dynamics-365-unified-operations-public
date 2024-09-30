---
title: Create an Azure file share in the Azure portal
description: Learn how to create a Microsoft Azure file share for Electronic invoicing, including how to store the connection string in Azure Key Vault.
author: achansoriya
ms.author: achansoriya
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 09/18/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 09/18/2024
ms.dyn365.ops.version: 10.0.39
---

# Create an Azure file share in the Azure portal

[!include [banner](../../includes/banner.md)]

Electronic documents that the Electronic Invoicing service generates can be stored in a Microsoft Azure file share that is provisioned under a storage account. To ensure that Electronic invoicing can access the file share, you must provide the connection string to the Electronic Invoicing service. In addition, to ensure that the connection string is securely stored, don't provide it directly. Instead, store it in an Azure key vault, and provide an Azure Key Vault secret.

## Prerequisites

Before you begin the procedures in this article, provision an Azure storage account. Learn more in [Configure an Azure storage account in the Azure portal](../global/gs-e-invoicing-create-azure-storage-account-azure-portal.md).

## Create an Azure file share

To create an Azure file share, follow these steps.

1. Select the storage account from your dashboard.
1. On the service menu, under **Data storage**, select **File shares**.

    ![Screenshot that shows File shares on the service menu.](../media/create-file-share.png)

1. At the top of the **File shares** page, select **File share**.
1. On the **New file share** page, in the **Name** field, enter a name for the new file share.

    > [!NOTE]
    > File share names can contain only lowercase letters, numbers, and hyphens. However, they can't contain two or more consecutive hyphens. In addition, they must begin and end with either a lowercase letter or a number.

1. To create the Azure file share, select **Review + create**, and then select **Create**.

To get the connection string, follow these steps.

1. Go to the [Azure portal](https://portal.azure.com/) with your subscription, and find the corresponding Storage account resource.
1. Go to **Security + Networking** \> **Access keys**
1. Under **key1**, copy the value in the **Connection string** field.

    ![Screenshot that shows Azure file share connection strings.](../media/azure-file-share-connection-string.png)

1. Store the **Connection string** value in a Key Vault secret. Learn how to set up Key Vault in [Configure an Azure key vault in the Azure portal](../global/gs-e-invoicing-create-azure-key-vault-azure-portal.md).
1. Refer to the Key Vault secret in Key Vault parameters. Learn more in [Configure Electronic invoicing parameters](../global/gs-e-invoicing-set-up-parameters.md).

> [!IMPORTANT]
> Don't confuse the **Connection string** value with the **Storage shared access signature (SAS)** token.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
