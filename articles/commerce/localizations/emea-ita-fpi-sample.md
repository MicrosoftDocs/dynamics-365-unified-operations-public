---
# required metadata

title: Fiscal printer integration sample for Italy
description: This topic provides an overview of the fiscal integration sample for Italy.
author: EvgenyPopovMBS
ms.date: 11/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
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
        - Print a fiscal receipt for carryout lines of a hybrid customer order.
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

- **Tender type mapping** – The mapping of payment methods that are configured for the store to payment types that the fiscal printer supports. The following example shows the default mapping.

    ```JSON
    {"PaymentMethods": [
        {"StorePaymentMethod":"1", "PrinterPaymentType":"0", "PrinterPaymentIndex":"00"},
        {"StorePaymentMethod":"3", "PrinterPaymentType":"2", "PrinterPaymentIndex":"00"},
        {"StorePaymentMethod":"4", "PrinterPaymentType":"2", "PrinterPaymentIndex":"01"},
        {"StorePaymentMethod":"6", "PrinterPaymentType":"0", "PrinterPaymentIndex":"01"},
        {"StorePaymentMethod":"8", "PrinterPaymentType":"6", "PrinterPaymentIndex":"01"}
        ],
        "DepositPaymentMethod": {"PrinterPaymentType":"2", "PrinterPaymentIndex":"00"}}
    ```

    Here is an explanation of the attributes in this mapping:

    - **StorePaymentMethod** is a payment method that is set up for the store at **Retail and Commerce \> Channel setup \> Payment methods \> Payment methods**.
    - **PrinterPaymentType** and **PrinterPaymentIndex** are the corresponding payment type and index that are defined in the Epson fiscal printer documentation.
    - **DepositPaymentMethod** is used to specify a printer's payment type and index for the part of the customer order pickup amount that is settled with the customer order deposit.

    The following table shows how the sample mapping of payment methods corresponds to store payment methods that are configured in the standard demo data.

    | Payment method | Payment method name |
    |----------------|---------------------|
    | 1              | Cash                |
    | 3              | Card                |
    | 4              | Customer account    |
    | 6              | Currency            |
    | 8              | Gift card           |

    You must modify the sample mapping according to the payment methods that are configured in your application.

- **Barcode type for receipt number** – The type of bar code that is used to show a receipt number on a fiscal receipt. The default mapping is **CODE128**.
- **Print fiscal data in receipt header** – If this parameter is turned on, store information will be printed on the fiscal receipt. This information includes the store's name, address, and tax identification number, and the cashier's name.
- **Fiscal printer department mapping** – The mapping of departments of the fiscal printer to value-added tax (VAT) rates, VAT exempt natures, and product types. The following example shows the default mapping.

    ```JSON
    {"Departments": [
        {"VATRate":"2200", "VATExemptNature":"", "ProductType":"0", "DepartmentNumber":"01"},
        {"VATRate":"2200", "VATExemptNature":"", "ProductType":"1", "DepartmentNumber":"02"},
        {"VATRate":"1000", "VATExemptNature":"", "ProductType":"0", "DepartmentNumber":"03"},
        {"VATRate":"1000", "VATExemptNature":"", "ProductType":"1", "DepartmentNumber":"04"},
        {"VATRate":"0500", "VATExemptNature":"", "ProductType":"0", "DepartmentNumber":"05"},
        {"VATRate":"0500", "VATExemptNature":"", "ProductType":"1", "DepartmentNumber":"06"},
        {"VATRate":"0400", "VATExemptNature":"", "ProductType":"0", "DepartmentNumber":"07"},
        {"VATRate":"0400", "VATExemptNature":"", "ProductType":"1", "DepartmentNumber":"08"},
        {"VATRate":"0000", "VATExemptNature":"", "ProductType":"0", "DepartmentNumber":"09"},
        {"VATRate":"0000", "VATExemptNature":"", "ProductType":"1", "DepartmentNumber":"10"},
        {"VATRate":"0000", "VATExemptNature":"NS", "ProductType":"0", "DepartmentNumber":"99"}]}
    ```

    Here is an explanation of the attributes in this mapping:

    - **VATRate** is a supported VAT rate that is configured as a sales tax code. The value in the mapping has two decimal places but no decimal separator. For example, **2200** represents 22 percent, and **1000** represents 10 percent.
    - **VATExemptNature** is applicable only in cases where the VAT rate is 0 (zero), including cases where there is no tax. Currently, **VATExemptNature** is supported only for gift cards, and the value in the mapping should correspond to the value of the **VATExemptNatureForGiftCard** property in the XML configuration file.
    - **ProductType** is the type of product. A value of **0** represents goods, and a value of **1** represents services.
    - **DepartmentNumber** is the number of the department that is configured in the printer and that corresponds to the previous three attributes.

    You must modify the sample mapping according to the VAT rates that are configured in your application and corresponding departments that are configured in your fiscal printer.

