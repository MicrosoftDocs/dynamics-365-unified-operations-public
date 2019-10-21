---
# required metadata

title: Deployment guidelines for cash registers for Sweden
description: This topic is a deployment guide for the Retail localization for Sweden.
author: 
manager: annbe
ms.date: 10/08/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Sweden
ms.search.industry: Retail
ms.author: sepism
ms.search.scope: Retail
ms.search.validFrom: 2019-10-08
ms.dyn365.ops.version: 10.0.7

---
# Deployment guidelines for cash registers for Sweden

[!include[banner](../includes/banner.md)]

## Introduction

This topic is a deployment guide that shows how to enable the Dynamics 365 Retail localization for Sweden. The localization consists of several extensions of Retail components. For more information about the Retail localization for Sweden, see [Control unit integration sample for Sweden](./emea-swe-fi-sample.md).

This localization is part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the CRT and Hardware station. To run this sample, you must modify and build the CRT and Hardware station projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet. Follow these steps to set up a development environment so that you can test and extend the sample.


### Enable Commerce runtime extensions

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.


#### DocumentProvider.CleanCashSample component

1. Find the **Runtime.Extensions.DocumentProvider.CleanCashSample** project, and build it.
2. In the **Runtime.Extensions.DocumentProvider.CleanCashSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

   - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
   - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

   - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
   - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample" />
    ```


#### Update extension configuration file

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsSweden" />
    ```


### Enable Hardware station extensions

The Hardware station extension components are included in the Hardware station samples. To complete the following procedures, open the solution, **HardwareStationSamples.sln.sln**, under **RetailSdk\\SampleExtensions\\HardwareStation**.


#### CleanCash component

1. Find the **HardwareStation.Extension.CleanCashSample** project, and build it.
2. In the **Extension.CleanCashSample\\bin\\Debug** folder, find following files:

   - The **Contoso.Commerce.HardwareStation.CleanCashSample.dll** assembly

3. Copy the assembly files to the Hardware station extensions folder:

   - **Shared hardware station:** Copy the files to the **bin** folder under the IIS Hardware station site location.
   - **Dedicated hardware station on Modern POS:** Copy the files to the Modern POS client broker location.

4. Find the extension configuration file for the Hardware station's extensions. The file is named **HardwareStation.Extension.config**.

   - **Shared hardware station:** The file is located under the IIS Hardware station site location.
   - **Dedicated hardware station on Modern POS:** The file is located under the Modern POS client broker location.

5. Add the following line to the **composition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.CleanCashSample.dll" />
    ```

### Enable Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Enable the extensions to be loaded by adding the following lines in **extensions.json**.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AuditEvent.SE"
            }
        ]
    }
    ```

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

3. Rebuild the solution.
4. Run Modern POS in the debugger, and test the functionality.


### Enable Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Enable the extensions to be loaded by adding the following lines in **extensions.json**.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AuditEvent.SE"
            }
        ]
    }
    ```

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

3. Rebuild the solution.
4. Run the solution by using the **Run** command and following the steps in the Retail SDK handbook.


### Production environment

The previous procedure enables the extensions that are components of the fiscal registration service integration sample. In addition, you must follow these steps to create deployable packages that contain Retail components, and to apply those packages in a production environment.

1. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder.

   - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section.

        ``` xml	
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsSweden" />
        ```

   - In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.CleanCashSample" />
        ```

