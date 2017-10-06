---
# required metadata

title: Deployment guidelines for cash registers for Norway
description: This topic is a deployment guide for the Retail localization for Norway
author: AlexChern0v
manager: olegkl
ms.date: 09/22/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Developer
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Retail
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Norway
ms.search.industry: Retail
ms.author: v-alexec
ms.search.validFrom: 2017-10-15
# ms.dyn365.ops.version: App update 4
---
# Deployment guidelines for cash registers for Norway

**SAMPLE CODE NOTICE**

**THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED, OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.  THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.**

**NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.**

This guide demonstrates how to enable the Microsoft Dynamics 365 for Retail localization for Norway. The localization consists of a number of extensions of Dynamics 365 for Retail components, including extensions for printing of custom fields in receipts, registration of additional audit events and sales and payment transactions in Point of Sale, digital signing of sales transactions, and printing of X/Z reports in local formats. For more information on the Microsoft Dynamics 365 for Retail localization for Norway, see [Cash registers for Norway](./emea-nor-cash-registers.md).

This sample is a part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT), Retail Server (RS) and point of sale (POS). To run this sample, you must modify and build the CRT, RS and POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

## Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

### The CRT extension components

The CRT extension components are included in CommerceRuntime samples. For following paragraphs open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\SampleExtensions\CommerceRuntime**.

#### ReceiptsNorway component
1. Find the ***Runtime.Extensions.ReceiptsNorway*** project and build it.

2. Locate the ***Contoso.Commerce.Runtime.ReceiptsNorway.dll*** assembly file in *`Extensions.ReceiptsNorway\bin\Debug`* folder.

3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the *`\bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the *`\ext`* folder under the local CRT client broker location.

4. Locate the extensions configuration file for CRT:
    - **Retail Server:** The file is named ***commerceruntime.ext.config*** and located in *`bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named ***CommerceRuntime.MPOSOffline.Ext.config***, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
    ```

    > [!NOTE]
    > Do **not** edit the *commerceruntime.config* and *CommerceRuntime.MPOSOffline.config* files. These files are not intended for any customizations.

#### RegisterAuditEvent sample component
1. Find the ***Runtime.Extensions.RegisterAuditEventSample*** project, and build it.
2. Locate the ***Contoso.Commerce.Runtime.RegisterAuditEventSample.dll*** assembly file in *`Extensions.RegisterAuditEventSample\bin\Debug`* folder

3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the *`\bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the *`\ext`* folder under the local CRT client broker location.

4. Locate the extensions configuration file for CRT:
    - **Retail Server:** The file is named ***commerceruntime.ext.config*** and located in *`bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named ***CommerceRuntime.MPOSOffline.Ext.config***, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
    ```

    > [!NOTE]
    > Do **not** edit the ***commerceruntime.config*** and ***CommerceRuntime.MPOSOffline.config*** files. These files are not intended for any customizations.

#### SalesPaymentTransExt component
1. Find the ***Runtime.Extensions.SalesPaymentTransExt*** project and build it.
2. Locate the ***Contoso.Commerce.Runtime.SalesPaymentTransExt.dll*** assembly file in *`Extensions.SalesPaymentTransExt\bin\Debug`* folder

3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the *`\bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the *`\ext`* folder under the local CRT client broker location.

4. Locate the extensions configuration file for CRT:
    - **Retail Server:** The file is named ***commerceruntime.ext.config*** and located in *`bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named ***CommerceRuntime.MPOSOffline.Ext.config***, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    ```

    > [!NOTE]
    > Do **not** edit the *commerceruntime.config* and *CommerceRuntime.MPOSOffline.config* files. These files are not intended for any customizations.

#### SalesTransactionSignature sample component
1. Find the ***Runtime.Extensions.SalesTransactionSignatureSample*** project.

2. Modify the ***App.config*** to specify Thumbprint, store location and store name for certificate you want to use for sales transaction signing, then build the project

3. Find the following files in *`Extensions.SalesTransactionSignatureSample\bin\Debug`* folder:
    - The ***Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll*** assembly
    - The ***Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config*** configuration file

3. Copy above files to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the *`\bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the *`\ext`* folder under the local CRT client broker location.

4. Locate the extensions configuration file for CRT:
    - **Retail Server:** The file is named ***commerceruntime.ext.config*** and located in *`bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named ***CommerceRuntime.MPOSOffline.Ext.config***, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

    > [!NOTE]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files are not intended for any customizations.

#### XZReportsNorway component
1. Find the ***Runtime.Extensions.XZReportsNorway*** project and build it.
2. Locate the ***Contoso.Commerce.Runtime.XZReportsNorway.dll*** assembly file in *`Extensions.XZReportsNorway\bin\Debug`* folder
3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the *`\bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the *`\ext`* folder under the local CRT client broker location.

