---
# required metadata

title: Fiscal printer integration sample for Italy
description: This topic provides an overview of the fiscal integration sample for Italy in Microsoft Dynamics 365 Commerce.
author: EvgenyPopovMBS
ms.date: 12/20/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: epopov
ms.search.validFrom: 2018-11-1

---
# Fiscal printer integration sample for Italy

[!include[banner](../includes/banner.md)]

This topic provides an overview of the fiscal integration sample for Italy in Microsoft Dynamics 365 Commerce.

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

        - Exclude an issued/recharged gift card line from a fiscal receipt for a sale.
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

### Gift cards

The fiscal printer integration sample implements the following rules that are related to gift cards:

- Exclude sales lines that are related to the *Issue gift card* and *Add to gift card* operations from the fiscal receipt.
- Don't print a fiscal receipt if it consists of only gift card lines.
- Deduct the total amount of gift cards that are issued or recharged in a transaction from payment lines of the fiscal receipt.
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
- The sample supports integration only with a fiscal printer that is working in the Registratore Telematico (RT)) mode.

## Set up fiscal integration for Italy

The fiscal printer integration sample for Italy is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Retail SDK. The sample is located in the **src\\FiscalIntegration\\EpsonFP90IIISample** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository (for example, [the sample in release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33/src/FiscalIntegration/EpsonFP90IIISample)). The sample [consists](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) of a fiscal document provider, which is an extension of the Commerce runtime (CRT), and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Retail SDK, see [Retail SDK architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Deployment guidelines for the fiscal printer integration sample for Italy (legacy)](emea-ita-fpi-sample-sdk.md).
>
> Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md).

