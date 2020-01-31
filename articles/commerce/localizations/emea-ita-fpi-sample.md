---
# required metadata

title: Fiscal printer integration sample for Italy
description: This topic provides an overview of the fiscal integration sample for Italy.
author: josaw
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
ms.search.region: Italy
ms.search.industry: Retail
ms.author: sepism
ms.search.validFrom: 2018-11-1
ms.dyn365.ops.version: 8.1.1

---
# Fiscal printer integration sample for Italy

[!include [banner](../includes/banner.md)]

## Introduction

The Commerce functionality for Italy includes a sample integration of the point of sale (POS) with a fiscal printer. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) so that it works with [Epson FP-90III Series](https://www.epson.it/products/sd/pos-printer/epson-fp-90iii-series) printers from Epson, and it enables communication with a fiscal printer in the web server mode via the EpsonFPMate web-service using Fiscal ePOS-Print API. The sample supports the Registratore Telematico (RT) mode only. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from Epson. For information about how to get the fiscal printer and operate it, contact [Epson Italia S.p.A](https://www.epson.it).

## Scenarios

The following scenarios are covered by the fiscal printer integration sample for Italy:

- Sales scenarios:

    - Print a fiscal receipt for cash-and-carry sales and returns.
    - Capture a response from the fiscal printer, and store it in the channel database.
    - Taxes:

        - Map to the fiscal printer's tax codes (departments).
        - Transfer mapped tax data to the fiscal printer.
        - Print taxes on a fiscal receipt.

    - Payments:

        - Map to the fiscal printer's methods of payment.
        - Print payments on a fiscal receipt.
        - Print change information.

    - Print line discounts.
    - Gift cards:

        - Exclude an issued/re-charged gift card line from a fiscal receipt for a sale.
        - Print a payment that uses a gift card as a regular method of payment.

    - Print fiscal receipts for customer order operations:

        - A fiscal receipt isn't printed for a customer order deposit.
        - Print a fiscal receipt for carry-out lines of a hybrid customer order.
        - Print a fiscal receipt for the pickup operation for a customer order.
        - Print a fiscal receipt for a return order.

    - Print a bar code for the receipt number on a fiscal receipt.
    - Print the [customer information](emea-ita-customer-information.md) that is specified for a sales transaction on a fiscal receipt. An example of this information is the customer's lottery code. 

- End of day statements (fiscal X and fiscal Z reports).
- Error handling, such as the following options:

    - Retry fiscal registration if a retry is possible, such as if the fiscal printer isn't connected, isn't ready or isn't responding, the printer is out of paper, or there is a paper jam.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Check the availability of the fiscal printer before a new sales transaction is opened or a sales transaction is finalized.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample:

- Value-added tax (VAT) rates mapping:

    *1 : 22.00 ; 2 : 10.00 ; 3 : 4.00 ; 4 : 0.00*

- Tender type mapping:

    *1 : 0 ; 2 : 1 ; 3 : 2 ; 4 : 2 ; 5 : 0 ; 6 : 0 ; 7 : 0 ; 8 : 2 ; 9 : 0 ; 10 : 2 ; 11 : 1*

### Gift cards

The fiscal printer integration sample implements the following rules that are related to gift cards:

- Exclude sales lines that are related to the *Issue gift card* and *Add to gift card* operations from the fiscal receipt.
- Don't print a fiscal receipt if it consists only of gift card lines.
- Deduct the total amount of gift cards that are issued or re-charged in a transaction from payment lines of the fiscal receipt.
- Save calculated adjustments of payment lines in the channel database with a reference to a corresponding fiscal transaction.
- Payment by gift card is considered a regular payment.

### Customer deposits and customer order deposits

The fiscal printer integration sample implements the following rules that are related to customer deposits and customer order deposits:

- Don't print a fiscal receipt if a transaction is a customer deposit.
- Don't print a fiscal receipt if a transaction contains only a customer order deposit or a customer order deposit refund.
- Print the amount of the previously paid deposit on a fiscal receipt for a customer order pickup operation.
- Deduct the customer order deposit amount from payment lines when a hybrid customer order is created.
- Save calculated adjustments of payment lines in the channel database with a reference to a fiscal transaction for a hybrid customer order.

### Limitations of the sample

- The fiscal printer supports only scenarios where sales tax is included in the price. Therefore, the **Price include sales tax** option must be set to **Yes** for both stores and customers.
- Daily reports (fiscal X and fiscal Z) are printed by using the format that is embedded in the fiscal printer's firmware.
- The fiscal printer doesn't support mixed transactions. The **Prohibit mixing sales and returns in one receipt** option should be set to **Yes** in POS functionality profiles.
- The sample supports integration only with a fiscal printer that is working in the RT (Registratore Telematico) mode.

## Set up Commerce for Italy

### Configure fiscal integration

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Retail channels](setting-up-fiscal-integration-for-retail-channel.md):

