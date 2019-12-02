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
> This sample fiscal integration functionality replaces the legacy [Sample for Retail POS integration with control units for Sweden](retail-sdk-control-unit-sample.md). The legacy sample does not take advantage of the [fiscal integration framework](./fiscal-integration-for-retail-channel.md) and will be deprecated in later updates. To learn how to migrate from the legacy sample to this sample, see the [Migrating from legacy integration sample](#migrating-from-legacy-integration-sample) section.

## Introduction

The Retail functionality for Sweden includes a sample integration of the point of sale (POS) with Sweden-specific fiscal devices called control units. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It's assumed that a control unit is physically connected to a Hardware station that POS is paired with. As an example, this sample uses the application programming interface (API) of the [CleanCash® Type A](https://www.retailinnovation.se/produkter) control unit by Retail Innovation HTT AB. Version 1.1.4 of the CleanCash® API is used. 

The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from Retail Innovation HTT AB. For information about how to get the control unit and operate it, contact [Retail Innovation HTT AB](https://www.retailinnovation.se/).

## Scenarios

The control unit integration sample for Sweden includes the following capabilities:

- Sales, returns, and receipt copies are automatically registered in a control unit that is connected to the Hardware station that is paired with the POS.
- The control code and the manufacturing number of the control unit for a registered transaction are captured from the control unit and saved in the transaction. This data is also referred to as *fiscal response*. The fiscal response can be viewed on the **Retail store transactions** page.
- Custom fields for the control code and the manufacturing number of the control unit can be added to a receipt layout, so that you can print the fiscal response for a transaction on a receipt.
- The fiscal response for a transaction is displayed in the **Electronic journal (Sweden)** channel report. 
- Error handling, such as the following options:
  - Retry fiscal registration if a retry is possible, such as if the control unit isn't connected, isn't ready or isn't responding.
  - Postpone fiscal registration.
  - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
  - Check the availability of the control unit before a new sales transaction is opened or a sales transaction is finalized.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is distributed as a part of the fiscal integration sample.

- **Value-added tax (VAT) code mapping** sets respective device-specific VAT codes to sales tax codes. VAT code mapping should have the following format:

  *1 : code1 ; 2 : code2*

  Where 
    1, 2, etc. - device-specific VAT codes,
    ";" - separator,
    code1, code2 - sales tax codes that are configured in Retail Headquarters.

Control units support up to 4 different VAT code, so the VAT code mapping may be set up as shown below:

*1 : code1 ; 2 : code2 ; 3 : code3 ; 4 : code4*

    > [!NOTE]
    > Several sales tax codes can be mapped to the same device-specific VAT code.

### Limitations of the sample

  - Customer order scenarios are not supported in the Control unit integration sample for Sweden for now.


## Setting up integration with control units

For more details about general setting for Sweden see [Setting up Retail for Sweden](./emea-swe-cash-registers.md#setting-up-retail-for-sweden).

### Configuring Sweden–specific receipts

#### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

Add the following POS labels to the **POS** section of **Language text** from the table:

| Language ID | Text ID | Text                   |
|-------------|---------|------------------------|
| en-US       | 900001  | Register control code  |
| en-US       | 900002  | Register device        |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page:

| Name                           | Type    | Caption text ID |
|--------------------------------|---------|-----------------|
| SE_FISCALREGISTERCONTROLCODE   | Receipt | 900001          |
| SE_FISCALREGISTERID            | Receipt | 900002          |


#### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Footer:** Add the following fields.

    - **Register control code**: this field prints the control code.
    - **Register device**: this field prints the manufacturing number of the control unit.

For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).


### Configure fiscal integration

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Retail channels](setting-up-fiscal-integration-for-retail-channel.md):

- [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Note also the settings for the fiscal registration process that are [specific to this control unit integration sample](#set-up-the-registration-process).
- [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
- [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).

## Deployment guidelines for cash registers for Sweden

This deployment guide shows how to enable the Dynamics 365 Retail localization for Sweden. The localization is a part of the Retail software development kit (SDK), for information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md). 

This sample consists of extensions for CRT, POS and Hardware station. To run this sample, you must modify and build the CRT and Hardware station projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Azure DevOps, where no files have been changed yet. Follow these steps to set up a development environment so that you can test and extend the sample.

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

### Set up the registration process

To enable the registration process, follow these steps to set up Retail Headquarters. For more details, see [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Go to **Retail \> Headquarters setup \> Parameters \> Retail shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the connector configuration. The file location is **RetailSdk\\SampleExtensions\\HardwareStation\\Extension.CleanCashSample\\Configuration\\ConnectorCleanCashSample.xml**.
3. Go to **Retail \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the document provider configuration. The configuration file is  **RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.CleanCashSample\\Configuration\\DocumentProviderFiscalCleanCashSample.xml**.
4. Go to **Retail \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile. Select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
5. Go to **Retail \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Update the connection settings as required.
6. Go to **Retail \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group, for the connector functional profile that you created earlier.
7. Go to **Retail \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, a fiscal registration process step, and select the fiscal connector group that you created earlier.
8. Go to **Retail \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
9. Go to **Retail \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the control unit will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
10. Open the distribution schedule (**Retail \> Retail IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

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

3. Enable the POS extension:

    - Open RetailSDK\POS\Extensions\extensions.json and add the following lines:

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
5. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create retail deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
6. Complete all the required setup tasks that are described in the [Set up Retail for Sweden](#set-up-retail-for-sweden) section.

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

## Migrating from legacy integration sample

If you are using the legacy [Sample for Retail POS integration with control units for Sweden](retail-sdk-control-unit-sample.md), you may need to migrate from it to the current integration sample. In order to uptake the change and receive timely updates for the features for Sweden in the future, you may need to upgrade, make minor code and configuration adjustments in the extensions that you built, and rebuild your solutions. No major changes are required in the extension logic that you created. The legacy integration sample and your customizations will continue working in case no changes are made from your side. This is done so that you can plan, prepare for, and execute the uptake for your environment.

### Migration process

The migration from the legacy integration sample to the current control unit integration sample should be done based on the concept of gradual update. This means that all Retail Headquarters and Retail Server components should already be updated before you begin updating the POS and Hardware station components.

To avoid a situation when an event or a transaction is signed twice (that is, by both the legacy extension and the current extension) or cannot be signed because of the missing configuration, it is recommended to turn off all POS and Hardware station devices that use the legacy sample and then update them simultaneously. This can be done, for example, on the store by store basis by updating the store's functionality profile and the Hardware station's hardware profile.

The migration process should consist of the following steps:

1. Update the Retail Headquarters components.
1. Update the Retail Server components and enable the extensions of the current sample.
1. Make sure all offline transactions are synchronized from offline-enabled MPOS devices.
1. Turn off all devices that use the components of the legacy sample.
1. Complete the setup tasks that are described in the [Setting up integration with control units](#setting-up-integration-with-control-units) section.
1. Update the POS and Hardware station components, disable the extensions that are parts of the legacy sample, and enable the extensions of the current sample.

    > [!NOTE]
    > Depending on the type of environment, please find more technical details of the migration process in the corresponding sections: [Migration in development environment](#migration-in-development-environment) or [Migration in production environment](#migration-in-production-environment).

### Migration in development environment

#### Update CRT

1. Find the **Runtime.Extensions.DocumentProvider.CleanCashSample** project and build it.

2. In the **Runtime.Extensions.DocumentProvider.CleanCashSample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample.dll** assembly file.

3. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

4. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **CommerceRuntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's in the bin\ext folder under the local CRT client broker location

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

5. Find and remove the legacy CRT extension in the extension configuration file:

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.FiscalRegisterReceiptSample" />
    ```

    > [!WARNING]
    > Do not execute this step until you update all POS devices that work with this CRT instance. 

6. Register the current sample CRT extensions in the extension configuration file by adding the following lines:

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsSweden" />
    ```

#### Update Hardware station

1. Find the **HardwareStation.Extension.CleanCashSample** project and build it.

2. In the **Extension.CleanCashSample\\bin\\Debug** folder, find the **Contoso.Commerce.HardwareStation.CleanCashSample.dll** assembly file.

3. Copy the assembly file to the Hardware station extensions folder:

    - **Shared hardware station:** Copy the file to the **bin** folder under the IIS Hardware station site location.
    - **Dedicated hardware station on Modern POS:** Copy the file to the Modern POS client broker location.

4. Find the **HardwareStation.Extension.config** extension configuration file:

    - **Remote Hardware station:** The file is located under the IIS Hardware station site location.
    - **Local Hardware station on Modern POS:** The file is located under the Modern POS client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

5. Find and remove the legacy Hardware station extension in the extension configuration file:

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

6. Add the following line to the **composition** section of the extension configuration file:

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.CleanCashSample.dll" />
    ```

#### Update Modern POS

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
2. Disable the legacy POS extension by removing the following lines from **extensions.json**:

    ``` json
    {
        "baseUrl": "FiscalRegisterSample"
    }
    ```

2. Enable the current sample POS extension by adding the following lines in **extensions.json**:

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
2. Disable the legacy POS extension by removing the following lines from **extensions.json**:
    ``` json
    {
        "baseUrl": "FiscalRegisterSample"
    }
    ```

2. Enable the current sample POS extension by adding the following lines in **extensions.json**:

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AuditEvent.SE"
            }
        ]
    }
    ```

### Migration in production environment

### Update CRT

1. Remove the legacy CRT extension in the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder:

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.FiscalRegisterReceiptSample" />
    ```

    > [!WARNING]
    > Do not execute this step until you update all POS devices that work with this CRT instance. 

2. Enable the current sample CRT extensions by making the following changes in the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder:

    ``` xml	
    <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsSweden" />
    ```
    
3. Make the following changes in the **BuildTools\\Customization.settings** package customization configuration file:

    - Add the following lines to include the current sample CRT extension in deployable packages:

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample.dll" />
    ```

### Update Hardware station

1. Remove the legacy Hardware station extension by modifying the **HardwareStation.Extension.config** configuration file:

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

2. Enable the current sample Hardware station extension:

     - In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml
        <add source="assembly" value="Contoso.Commerce.HardwareStation.CleanCashSample" />
        ```


3. Make the following changes in the **BuildTools\\Customization.settings** package customization configuration file:

    - Remove the following lines to exclude the legacy Hardware station extension from deployable packages:

    ``` xml 
     <ISV_CommerceRuntime_CustomizableFileInclude="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.Extension.FiscalRegisterSample.dll" />
    ```

    - Add the following line to include the current sample Hardware station extension in deployable packages:

    ``` xml
    <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.CleanCashSample.dll" />
    ```

### Update Modern POS

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.

2. Disable the legacy POS extension:

    - In the tsconfig.json file, add the FiscalRegisterSample folder to the exclude list.
    
    - Open RetailSDK\POS\Extensions\extensions.json and remove the following lines:
    
      ``` json
      {
          "baseUrl": "FiscalRegisterSample"
      }
      ```

3. Enable the current sample POS extension:

    - Open RetailSDK\POS\Extensions\extensions.json and add the following lines:
      ``` json
      {
          "extensionPackages": [
              {
                  "baseUrl": "Microsoft/AuditEvent.SE"
              }
          ]
      }
      ```

### Update Cloud POS

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.

2. Disable the legacy POS extension:

    - In the tsconfig.json file, add the FiscalRegisterSample folder to the exclude list.

    - Open RetailSDK\POS\Extensions\extensions.json and remove the following lines:
    
      ``` json
      {
          "baseUrl": "FiscalRegisterSample"
      }
      ```

4. Enable the current sample POS extension:

    - Open RetailSDK\POS\Extensions\extensions.json and add the following lines:
    
      ``` json
      {
          "extensionPackages": [
              {
                  "baseUrl": "Microsoft/AuditEvent.SE"
              }
          ]
      }
      ```

Run msbuild for the whole Retail SDK to create deployable packages. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
