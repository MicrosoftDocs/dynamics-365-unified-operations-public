---
# required metadata

title: Control unit integration sample for Sweden
description: This topic provides an overview of the fiscal integration sample for Sweden.
author:
manager: annbe
ms.date: 10/08/2019
ms.topic: article
ms.prod:
ms.service: dynamics-365-retail
ms.technology:

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang:
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Sweden
ms.search.industry: Retail
ms.author: sepism
ms.search.validFrom: 2019-10-08
ms.dyn365.ops.version: 10.0.7

---
# Control unit integration sample for Sweden

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This sample fiscal integration functionality replaces the earlier [Sample for POS integration with control units for Sweden](retail-sdk-control-unit-sample.md). The earlier sample doesn't take advantage of the [fiscal integration framework](./fiscal-integration-for-retail-channel.md) and will become obsolete in later updates. For information about how to migrate from the earlier sample to the current sample, see the [Migrating from the earlier integration sample](#migrating-from-the-earlier-integration-sample) section.

## Introduction

The Commerce functionality for Sweden includes a sample integration of the point of sale (POS) with Sweden-specific fiscal devices that are known as *control units*. This sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It's assumed that a control unit is physically connected to a Hardware station that the POS is paired with. As an example, this sample uses the application programming interface (API) of the [CleanCash Type A](https://www.retailinnovation.se/produkter) control unit by Retail Innovation HTT AB. Version 1.1.4 of the CleanCash API is used.