1. [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Also, make a note of the settings for the fiscal registration process that are [specific to this fiscal printer integration sample](#set-up-the-registration-process).
1. [Set up fiscal texts for discounts](setting-up-fiscal-integration-for-retail-channel.md#set-up-fiscal-texts-for-discounts).
1. [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Set up fiscal X/Z reports from the POS](setting-up-fiscal-integration-for-retail-channel.md#set-up-fiscal-xz-reports-from-the-pos).
1. [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).
1. [Set up the functionality for management of customer information in POS](emea-ita-customer-information.md#setup).
1. [Configure channel components](#configure-channel-components).

### Set up the registration process

To enable the registration process, follow these steps to set up Commerce headquarters. For more information, see [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Download configuration files for the fiscal document provider and the fiscal connector:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    1. Select a correct release branch version according to your SDK/application version (for example, **[release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33)**).
    1. Open **src \> FiscalIntegration \> EpsonFP90IIISample**.
    1. Download the fiscal document provider configuration file at **CommerceRuntime \> DocumentProvider.EpsonFP90IIISample \> Configuration \> DocumentProviderEpsonFP90IIISample.xml** (for example, [the file for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.33/src/FiscalIntegration/EpsonFP90IIISample/CommerceRuntime/DocumentProvider.EpsonFP90IIISample/Configuration/DocumentProviderEpsonFP90IIISample.xml)).
    1. Download the fiscal connector configuration file at **HardwareStation \> EpsonFP90IIIFiscalDeviceSample \> Configuration \> ConnectorEpsonFP90IIISample.xml** (for example, [the file for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.33/src/FiscalIntegration/EpsonFP90IIISample/HardwareStation/EpsonFP90IIIFiscalDeviceSample/Configuration/ConnectorEpsonFP90IIISample.xml).

    > [!WARNING]
    > Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. The configuration files for this fiscal integration sample are located in the following folders of the Retail SDK on a developer VM in LCS:
    >
    > - **Fiscal document provider configuration file:** RetailSdk\\SampleExtensions\\CommerceRuntime\\Extension.DocumentProvider.EpsonFP90IIISample\\Configuration\\DocumentProviderEpsonFP90IIISample.xml
    > - **Fiscal connector configuration file:** RetailSdk\\SampleExtensions\\HardwareStation\\Extension.EpsonFP90IIIFiscalDeviceSample\\Configuration\\ConnectorEpsonFP90IIISample.xml
    > 
    > Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the fiscal document provider configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the fiscal connector configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile. Select the document provider and the connector that you loaded earlier. Update the [data mapping settings](#default-data-mapping) as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the fiscal connector that you loaded earlier. Update the [connector settings](#fiscal-connector-settings) as required.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group for the connector functional profile that you created earlier.
7. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process and a fiscal registration process step, and select the fiscal connector group that you created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
9. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
10. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

#### Default data mapping

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

#### Fiscal connector settings

The following settings are included in the fiscal connector configuration that is provided as part of the fiscal integration sample:

- **Endpoint address** – The URL of the printer.
- **Date and time synchronization** – A value that specifies whether the date and time of the printer must be synced with the connected Hardware station.

### Configure channel components

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the fiscal printer integration sample for Italy (legacy)](emea-ita-fpi-sample-sdk.md).
>
> Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

#### Set up the development environment

To set up a development environment to test and extend the sample, follow these steps.

1. Clone or download the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository. Select a correct release branch version according to your SDK/application version. For more information, see [Download Retail SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md).
1. Open the fiscal printer integration solution at **Dynamics365Commerce.Solutions\\FiscalIntegration\\EpsonFP90IIISample\\EpsonFP90IIISample.sln**, and build it.
1. Install CRT extensions:

    1. Find the CRT extension installer:

        - **Commerce Scale Unit:** In the **EpsonFP90IIISample\\ScaleUnit\\ScaleUnit.EpsonFP90III.Installer\\bin\\Debug\\net461** folder, find the **ScaleUnit.EpsonFP90III.Installer** installer.
        - **Local CRT on Modern POS:** In the **EpsonFP90IIISample\\ModernPOS\\ModernPOS.EpsonFP90III.Installer\\bin\\Debug\\net461** folder, find the **ModernPOS.EpsonFP90III.Installer** installer.

    1. Start the CRT extension installer from the command line:

        - **Commerce Scale Unit:**

            ```Console
            ScaleUnit.EpsonFP90III.Installer.exe install --verbosity 0
            ```

        - **Local CRT on Modern POS:**

            ```Console
            ModernPOS.EpsonFP90III.Installer.exe install --verbosity 0
            ```

1. Install Hardware station extensions:

    1. In the **EpsonFP90IIISample\\HardwareStation\\HardwareStation.EpsonFP90III.Installer\\bin\\Debug\\net461** folder, find the **HardwareStation.EpsonFP90III.Installer** installer.
    1. Start the extension installer from the command line:

        ```Console
        HardwareStation.EpsonFP90III.Installer.exe install --verbosity 0
        ```

#### Production environment

Follow the steps in [Set up a build pipeline for a fiscal integration sample](fiscal-integration-sample-build-pipeline.md) to generate and release the Cloud Scale Unit and self-service deployable packages for the fiscal integration sample. The **EpsonFP90III build-pipeline.yml** template YAML file can be found in the **Pipeline\\YAML_Files** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository.

## Design of extensions

The fiscal printer integration sample for Italy is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Retail SDK. The sample is located in the **src\\FiscalIntegration\\EpsonFP90IIISample** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository (for example, [the sample in release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33/src/FiscalIntegration/EpsonFP90IIISample)). The sample [consists](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) of a fiscal document provider, which is an extension of CRT, and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Retail SDK, see [Retail SDK architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the fiscal printer integration sample for Italy (legacy)](emea-ita-fpi-sample-sdk.md). Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate printer-specific documents and handle responses from the fiscal printer.

#### Request handler

The **DocumentProviderEpsonFP90III** request handler is the entry point for the request to generate documents from the fiscal printer.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Commerce headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a printer-specific document that should be registered in the fiscal printer.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, and printing Z report.

#### Configuration

The configuration file for the fiscal document provider is located at **src\\FiscalIntegration\\EpsonFP90IIISample\\CommerceRuntime\\DocumentProvider.EpsonFP90IIISample\\Configuration\\DocumentProviderEpsonFP90IIISample.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings for the document provider to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal printer. This extension uses the HTTP protocol to submit documents that the CRT extension generates to the fiscal printer. It also handles the responses that are received from the fiscal printer.

#### Request handler

The **EpsonFP90IIISample** request handler is the entry point for handling request to the fiscal peripheral device.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Commerce headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to printers and returns the response from the fiscal printer.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the device.
- **InitializeFiscalDeviceRequest** – This request is used for printer initialization.

#### Configuration

The configuration file for the fiscal connector is located at **src\\FiscalIntegration\\EpsonFP90IIISample\\HardwareStation\\EpsonFP90IIIFiscalDeviceSample\\Configuration\\ConnectorEpsonFP90IIISample.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings for the connector to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