4. Locate the extensions configuration file for CRT:
    - **Retail Server:** The file is named ***commerceruntime.ext.config*** and located in *`bin\ext`* folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named ***CommerceRuntime.MPOSOffline.Ext.config***, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
    ```

    > [!NOTE]
    > Do **not** edit the *commerceruntime.config* and *CommerceRuntime.MPOSOffline.config* files. These files are not intended for any customizations.

### The Retail Server extension components

#### SalesTransactionSignature RS sample component

1. Find the ***RetailServer.Extensions.SalesTransactionSignatureSample*** project in *`RetailSDK\SampleExtensions\RetailServer\RetailServer.Extensions.SalesTransactionSignatureSample`* folder and build it

2. Locate the ***Contoso.RetailServer.SalesTransactionSignatureSample.dll*** assembly file in *`RetailServer\Extensions.SalesTransactionSignatureSample\bin\Debug`* folder

3. Copy the assembly file to the *`\bin`* folder under the IIS Retail Server site location.

4. Locate the configuration file for RS. The file is named ***web.config*** and located in root folder under the IIS Retail Server site location.

5. Register the RS extensions in ***extensionComposition*** section of configuration file.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

6. Register RS extension dependencies

    1. Find the following files in *`CommerceRuntime\Extensions.SalesTransactionSignatureSample\bin\Debug`*:
        - The ***Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll*** assembly
        - The ***Contoso.Commerce.Runtime.SalesTransactionSignatureSample.dll.config*** configuration file
    2. Copy above files to the *`\bin`* folder under the IIS Retail Server site location.

    3. Register the CRT change in the extensions configuration file for CRT, naming ***commerceruntime.ext.config***, and locating in *`bin`* folder under the IIS Retail Server site location.

    ``` xml
       <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
    ```

    > [!NOTE]
    > Do **not** edit the *commerceruntime.config* file. This file is not intended for any customizations.
    > 
    > This part is similar to including SalesTransactionSignature CRT extension component, but uses different destination folder: *`bin`*  instead of *`bin\ext`*, this is required for successful loading of RS extension.

### The Modern POS extension components

#### Implement the proxy code for offline mode 

This part is equivalent to the Retail Server controller, but it extends the local Commerce Runtime used when the client is not connected.

1. Change the @(RetailServerLibraryPathForProxyGeneration) section of *`customization.settings`* to use the new Retail Server assembly for proxy generation.

2. Implement the following interface methods in the ***StoreOperationsManager*** class. For the first iteration, add the following code:

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

3. In order to regenerate the proxy code, build the Proxies folder from command line (`msbuild /t:Rebuild`).

4. Open *`RetailSDK\Proxies\RetailProxy\Proxies.RetailProxy.csproj`*, add *`RetailSDK\SampleExtensions\CommerceRuntime\Extensions.SalesTransactionSignatureSample\CommerceRuntime.Extensions.SalesTransactionSignatureSample`* project to the solution and add a project reference to the ***RetailProxy*** project referencing ***SalesTransactionSignatureSample***.

5. Adjust the interface methods in the ***StoreOperationsManager*** class:

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

6. Update ***dllhost.exe.config*** so that the Client Broker will load new RetailProxy assembly
    ``` xml
        <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy" />
        <add key="AdaptorCallerFullTypeName" value="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller" />
    ```

#### Modern POS extensions components

1. Open the solution at ***RetailSdk\POS\ModernPOS.sln***, and make sure that it can be compiled without errors. Also make sure that Modern POS can be run from Microsoft Visual Studio using the **Run** command. (Modern POS must not be customized. You must enable User Account Control [UAC], and you must uninstall previously installed instances of Modern POS as required.)

2. Include existing ***AuditEventExtensionSample*** and ***SalesTransactionSignatureSample*** source code folders in the ***Pos.Extensions*** project.

3. Enable the extensions compiling in ***tsconfig.json*** by removing ***AuditEventExtensionSample*** and ***SalesTransactionSignatureSample*** folders from the exclude list.

4. Enable the extensions loading in ***extensions.json*** by adding the following lines in the appropriate place.

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    > [!NOTE]
    > Refer to ***readme.md*** instructions file in ***Pos.Extensions*** project for more details and samples how-to include source code folder and enable extensions loading

5. Rebuild the solution.

6. Run Modern POS in the debugger, and test the functionality.

### The Cloud POS extension components

1. Open the solution at **RetailSdk\POS\CloudPOS.sln**, and make sure it can be compiled without errors.

2. Include existing ***AuditEventExtensionSample*** and ***SalesTransactionSignatureSample*** source code folders in the ***Pos.Extensions*** project.

3. Enable the extensions compiling in ***tsconfig.json*** by removing ***AuditEventExtensionSample*** and ***SalesTransactionSignatureSample*** folders from the exclude list.

4. Enable the extensions loading in ***extensions.json*** by adding the following lines in the appropriate place.

    ``` json
    {
        "baseUrl": "AuditEventExtensionSample"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    }
    ```

    > [!NOTE]
    >
    > Refer to ***readme.md*** instructions file in Pos.Extensions project for more details and samples how-to include source code folder and enable extensions loading

5. Rebuild the solution.

6. Run the solution using the **Run** command and following the steps in the Retail SDK handbook.

7. Test the functionality.

### Set up required parameters in Retail Headquarters.

For more information, see [Cash registers for Norway](./emea-nor-cash-registers.md).

## Production environment

Follow these steps to create and apply deployable packages that contain Retail components in a production environment.

1. Make the following changes in the package configuration files under the **RetailSdk\Assets** folder:

    1. Add the following lines to the **composition** section of the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsNorway" />
        <add source="assembly" value="Contoso.Commerce.Runtime.RegisterAuditEventSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <add source="assembly" value="Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
        <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsNorway" />
        ```

    2. Add the following lines to the **appSettings** subsection of the **configuration** section of the **dllhost.exe.config** configuration file.

        ``` xml
        <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy"/>
        <add key="AdaptorCallerFullTypeName" value ="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller"/>
        ```

2. Make the following changes in the package customization configuration file **Customization.settings**
    1. Add the following lines to **```<ItemGroup Condition="'@(RetailServerLibraryPathForProxyGeneration)' == ''">```** section
        ``` xml
        <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll"/>
        ```

    2. Add following lines to **ItemGroup** section to include CRT extensions to deployable packages

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsNorway" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.RegisterAuditEventSample" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesTransactionSignatureSample" />
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsNorway" />
        ```

    3. Add following lines to **ItemGroup** section to include RS extension to deployable packages
        ``` xml
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        ```

3. Run **msbuild** for the whole Retail SDK to create deployable packages.

4. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