The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from Retail Innovation HTT AB. For information about how to get the control unit and operate it, contact [Retail Innovation HTT AB](https://www.retailinnovation.se/).

## Scenarios

The control unit integration sample for Sweden includes the following capabilities:

- Sales, returns, and receipt copies are automatically registered in a control unit that is connected to the Hardware station that is paired with the POS.
- The control code and the manufacturing number of the control unit for a registered transaction are captured from the control unit and saved in the transaction. This data is also referred to as a *fiscal response*. The fiscal response can be viewed on the **Store transactions** page.
- Custom fields for the control code and the manufacturing number of the control unit can be added to a receipt layout. In that way, you can print the fiscal response for a transaction on a receipt.
- The fiscal response for a transaction is shown on the **Electronic journal (Sweden)** channel report.
- Several error handling options are available. Here are some examples:

    - Retry fiscal registration, if a retry is possible. You can retry fiscal registration if, for example, the control unit isn't connected, isn't ready, or isn't responding.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Verify the availability of the control unit before a new sales transaction is opened or a sales transaction is finalized.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is distributed as a part of the fiscal integration sample.

**Value-added tax (VAT) code mapping** sets device-specific value-added tax (VAT) codes to corresponding sales tax codes. VAT code mapping should have the following format:

*1 : code1 ; 2 : code2*

Here is an explanation of this format:

- *1* and *2* are device-specific VAT codes.
- A semicolon (;) is used as a separator.
- *code1* and *code2* are sales tax codes that are configured in Headquarters.

Control units support up to four different VAT codes. Therefore, the VAT code mapping might be set up as shown here:

*1 : code1 ; 2 : code2 ; 3 : code3 ; 4 : code4*

> [!NOTE]
> Multiple sales tax codes can be mapped to the same device-specific VAT code.

### Limitations of the sample

The control unit integration sample for Sweden doesn't currently support customer order scenarios.

## Setting up the integration with control units

For more information about the setup that is required for Sweden, see [Setting up Commerce for Sweden](./emea-swe-cash-registers.md#setting-up-commerce-for-sweden).

### Configuring Sweden–specific receipts

#### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or greater than 900001.

Add the following POS labels in the **POS** section of the **Language text** page.

| Language ID | Text ID | Text                  |
|-------------|---------|-----------------------|
| en-US       | 900001  | Register control code |
| en-US       | 900002  | Register device       |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                         | Type    | Caption text ID |
|------------------------------|---------|-----------------|
| SE_FISCALREGISTERCONTROLCODE | Receipt | 900001          |
| SE_FISCALREGISTERID          | Receipt | 900002          |

#### Configure receipt formats

For every receipt format that is required, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the **Footer** section. Note that field names correspond to the language texts that you defined in the previous section of this topic.

- **Register control code** – This field prints the control code.
- **Register device** – This field prints the manufacturing number of the control unit.

For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

### Configure fiscal integration

Complete the fiscal integration setup steps that are described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md):

- [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Be sure to note the settings for the fiscal registration process that are [specific to this control unit integration sample](#set-up-the-registration-process).
- [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
- [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).

## Deployment guidelines for cash registers for Sweden

This topic serves as a deployment guide that shows how to enable the localization of Microsoft Dynamics 365 Commerce for Sweden. The localization is part of the Retail SDK. For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT), POS, and Hardware station. To run this sample, you must modify and build the CRT and Hardware station projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Azure DevOps, where no files have been changed yet.

Follow these steps to configure a development environment so that you can test and extend the sample. You must also complete all the required setup tasks that are described in the [Setting up the integration with control units](#setting-up-the-integration-with-control-units) section.

### Enable CRT extensions

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### DocumentProvider.CleanCashSample component

1. Find the **Runtime.Extensions.DocumentProvider.CleanCashSample** project, and build it.
2. In the **Runtime.Extensions.DocumentProvider.CleanCashSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Commerce Scale Unit:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample" />
    ```

#### Update the extension configuration file

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsSweden" />
    ```

### Enable Hardware station extensions

The Hardware station extension components are included in the Hardware station samples. To complete the following procedures, open the solution, **HardwareStationSamples.sln.sln**, under **RetailSdk\\SampleExtensions\\HardwareStation**.

#### CleanCash component

1. Find the **HardwareStation.Extension.CleanCashSample** project, and build it.
2. In the **Extension.CleanCashSample\\bin\\Debug** folder, find the **Contoso.Commerce.HardwareStation.CleanCashSample.dll** assembly file.
3. Copy the assembly file to the Hardware station extensions folder:

    - **Shared hardware station:** Copy the file to the **bin** folder under the IIS Hardware station site location.
    - **Dedicated hardware station on Modern POS:** Copy the file to the Modern POS client broker location.

4. Find the extension configuration file for the Hardware station's extensions. The file is named **HardwareStation.Extension.config**.

    - **Shared hardware station:** The file is under the IIS Hardware station site location.
    - **Dedicated hardware station on Modern POS:** The file is under the Modern POS client broker location.

5. Add the following line to the **composition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.CleanCashSample.dll" />
    ```

### Enable Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Enable the extensions that must be loaded by adding the following lines in the **extensions.json** file.

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
2. Enable the extensions that must be loaded by adding the following lines in the **extensions.json** file.

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

### Set up the registration process

To enable the registration process, follow these steps to set up Headquarters. For more details, see [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the connector configuration. The file location is **RetailSdk\\SampleExtensions\\HardwareStation\\Extension.CleanCashSample\\Configuration\\ConnectorCleanCashSample.xml**.
3. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the document provider configuration. The file location is **RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.CleanCashSample\\Configuration\\DocumentProviderFiscalCleanCashSample.xml**.
4. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile, and select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
5. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Update the connection settings as required.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group for the connector functional profile that you created earlier.
7. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, create a fiscal registration process step, and select the fiscal connector group that you created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
9. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the control unit will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
10. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

### Production environment

The previous procedure enables the extensions that are components of the fiscal registration service integration sample. In addition to completing that procedure, you must follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section.

        ``` xml	
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsSweden" />
        ```

    - In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.CleanCashSample" />
        ```

2. Make the following changes in the **Customization.settings** package customization configuration file under the **BuildTools** folder:

    - Add the following lines to include the CRT extensions in the deployable packages.

        ``` xml
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample.dll" />
        ```

    - Add the following line to include the Hardware station extension in the deployable packages.

        ``` xml
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.CleanCashSample.dll" />
        ```

3. Enable the POS extension by adding the following lines in the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

    ``` json
    {
        "extensionPackages": [
            {
            "baseUrl": "Microsoft/AuditEvent.SE"
            }
        ]
    }
    ```

4. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
5. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Design of the extensions

### CRT extension design

The purpose of the extension that is a fiscal document provider is to generate service-specific documents and handle responses from the fiscal registration service.

The CRT extension is **Runtime.Extensions.DocumentProvider.CleanCashSample**.

For more details about the design of the fiscal integration solution, see [Fiscal registration process and fiscal integration samples for fiscal devices](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices).

#### Request handler
	
There is a single **DocumentProviderCleanCash** request handler for the document provider. This handler is used to generate fiscal documents for the fiscal registration service.

This handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a service-specific document that should be registered in the fiscal registration service.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, sales events and audit events are supported.

#### Configuration

The **DocumentProviderFiscalCleanCashSample** configuration file is in the **Configuration** folder of the extension project. The purpose of this file is to enable settings for the document provider to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- VAT codes mapping

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal registration service.

The Hardware station extension is **HardwareStation.Extension.CleanCashSample**. It uses the HTTP protocol to submit documents that the CRT extension generates to the fiscal registration service. It also handles the responses that are received from the fiscal registration service.

#### Request handler

The **CleanCashHandler** request handler is the entry point for handling requests to the fiscal registration service.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to the fiscal registration service and returns a response from it.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the fiscal registration service.
- **InitializeFiscalDeviceRequest** – This request is used to initialize the fiscal registration service.

#### Configuration

The configuration file is in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the fiscal connector to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- **Connections string** – The control unit connection settings.
- **Timeout** – The amount of time, in milliseconds, that the driver will wait for a response from the fiscal registration service.

## Migrating from the earlier integration sample

If you're using the earlier [Sample for POS integration with control units for Sweden](retail-sdk-control-unit-sample.md), you might have to migrate from it to the current integration sample. To uptake the change and receive timely updates for the features for Sweden in the future, you might have to upgrade, make minor code and configuration adjustments in the extensions that you built, and rebuild your solutions. No major changes are required in the extension logic that you created. The earlier integration sample and your customizations will continue to work if no changes are made from your side. Therefore, you can plan, prepare for, and do the uptake for your environment.

### Migration process

The migration from the earlier integration sample to the current control unit integration sample should be based on the concept of a gradual update. In other words, all Headquarters and Commerce Scale Unit components should already be updated before you start to update the POS and Hardware station components.

To help prevent a situation where an event or transaction is signed twice (that is, it's signed by both the earlier extension and the current extension), or where it can't be signed because of the missing configuration, we recommend that you turn off all POS and Hardware station devices that use the earlier sample, and then update them simultaneously. This simultaneous update can be done, for example, on a store-by-store basis by updating the store's functionality profile and the Hardware station's hardware profile.

The migration process should consist of the following steps.

1. Update the Headquarters components.
1. Update the Commerce Scale Unit components, and enable the extensions of the current sample.
1. Make sure that all offline transactions are synced from offline-enabled MPOS devices.
1. Turn off all devices that use the components of the earlier sample.
1. Complete the setup tasks that are described in the [Setting up the integration with control units](#setting-up-the-integration-with-control-units) section.
1. Update the POS and Hardware station components, disable the extensions that are parts of the earlier sample, and enable the extensions of the current sample.

    > [!NOTE]
    > Depending on the type of environment, you can find more technical details about the migration process in either the [Migration in a development environment](#migration-in-a-development-environment) section or the [Migration in a production environment](#migration-in-a-production-environment) section.

### Migration in a development environment

#### Update CRT

1. Find the **Runtime.Extensions.DocumentProvider.CleanCashSample** project, and build it.
2. In the **Runtime.Extensions.DocumentProvider.CleanCashSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:

    - **Commerce Scale Unit:** Copy the assembly to the **\\bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **CommerceRuntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's in the **bin\\ext** folder under the local CRT client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

5. Find and remove the earlier CRT extension from the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.FiscalRegisterReceiptSample" />
    ```

    > [!WARNING]
    > Don't complete this step until you update all POS devices that work with this CRT instance.

6. Register the current sample CRT extensions in the extension configuration file by adding the following lines.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsSweden" />
    ```

#### Update Hardware station

1. Find the **HardwareStation.Extension.CleanCashSample** project, and build it.
2. In the **Extension.CleanCashSample\\bin\\Debug** folder, find the **Contoso.Commerce.HardwareStation.CleanCashSample.dll** assembly file.
3. Copy the assembly file to the Hardware station extensions folder:

    - **Shared hardware station:** Copy the file to the **bin** folder under the IIS Hardware station site location.
    - **Dedicated hardware station on Modern POS:** Copy the file to the Modern POS client broker location.

4. Find the **HardwareStation.Extension.config** extension configuration file:

    - **Remote Hardware station:** The file is under the IIS Hardware station site location.
    - **Local Hardware station on Modern POS:** The file is under the Modern POS client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

5. Find and remove the earlier Hardware station extension from the extension configuration file.

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

6. Add the following line to the **composition** section of the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.CleanCashSample.dll" />
    ```

#### Update Modern POS

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
2. Disable the earlier POS extension by removing the following lines from the **extensions.json** file.

    ``` json
    {
        "baseUrl": "FiscalRegisterSample"
    }
    ```

2. Enable the current sample POS extension by adding the following lines in the **extensions.json** file.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AuditEvent.SE"
            }
        ]
    }
    ```

#### Update Cloud POS

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. Disable the earlier POS extension by removing the following lines from the **extensions.json** file.

    ``` json
    {
        "baseUrl": "FiscalRegisterSample"
    }
    ```

2. Enable the current sample POS extension by adding the following lines in the **extensions.json** file.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AuditEvent.SE"
            }
        ]
    }
    ```

### Migration in a production environment

#### Update CRT

1. Remove the earlier CRT extension from the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.FiscalRegisterReceiptSample" />
    ```

    > [!WARNING]
    > Don't complete this step until you update all POS devices that work with this CRT instance.

2. Enable the current sample CRT extensions by making the following changes in the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder.

    ``` xml	
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsSweden" />
    ```

3. In the **Customization.settings** package customization configuration file under the **BuildTools** folder, add the following lines to include the current sample CRT extension in deployable packages.

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample.dll" />
    ```

#### Update Hardware station

1. Remove the earlier Hardware station extension by modifying the **HardwareStation.Extension.config** configuration file.

    # [Retail 7.3 and earlier](#tab/retail-7-3)

    Remove the following section from the **HardwareStation.Shared.config** and **HardwareStation.Dedicated.config** configuration files.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
    ```

    # [Retail 7.3.1 and later](#tab/retail-7-3-1)

    Remove the following section from the **HardwareStation.Extension.config** configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample" />
    ```

    # [Retail 10.0 and later](#tab/retail-10-0)

    Remove the following section from the **HardwareStation.Extension.config** configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.FiscalRegisterSample" />
    ```
    ---

2. Enable the current sample Hardware station extension by adding the following line to the **composition** section in the **HardwareStation.Extension.config** configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.CleanCashSample" />
    ```

3. Make the following changes in the **Customization.settings** package customization configuration file under the **BuildTools** folder:

    - Remove the following lines to exclude the earlier Hardware station extension from deployable packages.

        ``` xml 
        <ISV_CommerceRuntime_CustomizableFileInclude="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample.dll" />
        ```

    - Add the following line to include the current sample Hardware station extension in deployable packages.

        ``` xml
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.CleanCashSample.dll" />
        ```

#### Update Modern POS

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the **FiscalRegisterSample** folder to the exclude list.
    - Remove the following lines from the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

        ``` json
        {
            "baseUrl": "FiscalRegisterSample"
        }
        ```

3. Enable the current sample POS extension by adding the following lines in the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AuditEvent.SE"
            }
        ]
    }
    ```

#### Update Cloud POS

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the **FiscalRegisterSample** folder to the exclude list.
    - Remove the following lines from the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

        ``` json
        {
            "baseUrl": "FiscalRegisterSample"
        }
        ```

4. Enable the current sample POS extension by adding the following lines in the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AuditEvent.SE"
            }
        ]
    }
    ```

#### Create deployable packages

Run **msbuild** for the whole Retail SDK to create deployable packages. Apply the packages via LCS or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