2. Make the following changes in the **BuildTools\\Customization.settings** package customization configuration file.

   - Add the following lines to include the CRT extensions in the deployable packages.

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample.dll" />
        ```

   - Add the following line to include the Hardware station extension in the deployable packages.

        ``` xml
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.CleanCashSample.dll" />
        ```

3. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
4. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create retail deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
5. Complete all the required setup tasks that are described in the [Set up Retail for Sweden](#set-up-retail-for-sweden) section.


## Design of extensions

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate service-specific documents and handle responses from the fiscal registration service.

The CRT extension is **Runtime.Extensions.DocumentProvider.CleanCashSample**.

For more details about the design of the fiscal integration solution, see [Fiscal registration process and fiscal integration samples for fiscal devices](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices).


#### Request handler
	
There is a single **DocumentProviderCleanCash** request handler for document provider, which is used to generate fiscal documents for the fiscal registration service.

This handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Retail Headquarters.

The connector supports the following requests.

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a service-specific document that should be registered in the fiscal registration service.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales and audit events.


#### Configuration

The **DocumentProviderFiscalCleanCashSample** configuration file is located in the **Configuration** folder of the extension project.
The purpose of this file is to enable settings for the document provider to be configured from Retail Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added.

- VAT codes mapping


### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal registration service.

The Hardware station extension is **HardwareStation.Extension.CleanCashSample**. The Hardware station extension uses the HTTP protocol to submit documents that the CRT extension generates to the fiscal registration service. It also handles the responses that are received from the fiscal registration service.


#### Request handler

The **CleanCashHandler** request handler is the entry point for handling requests to the fiscal registration service.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Retail Headquarters.

The connector supports the following requests.

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to the fiscal registration service and returns a response from it.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the fiscal registration service.
- **InitializeFiscalDeviceRequest** – This request is used to initialize the fiscal registration service.


#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the fiscal connector to be configured from Retail Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added.

- **Connections string** – The control unit connection settings.
- **Timeout** – The amount of time, in milliseconds, that the driver will wait for a response from the fiscal registration service.



## Migrate your code

As a part of the work to simplify the servicing process and enhance partner and customer development experience an important change in localization strategy for Dynamics 365 for Retail is planned. Localization features are going to be gradually moved from "Retail SDK samples" to "Sealed extensions" model of delivery.

In order to uptake to the change and get the timely updates for localization features in the future you may need to upgrade, recompile, or do some minor code and configuration changes in the extensions that you've built. No major changes will be required in the extension logic that you've created. Currently exsiting extensions and localization samples will continue working in case no changes are made from your side. This is done so that you can plan and prepare the uptake for your environment. 

In case you are planning to uptake fiscal integrastion for Sweden it's required to disable previously released sample extensions for Retail POS integration with control units for Sweden.


### Delopment environment

Disable extensions released previously.


#### Harware station extensions uptake

1. Find the **HardwareStation.Extension.config** extensions configuration file for CRT.

   - **Remote Hardware station:** The file is located under the IIS Hardware station site location.
   - **Local Hardware station on Modern POS:** The file is located under the Modern POS client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

2. Find and remove the Harware station sample registration in extensions configuration file:

    # [Retail 7.3 and earlier](#tab/retail-7-3)

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
    ```

    # [Retail 7.3.1 and later](#tab/retail-7-3-1)

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
    ```

    # [Retail 10.0 and later](#tab/retail-10-0)

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.FiscalRegisterSample" />
    ```

    ---

#### CRT extensions uptake

1. Find the extensions configuration file for CRT:

   - **Retail Server:** The file is named **CommerceRuntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail server site location.
   - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the bin\ext folder under the local CRT client broker location

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

2. Find and remove the CRT sample registration in extensions configuration file:

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.FiscalRegisterReceiptSample" />
    ```


#### Modern POS extensions uptake

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**

2. Disable the sample extension from loading by removing the lines from **extensions.json**:
    ``` json
    {
        "baseUrl": "FiscalRegisterSample"
    }
    ```

#### Cloud POS extensions uptake

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**

2. Disable the sample extension from loading by removing the lines from **extensions.json**:
    ``` json
    {
        "baseUrl": "FiscalRegisterSample"
    }
    ```


### Production environment

1. Complete the steps in the [Modern POS extensions uptake](#Modern-POS-extensions-uptake) and [Cloud POS extensions uptake](#Cloud-POS-extensions-uptake) sections earlier in this topic.

2. Remove the old the CRT sample registration in the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder:

    ``` xml
    <add source="type" value="Contoso.Commerce.Runtime.FiscalRegisterReceipt, Contoso.Commerce.Runtime.FiscalRegisterReceipt" />
    ```

3. Modify the **HardwareStation.Extension.config** Hardware station configuration file.

        # [Retail 7.3 and earlier](#tab/retail-7-3)

        Remove the following section from the **HardwareStation.Shared.config** and **HardwareStation.Dedicated.config** configuration files.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
        ```

        # [Retail 7.3.1 and later](#tab/retail-7-3-1)

        Remove the following section from the **HardwareStation.Extension.config** configuration file:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
        ```
        
        # [Retail 10.0 and later](#tab/retail-10-0)

        Remove the following section from the **HardwareStation.Extension.config** configuration file:

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.FiscalRegisterSample" />
        ```

        ---

Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
