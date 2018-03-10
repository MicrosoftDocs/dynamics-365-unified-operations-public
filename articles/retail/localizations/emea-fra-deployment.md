---
# required metadata

title: Deployment guidelines for cash registers for France
description: This topic is a deployment guide for the Retail localization for France.
author: AlexChern0v
manager: ezubov
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: France
ms.search.industry: Retail
ms.author: v-alexec
ms.search.scope: Retail
ms.search.validFrom: 2018-3-15
ms.dyn365.ops.version: 7.3.2
---
# Deployment guidelines for cash registers for France

[!include[banner](../includes/banner.md)]

This topic is a deployment guide that shows how to enable the Microsoft Dynamics 365 for Retail localization for France. The localization consists of several extensions of Retail components. For example, the extensions let you print custom fields on receipts, register additional audit events and sales and payment transactions in Point of Sale (POS), digitally sign sales transactions, and print X and Z reports in local formats. For more information about the Retail localization for France, see [Cash registers for France](./emea-fra-cash-registers.md).

This sample is part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT), Retail Server, and POS. To run this sample, you must modify and build the CRT, Retail Server, and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

## Storing certificate for digital signing in Azure Key Valut

The digital signature extension uses a certificate installed into the local certificate storage of the machine on which Retail Server is deployed. The thumbprint of the certificate needs to be specified in the configuration file (see the section [???]() for more details). Dependining on the implementation topology, it may be required to store the certificate in an [Azure Key Vault storage](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-get-started).  The Dynamics 365 for Retail localization for France contains a code sample that demostrates how to override the signing flow and sign sales transactions by using a certificate that is stored in an Azure Key Vault storage.

### Prerequisites
The following steps are required to be able to use a certificate stored in an Azure Key Vault storage:

- An Azure Key Vault storage must be created. It is recommended that the storage is deployed in the same geographical region as the Retail Server;
- The certificate must be uploaded to the storage;
- The Retail Server application must be authorized to read secrets from the storage.

See [Get started with Azure Key Vault](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-get-started#add) for more details on working with Azure Key Vault.

### Using the sample

The **DigitalSignatureKeyVaultSample** project contains the sample code that uses a certifcate strored in an Azure Key Vault storage. In order to use the sample in a production environment, you need to implement the logic that will allow populating the following parameters in the **HashAndSignData** method of the **CertificateSignatureServiceRequestHandler** class:

- **Azure Key Vault URL**: the url of the Azure Key Vault storage:

    ``` csharp
    settings.Add(WellKnownKeyVaultSettings.KeyVaultUrl, "Set your Azure Key Vault url here");
    ```

- **Client Id**: an interactive Client ID of the AD application associated with the Azure Key Vault storage for authentication.  This client should have access to read secrets from the Azure Key Vault storage:

    ``` csharp
    settings.Add(WellKnownKeyVaultSettings.KeyVaultInteractiveClientId, "Set client id here");
    ```

- **Client Secret**: a Secret Key associated with the AD application used for authentication in Azure Key Vault storage:

    ``` csharp
    // Secret key value should be encrypted and stored in a safe place.
    settings.Add(WellKnownKeyVaultSettings.KeyVaultClientSecretKey, "Set secret key here");
    ```

- **Secret reference**: a secret reference to the certificate:

    ``` csharp
    SecretCertificate secretCertificate = settingsHelper.SecretProvider.GetSecret("vault:///{Specify secret reference}") as SecretCertificate;
    ```

To override the signing flow you need to:

1.	Build the **DigitalSignatureKeyVaultSample** project and copy the assembly **Commerce.Runtime.DigitalSignatureKeyVaultSample.dll** to the Retail server folder **bin\ext**;

2.	Update the **commerceRuntime.ext.config** file by adding the following line to the **composition** section:

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.DigitalSignatureKeyVaultSample " />
    ```

> [!NOTE] 
> The thumbprint of the certificate used for digital signing should be specified in the configuration file of the SequentialSignatureRegister assembly (see the section [???]() for more details), even if the certificate is stored in the Azure Key Vault storage.

## Specifying application attributes to be printed in receipts

The following application attributes may be printed in receipts via custom fields (see [Cash registers for France](./emea-fra-cash-registers.md) for more details):

- **Build number**: the software version of the POS application. By default it is equal to the POS build number assigned by Microsoft;
- **Certificate category** and **Certificate number**: the category and the number of the certificate of compliance issued by an accredited body for the application. By default it is equal to the category and the number of the certificate granted to Microsoft:
    - Microsoft Dynamics 365 for Finance and Operations, Enterprise edition:
        - Certificate category: **C**
        - Certificate number: **18/0202**
    - Microsoft Dynamics 365 for Retail:
        - Certificate category: **B**
        - Certificate number: **18/0203**

> [!NOTE]
> By default, the certificate category and number assigned to Dynamics 365 for Finance and Operations, Enterprise edition, are printed. If you are implementing Dynamics 365 for Retail, you need to override the certificate category and number (see below for more instructions).

### Overriding build number

If you customize the POS application, you must specify the software version/build number in **???**.

### Overriding certificate category and certificate number

If you customize the POS application, and your customizations affect the compliance of the application, you may need to request a new certificate of compliance from an accredited body. In this case you will need to override the certificate category and number. You must specify the certificate category and number in **???**.

> [!NOTE]
> You also need to override the certificate category and number if you are implementing Dynamics 365 for Retail. Use the certificate category and number provided above in this case.