- **VAT exempt nature for gift card** – The VAT exempt nature that should be applied when a gift card is issued or refilled. The value should correspond to some entry in the fiscal printer department mapping. The default mapping is **NS**.
- **Enable free of charge items** – If this parameter is turned on, the special *omaggio* discount adjustment type for items that have a 100-percent discount is enabled.
- **Info code for return origin** – The info code that is used to capture the origin of a return transaction if no original sales receipt is provided. This parameter is used together with the **Info code for original sales date** and **Return origin mapping** parameters to generate a correct message in the fiscal receipt about the origin of a return transaction if no original sales transaction exists. 

    This info code should be configured to enable the user to select or enter one of the possible origins of returns in your stores. For example, it can be configured as a list of subcodes (such as **Return from site** or **Return from kiosk**). The **Return origin mapping** parameter is then used to translate the value of the info code into a command for the fiscal printer.

    The info code that is selected for **Info code for return origin** should be configured as a mandatory info code that is fired one time per sales transaction. It should be assigned as the **Return product** info code in the POS functionality profile, so that it's fired when the **Return product** operation is run.

    No default value is specified for this mapping. You must select an info code that is configured in your application.

- **Info code for original sales date** – The info code that is used to capture the original sales date for a return transaction if no original sales receipt is provided. This parameter is used together with the **Info code for return origin** and **Return origin mapping** parameters to generate a correct message in the fiscal receipt about the origin of a return transaction if no original sales transaction exists.

    The info code should be configured so that the **Input type** field is set to **Date**. It should be configured as a mandatory info code that is fired one time per sales transaction. It should also be assigned as the **Linked info code** for the info code that is selected for the **Info code for return origin** parameter, so that the two info codes are fired one after another.

    No default value is specified for this mapping. You must select an info code that is configured in your application.

- **Return origin mapping** – The mapping of return origins that is used to print the origin of a return transaction if no original sales receipt is provided. This parameter is used together with the **Info code for return origin** and **Info code for original sales date** parameters to generate a correct message in the fiscal receipt about the origin of a return transaction if no original sales transaction exists. The following example shows the default mapping.

    ```JSON
    {"ReturnOrigins": [
        {"ReturnOrigin":"1", "PrinterReturnOrigin":"POS"},
        {"ReturnOrigin":"2", "PrinterReturnOrigin":"ND"}
        ],
        "PrinterReturnOriginWithoutFiscalData":"POS"}
    ```

    Here is an explanation of the attributes in this mapping:

    - **ReturnOrigin** is one of possible origins of returns in your stores. The value should correspond to a value of the **Info code for return origin** parameter.
    - **PrinterReturnOrigin** is one of the return origins that the fiscal printer accepts (**POS**, **VR**, or **ND**).
    - **PrinterReturnOriginWithoutFiscalData** is the return origin that the fiscal printer accepts and that corresponds to a return transaction that is linked to an original sales transaction that doesn't have linked fiscal data, because it wasn't registered through a fiscal printer. In this case, the original sales date is identified as the date of the original sales transaction.

The following default data mappings are obsolete and are kept only for backward compatibility:

- Value-added tax (VAT) codes mapping
- Deposit payment type

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

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md):

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

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the bin\\ext folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

1. Register the CRT change in the extensions configuration file. Add **source="assembly" value="Contoso.Commerce.Runtime.DocumentProvider.EpsonFP90IIISample"**.
1. Restart the Commerce Scale Unit:

    - **Commerce Scale Unit:** Restart the Commerce Scale Unit site from IIS Manager.
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
3. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Connector Technical profiles**. Create a new profile, and then select the loaded connector from the earlier step. Update the connection settings if an update is required.
4. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Connector Functional profiles**. Create a new profile, and then select the loaded connector and document provider from the earlier steps. Update data mapping settings if an update is required.
5. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Connector Functional group**. Create a new group, and then select the connector functional profile from the earlier step.
6. Go to **Retail and Commerce \> Channel Setup \> Fiscal Integration \> Registration process**. Create a new process, and then select the connector functional group from the earlier step.
7. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Open the functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the registration process that was created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Open the hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile.
9. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and then select jobs **1070** and **1090** to transfer data to the channel database.

### Production environment

To create deployable packages that contain Commerce components, and apply those packages in a production environment, follow these steps.

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

4. Start the MSBuild Command Prompt for Visual Studio utility, and then run **msbuild** under the Retail SDK folder to create deployable packages.
5. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Design of extensions

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate printer-specific documents and handle responses from the fiscal printer.

The Commerce runtime extension is **Runtime.Extensions.DocumentProvider.EpsonFP90IIISample**.

For more details about the design of the fiscal integration solution, see [Fiscal registration process and fiscal integration samples for fiscal devices](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices and services).

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


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
