---
# required metadata

title: Fiscal printer integration sample for Italy
description: This topic provides an overview of the fiscal integration sample for Italy.
author: josaw
manager: annbe
ms.date: 11/01/2018
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

The Microsoft Dynamics 365 for Retail functionality for Italy includes a sample of integration of POS with a fiscal printer. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) to work with [Epson FP-90III Series](http://www.epson.it/products/sd/pos-printer/epson-fp-90iii-series) from Epson and enables the communication with a fiscal printer in the web server mode via the EpsonFPMate web-service using Fiscal ePOS-Print API. The sample supports the Registratore Telematico (RT) mode only. The sample is provided in form of source code and is part of the Retail SDK.

Microsoft does not ship any hardware, software or documentation from Epson. Please contact [Epson Italia S.p.A](http://www.epson.it) for information on how to acquire the fiscal printer and operate it.
 
## Overview

The following scenarios are covered by the fiscal printer integration sample for Italy:
  - Sales scenarios:
    - Printing a fiscal receipt for cash and carry sales and returns
	- Capturing a response from the fiscal printer and storing in Channel DB
	- Taxes:
	  - Mapping to fiscal printer's tax codes (departments)
	  - Transfering mapped tax data to a fiscal printer
	  Printing in a fiscal receipt
    - Payments:
		- Mapping to fiscal printer's methods of payment
	    - Printing in a fiscal receipt
		- Printing change information
	- Printing line discounts
    - Gift cards:
	  - Excluding an issued/re-charged gift card line from a fiscal receipt
	  - Printing a payment with a gift card as a regular method of payment
	- Printing fiscal receipts for customer orders order operations:
	  - Excluding customer order deposit
	  - Carry-out lines of a hybrid customer order
	  - Customer order pickup
	  - Return order
	- Printing barcode in fiscal receipts
  - End of day statements (fiscal X, fiscal Z reports)
  - Error handling:
	- Retry fiscal registration when it's possible: printer not connected/not ready/not responding, printer out of paper, paper jam, etc.
	- Postpone fiscal registration.
    - Skip fiscal registration or mark the transaction as registered, including info codes to capture the reason of failure and additional information.

## Set up Retail for Italy

### Enabling extensions

##### Commerce runtime extension components

The Commerce runtime extension components are included in the Retail SDK. To complete the following procedures, open the CRT solution, CommerceRuntimeSamples.sln, under RetailSdk\SampleExtensions\CommerceRuntime.

1. Find the Runtime.Extensions.DocumentProvider.EpsonFP90IIISample project and build it.
1. In the Extensions.DocumentProvider.EpsonFP90IIISample\bin\Debug folder, find the Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample.dll assembly file.
1. Copy the assembly file to the CRT extensions folder:
	- Retail Server: Copy the assembly to the \bin\ext folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
	- Local CRT on Modern POS: Copy the assembly to the \ext folder under the local CRT client broker location.
1. Find the extensions configuration file for CRT:
	- Retail Server: The file is named commerceruntime.ext.config, and it's in the bin\ext folder under the IIS Retail Server site location.
	- Local CRT on Modern POS: The file is named CommerceRuntime.MPOSOffline.Ext.config, and it's under the local CRT client broker location.
1. Register the CRT change in the extensions configuration file. Add source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample" 
1. Restart the Retail service:
	- Retail Server: Restart the Retail service site from IIS Manager.
	- Client broker: End the dllhost.exe process in Task Manager, and then restart Modern POS.

##### Hardware station extension components
The Hardware station extension components are included in the Retail SDK. To complete the following procedures, open the Hardware Station solution, HardwareStationSamples.sln, under RetailSdk\SampleExtensions\HardwareStation.

1. Find the HardwareStation.Extensions.EpsonFP90IIIFiscalDeviceSample project and build it.
1. In the Extensions.EpsonFP90IIIFiscalDeviceSample \bin\Debug folder, find the Contoso.Commerce.HardwareStation.EpsonFP90IIIFiscalDeviceSample.dll assembly file.
1. Copy the files to a deployed Hardware station machine:
	- Remote Hardware station: Copy the files to the bin folder under the Microsoft Internet Information Services (IIS) Hardware station site location.
	- Local Hardware station: Copy the files to the Modern POS client broker location.
1. Find the configuration file for the Hardware station's extensions. The file is named HardwareStation.Extension.config:
	- Remote Hardware station: The file is located under the IIS Hardware station site location.
	- Local Hardware station: The file is located under the Modern POS client broker location.
	
1. Add the following section to the composition section of the config file.	
	<add source="assembly" value="Contoso.Commerce.HardwareStation.Extension.EpsonFP90IIIFiscalDeviceSample" />
1. Restart the Hardware station service:
	- Remote Hardware station: Restart the Hardware station site from IIS Manager.
	- Local Hardware station: End the dllhost.exe process in Task Manager, and then restart Modern POS.

### Set up the registration process

To enable the registration process, set up the Headquarters using the steps below. For more details, see [How to set up a fiscal registration process](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/fpi-sample-pol/articles/retail/localizations/fiscal-integration-for-retail-channel.md#how-to-set-up-a-fiscal-registration-process).

1. Open **Retail > Channel Setup > Fiscal Integration > Fiscal Connectors**. Import the configuration from RetailSdk\SampleExtensions\CommerceRuntime\Entension.DocumentProvider.EpsonFP90IIISample\Configuration\DocumentProviderEpsonFP90IIISample.xml.

2. Open **Retail > Channel Setup > Fiscal Integration > Fiscal Document providers**. Import the configuration from RetailSdk\SampleExtensions\HardwareStation\Entension.EpsonFP90IIIFiscalDeviceSample\Configuration\ConnectorEpsonFP90IIISample.xml.

3. Open **Retail > Channel Setup > Fiscal Integration > Connector Technical profiles**. Create a new profile and select the loaded connector from the step above. Update connection settings if needed.

4. Open **Retail > Channel Setup > Fiscal Integration > Connector Functional profiles**. Create a new profile and select the loaded connector and document provider from the steps above. Update data mapping settings if needed

5. Open **Retail > Channel Setup > Fiscal Integration > Connector Functional group**. Create a new group and select the connector functional profile from the step above.

6. Open **Retail > Channel Setup > Fiscal Integration > Registration process**. Create a new process. Select the connector functional group from the step above.

7. Open Functionality profile linked to the store where the registration process should be activated. Expand the **Fiscal registration process** FastTab. Select the created registration process from the step above.

8. Open the Hardware profile that is linked to the hardware station to which the fiscal printer will be connected. Expand the **Fiscal peripherals** FastTab. Select the connector technical profile.

9. Open Distribution scheduler and select job **1070** to transfer data to the Channel database.

## Commerce runtime extension design

The purpose of the extension (Document provider) is to generate printer-specific documents and handle responses from the fiscal printer.

Commerce runtime extension: **Runtime.Extensions.DocumentProvider.EpsonFP90IIISample**. 

For more details about the the fiscal integration solution design, see [Solution design for local fiscal devices](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/fpi-sample-pol/articles/retail/localizations/fiscal-integration-functionality.md#solution-design-for-local-fiscal-devices).

### Request handler
	
The request handler DocumentProviderEpsonFP90III is the entry point for the request to generate documents from the fiscal printer.

The handler is inherited from the INamedRequestHandler interface. The Method HandlerName is responsible for returning the name of the handler. It should match the connector document provider name specified in HQ.

The connector supports the following requests:
- GetFiscalDocumentDocumentProviderRequest- Contains information about what document should be generated. Returns a printer-specific document that should be registered in the fiscal printer.
- GetSupportedRegistrableEventsDocumentProviderRequest - Returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, and printing Z report.

### Configuration
The configuration file is found in the Configuration folder of the extension project. The purpose of the file is to allow to configure settings for the document provider from the HQ. The file format aligns fiscal integration configuration requirements. The following settings have been added:
- VAT codes mapping
- VAT rates mapping
- Tender type mapping
- Barcode type for receipt number
- Deposit payment type

## Hardware station extension design

The purpose of the extension (Connector) is to communicate with the fiscal printer.

Hardware station extension: **HardwareStation.Extensions.EpsonFP90IIIFiscalDeviceSample**.

The Hardware station extension submits documents generated by the Commerce runtime extension to the fiscal printer (via HTTP protocol) and handles the responses received from it.

### Request handler
The request handler EpsonFP90IIISample is the entry point for handling request to the fiscal peripheral device. The handler is inherited from INamedRequestHandler interface. Method HandlerName is responsible for returning the name of the handler, it should match the fiscal connector name specified in HQ.

The connector supports the following requests:
- SubmitDocumentFiscalDeviceRequest - Sends document to printers and returns response from the fiscal printer.
- IsReadyFiscalDeviceRequest - Used for a health check of the device.
- InitializeFiscalDeviceRequest - Used for printer initialization.


### Configuration
The configuration file is found in **Configuration** folder of the extension project. The purpose of the file is to allow to configure settings for the connector provider from the HQ. The file format aligned fiscal Integration configuration requirements. The following settings have been added:
- Endpoint address - URL of the printer.
- Date and time synchronization - This indicates if you need to the sync date and time of the printer with the connected hardware station. The date and time of the printer will be synchronized with the Hardware station time.

## Limitations of the sample

  - The fiscal printer supports the scenarios with salex tax included in price only. So, the parameter **Price include sales tax** must be set to **Yes** both for retail stores and customers.
  - Daily reports (fiscal X, fiscal Z) are printed using the format embedded in the fiscal printer firmware.
  - Mixed transactions are not supported by the fiscal printer. The parameter **Prohibit mixing sales and returns in one receipt** should be set to **Yes** in POS functionality profiles.
  - The sample supports integration with the fiscal prtinter working in the data transfer fiscal printer mode only also called **RT mode (Registratore Telematico)**. 
