---
title: Customer certificates and secrets
description: This article explains how to set up customer certificates and secrets in Electronic invoicing.
author: gionoder
ms.date: 03/06/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Customer certificates and secrets

[!include [banner](../includes/banner.md)]

If you already have a Microsoft Azure Key Vault reference in Regulatory Configuration Service (RCS), you can create references to the Key Vault certificates and secrets. If you don't yet have a Key Vault reference, see [Service environments](e-invoicing-service-environments.md) for information about how to create it.

## Create certificates and secrets

To create and set up certificates and secrets, follow these steps.

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing** tile.
3. On the **Environment setup** page, on the Action Pane, select **Service environments**.
4. On the **Service environments** page, on the Action Pane, select **Key Vault parameters**.
5. On the **Key Vault parameters** page, select a Key Vault reference, and then, in the **Certificates** section, select **Add**.
6. In the **Name** field, enter the name of the Key Vault certificate or secret. For more information, see [Create an Azure storage account in the Azure portal](e-invoicing-create-azure-storage-account-azure-portal.md).
7. In the **Description** field, enter a description.
8. In the **Type** field, select **Certificate** if you're referencing the certificate that is stored in the key vault. Select **Secret** if you're referencing the secret that is stored in the key vault.
9. Select **Save**.

    > [!NOTE]
    > In some scenarios, you must use public certificates that have the .cer file name extension. However, Key Vault doesn't support importing and storing certificates of this type as Key Vault certificates. In these scenarios, you should save the .cer file as a Base-64-encoded X.509 (.CER) string. Then, in a Key Vault secret, store the string that appears between the **BEGIN CERTIFICATE** line and the **END CERTIFICATE** line in the file. In the service environment, you should still create a reference to the Key Vault record and set the **Type** field to **Certificate**.

10. As an alternative to the approach that's described in the preceding note, use the following PowerShell script to generate a Base-64 string of the .cer certificate file.

    ```powershell
    $FilePath = ''
    $Cer = New-Object -TypeName System.Security.Cryptography.X509Certificates.X509Certificate2($FilePath)
    $BinCert = $Cer.GetRawCertData()
    $Base64Cert = [System.Convert]::ToBase64String($BinCert)
    echo $Base64Cert
    ```

## Create a chain of certificates

If your country/region-specific invoices require a chain of certificates to apply digital signatures or establish a secure (Secure Sockets Layer \[SSL\]) connection to external web services, create a chain of certificates where the certificates are in the following order:

1. Root certificates
2. Intermediate certificates
3. End-user certificates

Root certificate authorities (CAs) are a trusted source of certificates. Intermediate CA certificates are bridges that link the end-user certificates to the root CA certificates.

To create and set up a chain of certificates, follow these steps.

1. On the **Key Vault parameters** page, on the Action Pane, select **Chain of certificates**.
2. Select **New** to create a chain of certificates.
3. In the **Name** field, enter the name of the chain of certificates.
4. In the **Description** field, enter a description.
5. In the **Certificates** section, select **Add** to add a certificate to the chain.
6. Use the **Up** or **Down** button to change the position of the certificate in the chain. Keep the CA root certificate at the top of the list and the end-user certificate at the bottom.
7. Select **Save**.

You can create as many Key Vault references in RCS as you want. Remember that the secret for the storage shared access signature (SAS) token is used to link a given service environment to the Key Vault reference. You can reference the Key Vault certificates and secrets that are stored in a key vault that also contains the secret for the storage SAS token that you use when you set up the service environment.
