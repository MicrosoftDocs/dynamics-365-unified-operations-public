---

# required metadata

title: Fiscal printer integration sample for Poland
description: This topic provides an overview of the fiscal integration sample for Poland.
author: josaw
manager: annbe
ms.date: 02/01/2019
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
ms.search.region: Poland
ms.search.industry: Retail
ms.author: v-dmpere
ms.search.validFrom: 2019-2-1
ms.dyn365.ops.version: 10.0.1

---

# Fiscal printer integration sample for Poland

[!include[banner](../includes/banner.md)]

## Introduction

The Microsoft Dynamics 365 for Retail functionality for Poland includes a sample of integration of POS with a fiscal printer. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and supports the POSNET THERMAL HD 2.02 protocol for fiscal printers from [Posnet Polska S.A.](http://www.posnet.com.pl). The sample enables the communication with a fiscal printer connected via a COM port using a native software driver. It was implemented and tested with a software emulator provided by Posnet for the Posnet Thermal HD FV EJ fiscal printer. The sample is provided in form of source code and is part of the Retail SDK.

Microsoft does not ship any hardware, software, or documentation from Posnet. Please contact [Posnet Polska S.A.](http://www.posnet.com.pl) for information on how to acquire the fiscal printer and operate it.

## Scenarios

The following scenarios are covered by the fiscal printer integration sample for Poland.
- Sales scenarios:
	- Print a fiscal receipt for cash and carry sales and returns.
	- Capture a response from the fiscal printer and store it in the Channel DB.
	- Taxes:
	  - Map to fiscal printer's tax codes (departments);
	  - Transfer mapped tax data to the fiscal printer.
	- Payments:
	  - Map to fiscal printer's methods of payment;
	  - Print payments in a fiscal receipt;
	  - Print change information.
	- Print line discounts.
	- Gift cards:
	  - Exclude an issued/re-charged gift card line from a fiscal receipt for a sale;
	  - Print a payment with a gift card as a regular method of payment.
	- Print fiscal receipts for customer order operations:
	  - Fiscal receipt is not printed for a customer order deposit;
	  - Print a fiscal receipt for carry-out lines of a hybrid customer order;
	  - Print a fiscal receipt for the pickup operation for a customer order;
	  - Print a fiscal receipt for a return order.
	- Print barcode for the receipt number in a fiscal receipt.
- End of day statements (fiscal X, fiscal Z reports).
- Error handling, including the following options:
	- Retry fiscal registration if it's possible; for example, if the fiscal printer is not connected/not ready/not responding, the printer is out of paper, there is a paper jam, etc.;
	- Postpone fiscal registration;
	- Skip fiscal registration or mark the transaction as registered, including info codes to capture the reason of failure and additional information.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration provided as part of the fiscal integration sample:

  - VAT rates mapping:
   
     *0 : 23.00 ; 1 : 8.00 ; 2 : 5.00 ; 3 : 0.00*

  - Tender type mapping:

     *0 : 0 ;  1 : 0 ; 2 : 2 ; 3 : 2 ; 4 : 0 ; 5 : 0 ; 6 : 0 ; 7 : 2 ; 8 : 0*

### Handling gift cards

The fiscal printer integration sample implements the following rules in regard to gift cards:

- Exclude sales lines related to the operations *Issue gift card* or *Add to gift card* from the fiscal receipt;
- Do not print a fiscal receipt if it consists of gift card lines only;
- Deduct total amount of gift cards issued or re-charged in a transaction from payment lines of the fiscal receipt; 
- Save calculated adjustments of payment lines in the Channel DB with a reference to a corresponding fiscal transaction;
- Payment by gift card is considered as a regular payment.

### Handling customer deposits and customer order deposits

The fiscal printer integration sample implements the following rules in regard to customer deposits and customer order deposits:

- Do not print a fiscal receipt if a transaction is a customer deposit;
- Do not print a fiscal receipt if a transaction contains a customer order deposit or a customer order deposit refund only;
- Print the amount of the previously paid deposit in a fiscal receipt for a customer order pickup operation;
- Deduct the customer order deposit amount from payment lines when a hybrid customer order is created;
- Save calculated adjustments of payment lines in the Channel DB with a reference to a fiscal transaction for a hybrid customer order.

## Set up Retail for Poland

### Enabling extensions

##### CRT extension components

The CRT extension components are included in the Retail SDK. To complete the following procedures, open the CRT solution, CommerceRuntimeSamples.sln, under **RetailSdk\SampleExtensions\CommerceRuntime**.

1. Find the **Runtime.Extensions.DocumentProvider.PosnetSample** project and build it.
2. In the **Extensions.DocumentProvider.PosnetSample\bin\Debug** folder, find the **Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample.dll** assembly file.
3. Copy the assembly file to the CRT extensions folder:
	- Retail Server: Copy the assembly to the **\bin\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
	- Local CRT on Modern POS: Copy the assembly to the **\ext** folder under the local CRT client broker location.
4. Find the extensions configuration file for CRT:
	- Retail Server: The file is named commerceruntime.ext.config, and it's in the bin\ext folder under the IIS Retail Server site location.
	- Local CRT on Modern POS: The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.
5. Register the CRT change in the extension's configuration file. Add source="assembly" **value="Contoso.Commerce.Runtime.Extensions.DocumentProvider.PosnetSample"**
6. Restart the Retail service:
	- Retail Server: Restart the Retail service site from IIS Manager.
	- Client broker: End the dllhost.exe process in Task Manager, and then restart Modern POS.

##### Hardware station extension components
The Hardware station extension components are included in the Retail SDK. To complete the following procedures, open the Hardware Station solution, **HardwareStationSamples.sln**, under **RetailSdk\SampleExtensions\HardwareStation**.

1. Find the **Extension.PosnetThermalFVFiscalPrinterSample** project and build it.
2. In the **Extension.PosnetThermalFVFiscalPrinterSample\bin\Debug** folder, find the **Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample.dll** assembly file.
3. Copy the files to a deployed Hardware station machine:
	- Remote Hardware station: Copy the files to the bin folder under the Microsoft Internet Information Services (IIS) Hardware station site location. Copy printer driver libraries (libposcmbth.dll, libcmbth_serial.dll, cmbth_pl.lng).
4. Find the configuration file for the Hardware station's extensions. The file is named HardwareStation.Extension.config:
	- Remote Hardware station: The file is located under the IIS Hardware station site location.

5. Add the following section to the composition section of the config file.	
	<add source="assembly" value="Contoso.Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample" />
6. Restart the Hardware station service:
	- Remote Hardware station: Restart the Hardware station site from IIS Manager.

### Set up the registration process

To enable the registration process, set up Retail Headquarters using the steps below. For more details, see [How to set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel#how-to-set-up-a-fiscal-registration-process).

1. Open **Retail > Channel Setup > Fiscal Integration > Fiscal Connectors**. Import the configuration from **RetailSdk\SampleExtensions\HardwareStation\Extension.Posnet.ThermalDeviceSample\Configuration\ConnectorConnectorPosnetThermalFVEJ.xml**.
2. Open **Retail > Channel Setup > Fiscal Integration > Fiscal Document providers**. Import the configuration from **RetailSdk\SampleExtensions\CommerceRuntime\Extension.DocumentProvider.PosnetSample\Configuration\DocumentProviderPosnetSample.xml**.
3. Open **Retail > Channel Setup > Fiscal Integration > Connector Technical profiles**. Create a new profile and select the loaded connector from the step above. Update connection settings if needed.
4. Open **Retail > Channel Setup > Fiscal Integration > Connector Functional profiles**. Create a new profile and select the loaded connector and document provider from the steps above. Update data mapping settings, if needed.
5. Open **Retail > Channel Setup > Fiscal Integration > Connector Functional group**. Create a new group and select the connector functional profile from the step above.
6. Open **Retail > Channel Setup > Fiscal Integration > Registration process**. Create a new process. Select the connector functional group from the step above.
7. Open the Functionality profile linked to the store where the registration process should be activated. Expand the **Fiscal registration process** FastTab. Select the registration process created in the step above.
8. Open the Hardware profile that is linked to the hardware station to which the fiscal printer will be connected. Expand the **Fiscal peripherals** FastTab. Select the connector technical profile.
9. Open the Distribution scheduler and select job **1070** to transfer data to the Channel database.

## Commerce runtime extension design

The purpose of the extension (Document provider) is to generate printer-specific documents and handle responses from the fiscal printer.

Commerce runtime extension: **Commerce.Runtime.DocumentProvider.PosnetSample.DocumentProviderPosnetProtocol**. This extension generates the set of printer-specific commands defined by POSNET specification 19-3678 in JSON format.

For more details about the fiscal integration solution design, see [Fiscal registration process and fiscal integration sample for fiscal device](fiscal-integration-for-retail-channel#fiscal-registration-process-and-fiscal-integration-sample-for-fiscal-device).

### Request handler
	
The request handler DocumentProviderPosnetProtocol is the entry point for the request to generate documents from the fiscal printer.

The handler is inherited from the INamedRequestHandler interface. The Method HandlerName is responsible for returning the name of the handler. It should match the connector document provider name specified in HQ.

The connector supports the following requests:
- **GetFiscalDocumentDocumentProviderRequest** - Contains information about what document should be generated. Returns a printer-specific document that should be registered in the fiscal printer.
- **GetSupportedRegistrableEventsDocumentProviderRequest** - Returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, and printing Z report.
- **SaveFiscalRegistrationResultDocumentProviderRequest** - Saves the response from the printer.


### Configuration
The configuration file is found in the Configuration folder of the extension project. The purpose of the file is to allow to configure settings for the document provider from the HQ. The file format aligns fiscal integration configuration requirements. The following settings have been added:
- VAT rates mapping
- Tender type mapping
- Deposit payment type

## Hardware station extension design

The purpose of the extension (Connector) is to communicate with the fiscal printer.

Hardware station extension: **Commerce.HardwareStation.PosnetThermalFVFiscalPrinterSample.FiscalPrinterHandler**. This extension submits commands generated by the Commerce runtime extension to the fiscal printer by calling the functions of the POSNET driver provided by the manufacturer, and handles device errors.

### Request handler
The request handler FiscalPrinterHandler is the entry point for handling the request to the fiscal peripheral device. The handler is inherited from INamedRequestHandler interface. Method HandlerName is responsible for returning the name of the handler, it should match the fiscal connector name specified in HQ.

The connector supports the following requests:
- **SubmitDocumentFiscalDeviceRequest** - Sends documents to printers and returns response from the fiscal printer.
- **IsReadyFiscalDeviceRequest** - Used for a health check of the device.
- **InitializeFiscalDeviceRequest** - Used for printer initialization.


### Configuration
The configuration file is found in **Configuration** folder of the extension project. The purpose of the file is to allow to configure settings for the connector provider from the HQ. The file format aligns fiscal integration configuration requirements. The following settings have been added:
- **Connection string** - The string describes the details of the connection to the device in the format supported by the driver. See POSNET driver documentation for details.
- **Date and time synchronization** - This indicates if you need to sync the date and time of the printer with the connected hardware station. The date and time of the printer will be synchronized with the Hardware station time.
- **Device timeout** - The time in milliseconds the driver will wait for response from device. See POSNET driver documentation for details.

## Limitations of the sample

  - The fiscal printer supports the scenarios with sales tax included in price only. So, the parameter **Price include sales tax** must be set to **Yes** both for retail stores and customers.
  - Daily reports (fiscal X, fiscal Z) are printed using the embedded format *Shift report*.
  - Printing of barcode in fiscal receipts is considered as a potential customization, since this feature is not supported in the embedded formats and can be implemented through using the customizable report *Super-format* only.
  - Mixed transactions are not supported by the fiscal printer. The parameter **Prohibit mixing sales and returns in one receipt** should be set to **Yes** in POS functionality profiles.
