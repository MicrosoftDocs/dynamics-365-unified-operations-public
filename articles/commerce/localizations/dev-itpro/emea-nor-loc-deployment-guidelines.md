---
title: Deployment guidelines for cash registers for Norway (legacy)
description: This article is a deployment guide that shows how to enable the Microsoft Dynamics 365 Commerce localization for Norway.
author: EvgenyPopovMBS
ms.date: 02/26/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2018-2-28
ms.custom: 
  - bap-template
---
# Deployment guidelines for cash registers for Norway (legacy)

[!include [banner](../../../finance/includes/banner.md)]

> [!WARNING]
> This sample fiscal integration functionality doesn't take advantage of the [fiscal integration framework](fiscal-integration-for-retail-channel.md) and will be deprecated in later updates. You should instead use the [functionality that is based on the fiscal integration framework](emea-nor-fi-deployment.md).

This article is a deployment guide that shows how to enable the Microsoft Dynamics 365 Commerce localization for Norway. The localization consists of several extensions of Commerce components. For example, the extensions let you print custom fields on receipts, register additional audit events, sales transactions, and payment transactions in Point of Sale (POS), digitally sign sales transactions, and print X and Z reports in local formats. For more information about the localization for Norway, see [Cash register functionality for Norway](../norway/emea-nor-cash-registers.md).

This sample is part of the Retail software development kit (SDK). For information about the SDK, see the [Retail software development kit (SDK) architecture](../../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT), Retail Server, and POS. To run this sample, you must modify and build the CRT, Retail Server, and POS projects. Use an unmodified Retail SDK to make the changes that are described in this article. Use a source control system, such as Microsoft Visual Studio Online (VSO), where no files are changed yet.

> [!NOTE]
> - In Commerce 10.0.8 and later versions, Retail Server is known as Commerce Scale Unit. Because this article applies to multiple previous versions of the app, *Retail Server* is used throughout the article.
> - Some steps in the procedures in this article differ, depending on the version of Commerce that you're using. For more information, see [What's new or changed in Dynamics 365 Retail](../../get-started/whats-new.md).

### Using certificate profiles in Commerce channels

In Commerce versions 10.0.15 and later, use the [User-defined certificate profiles for retail stores](../global/certificate-profiles-for-retail-stores.md) feature that supports failover to offline when Key Vault or Commerce headquarters aren't available. This feature extends the [Manage secrets for retail channels](../../dev-itpro/manage-secrets.md) feature.

To apply this functionality in the CRT extension, follow these steps:

