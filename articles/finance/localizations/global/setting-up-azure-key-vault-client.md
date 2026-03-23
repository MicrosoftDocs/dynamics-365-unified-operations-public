---
title: Set up the Azure Key Vault client
description: Learn about storing advanced certificates and defining the certificate storage type, including overviews on local storage and Azure Key Vault storage.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.search.validFrom: 2019-06-01
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Set up the Azure Key Vault client

[!include [banner](../../includes/banner.md)]

The functionality for storing advanced certificates lets you define the type of certificate storage that finance and operations apps use.

This functionality provides two options for storing certificates: local storage and Microsoft Azure Key Vault storage. You can define the option by setting the new **Use advanced certificate store** option on the **General** tab of the **System parameters** page (**System administration** \> **Setup** \> **System parameters**).

- **Local storage** – Use this storage option with on-premises deployments and any kind of on-premises development environment. Set the **Use advanced certificate store** option to **No** to use it. Use this storage option for development environments that are used for development and validation purposes, where you need to validate the certificate and work with it.
- **Azure Key Vault storage** – Use this storage option for cloud deployments, but you can also use it with on-premises deployed environments and any kind of on-premises development environment. Set the **Use advanced certificate store** option to **Yes** to use it. This storage option is the only option for a production environment in the Azure cloud.

:::image type="content" source="../media/1_System_parameters.jpg" alt-text="Screenshot of the System parameters page, General tab.":::

Before you can work with certificates that are stored in Key Vault, you need to complete some setup. For information about the required settings, see the following Microsoft Knowledge Base (KB) article: [4040294 - Maintaining Azure Key Vault storage](https://support.microsoft.com/en-us/help/4040294/maintaining-azure-key-vault-storage). After you set up the Key Vault storage, link to the certificates in finance and operations apps.

After you install the certificate in Key Vault, set it up in the application.

1. Go to **System administration** \> **Setup** \> **Key Vault parameters**.
2. Select **New** to create a new instance.
3. Enter a name and description. On the **General** FastTab, set the fields that are required for the integration with Key Vault storage:

- **Key Vault URL** – Enter the default Key Vault URL if the secret reference doesn't already define it.
- **Key Vault client** – Enter the interactive client ID of the Microsoft Entra application that is associated with the Key Vault storage for authentication.
- **Key Vault secret key** – Enter the secret key that is associated with the Microsoft Entra application that is used for authentication with the Key Vault storage.

   > [!NOTE]
   > If you use several Key Vault storages, set up a separate instance for each instance on the **Key Vault parameters** page.

1. On the **Certificates** FastTab, select **Add** to add your certificates. For each certificate, set the following fields:

- **Name**
- **Description**
- **Key Vault certificate secret** – Enter a secret reference to the certificate.

The format of a Key Vault certificate secret must resemble the following example:

vault://\<KeyVaultName\*\>/\<SecretName\>/\<SecretVersion\*\>

Attributes that are marked with an asterisk (\*) are optional. However, the **\<SecretName\>** attribute is required. In most cases, you can define a Key Vault secret key in the following format:

vault:///\<SecretName\>

If you don't define the secret version in the Key Vault secret key, the system retrieves the active certificate that has the latest expiration date.

:::image type="content" source="../media/2_Key_Vault_parameters.jpg" alt-text="Screenshot of the Key vault parameters page.":::

   > [!NOTE]
   > The Key Vault storage functionality has been extended so that it includes caching of certificates. Use the following configuration recommendations:

- Specify a secret version in the Key Vault certificate secret.
> - Specify a secret version in the Key Vault certificate secret.

Use the **Validate** function to verify that you've correctly defined the reference to the certificate, and that the certificate is valid.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