- [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Note also the settings for the fiscal registration process that are [specific to this fiscal printer integration sample](#set-up-the-registration-process).
- [Set up fiscal texts for discounts](setting-up-fiscal-integration-for-retail-channel.md#set-up-fiscal-texts-for-discounts).
- [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
- [Set up fiscal X/Z reports from the POS](setting-up-fiscal-integration-for-retail-channel.md#set-up-fiscal-xz-reports-from-the-pos).
- [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).
- [Set up the functionality for management of customer information in POS](emea-ita-customer-information.md#setup)

### Enable extensions

#### Commerce runtime extension components

The Commerce runtime extension components are included in the Retail SDK. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

1. Find the **Runtime.Extensions.DocumentProvider.EpsonFP90IIISample** project, and build it.
1. In the **Extensions.DocumentProvider.EpsonFP90IIISample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.dll** assembly file.
1. Copy the assembly file to the CRT extensions folder:

    - **Commerce Scale Unit:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

1. Find the extensions configuration file for CRT:

    - **Commerce Scale Uni:** The file is named **commerceruntime.ext.config**, and it's in the bin\\ext folder under the IIS Commerce Scale Uni site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

1. Register the CRT change in the extensions configuration file. Add **source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample"**.
1. Restart the Commerce Scale Unit:

    - **Commerce Scale Uni:** Restart the Commerce Scale Uni site from IIS Manager.
    - **Client broker:** End the **dllhost.exe** process in Task Manager, and then restart Modern POS.

#### Hardware station extension components

The Hardware station extension components are included in the Retail SDK. To complete the following procedures, open the Hardware Station solution, **HardwareStationSamples.sln**, under **RetailSdk\\SampleExtensions\\HardwareStation**.

1. Find the **HardwareStation.Extensions.EpsonFP90IIIFiscalDeviceSample** project, and build it.
2. In the **Extensions.EpsonFP90IIIFiscalDeviceSample\\bin\\Debug** folder, find the **Contoso.Commerce.HardwareStation.EpsonFP90IIIFiscalDeviceSample.dll** assembly file.
3. Copy the files to a deployed Hardware station machine:

    - **Remote Hardware station:** Copy the files to the **bin** folder under the IIS Hardware station site location.
    - **Local Hardware station:** Copy the files to the Modern POS client broker location.

4. Find the configuration file for the Hardware station's extensions. The file is named **HardwareStation.Extension.config**:

    - **Remote Hardware station:** The file is located under the IIS Hardware station site location.
    - **Local Hardware station:** The file is located under the Modern POS client broker location.
	
5. Add the following section to the **composition** section of the config file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.EpsonFP90IIIFiscalDeviceSample" />
    ```

6. Restart the Hardware station service:

    - **Remote Hardware station:** Restart the Hardware station site from IIS Manager.
    - **Local Hardware station:** End the **dllhost.exe** process in Task Manager, and then restart Modern POS.

### Set up the registration process

To enable the registration process, follow these steps to set up Headquarters. For more details, see [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Fiscal Connectors**. Import the configuration from **RetailSdk\\SampleExtensions\\HardwareStation\\Entension.EpsonFP90IIIFiscalDeviceSample\\Configuration\\ConnectorEpsonFP90IIISample.xml**.
2. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Fiscal Document providers**. Import the configuration from **RetailSdk\\SampleExtensions\\CommerceRuntime\\Entension.DocumentProvider.EpsonFP90IIISample\\Configuration\\DocumentProviderEpsonFP90IIISample.xml**.
3. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Connector Technical profiles**. Create a new profile, and select the loaded connector from the earlier step. Update the connection settings if an update is required.
4. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Connector Functional profiles**. Create a new profile, and select the loaded connector and document provider from the earlier steps. Update data mapping settings if an update is required.
5. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Connector Functional group**. Create a new group, and select the connector functional profile from the earlier step.
6. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Registration process**. Create a new process, and select the connector functional group from the earlier step.
7. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Open the functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the registration process that was created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Open the hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile.
9. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

### Production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Complete the steps that are described in the [Enable extensions](#enable-extensions) section earlier in this topic.
2. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following line to the **composition** section.

        ``` xml	
        <add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample" />
        ```

    - In the **HardwareStation.Extension.config** configuration file, add the following line to the **composition** section.

        ``` xml 
        <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.EpsonFP90IIIFiscalDeviceSample" />
        ```

3. Make the following changes in the **BuildTools\\Customization.settings** package customization configuration file:

    - Add the following line to include the CRT extension in the deployable packages.

        ``` xml	
        <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.dll"/>
        ```

    - Add the following line to include the Hardware station extension in the deployable packages.

        ``` xml	
        <ISV_HardwareStation_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.HardwareStation.EpsonFP90IIIFiscalDeviceSample.dll"/>
        ```

4. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
5. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create retail deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Design of extensions

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate printer-specific documents and handle responses from the fiscal printer.

The Commerce runtime extension is **Runtime.Extensions.DocumentProvider.EpsonFP90IIISample**.

For more details about the design of the fiscal integration solution, see [Fiscal registration process and fiscal integration samples for fiscal devices](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices).

#### Request handler
	
The **DocumentProviderEpsonFP90III** request handler is the entry point for the request to generate documents from the fiscal printer.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a printer-specific document that should be registered in the fiscal printer.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, and printing Z report.

#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the document provider to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- VAT codes mapping
- VAT rates mapping
- Tender type mapping
- Barcode type for receipt number
- Deposit payment type

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal printer.

The Hardware station extension is **HardwareStation.Extension.EpsonFP90IIIFiscalDeviceSample**. This extension uses the HTTP protocol to submit documents that the Commerce runtime extension generates to the fiscal printer. It also handles the responses that are received from the fiscal printer.

#### Request handler

The **EpsonFP90IIISample** request handler is the entry point for handling request to the fiscal peripheral device.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to printers and returns the response from the fiscal printer.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the device.
- **InitializeFiscalDeviceRequest** – This request is used for printer initialization.

#### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable settings for the connector to be configured from Headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- **Endpoint address** – The URL of the printer.
- **Date and time synchronization** – This setting specifies whether the date and time of the printer must be synced with the connected Hardware station.
