---
# required metadata

title: Fiscal printer integration sample for Italy
description: This topic provides an overview of the fiscal integration sample for Italy.
author: josaw
manager: annbe
ms.date: 01/23/2019
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

[!include[banner](../includes/banner.md)]

## Introduction

The Microsoft Dynamics 365 for Retail functionality for Italy includes a sample integration of the point of sale (POS) with a fiscal printer. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel) so that it works with [Epson FP-90III Series](http://www.epson.it/products/sd/pos-printer/epson-fp-90iii-series) printers from Epson, and it enables communication with a fiscal printer in the web server mode via the EpsonFPMate web-service using Fiscal ePOS-Print API. The sample supports the Registratore Telematico (RT) mode only. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from Epson. For information about how to get the fiscal printer and operate it, contact [Epson Italia S.p.A](http://www.epson.it).
 
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

    - Print a barcode for the receipt number on a fiscal receipt.

- End of day statements (fiscal X and fiscal Z reports).
- Error handling, such as the following options:

    - Retry fiscal registration if a retry is possible, such as if the fiscal printer isn't connected, isn't ready or isn't responding, the printer is out of paper, or there is a paper jam.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample:

- Value-added tax (VAT) rates mapping:

    *1 : 21.00 ; 2 : 10.00 ; 3 : 4.00 ; 4 : 0.00*

- Tender type mapping:

    *1 : 0 ; 2 : 1 ; 3 : 2 ; 4 : 2 ; 5 : 0 ; 6 : 0 ; 7 : 0 ; 8 : 2 ; 9 : 0 ; 10 : 2 ; 11 : 1*

### Handling gift cards

The fiscal printer integration sample implements the following rules that are related to gift cards:

- Exclude sales lines that are related to the *Issue gift card* and *Add to gift card* operations from the fiscal receipt.
- Don't print a fiscal receipt if it consists only of gift card lines.
- Deduct the total amount of gift cards that are issued or re-charged in a transaction from payment lines of the fiscal receipt.
- Save calculated adjustments of payment lines in the channel database with a reference to a corresponding fiscal transaction.
- Payment by gift card is considered a regular payment.

### Handling customer deposits and customer order deposits

The fiscal printer integration sample implements the following rules that are related to customer deposits and customer order deposits:

- Don't print a fiscal receipt if a transaction is a customer deposit.
- Don't print a fiscal receipt if a transaction contains only a customer order deposit or a customer order deposit refund.
- Print the amount of the previously paid deposit on a fiscal receipt for a customer order pickup operation.
- Deduct the customer order deposit amount from payment lines when a hybrid customer order is created.
- Save calculated adjustments of payment lines in the channel database with a reference to a fiscal transaction for a hybrid customer order.

## Set up Retail for Italy

### Enabling extensions

##### Commerce runtime extension components

The Commerce runtime extension components are included in the Retail SDK. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**, under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

1. Find the **Runtime.Extensions.DocumentProvider.EpsonFP90IIISample** project, and build it.
1. In the **Extensions.DocumentProvider.EpsonFP90IIISample\\bin\\Debug** folder, find the **Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.dll** assembly file.
1. Copy the assembly file to the CRT extensions folder:

    - **Retail Server:** Copy the assembly to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** Copy the assembly to the **\\ext** folder under the local CRT client broker location.

1. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the bin\\ext folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

1. Register the CRT change in the extensions configuration file. Add **source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample"**.
1. Restart the Retail service:

    - **Retail Server:** Restart the Retail service site from IIS Manager.
    - **Client broker:** End the **dllhost.exe** process in Task Manager, and then restart Modern POS.

##### Hardware station extension components

The Hardware station extension components are included in the Retail SDK. To complete the following procedures, open the Hardware Station solution, **HardwareStationSamples.sln**, under **RetailSdk\\SampleExtensions\\HardwareStation**.

1. Find the **HardwareStation.Extensions.EpsonFP90IIIFiscalDeviceSample** project, and build it.
1. In the **Extensions.EpsonFP90IIIFiscalDeviceSample\\bin\\Debug** folder, find the **Contoso.Commerce.HardwareStation.EpsonFP90IIIFiscalDeviceSample.dll** assembly file.
1. Copy the files to a deployed Hardware station machine:

    - **Remote Hardware station:** Copy the files to the **bin** folder under the IIS Hardware station site location.
    - **Local Hardware station:** Copy the files to the Modern POS client broker location.

1. Find the configuration file for the Hardware station's extensions. The file is named **HardwareStation.Extension.config**:

    - **Remote Hardware station:** The file is located under the IIS Hardware station site location.
    - **Local Hardware station:** The file is located under the Modern POS client broker location.
	
1. Add the following section to the **composition** section of the config file.

    ```
    <add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.EpsonFP90IIIFiscalDeviceSample" />
    ```

1. Restart the Hardware station service:

    - **Remote Hardware station:** Restart the Hardware station site from IIS Manager.
    - **Local Hardware station:** End the **dllhost.exe** process in Task Manager, and then restart Modern POS.

### Set up the registration process

To enable the registration process, follow these steps to set up Retail Headquarters. For more details, see [How to set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel#how-to-set-up-a-fiscal-registration-process).

1. Go to **Retail \> Channel Setup \> Fiscal Integration \> Fiscal Connectors**. Import the configuration from **RetailSdk\\SampleExtensions\\HardwareStation\\Entension.EpsonFP90IIIFiscalDeviceSample\\Configuration\\ConnectorEpsonFP90IIISample.xml**.
2. Go to **Retail \> Channel Setup \> Fiscal Integration \> Fiscal Document providers**. Import the configuration from **RetailSdk\\SampleExtensions\\CommerceRuntime\\Entension.DocumentProvider.EpsonFP90IIISample\\Configuration\\DocumentProviderEpsonFP90IIISample.xml**.
3. Go to **Retail \> Channel Setup \> Fiscal Integration \> Connector Technical profiles**. Create a new profile, and select the loaded connector from the earlier step. Update the connection settings if an update is required.
4. Go to **Retail \> Channel Setup \> Fiscal Integration \> Connector Functional profiles**. Create a new profile, and select the loaded connector and document provider from the earlier steps. Update data mapping settings if an update is required.
5. Go to **Retail \> Channel Setup \> Fiscal Integration \> Connector Functional group**. Create a new group, and select the connector functional profile from the earlier step.
6. Go to **Retail \> Channel Setup \> Fiscal Integration \> Registration process**. Create a new process, and select the connector functional group from the earlier step.
7. Go to **Retail \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Open the functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the created registration process from the earlier step.
8. Go to **Retail \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Open the hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile.
9. Open the distribution schedule (**Retail \> Retail IT > Distribution schedule**), and select job **1070** to transfer data to the channel database.

## Commerce runtime extension design

The purpose of the extension (document provider) is to generate printer-specific documents and handle responses from the fiscal printer.

Commerce runtime extension: **Runtime.Extensions.DocumentProvider.EpsonFP90IIISample**.

For more details about the design of the fiscal integration solution, see [Fiscal registration process and fiscal integration sample for fiscal device](fiscal-integration-for-retail-channel#fiscal-registration-process-and-fiscal-integration-sample-for-fiscal-device).

### Request handler
	
The **DocumentProviderEpsonFP90III** request handler is the entry point for the request to generate documents from the fiscal printer.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Retail Headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a printer-specific document that should be registered in the fiscal printer.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, and printing Z report.

### Configuration

The configuration file is located in the **Configuration** folder of the extension project. The purpose of the file is to enable configuration of settings for the document provider from Retail Headquarters. The file format aligns fiscal integration configuration requirements. The following settings have been added:

- VAT codes mapping
- VAT rates mapping
- Tender type mapping
- Barcode type for the receipt number
- Deposit payment type

## Hardware station extension design

The purpose of the extension (connector) is to communicate with the fiscal printer.

Hardware station extension: **HardwareStation.Extensions.EpsonFP90IIIFiscalDeviceSample**

The Hardware station extension submits documents that the Commerce runtime extension generates to the fiscal printer (via HTTP protocol). It also handles the responses that are received from the fiscal printer.

### Request handler

The **EpsonFP90IIISample** request handler is the entry point for handling request to the fiscal peripheral device.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Retail Headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to printers and returns the response from the fiscal printer.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the device.
- **InitializeFiscalDeviceRequest** – This request is used for printer initialization.

### Configuration

The configuration file is found in the **Configuration** folder of the extension project. The purpose of the file is to enable configuration of settings for the connector provider from Retail Headquarters. The file format aligns fiscal integration configuration requirements. The following settings have been added:

- **Endpoint address** – The URL of the printer.
- **Date and time synchronization** – This setting indicates whether you must sync the date and time of the printer with the connected Hardware station. The date and time of the printer will be synced with the Hardware station time.

## Limitations of the sample

- The fiscal printer supports only scenarios where sales tax is included in the price. Therefore, the **Price include sales tax** option must be set to **Yes** for both retail stores and customers.
- Daily reports (fiscal X and fiscal Z) are printed by using the format that is embedded in the fiscal printer firmware.
- Mixed transactions aren't supported by the fiscal printer. The **Prohibit mixing sales and returns in one receipt** option should be set to **Yes** in POS functionality profiles.
- The sample supports integration only with a fiscal printer that is working in the RT (Registratore Telematico) mode. 
