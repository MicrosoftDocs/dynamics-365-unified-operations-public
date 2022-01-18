---
# required metadata

title: Customer certificates and secrets
description: This topic provides description of customer's certificates and secrets setup in Electronic Invoicing.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]


If you already have a Key Vault reference in RCS you can create references to the Azure Key Vault Certificates and Secrets. If you haven't created a Key Vault reference, please follow the instruction in [Service environments](e-inv_tut-setup-electronic-invoicing_setup-env_service-env.md).

To create and setup certificates and secrets, follow the instruction below.
1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing** tile.
3. On the **Environment setup** page, on the Action Pane, select **Service environments**.


### Create a digital certificate or secret reference
1. On the Action pane in Service environments, select Key Vault parameters
2. Select a Key Vault reference created in the previous steps and in the **Certificates** section, select **Add**
3. In the **Name** field, enter the name of the Azure Key Vault Certificate or Secret name. For more information, see [Create an Azure storage account and a key vault](e-inv_tut-setup-electronic-invoicing_azure_create-storage.md).
4. In the **Description** field, enter any description
5. In the **Type** field, select **Certificate** if you refer to the Certificate stored in Key Vault, or Secret if you refer to the Secret stored in Key Vault
6. Select **Save**

> [!NOTE]
> In some scenarios you have to use public certificates that have extension ".cer". Azure Key Vault doesn't support importing and storing this type of certificates as Key Vault Certificate. In this case you should save ".cer" file as Base-64 encoded X.509 (.CER) string and store in Azure Kye Vault Secret the string from the file that is between lines BEGIN CERTIFICATE and END CERTIFICATE. In the service environment you should still create a reference to the Key Vault record with type Certificate.


## Create Chain of certificates

If your country/region-specific invoices require a chain of certificates to apply digital signatures or establish secure connection (SSL) to external web services, you should create a chain of certificates. The certificate chain order consists of root certificates, intermediate certificates, and the end-user certificate. Root CAs are a trusted source of certificates. Intermediate CAs are bridges that link the end-user certificate to the root CA.

1. On the Action pane in Key Vault parameters, select **Chain of certificates**.
2. Select **New** to create a chain of certificates.
3. In the **Name** field, enter the name of the chain of certificate. In the **Description** field, enter a description.
4. In the **Certificates** section, select **Add** to add a certificate to the chain.
5. Use the **Up** or **Down** button to change the position of the certificate in the chain. You should keep the order where CA root certificate is on top, and end-user certificate is in the bottom of the list.
6. Select **Save**

You can create as many Key Vault references in RCS as you want. It is important to keep in mind that particular Service environment will be linked to the Key Vault reference based on the Storage SAS token secret. You will be able to refer to the Azure Key Vault Certificates and Secrets stored in the Key Vault that also contains Storage SAS token secret you use during Service environment setup.
