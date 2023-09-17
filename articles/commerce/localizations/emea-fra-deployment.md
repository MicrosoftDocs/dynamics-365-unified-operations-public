---
# required metadata

title: Deployment guidelines for cash registers for France (legacy)
description: This article is a deployment guide for the Commerce localization for France.
author: EvgenyPopovMBS
ms.date: 08/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: France
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-4-13
ms.dyn365.ops.version: 7.3.2

---
# Deployment guidelines for cash registers for France (legacy)

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> This sample fiscal integration functionality doesn't take advantage of the [fiscal integration framework](./fiscal-integration-for-retail-channel.md) and will be deprecated in later updates. You should use the [functionality that is based on the fiscal integration framework](./emea-fra-fi-deployment.md) instead.

This article is a deployment guide that shows how to enable the Dynamics 365 Commerce localization for France. The localization consists of several extensions of components. For example, the extensions let you print custom fields on receipts, register additional audit events, sales transactions, and payment transactions in Point of Sale (POS), digitally sign sales transactions, and print X and Z reports in local formats. For more information about the localization for France, see [Cash register functionality for France](./emea-fra-cash-registers.md).

This localization is part of the Retail software development kit (SDK). For information about how to install and use the SDK, see the [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This localization consists of extensions for the Commerce runtime (CRT), Retail Server, and POS. To run this sample, you must modify and build the CRT, Retail Server, and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this article. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

> [!NOTE]
> In Commerce 10.0.8 and above, Retail Server is known as Commerce Scale Unit. Because this article applies to multiple previous versions of the app, *Retail Server* is used throughout the article.

## Storing a certificate for digital signing in Azure Key Vault

The digital signature extension uses a certificate that is installed in the local certificate storage of the machine where Retail Server is deployed. The thumbprint of the certificate must be specified in the configuration file (see the [SequentialSignatureRegister component](#sequentialsignatureregister-component) section later in this article). Depending on the implementation topology, the certificate might have to be stored in [Microsoft Azure Key Vault storage](/azure/key-vault/key-vault-get-started). The localization for France contains a code sample that shows how to override the signing flow and sign sales transactions by using a certificate that is stored in Azure Key Vault storage.

### Prerequisites

The following steps must be completed before you can use a certificate that is stored in Azure Key Vault storage:

- The Azure Key Vault storage must be created. We recommend that you deploy the storage in the same geographical region as the Retail Server.
- The certificate must be uploaded to the storage.
- The Retail Server application must be authorized to read secrets from the storage.

For more information about how to work with Azure Key Vault, see [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started).

### Using the sample

The **DigitalSignatureKeyVaultSample** project contains sample code that uses a certificate that is stored in Azure Key Vault storage. To use the sample in a production environment, you must implement logic so that the following parameters can be specified in the **HashAndSignData** method of the **CertificateSignatureServiceRequestHandler** class:

- **Azure Key Vault URL** – The URL of the Azure Key Vault storage.

    ``` csharp
    settings.Add(WellKnownKeyVaultSettings.KeyVaultUrl, "Set your Azure Key Vault URL here");
    ```

- **Client ID** – An interactive client ID of the Azure Active Directory (Azure AD) application that is associated with the Azure Key Vault storage for authentication purposes. This client should have access to read secrets from the Azure Key Vault storage.

    ``` csharp
    settings.Add(WellKnownKeyVaultSettings.KeyVaultInteractiveClientId, "Set the client ID here");
    ```

- **Client secret** – A secret key that is associated with the Azure AD application that is used for authentication in the Azure Key Vault storage.

    ``` csharp
    // Secret key value should be encrypted and stored in a safe place.
    settings.Add(WellKnownKeyVaultSettings.KeyVaultClientSecretKey, "Set the secret key here");
    ```

- **Secret reference** – A secret reference to the certificate.

    ``` csharp
    SecretCertificate secretCertificate = settingsHelper.SecretProvider.GetSecret("vault:///{Specify the secret reference}") as SecretCertificate;
    ```

To override the signing flow, follow these steps.

1. Build the **DigitalSignatureKeyVaultSample** project, and copy the **Contoso.Commerce.Runtime.DigitalSignatureKeyVaultSample.dll** assembly to the **bin\\ext** Retail Server folder.
2. Update the **commerceRuntime.ext.config** file by adding the following line to the **composition** section.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DataSignatureKeyVaultSample" />
    ```

> [!NOTE]
> The thumbprint of the certificate that is used for digital signing should be specified in the configuration file of the SequentialSignatureRegister assembly, even if the certificate is stored in Azure Key Vault storage. For more information, see the [SequentialSignatureRegister component](#sequentialsignatureregister-component) section later in this article.

### Using certificate profiles in Commerce channels

In Commerce version 10.0.15 and later, you can use the [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature that supports failover to offline when Key Vault or Headquarters are not available. The feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature.

To apply the new feature in the CRT extension, follow these steps.

1. Create a new CRT extension project (C# class library project type). Use the sample templates from the Retail software development kit (SDK) (RetailSDK\SampleExtensions\CommerceRuntime).
2. Add custom handler for CertificateSignatureServiceRequest in the SequentialSignatureRegister project.
3. To read a secret call, GetUserDefinedSecretCertificateServiceRequest using a constructor with profileId parameter. That will start the functionality working with settings from Certificate profiles. Based on the settings, the certificate will be retrieved either from Azure Key Vault or local machine storage.

	``` csharp
	GetUserDefinedSecretCertificateServiceRequest getUserDefinedSecretCertificateServiceRequest = new GetUserDefinedSecretCertificateServiceRequest(profileId: "ProfileId", secretName: null, thumbprint: null, expirationInterval: null);
	GetUserDefinedSecretCertificateServiceResponse getUserDefinedSecretCertificateServiceResponse = request.RequestContext.Execute<GetUserDefinedSecretCertificateServiceResponse>(getUserDefinedSecretCertificateServiceRequest);
	
	X509Certificate2 Certificate = getUserDefinedSecretCertificateServiceResponse.Certificate;
	```

4. When the certificate is retrieved, proceed with data signing.
5. Build the CRT extension project.
6. Copy the output class library and paste it into ...\RetailServer\webroot\bin\Ext for manual testing.
7. In the CommerceRuntime.Ext.config file, update the extension composition section with the custom library information.

## Specifying application attributes that will be printed on receipts

You can use custom fields to print the following application attributes on receipts<!-- (for more information, see [Cash registers for France](./emea-fra-cash-registers.md))-->:

- **Build number** – The software version of the POS application. By default, the value should equal the POS build number that Microsoft assigned to the POS application.
- **Certificate category** and **Certificate number** – The category and number of the certificate of compliance that an accredited body issues for the application. By default, the values equal the category and the number of the certificate that is granted to Microsoft:

    - Microsoft Dynamics 365 for Commerce:

        - **Certificate category:** C
        - **Certificate number:** 18/0202

    - Microsoft Dynamics 365 for Commerce:

        - **Certificate category:** B
        - **Certificate number:** 18/0203

    > [!NOTE]
    > By default, the certificate category and number that are assigned are printed. If you're implementing Commerce, you must override the certificate category and number.

If you customize the POS application, and your customizations affect the compliance of the application, you might have to request a new certificate of compliance from an accredited body. In this case, you must override the build number, and the certificate category and number. Otherwise, the default values for the certificate category and number will be printed, but you must still specify the POS build number that Microsoft assigned to the POS application.

### Overriding the build number

The software version/build number and publisher are specified in **RetailSDK\\BuildTools\\Customization.settings**.

```xml
<CustomVersion Condition="'$(CustomVersion)' == ''">1.0.0.1</CustomVersion>
<CustomName Condition="'$(CustomName)' == ''">Contoso Retail Customization</CustomName> 
<CustomDescription Condition="'$(CustomDescription)' == ''">Contoso Retail Customization</CustomDescription>
<CustomPublisher Condition="'$(CustomPublisher)' == ''">CN=Contoso Ltd.</CustomPublisher>
<CustomPublisherDisplayName Condition="'$(CustomPublisherDisplayName)' == ''">Contoso Ltd.</CustomPublisherDisplayName>
<CustomCopyright Condition="'$(CustomCopyright)' == ''">Copyright © 2016</CustomCopyright>
```

### Overriding the certificate category and number

The certificate category and number are specified in **RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.ReceiptsFrance\\GetSalesTransactionCustomReceiptFieldService**.

``` csharp
/// <summary>
/// Certification category.
/// </summary>
private const string CertificationCategory = "C";

/// <summary>
/// Certificate number.
/// </summary>
private const string CertificateNumber = "18/0202";
```

> [!NOTE]
> You must also override the certificate category and number if you're implementing Commerce. In this case, use the certificate category and number that are provided in the [Specifying application attributes that will be printed on receipts](#specifying-application-attributes-that-will-be-printed-on-receipts) section earlier in this article.

## Development environment

Follow these steps to set up a development environment so that you can test and extend the localization functionality.

### CRT extension components

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### CommonFrance component

1. Find the **Runtime.Extensions.CommonFrance** project, and build it.
2. In the **Extensions.CommonFrance\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.CommonFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.CommonFrance" />
    ```

#### ReceiptsFrance component

1. Find the **Runtime.Extensions.ReceiptsFrance** project, and build it.
2. In the **Extensions.ReceiptsFrance\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.ReceiptsFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsFrance" />
    ```

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

#### SalesPaymentTransExtFrance component

1. Find the **Runtime.Extensions.SalesPaymentTransExtFrance** project, and build it.
2. In the **Extensions.SalesPaymentTransExtFrance\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExtFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtFrance" />
    ```

#### SequentialSignatureFrance component

1. Find the **Runtime.Extensions.SequentialSignatureFrance** project, and build it.
2. In the **Extensions.SequentialSignatureFrance\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureFrance" />
    ```

#### SequentialSignatureRegister component

1. Find the **Runtime.Extensions.SequentialSignatureRegister** project.
2. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions. The **certificateThumbprint** property is the only mandatory property. The value must be a string that is 40 characters long in upper case and that doesn't include any delimiters. For more information, see [How to retrieve the thumbprint of a certificate](/dotnet/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate).

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
        <configSections>
            <section name="SequentialSignatureRegister" type="Contoso.Commerce.Runtime.SequentialSignatureRegister.Configuration.SequentialSignatureRegisterConfigSection, Contoso.Commerce.Runtime.SequentialSignatureRegister"/>
        </configSections>
        <SequentialSignatureRegister certificateThumbprint="insert key certificateThumbprint here" certificateStoreLocation="LocalMachine" certificateStoreName="My"/>
        <startup>
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5.1"/>
        </startup>
    </configuration>
    ```

3. Build the project.
4. In the **Extensions.SequentialSignatureRegister\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll** assembly file
    - The **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config** configuration file

5. Copy the files to the CRT extension folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

6. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

7. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    ```

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project, and build it.
2. In the **Extensions.SequentialSignatureRegister.Contracts\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

#### XZReportsFrance component

1. Find the **Runtime.Extensions.XZReportsFrance** project, and build it.
2. In the **Extensions.XZReportsFrance\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.XZReportsFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
    ```

#### RestrictingShiftDuration component

# [Retail 7.3.2 and later](#tab/retail-7-3-2)

1. Find the **Runtime.Extensions.RestrictingShiftDuration** project, and build it.
2. In the **Extensions.RestrictingShiftDuration\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.RestrictingShiftDuration.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RestrictingShiftDuration" />
    ```

# [Retail 7.3.5 and later](#tab/retail-7-3-5)

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
    ```

# [Retail 8.1.1 and later](#tab/retail-8-1-1)

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
    ```

---

### Retail Server extension components

#### SalesTransactionSignature Retail Server sample component

1. In the **RetailSDK\\SampleExtensions\\RetailServer\\RetailServer.Extensions.SalesTransactionSignatureSample** folder, find the **RetailServer.Extensions.SalesTransactionSignatureSample** project, and build it.
2. In the **RetailServer\\Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the **Contoso.RetailServer.SalesTransactionSignatureSample.dll** assembly file.
3. Copy the assembly file to the **\\bin\\ext** folder under the IIS Retail Server site location.
4. Find the configuration file for Retail Server. The file is named **web.config**, and it's in the root folder under the IIS Retail Server site location.
5. Register the Retail Server extensions in the **extensionComposition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

### Proxy extension component

You must complete the following procedure to enable the extensions in offline mode for Modern POS.

#### SalesTransactionSignature Retail proxy sample component

1. In the **RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions.SalesTransactionSignatureSample** folder, find the **RetailServer.Extensions.SalesTransactionSignatureSample** project, and build it.
2. In the **RetailProxy\\RetailProxy.Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the **Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample** assembly file.
3. Copy the assembly files to the **\\ext** folder under the local CRT client broker location.
4. Register the proxy change in the extensions configuration file. The file is named **RetailProxy.MPOSOffline.ext.config**, and it's under the local CRT client broker location.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
    ```

### Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Include the following existing source code folders in the **Pos.Extensions** project.

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - RestrictingShiftDuration
    - SalesTransBuildNumberSample

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - SalesTransBuildNumberSample

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - SalesTransBuildNumberSample

    ---

    > [!NOTE]
    > To view all files in the project folder, not just the files that are included in the project, select the **Show All Files** button in Solution Explorer. If this button isn't available, make sure that you selected the project. The icons of files and folders that aren't currently part of the project have a dotted outline. Right-click the folder to include in the project, and then select **Include in Project**.

3. Enable the extensions to be compiled by removing the following folders from the exclude list in **tsconfig.json**:

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - RestrictingShiftDuration
    - SalesTransBuildNumberSample

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - SalesTransBuildNumberSample

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - SalesTransBuildNumberSample

    ---

4. Enable the extensions to be loaded by adding the following lines in **extensions.json**:

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    ``` json
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SequentialSignature"
    },
    {
        "baseUrl": "AuditEventSignatureSample"
    },
    {
        "baseUrl": "RestrictingShiftDuration"
    },
    {
        "baseUrl": "SalesTransBuildNumberSample"
    }
    ```

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    ``` json
    {
        "baseUrl": "Microsoft/RestrictShiftDuration"
    },
    {
        "baseUrl": "Microsoft/AuditEvent.FR"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SequentialSignature"
    },
    {
        "baseUrl": "AuditEventSignatureSample"
    },
    {
        "baseUrl": "SalesTransBuildNumberSample"
    }
    ```

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    ``` json
    {
        "baseUrl": "Microsoft/RestrictShiftDuration"
    },
    {
        "baseUrl": "Microsoft/AuditEvent.FR"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SequentialSignature"
    },
    {
        "baseUrl": "AuditEventSignatureSample"
    },
    {
        "baseUrl": "SalesTransBuildNumberSample"
    }
    ```

    ---

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

5. Rebuild the solution.
6. Run Modern POS in the debugger, and test the functionality.

### Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Include the following existing source code folders in the **Pos.Extensions** project:

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - RestrictingShiftDuration
    - SalesTransBuildNumberSample

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - SalesTransBuildNumberSample

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - SalesTransBuildNumberSample

    ---

    > [!NOTE]
    > To view all files in the project folder, not just the files that are included in the project, select the **Show All Files** button in Solution Explorer. If this button isn't available, make sure that you selected the project. The icons of files and folders that aren't currently part of the project have a dotted outline. Right-click the folder to include in the project, and then select **Include in Project**.

3. Enable the extensions to be compiled by removing the following folders from the exclude list in **tsconfig.json**:

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - RestrictingShiftDuration
    - SalesTransBuildNumberSample

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - SalesTransBuildNumberSample

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - SalesTransBuildNumberSample

    ---

4. Enable the extensions to be loaded by adding the following lines in **extensions.json**:

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    ``` json
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SequentialSignature"
    },
    {
        "baseUrl": "AuditEventSignatureSample"
    },
    {
        "baseUrl": "RestrictingShiftDuration"
    },
    {
        "baseUrl": "SalesTransBuildNumberSample"
    }
    ```

    # [Retail 7.3.5 and later](#tab/retail-7-3-5)

    ``` json
    {
        "baseUrl": "Microsoft/RestrictShiftDuration"
    },
    {
        "baseUrl": "Microsoft/AuditEvent.FR"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SequentialSignature"
    },
    {
        "baseUrl": "AuditEventSignatureSample"
    },
    {
        "baseUrl": "SalesTransBuildNumberSample"
    }
    ```

    # [Retail 8.1.1 and later](#tab/retail-8-1-1)

    ``` json
    {
        "baseUrl": "Microsoft/RestrictShiftDuration"
    },
    {
        "baseUrl": "Microsoft/AuditEvent.FR"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SequentialSignature"
    },
    {
        "baseUrl": "AuditEventSignatureSample"
    },
    {
        "baseUrl": "SalesTransBuildNumberSample"
    }
    ```

    ---

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

5. Rebuild the solution.
6. Run the solution by using the **Run** command and following the steps in the Retail SDK handbook.
7. Test the functionality.

### Set up required parameters in Headquarters

For more information, see [Cash register functionality for France](./emea-fra-cash-registers.md).

## Production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Complete the steps in the [Cloud POS extension components](#cloud-pos-extension-components) or [Modern POS extension components](#modern-pos-extension-components) section earlier in this article.
2. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section:

        # [Retail 7.3.2 and later](#tab/retail-7-3-2)

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.CommonFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.RestrictingShiftDuration" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
        ```

        # [Retail 7.3.5 and later](#tab/retail-7-3-5)

        ``` xml
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
        <add source="assembly" value="Contoso.Commerce.Runtime.CommonFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
        ```

        # [Retail 8.1.1 and later](#tab/retail-8-1-1)

        ``` xml
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
        <add source="assembly" value="Contoso.Commerce.Runtime.CommonFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureFrance" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
        ```

        ---

        To use a certificate that is stored in Azure Key Vault storage for digital signing, add the following line.

        > [!NOTE]
        > Before you add this line, complete the steps in the [Storing a certificate for digital signing in Azure Key Vault](#storing-a-certificate-for-digital-signing-in-azure-key-vault) section earlier in this article.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.DataSignatureKeyVaultSample" />
        ```

    2. In the **RetailProxy.MPOSOffline.ext.config** configuration file, add the following lines to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

3. Make the following changes in the **Customization.settings** package customization configuration file:

    1. Add the following lines to the **ItemGroup** section to include the Commerce proxy extension in the deployable packages.

        ``` xml
        <ISV_RetailProxy_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample.dll" />
        ```

    2. Add the following lines to the **ItemGroup** section to include the CRT extensions in the deployable packages:

        # [Retail 7.3.2 and later](#tab/retail-7-3-2)

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.CommonFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.RestrictingShiftDuration.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExtFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsFrance.dll" />
        ```

        # [Retail 7.3.5 and later](#tab/retail-7-3-5)

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.CommonFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExtFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsFrance.dll" />
        ```

        # [Retail 8.1.1 and later](#tab/retail-8-1-1)

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.CommonFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExtFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureFrance.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsFrance.dll" />
        ```

        ---

        To use a certificate that is stored in Azure Key Vault storage for digital signing, add the following line.

        > [!NOTE]
        > Before you add this line, complete the steps in the [Storing a certificate for digital signing in Azure Key Vault](#storing-a-certificate-for-digital-signing-in-azure-key-vault) section, earlier in this article.

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DataSignatureKeyVaultSample.dll" />
        ```

    3. Add the following lines to the **ItemGroup** section to include the Retail Server extension in the deployable packages.

        ``` xml
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        ```

4. Update the Retail Server configuration file. In **RetailSDK\\Packages\\RetailServer\\Code\\web.config**, add the following lines to the **extensionComposition** section.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

5. Modify the certificate's configuration file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions. Then copy the configuration file to the **References** folder. The file is named **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config**, and it's under **Extensions.SequentialSignatureRegister\\bin\\Debug**.
6. Override the build number and the category and number of the certificate of compliance, as required. For more information, see the instructions in the [Specifying application attributes that will be printed on receipts](#specifying-application-attributes-that-will-be-printed-on-receipts) section earlier in this article.
7. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
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
