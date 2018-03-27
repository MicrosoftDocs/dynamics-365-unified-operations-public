---
# required metadata

title: Deployment guidelines for cash registers for France
description: This topic is a deployment guide for the Retail localization for France.
author: AlexChern0v
manager: ezubov
ms.date: 03/27/2018
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

This topic is a deployment guide that shows how to enable the Microsoft Dynamics 365 for Retail localization for France. The localization consists of several extensions of Retail components. For example, the extensions let you print custom fields on receipts, register additional audit events and sales and payment transactions in Point of Sale (POS), digitally sign sales transactions, and print X and Z reports in local formats. <!--For more information about the Retail localization for France, see [Cash registers for France](./emea-fra-cash-registers.md).-->

This localization is part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This localization consists of extensions for the Commerce runtime (CRT), Retail Server, and POS. To run this sample, you must modify and build the CRT, Retail Server, and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

## Storing certificate for digital signing in Azure Key Vault

The digital signature extension uses a certificate installed into the local certificate storage of the machine on which Retail Server is deployed. The thumbprint of the certificate needs to be specified in the configuration file (see the section [SequentialSignatureRegister component](#sequentialsignatureregister-component) for more details). Depending on the implementation topology, it may be required to store the certificate in an [Azure Key Vault storage](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-get-started). The Dynamics 365 for Retail localization for France contains a code sample that demonstrates how to override the signing flow and sign sales transactions by using a certificate that is stored in an Azure Key Vault storage.

### Prerequisites
The following steps are required to be able to use a certificate stored in an Azure Key Vault storage:

- An Azure Key Vault storage must be created. It is recommended that the storage is deployed in the same geographical region as the Retail Server;
- The certificate must be uploaded to the storage;
- The Retail Server application must be authorized to read secrets from the storage.

See [Get started with Azure Key Vault](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-get-started) for more details on working with Azure Key Vault.

### Using the sample

The **DigitalSignatureKeyVaultSample** project contains the sample code that uses a certificate stored in an Azure Key Vault storage. In order to use the sample in a production environment, you need to implement the logic that will allow populating the following parameters in the **HashAndSignData** method of the **CertificateSignatureServiceRequestHandler** class:

- **Azure Key Vault URL**: the URL of the Azure Key Vault storage:

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

1. Build the **DigitalSignatureKeyVaultSample** project and copy the assembly **Contoso.Commerce.Runtime.DigitalSignatureKeyVaultSample.dll** to the Retail server folder **bin\ext**;

2. Update the **commerceRuntime.ext.config** file by adding the following line to the **composition** section:

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DigitalSignatureKeyVaultSample" />
    ```

> [!NOTE] 
> The thumbprint of the certificate used for digital signing should be specified in the configuration file of the SequentialSignatureRegister assembly (see the section [SequentialSignatureRegister component](#sequentialsignatureregister-component) for more details), even if the certificate is stored in the Azure Key Vault storage.

## Specifying application attributes to be printed in receipts

The following application attributes may be printed in receipts via custom fields <!--(see [Cash registers for France](./emea-fra-cash-registers.md) for more details)-->:

- **Build number**: the software version of the POS application. By default it should be equal to the POS build number assigned by Microsoft to the POS application;
- **Certificate category** and **Certificate number**: the category and the number of the certificate of compliance issued by an accredited body for the application. By default it is equal to the category and the number of the certificate granted to Microsoft:
    - Microsoft Dynamics 365 for Finance and Operations, Enterprise edition:
        - Certificate category: **C**
        - Certificate number: **18/0202**
    - Microsoft Dynamics 365 for Retail:
        - Certificate category: **B**
        - Certificate number: **18/0203**

    > [!NOTE]
    > By default, the certificate category and number assigned to Dynamics 365 for Finance and Operations, Enterprise edition, are printed. If you are implementing Dynamics 365 for Retail, you need to override the certificate category and number.

If you customize the POS application, and your customizations affect the compliance of the application, you may need to request a new certificate of compliance from an accredited body. In this case you will need to override the build number and the certificate category and number. Otherwise, the default values for the certificate category and number will be printed, but you still need to specify the POS build number assigned by Microsoft to the POS application.

### Overriding build number

The software version/build number and publisher are specified in **RetailSDK\\BuildTools\\Customization.settings**.

```xml
    <CustomVersion Condition="'$(CustomVersion)' == ''">1.0.0.1</CustomVersion>
    <CustomName Condition="'$(CustomName)' == ''">Contoso Retail Customization</CustomName> 
    <CustomDescription Condition="'$(CustomDescription)' == ''">Contoso Retail Customization</CustomDescription>
    <CustomPublisher Condition="'$(CustomPublisher)' == ''">CN=Contoso Ltd.</CustomPublisher>
    <CustomPublisherDisplayName Condition="'$(CustomPublisherDisplayName)' == ''">Contoso Ltd.</CustomPublisherDisplayName>
    <CustomCopyright Condition="'$(CustomCopyright)' == ''">Copyright © 2016</CustomCopyright>
```

### Overriding certificate category and number

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
> You also need to override the certificate category and number if you are implementing Dynamics 365 for Retail. Use the certificate category and number provided above in this case.

## Development environment

Follow these steps to set up a development environment, so that you can test and extend the localization functionality.

### CRT extension components

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### CommonFrance component

1. Find the **Runtime.Extensions.CommonFrance** project, and build it.
2. In the **Extensions.CommonFrance\\bin\Debug** folder, find the **Contoso.Commerce.Runtime.CommonFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Internet Information Services (IIS) Retail Server site location.
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
2. In the **Extensions.ReceiptsFrance\\bin\Debug** folder, find the **Contoso.Commerce.Runtime.ReceiptsFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsFrance" />
    ```

#### RestrictingShiftDuration component

1. Find the **Runtime.Extensions.RestrictingShiftDuration** project, and build it.
2. In the **Extensions.RestrictingShiftDuration\\bin\Debug** folder, find the **Contoso.Commerce.Runtime.RestrictingShiftDuration.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RestrictingShiftDuration" />
    ```

#### SalesPaymentTransExt component

1. Find the **Runtime.Extensions.SalesPaymentTransExt** project, and build it.
2. In the **Extensions.SalesPaymentTransExt\\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExt.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Internet Information Services (IIS) Retail Server site location.
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
2. In the **Extensions.SalesPaymentTransExtFrance\\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SalesPaymentTransExtFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Internet Information Services (IIS) Retail Server site location.
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
2. In the **Extensions.SequentialSignatureFrance\\bin\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureFrance" />
    ```

#### SequentialSignatureRegister component

1. Find the **Runtime.Extensions.SalesTransactionSignatureSample** project.

2. Modify the **App.config** file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions. The **certificateThumbprint** property is the only mandatory property. It must be a 40 character-long string without any delimiters. See [How to retrieve the thumbprint of a certificate](https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate) for more details.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
        <configSections>
            <section name="SalesTransactionSignature" type="Microsoft.Dynamics.Commerce.Runtime.SalesTransactionSignatureSample.Configuration.SalesTransactionSignatureConfigSection, Microsoft.Dynamics.Commerce.Runtime.SalesTransactionSignatureSample"/>
        </configSections>
        <SalesTransactionSignature certificateThumbprint="insert key certificateThumbprint here" certificateStoreLocation="LocalMachine" certificateStoreName="My"/>
        <startup>
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5.1"/>
        </startup>
    </configuration>
    ```

3. Build the project.

4. In the **Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the following files:

    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll** assembly file
    - The **Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config** configuration file

5. Copy the files to the CRT extension folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

6. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

7. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

#### SequentialSignatureRegister.Contracts component

1. Find the **Runtime.Extensions.SequentialSignatureRegister.Contracts** project, and build it.
2. In the **Extensions.SequentialSignatureRegister.Contracts\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

#### XZReportsFrance component

1. Find the **Runtime.Extensions.XZReportsFrance** project, and build it.
2. In the **Extensions.XZReportsFrance\\bin\Debug** folder, find the **Contoso.Commerce.Runtime.XZReportsFrance.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
    ```

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

### Retail proxy extension component

> [!NOTE]
> Steps in this section are required to enable the extensions in the offline mode of Modern POS

#### SalesTransactionSignature Retail proxy sample component

1. In the **RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions.SalesTransactionSignatureSample** folder, find the **RetailServer.Extensions.SalesTransactionSignatureSample** project, and build it.

2. In the **RetailProxy\\RetailProxy.Extensions.SalesTransactionSignatureSample\\bin\\Debug** folder, find the **Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample** assembly file.

3. Copy the assembly files to the **\\ext** folder under the local CRT client broker location.

4. Register the Retail proxy change in the extensions configuration file. The file is named **RetailProxy.MPOSOffline.ext.config**, and it's under the local CRT client broker location.

    ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
    ```

### Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Include the following existing source code folders in the **Pos.Extensions** project.

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - RestrictingShiftDuration
    - SalesTransBuildNumberSample

    > [!Note]
    > Click the button ```Show All Files``` in the Solution Explorer to view all files in the project folder and not just those that are included in the project. If the button is not available, make sure you selected the project. Files and folders that are not currently part of the project will have their icons shown with dotted outlines. Right-click the folder you want to include and select Include in Project.

3. Enable the extensions to be compiled by removing the following folders from the exclude list in **tsconfig.json**:

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - RestrictingShiftDuration
    - SalesTransBuildNumberSample

4. Enable the extensions to be loaded by adding the following lines in **extensions.json**:

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

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

5. Rebuild the solution.

6. Run Modern POS in the debugger, and test the functionality.


### Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.

2. Include the following existing source code folders in the **Pos.Extensions** project.

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - RestrictingShiftDuration
    - SalesTransBuildNumberSample

    > [!Note]
    > Click the button ```Show All Files``` in the Solution Explorer to view all files in the project folder and not just those that are included in the project. If the button is not available, make sure you selected the project. Files and folders that are not currently part of the project will have their icons shown with dotted outlines. Right-click the folder you want to include and select Include in Project.

3. Enable the extensions to be compiled by removing the following folders from the exclude list in **tsconfig.json**:

    - SalesTransactionSignatureSample
    - SequentialSignature
    - AuditEventSignatureSample
    - RestrictingShiftDuration
    - SalesTransBuildNumberSample

4. Enable the extensions to be loaded by adding the following lines in **extensions.json**:

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

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

5. Rebuild the solution.

6. Run the solution by using the Run command and following the steps in the Retail SDK handbook.

7. Test the functionality.

## Production environment

Follow these steps to create deployable packages that contain Retail components, and to apply those packages in a production environment.

1. Complete the above **Cloud POS extension components** or **Modern POS extension components** sections.

2. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section:

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

        Add the following line to use a certificate for digital signing stored in an Azure Key Vault storage:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.DigitalSignatureKeyVaultSample" />
        ```

        > [!NOTE]
        > Complete the section [Storing certificate for digital signing in Azure Key Vault](#storing-certificate-for-digital-signing-in-azure-key-vault) first.

    2. In the **RetailProxy.MPOSOffline.ext.config** configuration file, add the following lines to the **composition** section:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample" />
        ```

3. Make the following changes in the **Customization.settings** package customization configuration file:

    1. Add the following lines to the **ItemGroup** section to include the Retail proxy extension in the deployable packages:

        ``` xml
            <ISV_RetailProxy_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.RetailProxy.SalesTransactionSignatureSample.dll" />
        ```

    2. Add the following lines to the **ItemGroup** section to include the CRT extensions in the deployable packages:

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
        
        Add the following line to use a certificate for digital signing stored in an Azure Key Vault storage:

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DigitalSignatureKeyVaultSample.dll" />
        ```

        > [!NOTE]
        > Complete the section [Storing certificate for digital signing in Azure Key Vault](#storing-certificate-for-digital-signing-in-azure-key-vault) first.

    3. Add the following lines to the **ItemGroup** section to include the Retail Server extension in the deployable packages:

        ``` xml
            <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        ```

4. Update the Retail Server configuration file. In **RetailSDK\\Packages\\RetailServer\\Code\\web.config** add the following lines to the **extensionComposition** section:

    ``` xml
        <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

5. Modify the certificate's configuration file by specifying the thumbprint, store location, and store name for the certificate that should be used to sign sales transactions. Then copy the configuration file to the **References** folder. The file is named **Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config** and is located under **Extensions.SequentialSignatureRegister\\bin\\Debug**.

6. Override the build number and the category and number of the certificate of compliance, if needed. See instructions in the section [Specifying application attributes to be printed in receipts](#specifying-application-attributes-to-be-printed-in-receipts) for more details.

7. Open MSBuild Command Prompt for Visual Studio utility and run **msbuild** under Retail SDK folder to create deployable packages.

8. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

### Enable the digital signature in offline mode for Modern POS

To enable the digital signature in offline mode for Modern POS, you must follow these steps after you activate Modern POS on a new device.

1. Sign in to POS.
2. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending downloads** field is **0** (zero), the database is fully synchronized.
3. Sign out of POS.
4. Wait a while for the offline database to be fully synchronized.
5. Sign in to POS.
6. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synchronized.
7. Restart Modern POS.
