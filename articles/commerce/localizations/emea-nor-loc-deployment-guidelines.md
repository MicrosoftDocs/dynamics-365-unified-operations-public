---
# required metadata

title: Deployment guidelines for cash registers for Norway (legacy)
description: This topic is a deployment guide that shows how to enable the Microsoft Dynamics 365 Commerce localization for Norway.
author: EvgenyPopovMBS
ms.date: 12/20/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: epopov
ms.search.validFrom: 2018-2-28

---
# Deployment guidelines for cash registers for Norway (legacy)

[!include [banner](../includes/banner.md)]

This topic is a deployment guide that shows how to enable the Microsoft Dynamics 365 Commerce localization for Norway. The localization consists of several extensions of Commerce components. For example, the extensions let you print custom fields on receipts, register additional audit events, sales transactions, and payment transactions in Point of Sale (POS), digitally sign sales transactions, and print X and Z reports in local formats. For more information about the localization for Norway, see [Cash register functionality for Norway](./emea-nor-cash-registers.md).

This sample is part of the Retail software development kit (SDK). For information about the SDK, see the [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT), Retail Server, and POS. To run this sample, you must modify and build the CRT, Retail Server, and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

> [!NOTE]
> In Commerce 10.0.8 and above, Retail Server is known as Commerce Scale Unit. Because this topic applies to multiple previous versions of the app, *Retail Server* is used throughout the topic.
>
> Some steps in the procedures in this topic differ, depending on the version of Commerce that you're using. For more information, see [What's new or changed in Dynamics 365 Retail](../get-started/whats-new.md).

### Using certificate profiles in Commerce channels