1. Create a new CRT extension project (C# class library project type). Use the sample templates from the Retail software development kit (SDK) (RetailSDK\SampleExtensions\CommerceRuntime).
1. Add custom handler for CertificateSignatureServiceRequest in the SequentialSignatureRegister project.
1. To read a secret, call `GetUserDefinedSecretCertificateServiceRequest` by using a constructor with the profileId parameter. This call starts the functionality that works with settings from certificate profiles. Based on the settings, the certificate is retrieved either from Azure Key Vault or local machine storage.

    ```csharp
    GetUserDefinedSecretCertificateServiceRequest getUserDefinedSecretCertificateServiceRequest = new GetUserDefinedSecretCertificateServiceRequest(profileId: "ProfileId", secretName: null, thumbprint: null, expirationInterval: null);
    GetUserDefinedSecretCertificateServiceResponse getUserDefinedSecretCertificateServiceResponse = request.RequestContext.Execute<GetUserDefinedSecretCertificateServiceResponse>(getUserDefinedSecretCertificateServiceRequest);

    X509Certificate2 Certificate = getUserDefinedSecretCertificateServiceResponse.Certificate;
    ```

1. When the certificate is retrieved, proceed with data signing.
1. Build the CRT extension project.
1. Copy the output class library and paste it into ...\RetailServer\webroot\bin\Ext for manual testing.
1. In the CommerceRuntime.Ext.config file, update the extension composition section with the custom library information.

## Development environment

Complete these procedures to set up a development environment so that you can test and extend the sample.

### The CRT extension components

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### ReceiptsNorway component

1. Find the **Runtime.Extensions.ReceiptsNorway** project, and build it.
1. In the **Extensions.ReceiptsNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.ReceiptsNorway.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesPaymentTransExt component

1. Find the **Runtime.Extensions.SalesPaymentTransExt** project, and build it.
1. In the **Extensions.SalesPaymentTransExt\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExt.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### XZReportsNorway component

1. Find the **Runtime.Extensions.XZReportsNorway** project, and build it.
1. In the **Extensions.XZReportsNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.XZReportsNorway.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Application update 4](#tab/app-update-4)

#### RegisterAuditEvent sample component

1. Find the **Runtime.Extensions.RegisterAuditEventSample** project, and build it.
1. In the **Extensions.RegisterAuditEventSample\bin\Debug** folder, find the **Contoso.Commerce.Runtime.RegisterAuditEventSample.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignature sample component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample** project.
1. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
1. Build the project.
1. In the **Extensions.SalesTransactionSignatureSample\bin\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

1. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Application update 5 and later](#tab/app-update-5-and-later)

#### RegisterAuditEvent sample component

1. Find the **Runtime.Extensions.RegisterAuditEventSample** project, and build it.
1. In the **Extensions.RegisterAuditEventSample\bin\Debug** folder, find the **Contoso.Commerce.Runtime.RegisterAuditEventSample.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignature sample component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample** project.
1. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
1. Build the project.
1. In the **Extensions.SalesTransactionSignatureSample\bin\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

1. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignatureSample.Messages component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample.Messages** project.
1. In the **Extensions.SalesTransactionSignatureSample.Messages\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 7.3.1](#tab/retail-7-3-1)

#### RegisterAuditEvent sample component

1. Find the **Runtime.Extensions.RegisterAuditEventSample** project, and build it.
1. In the **Extensions.RegisterAuditEventSample\bin\Debug** folder, find the **Contoso.Commerce.Runtime.RegisterAuditEventSample.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignature sample component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample** project.
1. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
1. Build the project.
1. In the **Extensions.SalesTransactionSignatureSample\bin\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

1. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project.
1. In the **Extensions.SequentialSignatureRegister.Contracts\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

# [Retail 7.3.2 and later](#tab/retail-7-3-2)

#### RegisterAuditEvent sample component

1. Find the **Runtime.Extensions.RegisterAuditEventSample** project, and build it.
1. In the **Extensions.RegisterAuditEventSample\bin\Debug** folder, find the **Contoso.Commerce.Runtime.RegisterAuditEventSample.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister component

1. Find the **Runtime.Extensions.SequentialSignatureRegister** project.
1. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
1. Build the project.
1. In the **Extensions.SequentialSignatureRegister\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll** assembly file
    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config** configuration file

1. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignatureNorway component

1. Find the **Runtime.Extensions.SalesTransactionSignatureNorway** project.
1. In the **Extensions.SalesTransactionSignatureNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project.
1. In the **Extensions.SequentialSignatureRegister.Contracts\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

#### SalesPaymentTransExtNorway component

1. Find the **Runtime.Extensions.SalesPaymentTransExtNorway** project, and build it.
1. In the **Extensions.SalesPaymentTransExtNorway\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 7.3.5 and later](#tab/retail-7-3-5)

#### RegisterAuditEventNorway component

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister component

1. Find the **Runtime.Extensions.SequentialSignatureRegister** project.
1. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
1. Build the project.
1. In the **Extensions.SequentialSignatureRegister\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll** assembly file
    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config** configuration file

1. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignatureNorway component

1. Find the **Runtime.Extensions.SalesTransactionSignatureNorway** project.
1. In the **Extensions.SalesTransactionSignatureNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project.
1. In the **Extensions.SequentialSignatureRegister.Contracts\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

#### SalesPaymentTransExtNorway component

1. Find the **Runtime.Extensions.SalesPaymentTransExtNorway** project, and build it.
1. In the **Extensions.SalesPaymentTransExtNorway\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 8.1.1 and later](#tab/retail-8-1-1)

#### RegisterAuditEventNorway component

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister component

1. Find the **Runtime.Extensions.SequentialSignatureRegister** project.
1. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
1. Build the project.
1. In the **Extensions.SequentialSignatureRegister\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll** assembly file
    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config** configuration file

1. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignatureNorway component

1. Find the **Runtime.Extensions.SalesTransactionSignatureNorway** project.
1. In the **Extensions.SalesTransactionSignatureNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project.
1. In the **Extensions.SequentialSignatureRegister.Contracts\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

#### SalesPaymentTransExtNorway component

1. Find the **Runtime.Extensions.SalesPaymentTransExtNorway** project, and build it.
1. In the **Extensions.SalesPaymentTransExtNorway\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll** assembly file.
1. Copy the assembly to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\ext** folder under the local CRT client broker location.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's located under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

---

### The Retail Server extension components

#### SalesTransactionSignature Retail Server sample component

1. Find the **RetailServer.Extensions.SalesTransactionSignatureSample** project in the **RetailSDK\SampleExtensions\RetailServer\RetailServer.Extensions.SalesTransactionSignatureSample** folder, and build it.
1. Find the **Contoso.RetailServer.SalesTransactionSignatureSample.dll** assembly file in the **RetailServer\Extensions.SalesTransactionSignatureSample\bin\Debug** folder.
1. Copy the assembly file to the Retail Server extensions folder.

    # [Application update 4](#tab/app-update-4)

    The folder is the **\bin** folder under the IIS Retail Server site location.

    # [Application update 5 and later](#tab/app-update-5-and-later)

    The folder is the **\bin** folder under the IIS Retail Server site location.

    # [Retail 7.3.1](#tab/retail-7-3-1)

    The folder is the **\bin\ext** folder under the IIS Retail Server site location.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    The folder is the **\bin\ext** folder under the IIS Retail Server site location.

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    The folder is the **\bin\ext** folder under the IIS Retail Server site location.

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    The folder is the **\bin\ext** folder under the IIS Retail Server site location.

    ---

1. Find the configuration file for Retail Server. The file is named **web.config**, and you can find it in the root folder under the IIS Retail Server site location.
1. Register the Retail Server extensions in the **extensionComposition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

1. Register the dependencies of the Retail Server extensions.

    # [Application update 4](#tab/app-update-4/)

    1. In the **CommerceRuntime\Extensions.SalesTransactionSignatureSample\bin\Debug** folder, find the following files:

        - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
        - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

    1. Copy the files to the **\bin** folder under the IIS Retail Server site location.
    1. Register the CRT change in the extension configuration file for CRT. This file is named **commerceruntime.ext.config**, and you can find it in the **bin** folder under the IIS Retail Server site location.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
        ```

    # [Application update 5 and later](#tab/app-update-5-and-later/)

    1. In the **CommerceRuntime\Extensions.SalesTransactionSignatureSample.Messages\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll** assembly file.
    1. Copy the file to the **\bin** folder under the IIS Retail Server site location.
    1. Register the CRT change in the extension configuration file for CRT. This file is named **commerceruntime.ext.config**, and you can find it in the **bin** folder under the IIS Retail Server site location.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages" />
        ```

    # [Retail 7.3.1](#tab/retail-7-3-1)

    > [!NOTE]
    > No actions are required.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    > [!NOTE]
    > No actions are required.

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    > [!NOTE]
    > No actions are required.

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    > [!NOTE]
    > No actions are required.

    ---

### The Modern POS extension components

#### Implement the proxy code for offline mode

This part is equivalent to the Retail Server controller, but it extends the local CRT that the client uses when it's not connected.

1. In the **customization.settings** file, change the **@(RetailServerLibraryPathForProxyGeneration)** section so that it uses the new Retail Server assembly for proxy generation.
1. Implement the following interface methods in the **StoreOperationsManager** class. For the first iteration, add the following code:

    # [Application update 4](#tab/app-update-4)

    ``` csharp
    public Task<bool> SalesTransactionSignatureServiceIsReady()
    {
        throw new NotImplementedException();
    }
    public Task<FiscalTransaction> GetLastFiscalTransaction(string storeNumber, string terminalId)
    {
        throw new NotImplementedException();
    }
    ```

    # [Application update 5 and later](#tab/app-update-5-and-later)

    ``` csharp
    public Task<bool> SalesTransactionSignatureServiceIsReady(string correlationId)
    {
        throw new NotImplementedException();
    }
    public Task<FiscalTransaction> GetLastFiscalTransaction(string storeNumber, string terminalId)
    {
        throw new NotImplementedException();
    }
    ```

    # [Retail 7.3.1](#tab/retail-7-3-1)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    > [!NOTE]
    > This step doesn't apply to this version.

    ---

1. To regenerate the proxy code, build the **Proxies** folder from the command line by using the **msbuild /t:Rebuild** command.
1. Resolve the **Proxies.RetailProxy** project dependencies:

    # [Application update 4](#tab/app-update-4)

    Open **RetailSDK\\Proxies\\RetailProxy\\Proxies.RetailProxy.csproj**. Add the **RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.SalesTransactionSignatureSample\\CommerceRuntime.Extensions.SalesTransactionSignatureSample** project to the solution. Add a project reference to the **RetailProxy** project to reference **SalesTransactionSignatureSample**.

    # [Application update 5 and later](#tab/app-update-5-and-later)

    Open **RetailSDK\\Proxies\\RetailProxy\\Proxies.RetailProxy.csproj**. Add the **RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.SalesTransactionSignatureSample.Messages\\CommerceRuntime.Extensions.SalesTransactionSignatureSample.Messages** project to the solution. Add a project reference to the **RetailProxy** project to reference **SalesTransactionSignatureSample.Messages**.

    # [Retail 7.3.1](#tab/retail-7-3-1)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    > [!NOTE]
    > This step doesn't apply to this version.

    ---

1. Adjust the interface methods in the **StoreOperationsManager** class:

    # [Application update 4](#tab/app-update-4)

    ``` csharp
    public Task<bool> SalesTransactionSignatureServiceIsReady()
    {
        return Task.Run(() => CommerceRuntimeManager.Runtime.Execute<SalesTransactionSignatureServiceIsReadyResponse>(new SalesTransactionSignatureServiceIsReadyRequest(), null).IsReady);
    }
    public Task<FiscalTransaction> GetLastFiscalTransaction(string storeNumber, string terminalId)
    {
        return Task.Run(() => CommerceRuntimeManager.Runtime.Execute<GetLastFiscalTransactionResponse>(new GetLastFiscalTransactionRequest(), null).FiscalTransaction);
    }
    ```

    # [Application update 5 and later](#tab/app-update-5-and-later)

    ``` csharp
    public Task<bool> SalesTransactionSignatureServiceIsReady(string correlationId)
    {
        return Task.Run(() => CommerceRuntimeManager.Runtime.Execute<SalesTransactionSignatureServiceIsReadyResponse>(new SalesTransactionSignatureServiceIsReadyRequest(), null).IsReady);
    }
    public Task<FiscalTransaction> GetLastFiscalTransaction(string storeNumber, string terminalId)
    {
        return Task.Run(() => CommerceRuntimeManager.Runtime.Execute<GetLastFiscalTransactionResponse>(new GetLastFiscalTransactionRequest(), null).FiscalTransaction);
    }
    ```

    # [Retail 7.3.1](#tab/retail-7-3-1)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    > [!NOTE]
    > This step doesn't apply to this version.

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    > [!NOTE]
    > This step doesn't apply to this version.

    ---

1. Update the **dllhost.exe.config** file so that the client broker loads the new RetailProxy assembly.

    ``` xml
    <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy" />
    <add key="AdaptorCallerFullTypeName" value="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller" />
    ```

#### Retail proxy extension component (Retail 7.3.1 and later)

Complete the following procedure only if you're using Retail 7.3.1 and later.

1. In the **RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions.SalesTransactionSignatureSample** folder, find the **RetailServer.Extensions.SalesTransactionSignatureSample** project, and build it.
1. In the **RetailProxy\\RetailProxy.Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the **Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample** assembly file.
1. Copy the assembly files to the **\\ext** folder under the local CRT client broker location.
1. Register the Retail proxy change in the extension configuration file. The file is named **RetailProxy.MPOSOffline.ext.config**, and it's under the local CRT client broker location.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
    ```

#### Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it compiles without errors. Also, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Don't customize Modern POS. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

1. Include the following existing source code folders in the **Pos.Extensions** project.

    # [Application update 4](#tab/app-update-4)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Application update 5 and later](#tab/app-update-5-and-later)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Retail 7.3.1](#tab/retail-7-3-1)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    ---

1. Enable the extensions to compile in **tsconfig.json** by removing the following folders from the exclude list.

    # [Application update 4](#tab/app-update-4)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Application update 5 and later](#tab/app-update-5-and-later)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Retail 7.3.1](#tab/retail-7-3-1)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    ---

1. Enable the extensions to load in **extensions.json** by adding the following lines in the appropriate place.

    # [Application update 4](#tab/app-update-4)

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    # [Application update 5 and later](#tab/app-update-5-and-later)

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    # [Retail 7.3.1](#tab/retail-7-3-1)

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureNorway"
    },
    {
        "baseUrl": "SequentialSignature"
    }
    ```

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    ``` json
    {
        "baseUrl": "Microsoft/AuditEvent.NO"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureNorway"
    },
    {
        "baseUrl": "SequentialSignature"
    }
    ```

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    ``` json
    {
        "baseUrl": "Microsoft/AuditEvent.NO"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureNorway"
    },
    {
        "baseUrl": "SequentialSignature"
    }
    ```

    ---

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run Modern POS in the debugger, and test the functionality.

### Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it compiles without errors.
1. Include the following existing source code folders in the **Pos.Extensions** project.

    # [Application update 4](#tab/app-update-4)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Application update 5 and later](#tab/app-update-5-and-later)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Retail 7.3.1](#tab/retail-7-3-1)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    ---

1. Enable the extensions to compile in **tsconfig.json** by removing the following folders from the exclude list.

    # [Application update 4](#tab/app-update-4)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Application update 5 and later](#tab/app-update-5-and-later)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Retail 7.3.1](#tab/retail-7-3-1)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    - AuditEventExtensionSample
    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    - SalesTransactionSignatureSample
    - SalesTransactionSignatureNorway
    - SequentialSignature

    ---

1. Enable the extensions to load in **extensions.json** by adding the following lines in the appropriate place.

    # [Application update 4](#tab/app-update-4)

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    # [Application update 5 and later](#tab/app-update-5-and-later)

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    # [Retail 7.3.1](#tab/retail-7-3-1)

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureNorway"
    },
    {
        "baseUrl": "SequentialSignature"
    }
    ```

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    ``` json
    {
        "baseUrl": "Microsoft/AuditEvent.NO"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureNorway"
    },
    {
        "baseUrl": "SequentialSignature"
    }
    ```

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    ``` json
    {
        "baseUrl": "Microsoft/AuditEvent.NO"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureNorway"
    },
    {
        "baseUrl": "SequentialSignature"
    }
    ```

    ---

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run the solution by using the **Run** command and follow the steps in the Retail SDK handbook.
1. Test the functionality.

### Set up required parameters in Headquarters

For more information, see [Cash register functionality for Norway](../norway/emea-nor-cash-registers.md).

## Production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Complete the steps in the [Cloud POS extension components](#cloud-pos-extension-components) or [Modern POS extension components](#modern-pos-extension-components) section earlier in this article.
1. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section:

        # [Application update 4](#tab/app-update-4)

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
        ```

        # [Application update 5 and later](#tab/app-update-5-and-later)

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
        ```

        # [Retail 7.3.1](#tab/retail-7-3-1)

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
        ```

        # [Retail 7.3.2 and later](#tab/retail-7-3-2)

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
        ```

        # [Retail 7.3.5 and later](#tab/retail-7-3-5)

        ``` xml
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
        ```

        # [Retail 8.1.1 and later](#tab/retail-8-1-1)

        ``` xml
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
        ```

        ---

    1. Enable Commerce Proxy customization:

        # [Application update 4](#tab/app-update-4)

        In the **dllhost.exe.config** file, add the following lines to the **appSettings** subsection of the **configuration** section.

        ``` xml
        <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy"/>
        <add key="AdaptorCallerFullTypeName" value ="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller"/>
        ```

        # [Application update 5 and later](#tab/app-update-5-and-later)

        In the **dllhost.exe.config** file, add the following lines to the **appSettings** subsection of the **configuration** section.

        ``` xml
        <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy"/>
        <add key="AdaptorCallerFullTypeName" value ="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller"/>
        ```

        # [Retail 7.3.1](#tab/retail-7-3-1)

        In the **RetailProxy.MPOSOffline.ext.config** file, add the following lines to the **composition** section:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

        # [Retail 7.3.2 and later](#tab/retail-7-3-2)

        In the **RetailProxy.MPOSOffline.ext.config** file, add the following lines to the **composition** section:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

        # [Retail 7.3.5 and later](#tab/retail-7-3-5)

        In the **RetailProxy.MPOSOffline.ext.config** file, add the following lines to the **composition** section:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

        # [Retail 8.1.1 and later](#tab/retail-8-1-1)

        In the **RetailProxy.MPOSOffline.ext.config** file, add the following lines to the **composition** section:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

        ---

1. Make the following changes in the **Customization.settings** package customization configuration file:

    1. Enable Retail Proxy customization.

        # [Application update 4](#tab/app-update-4)

        Add the following lines to the **&lt;ItemGroup Condition="'@(RetailServerLibraryPathForProxyGeneration)' == ''"&gt;** section.

        ``` xml
        <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll"/>
        ```

        # [Application update 5 and later](#tab/app-update-5-and-later)

        Add the following lines to the **&lt;ItemGroup Condition="'@(RetailServerLibraryPathForProxyGeneration)' == ''"&gt;** section.

        ``` xml
        <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll"/>
        ```

        # [Retail 7.3.1](#tab/retail-7-3-1)

        Add the following lines to the **ItemGroup** section to include the Retail proxy extension in the deployable packages:

        ``` xml
        <ISV_RetailProxy_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample.dll" />
        ```

        # [Retail 7.3.2 and later](#tab/retail-7-3-2)

        Add the following lines to the **ItemGroup** section to include the Retail proxy extension in the deployable packages:

        ``` xml
        <ISV_RetailProxy_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample.dll" />
        ```

        # [Retail 7.3.5 and later](#tab/retail-7-3-5)

        Add the following lines to the **ItemGroup** section to include the Retail proxy extension in the deployable packages:

        ``` xml
        <ISV_RetailProxy_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample.dll" />
        ```

        # [Retail 8.1.1 and later](#tab/retail-8-1-1)

        Add the following lines to the **ItemGroup** section to include the Retail proxy extension in the deployable packages:

        ``` xml
        <ISV_RetailProxy_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample.dll" />
        ```

        ---

    1. Add the following lines to the **ItemGroup** section to include the CRT extensions in the deployable packages:

        # [Application update 4](#tab/app-update-4)

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.RegisterAuditEventSample.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway.dll" />
        ```

        # [Application update 5 and later](#tab/app-update-5-and-later)

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.RegisterAuditEventSample.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway.dll" />
        ```

        # [Retail 7.3.1](#tab/retail-7-3-1)

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.RegisterAuditEventSample.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway.dll" />
        ```

        # [Retail 7.3.2 and later](#tab/retail-7-3-2)

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.RegisterAuditEventSample.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway.dll" />
        ```

        # [Retail 7.3.5 and later](#tab/retail-7-3-5)

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway.dll" />
        ```

        # [Retail 8.1.1 and later](#tab/retail-8-1-1)

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway.dll" />
        ```

        ---

    1. Add the following lines to the **ItemGroup** section to include the Retail Server extension in the deployable packages:

        # [Application update 4](#tab/app-update-4)

        ``` xml
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll" />
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config" />
        ```

        # [Application update 5 and later](#tab/app-update-5-and-later)

        ``` xml
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll" />
        ```

        # [Retail 7.3.1](#tab/retail-7-3-1)

        ``` xml
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        ```

        # [Retail 7.3.2 and later](#tab/retail-7-3-2)

        ``` xml
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        ```

        # [Retail 7.3.5 and later](#tab/retail-7-3-5)

        ``` xml
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        ```

        # [Retail 8.1.1 and later](#tab/retail-8-1-1)

        ``` xml
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        ```

        ---

1. Modify the following files to include the resource files for Norway in deployable packages:
    - `Packages\_SharedPackagingProjectComponents\Sdk.ModernPos.Shared.csproj`
    - `Packages\RetailServer\Sdk.RetailServerSetup.proj`
  
  - For the **Sdk.ModernPos.Shared.csproj** file 
    - Add line to the **ItemGroup** section
    
        ``` xml
        <<File_name> Include="$(SdkReferencesPath)\nb-NO\*" />
        ```
    > [!Note]
    > Instead of the `<File_name>` specify a name of the resource file. The same is relevant for the other examples given below.
 
    - Add line to the **Target Name="CopyPackageFiles"** section
       ``` xml
        <Copy SourceFiles="@(<File_name>)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\nb-NO" SkipUnchangedFiles="true" />
        ```
  
  - For the **Sdk.RetailServerSetup.proj** file 
    - Add line to the **ItemGroup** section
        ``` xml
        <<File_name> Include="$(SdkReferencesPath)\nb-NO\*" />
        ```    
    - Add line to the **Target Name="CopyPackageFiles"** section
         ``` xml
        <Copy SourceFiles="@(<File_name>)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\nb-NO" SkipUnchangedFiles="true" />
        ```    

1. Modify the certificate's configuration file by specifying the thumbprint, store location, and store name for the certificate that you want to use to sign sales transactions. Then copy the configuration file to the **References** folder.

    # [Application update 4](#tab/app-update-4)

    The file is named **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config**, and it's under **CommerceRuntime\\Extensions.SalesTransactionSignatureSample\\bin\\Debug**.

    # [Application update 5 and later](#tab/app-update-5-and-later)

    The file is named **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config**, and it's under **CommerceRuntime\\Extensions.SalesTransactionSignatureSample\\bin\\Debug**.

    # [Retail 7.3.1](#tab/retail-7-3-1)

    The file is named **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config**, and it's under **CommerceRuntime\\Extensions.SalesTransactionSignatureSample\\bin\\Debug**.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    The file is named **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config**, and it's under **Extensions.SequentialSignatureRegister\\bin\\Debug**.

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    The file is named **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config**, and it's under **Extensions.SequentialSignatureRegister\\bin\\Debug**.

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    The file is named **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config**, and it's under **Extensions.SequentialSignatureRegister\\bin\\Debug**.

    ---

1. Update the Retail Server configuration file. In the **RetailSDK\\Packages\\RetailServer\\Code\\web.config** file, add the following lines to the **extensionComposition** section.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

1. Run **msbuild** for the whole Retail SDK to create deployable packages.
1. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../../dev-itpro/retail-sdk/retail-sdk-packaging.md).

### Enable the digital signature in offline mode for Modern POS

To enable the digital signature in offline mode for Modern POS, follow these steps after you activate Modern POS on a new device.

1. Sign in to POS.
1. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending downloads** field is **0** (zero), the database is fully synchronized.
1. Sign out of POS.
1. Wait a while for the offline database to be fully synchronized.
1. Sign in to POS.
1. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synchronized.
1. Restart Modern POS.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
