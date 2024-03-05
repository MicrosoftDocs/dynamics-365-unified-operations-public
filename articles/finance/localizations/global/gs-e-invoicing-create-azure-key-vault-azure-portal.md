---
title: Create an Azure key vault in the Azure portal (preview)
description: This article explains how to create a Microsoft Azure key vault for Electronic invoicing (preview).
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

# Create an Azure key vault in the Azure portal (preview)

[!INCLUDE[banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

All the secrets and certificates that are used in the Electronic Invoicing service must be stored in a Microsoft Azure key vault. This approach helps ensure that you don't work directly with the secrets, and that the secrets are securely stored. When you must use digital signing or secure a connection to external web services, set the reference to the Key Vault secrets and certificates instead of using the secrets and certificates directly.

1. Create a key vault in the tenant where Regulatory Configuration Service (RCS) is installed. For more information, see [Create a key vault using the Azure portal](/azure/key-vault/general/quick-create-portal).

    Next, you must set up the access policy to grant the Electronic Invoicing service the correct level of secure access to the secret that you created.

1. Go to **Settings** \> **Access policies**, and select **Add Access Policy**.
1. In the **Secret permissions** field, select the **Get** and **List** operations.

    :::image type="content" source="../media/add-access-policy-page.png" alt-text="Screenshot that shows secret permissions set for the Get and List operations on the Add access policy page.":::

1. In the **Certificate permissions** field, select the **Get** and **List** operations.
1. In the **Select principal** field, select **None selected**.
1. In the **Principal** dialog box, select the principal by adding **e-Invoicing Service**.

    > [!NOTE]
    > If **e-Invoicing Service** isn't in the list of principals in your tenant, run the following command in the Azure portal.
    >
    > `New-AzureADServicePrincipal -AppId "ecd93392-c922-4f48-9ddf-10741e4a9b65"`

1. Select **Add**, and then select **Save**.
1. On the **Overview** page, copy the value of the Domain Name System (DNS) name for the key vault. This value will be used during the setup of the service in RCS and will be referred to as the **Key Vault URI** value. For more information about how to set up RCS, see [Set up Regulatory Configuration Services (RCS)](e-invoicing-set-up-rcs.md).