In Commerce versions 10.0.15 and later, you can use the [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature that supports failover to offline when Key Vault or Commerce headquarters aren't available. The feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature.

To apply this functionality in the CRT extension, follow these steps.

1. Create a new CRT extension project (C# class library project type). Use the sample templates from the Retail software development kit (SDK) (RetailSDK\SampleExtensions\CommerceRuntime).

2. Add custom handler for CertificateSignatureServiceRequest in the SequentialSignatureRegister project.

3. To read a secret call, `GetUserDefinedSecretCertificateServiceRequest` using a constructor with profileId parameter. That will start the functionality working with settings from Certificate profiles. Based on the settings, the certificate will be retrieved either from Azure Key Vault or local machine storage.

    ```csharp
    GetUserDefinedSecretCertificateServiceRequest getUserDefinedSecretCertificateServiceRequest = new GetUserDefinedSecretCertificateServiceRequest(profileId: "ProfileId", secretName: null, thumbprint: null, expirationInterval: null);
    GetUserDefinedSecretCertificateServiceResponse getUserDefinedSecretCertificateServiceResponse = request.RequestContext.Execute<GetUserDefinedSecretCertificateServiceResponse>(getUserDefinedSecretCertificateServiceRequest);

    X509Certificate2 Certificate = getUserDefinedSecretCertificateServiceResponse.Certificate;
    ```

4. When the certificate is retrieved, proceed with data signing.

5. Build the CRT extension project.

6. Copy the output class library and paste it into ...\RetailServer\webroot\bin\Ext for manual testing.

7. In the CommerceRuntime.Ext.config file, update the extension composition section with the custom library information.

## Development environment

Complete these procedures to set up a development environment so that you can test and extend the sample.

### The CRT extension components

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### ReceiptsNorway component

1. Find the **Runtime.Extensions.ReceiptsNorway** project, and build it.
2. In the **Extensions.ReceiptsNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.ReceiptsNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesPaymentTransExt component

1. Find the **Runtime.Extensions.SalesPaymentTransExt** project, and build it.
2. In the **Extensions.SalesPaymentTransExt\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExt.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### XZReportsNorway component

1. Find the **Runtime.Extensions.XZReportsNorway** project, and build it.
2. In the **Extensions.XZReportsNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.XZReportsNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Application update 4](#tab/app-update-4)

#### RegisterAuditEvent sample component

1. Find the **Runtime.Extensions.RegisterAuditEventSample** project, and build it.
2. In the **Extensions.RegisterAuditEventSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.RegisterAuditEventSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignature sample component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample** project.
2. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
3. Build the project.
4. In the **Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

5. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

6. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

7. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Application update 5 and later](#tab/app-update-5-and-later)

#### RegisterAuditEvent sample component

1. Find the **Runtime.Extensions.RegisterAuditEventSample** project, and build it.
2. In the **Extensions.RegisterAuditEventSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.RegisterAuditEventSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignature sample component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample** project.
2. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
3. Build the project.
4. In the **Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

5. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

6. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

7. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignatureSample.Messages component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample.Messages** project.
2. In the **Extensions.SalesTransactionSignatureSample.Messages\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 7.3.1](#tab/retail-7-3-1)

#### RegisterAuditEvent sample component

1. Find the **Runtime.Extensions.RegisterAuditEventSample** project, and build it.
2. In the **Extensions.RegisterAuditEventSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.RegisterAuditEventSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignature sample component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample** project.
2. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
3. Build the project.
4. In the **Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

5. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

6. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

7. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project.
2. In the **Extensions.SequentialSignatureRegister.Contracts\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

# [Retail 7.3.2 and later](#tab/retail-7-3-2)

#### RegisterAuditEvent sample component

1. Find the **Runtime.Extensions.RegisterAuditEventSample** project, and build it.
2. In the **Extensions.RegisterAuditEventSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.RegisterAuditEventSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister component

1. Find the **Runtime.Extensions.SequentialSignatureRegister** project.
2. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
3. Build the project.
4. In the **Extensions.SequentialSignatureRegister\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll** assembly file
    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config** configuration file

5. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

6. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

7. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignatureNorway component

1. Find the **Runtime.Extensions.SalesTransactionSignatureNorway** project.
2. In the **Extensions.SalesTransactionSignatureNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project.
2. In the **Extensions.SequentialSignatureRegister.Contracts\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

#### SalesPaymentTransExtNorway component

1. Find the **Runtime.Extensions.SalesPaymentTransExtNorway** project, and build it.
2. In the **Extensions.SalesPaymentTransExtNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 7.3.5 and later](#tab/retail-7-3-5)

#### RegisterAuditEventNorway component

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister component

1. Find the **Runtime.Extensions.SequentialSignatureRegister** project.
2. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
3. Build the project.
4. In the **Extensions.SequentialSignatureRegister\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll** assembly file
    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config** configuration file

5. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

6. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

7. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignatureNorway component

1. Find the **Runtime.Extensions.SalesTransactionSignatureNorway** project.
2. In the **Extensions.SalesTransactionSignatureNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project.
2. In the **Extensions.SequentialSignatureRegister.Contracts\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

#### SalesPaymentTransExtNorway component

1. Find the **Runtime.Extensions.SalesPaymentTransExtNorway** project, and build it.
2. In the **Extensions.SalesPaymentTransExtNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

# [Retail 8.1.1 and later](#tab/retail-8-1-1)

#### RegisterAuditEventNorway component

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister component

1. Find the **Runtime.Extensions.SequentialSignatureRegister** project.
2. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions.
3. Build the project.
4. In the **Extensions.SequentialSignatureRegister\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll** assembly file
    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config** configuration file

5. Copy the files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

6. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

7. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SalesTransactionSignatureNorway component

1. Find the **Runtime.Extensions.SalesTransactionSignatureNorway** project.
2. In the **Extensions.SalesTransactionSignatureNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project.
2. In the **Extensions.SequentialSignatureRegister.Contracts\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

#### SalesPaymentTransExtNorway component

1. Find the **Runtime.Extensions.SalesPaymentTransExtNorway** project, and build it.
2. In the **Extensions.SalesPaymentTransExtNorway\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExtNorway.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtNorway" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

---

### The Retail Server extension components

#### SalesTransactionSignature Retail Server sample component

1. In the **RetailSDK\\SampleExtensions\\RetailServer\\RetailServer.Extensions.SalesTransactionSignatureSample** folder, find the **RetailServer.Extensions.SalesTransactionSignatureSample** project, and build it.
2. In the **RetailServer\\Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the **Contoso.RetailServer.SalesTransactionSignatureSample.dll** assembly file.
3. Copy the assembly file to the Retail Server extensions folder.

    # [Application update 4](#tab/app-update-4)

    The folder is the **\\bin** folder under the IIS Retail Server site location.

    # [Application update 5 and later](#tab/app-update-5-and-later)

    The folder is the **\\bin** folder under the IIS Retail Server site location.

    # [Retail 7.3.1](#tab/retail-7-3-1)

    The folder is the **\\bin\\ext** folder under the IIS Retail Server site location.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    The folder is the **\\bin\\ext** folder under the IIS Retail Server site location.

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    The folder is the **\\bin\\ext** folder under the IIS Retail Server site location.

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    The folder is the **\\bin\\ext** folder under the IIS Retail Server site location.

    ---

4. Find the configuration file for Retail Server. The file is named **web.config**, and it's in the root folder under the IIS Retail Server site location.
5. Register the Retail Server extensions in the **extensionComposition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

6. Register the dependencies of the Retail Server extensions.

    # [Application update 4](#tab/app-update-4/)

    1. In the **CommerceRuntime\\Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the following files:

        - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
        - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

    2. Copy the files to the **\\bin** folder under the IIS Retail Server site location.
    3. Register the CRT change in the extension configuration file for CRT. This file is named **commerceruntime.ext.config**, and it's in the **bin** folder under the IIS Retail Server site location.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
        ```

    # [Application update 5 and later](#tab/app-update-5-and-later/)

    1. In the **CommerceRuntime\\Extensions.SalesTransactionSignatureSample.Messages\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.Messages.dll** assembly file.
    2. Copy the file to the **\\bin** folder under the IIS Retail Server site location.
    3. Register the CRT change in the extension configuration file for CRT. This file is named **commerceruntime.ext.config**, and it's in the **bin** folder under the IIS Retail Server site location.

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

This part is equivalent to the Retail Server controller, but it extends the local CRT that is used when the client isn't connected.

1. In the **customization.settings** file, change the **@(RetailServerLibraryPathForProxyGeneration)** section so that it uses the new Retail Server assembly for proxy generation.
2. Implement the following interface methods in the **StoreOperationsManager** class. For the first iteration, add the following code:

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

3. To regenerate the proxy code, build the **Proxies** folder from the command line by using the **msbuild /t:Rebuild** command.
4. Resolve the **Proxies.RetailProxy** project dependencies:

    # [Application update 4](#tab/app-update-4)

    Open **RetailSDK\\Proxies\\RetailProxy\\Proxies.RetailProxy.csproj**, add the **RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.SalesTransactionSignatureSample\\CommerceRuntime.Extensions.SalesTransactionSignatureSample** project to the solution, and add a project reference to the **RetailProxy** project to reference **SalesTransactionSignatureSample**.

    # [Application update 5 and later](#tab/app-update-5-and-later)

    Open **RetailSDK\\Proxies\\RetailProxy\\Proxies.RetailProxy.csproj**, add the **RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.SalesTransactionSignatureSample.Messages\\CommerceRuntime.Extensions.SalesTransactionSignatureSample.Messages** project to the solution, and add a project reference to the **RetailProxy** project to reference **SalesTransactionSignatureSample.Messages**.

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

5. Adjust the interface methods in the **StoreOperationsManager** class:

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

6. Update the **dllhost.exe.config** file so that the client broker loads the new RetailProxy assembly.

    ``` xml
    <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy" />
    <add key="AdaptorCallerFullTypeName" value="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller" />
    ```

#### Retail proxy extension component (Retail 7.3.1 and later)

Complete the following procedure only if you're using Retail 7.3.1 and later.

1. In the **RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions.SalesTransactionSignatureSample** folder, find the **RetailServer.Extensions.SalesTransactionSignatureSample** project, and build it.
2. In the **RetailProxy\\RetailProxy.Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the **Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample** assembly file.
3. Copy the assembly files to the **\\ext** folder under the local CRT client broker location.
4. Register the Retail proxy change in the extension configuration file. The file is named **RetailProxy.MPOSOffline.ext.config**, and it's under the local CRT client broker location.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
    ```

#### Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Include the following existing source code folders in the **Pos.Extensions** project.

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

3. Enable the extensions to be compiled in **tsconfig.json** by removing the following folders from the exclude list.

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

4. Enable the extensions to be loaded in **extensions.json** by adding the following lines in the appropriate place.

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

5. Rebuild the solution.
6. Run Modern POS in the debugger, and test the functionality.

### Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Include following existing source code folders in the **Pos.Extensions** project.

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

3. Enable the extensions to be compiled in **tsconfig.json** by removing following folders from the exclude list.

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

4. Enable the extensions to be loaded in **extensions.json** by adding the following lines in the appropriate place.

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

5. Rebuild the solution.
6. Run the solution by using the **Run** command and following the steps in the Retail SDK handbook.
7. Test the functionality.

### Set up required parameters in Headquarters

For more information, see [Cash register functionality for Norway](./emea-nor-cash-registers.md).

## Production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Complete the steps in the [Cloud POS extension components](#cloud-pos-extension-components) or [Modern POS extension components](#modern-pos-extension-components) section earlier in this topic.
2. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

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

    2. Enable Commerce Proxy customization:

        # [Application update 4](#tab/app-update-4)

        In the **dllhost.exe.config** configuration file, add the following lines to the **appSettings** subsection of the **configuration** section.

        ``` xml
        <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy"/>
        <add key="AdaptorCallerFullTypeName" value ="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller"/>
        ```

        # [Application update 5 and later](#tab/app-update-5-and-later)

        In the **dllhost.exe.config** configuration file, add the following lines to the **appSettings** subsection of the **configuration** section.

        ``` xml
        <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy"/>
        <add key="AdaptorCallerFullTypeName" value ="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller"/>
        ```

        # [Retail 7.3.1](#tab/retail-7-3-1)

        In the **RetailProxy.MPOSOffline.ext.config** configuration file, add the following lines to the **composition** section:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

        # [Retail 7.3.2 and later](#tab/retail-7-3-2)

        In the **RetailProxy.MPOSOffline.ext.config** configuration file, add the following lines to the **composition** section:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

        # [Retail 7.3.5 and later](#tab/retail-7-3-5)

        In the **RetailProxy.MPOSOffline.ext.config** configuration file, add the following lines to the **composition** section:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

        # [Retail 8.1.1 and later](#tab/retail-8-1-1)

        In the **RetailProxy.MPOSOffline.ext.config** configuration file, add the following lines to the **composition** section:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

        ---

3. Make the following changes in the **Customization.settings** package customization configuration file:

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

    2. Add the following lines to the **ItemGroup** section to include the CRT extensions in the deployable packages:

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

    3. Add following lines to the **ItemGroup** section to include the Retail Server extension in the deployable packages:

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

4. Modify the following files to include the resource files for Norway in deployable packages:
    - Packages\_SharedPackagingProjectComponents\Sdk.ModernPos.Shared.csproj
    - Packages\RetailServer\Sdk.RetailServerSetup.proj
  
  - For the **Sdk.ModernPos.Shared.csproj** file 
    - Add line to the **ItemGroup** section
    
        ``` xml
        <<File_name> Include="$(SdkReferencesPath)\nb-NO\*" />
        ```
    > [!Note]
    > Instead of the <File_name> specify a name of the resource file. The same is relevant for the other examples given below.
 
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

5. Modify the certificate's configuration file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions. Then copy the configuration file to the **References** folder.

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

6. Update Retail Server configuration file. In the **RetailSDK\\Packages\\RetailServer\\Code\\web.config** file, add the following lines to the **extensionComposition** section.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

7. Run **msbuild** for the whole Retail SDK to create deployable packages.
8. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

### Enable the digital signature in offline mode for Modern POS

To enable the digital signature in offline mode for Modern POS, you must follow these steps after you activate Modern POS on a new device.

1. Sign in to POS.
2. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending downloads** field is **0** (zero), the database is fully synchronized.
3. Sign out of POS.
4. Wait a while for the offline database to be fully synchronized.
5. Sign in to POS.
6. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synchronized.
7. Restart Modern POS.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
