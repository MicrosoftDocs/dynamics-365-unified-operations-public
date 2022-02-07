---
# required metadata

title: Customer certificates and secrets
description: This topic provides description of customer's certificates and secrets setup in Electronic Invoicing.
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
ms.custom: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Customer certificates and secrets

[!include [banner](../includes/banner.md)]


If you already have a Key Vault reference in the Regulatory Configuration Service (RCS), you can create references to the Azure Key Vault Certificates and Secrets. If you haven't created a Key Vault reference, see the topic, [Service environments](e-invoicing-service-environments.md).

To create and set up certificates and secrets, complete the following steps.

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing** tile.
3. On the **Environment setup** page, on the Action Pane, select **Service environments**.
4. On the **Service environments** page, on the Action Pane, select **Key Vault parameters**.
5. Select a Key Vault reference, and in the **Certificates** section, select **Add**
6. In the **Name** field, enter the name of the Azure Key Vault Certificate or Secret name. For more information, see [Create an Azure storage account in Azure portal](e-invoicing-create-azure-storage-account-azure-portal.md).
7. In the **Description** field, enter a description.
8. In the **Type** field, select **Certificate** if you refer to the Certificate stored in the Key Vault. Select **Secret** if you refer to the Secret stored in the Key Vault
9. Select **Save**

  > [!NOTE]
  > In some scenarios you have to use public certificates that have the extension ".cer". The Azure Key Vault doesn't support import and storage of this certificate typeas the Key Vault Certificate. In this case, save the ".cer" file as a Base-64 encoded X.509 (.CER) string and store the string from the file that is between lines **BEGIN CERTIFICATE** and **END CERTIFICATE** in the Azure Key Vault Secret. In the service environment, create a reference to the Key Vault record with the type, **Certificate**.


## Create a chain of certificates

If your country/region-specific invoices require a chain of certificates to apply digital signatures or establish secure connection (SSL) to external web services, create a chain of certificates. The certificate chain order consists of root certificates, intermediate certificates, and the end-user certificate. Root CAs are a trusted source of certificates. Intermediate CAs are bridges that link the end-user certificate to the root CA.

1. On the **Key vault parameters** page, on the Action Pane, select **Chain of certificates**.
2. Select **New**, and in the **Name** field, enter the name of the chain of certificate. 
3. In the **Description** field, enter a description.
4. In the **Certificates** section, select **Add** to add a certificate to the chain.
5. Use the **Up** or **Down** button to change the position of the certificate in the chain. Keep the order where the CA root certificate is on top, and the end-user certificate is in the bottom of the list.
6. Select **Save**

You can create as many Key Vault references in RCS as you want. Keep in mind that a particular Service environment will be linked to the Key Vault reference based on the Storage SAS token secret. You can refer to the Azure Key Vault Certificates and Secrets stored in the Key Vault that also contains Storage SAS token secret you use during the Service environment setup.
