---
# required metadata

title: Fiscal printer integration sample for Poland
description: This topic provides an overview of the fiscal integration sample for Poland in Microsoft Dynamics 365 Commerce.
author: EvgenyPopovMBS
ms.date: 12/20/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: epopov
ms.search.validFrom: 2019-2-1

---
# Fiscal printer integration sample for Poland

[!include[banner](../includes/banner.md)]

This topic provides an overview of the fiscal integration sample for Poland in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce functionality for Poland includes a sample integration of the point of sale (POS) with a fiscal printer. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and supports the POSNET THERMAL HD 2.02 protocol for fiscal printers from [Posnet Polska S.A.](https://www.posnet.com.pl) The sample enables communication with a fiscal printer that is connected via a COM port by using a native software driver. It was implemented and tested by using a software emulator that Posnet provided for the Posnet Thermal HD FV EJ fiscal printer. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from Posnet. For information about how to get the fiscal printer and operate it, contact [Posnet Polska S.A.](https://www.posnet.com.pl)

## Scenarios

The following scenarios are covered by the fiscal printer integration sample for Poland:

- Sales scenarios:

    - Print a fiscal receipt for cash-and-carry sales and returns.
    - Capture a response from the fiscal printer, and store it in the channel database.
    - Taxes:

        - Map to the fiscal printer's tax codes (departments).
        - Transfer mapped tax data to the fiscal printer.

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

    - Print the [customer information](emea-pol-customer-information.md) that is specified for a sales transaction on a fiscal receipt. An example of this information is the customer's VAT number.

- End of day statements (fiscal X and fiscal Z reports).
- Error handling, such as the following options:

    - Retry fiscal registration if a retry is possible, such as if the fiscal printer isn't connected, isn't ready, or isn't responding, the printer is out of paper, or there is a paper jam.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Check the availability of the fiscal printer before a new sales transaction is opened or a sales transaction is finalized.

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
- Daily reports (fiscal X and fiscal Z) are printed by using the embedded *Shift report* format.
- Printing a bar code on fiscal receipts is considered a potential customization, because this feature isn't supported in the embedded formats and can be implemented only by using the customizable **Super-format** report.
- The fiscal printer doesn't support mixed transactions. The **Prohibit mixing sales and returns in one receipt** option should be set to **Yes** in POS functionality profiles.

## Set up fiscal integration for Poland

The fiscal printer integration sample for Poland is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Retail SDK. The sample is located in the **src\\FiscalIntegration\\Posnet** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository (for example, [the sample in release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33/src/FiscalIntegration/Posnet)). The sample [consists](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) of a fiscal document provider, which is an extension of the Commerce runtime (CRT), and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Retail SDK, see [Retail SDK architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Deployment guidelines for the fiscal printer integration sample for Poland (legacy)](emea-pol-fpi-sample-sdk.md).
>
> Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md).

1. [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Also, make a note of the settings for the fiscal registration process that are [specific to this fiscal printer integration sample](#set-up-the-registration-process).
1. [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Set up fiscal X/Z reports from the POS](setting-up-fiscal-integration-for-retail-channel.md#set-up-fiscal-xz-reports-from-the-pos).
1. [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).
1. [Configure channel components](#configure-channel-components).

### Set up the registration process

To enable the registration process, follow these steps to set up Commerce headquarters. For more information, see [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Download configuration files for the fiscal document provider and the fiscal connector:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    1. Select a correct release branch version according to your SDK/application version (for example, **[release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33)**).
    1. Open **src \> FiscalIntegration \> Posnet**.
    1. Download the fiscal document provider configuration file at **CommerceRuntime \> DocumentProvider.PosnetSample \> Configuration \> DocumentProviderPosnetSample.xml** (for example, [the file for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.33/src/FiscalIntegration/Posnet/CommerceRuntime/DocumentProvider.PosnetSample/Configuration/DocumentProviderPosnetSample.xml)).
    1. Download the fiscal connector configuration file at **HardwareStation \> ThermalDeviceSample \> Configuration \> ConnectorPosnetThermalFVEJ.xml** (for example, [the file for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.33/src/FiscalIntegration/Posnet/HardwareStation/ThermalDeviceSample/Configuration/ConnectorPosnetThermalFVEJ.xml)).

    > [!WARNING]
    > Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. The configuration files for this fiscal integration sample are located in the following folders of the Retail SDK on a developer VM in LCS:
    >
    > - **Fiscal document provider configuration file:** RetailSdk\\SampleExtensions\\CommerceRuntime\\Extension.DocumentProvider.PosnetSample\\Configuration\\DocumentProviderPosnetSample.xml
    > - **Fiscal connector configuration file:** RetailSdk\\SampleExtensions\\HardwareStation\\Extension.Posnet.ThermalDeviceSample\\Configuration\\ConnectorPosnetThermalFVEJ.xml
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

- **Value-added tax (VAT) rates mapping** – The mapping of tax percentage values that are set up for the sales tax codes to fiscal printer–specific VAT rates. Here is the default mapping:

    ```
    0 : 23.00 ; 1 : 8.00 ; 2 : 5.00 ; 3 : 0.00
    ```

    The first component in each pair represents a VAT rate number that is configured in the fiscal printer. The second component represents the corresponding VAT rate. For more information about the fiscal printer VAT rate configuration, see the POSNET driver documentation.

- **Tender type mapping** – The mapping of payment methods that are configured for the store to payment forms that are supported by the fiscal printer. Here is the default mapping:

    ```
    0 : 0 ; 1 : 0 ; 2 : 2 ; 3 : 2 ; 4 : 0 ; 5 : 0 ; 6 : 0 ; 7 : 2 ; 8 : 0
    ```

    The first component in each pair represents a payment method that is set up for the store. The second component represents the corresponding payment form that is supported by the fiscal printer. For more information about payment forms that the fiscal printer supports, see the POSNET driver documentation. You must modify the sample mapping according to the payment methods that are configured in your application.

#### Fiscal connector settings

The following settings are included in the fiscal connector configuration that is provided as part of the fiscal integration sample:

- **Connection string** – A string that describes the details of the connection to the device in a format that is supported by the driver. For more information, see the POSNET driver documentation.
- **Date and time synchronization** – A value that specifies whether the date and time of the printer must be synced with the connected Hardware station.
- **Device timeout** – The amount of time, in milliseconds, that the driver will wait for a response from the device. For more information, see the POSNET driver documentation.

### Configure channel components

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the fiscal printer integration sample for Poland (legacy)](emea-pol-fpi-sample-sdk.md).
>
> Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

#### Set up the development environment

To set up a development environment to test and extend the sample, follow these steps.

1. Clone or download the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository. Select a correct release branch version according to your SDK/application version. For more information, see [Download Retail SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md).
1. Open the fiscal printer integration solution at **Dynamics365Commerce.Solutions\\FiscalIntegration\\Posnet\\Posnet.sln**, and build it.
1. Install CRT extensions:

    1. Find the CRT extension installer:

        - **Commerce Scale Unit:** In the **Posnet\\ScaleUnit\\ScaleUnit.Posnet.Installer\\bin\\Debug\\net461** folder, find the **ScaleUnit.Posnet.Installer** installer.
        - **Local CRT on Modern POS:** In the **Posnet\\ModernPOS\\ModernPOS.Posnet.Installer\\bin\\Debug\\net461** folder, find the **ModernPOS.Posnet.Installer** installer.

    1. Start the CRT extension installer from the command line:

        - **Commerce Scale Unit:**

            ```Console
            ScaleUnit.Posnet.Installer.exe install --verbosity 0
            ```

        - **Local CRT on Modern POS:**

            ```Console
            ModernPOS.Posnet.Installer.exe install --verbosity 0
            ```

1. Install Hardware station extensions:

    1. In the **Posnet\\HardwareStation\\HardwareStation.PosnetThermalFVFiscalPrinter.Installer\\bin\\Debug\\net461** folder, find the **HardwareStation.PosnetThermalFVFiscalPrinter.Installer** installer.
    1. Start the extension installer from the command line:

        ```Console
        HardwareStation.PosnetThermalFVFiscalPrinter.Installer.exe install --verbosity 0
        ```

#### Production environment

Follow the steps in [Set up a build pipeline for a fiscal integration sample](fiscal-integration-sample-build-pipeline.md) to generate and release the Cloud Scale Unit and self-service deployable packages for the fiscal integration sample. The **Posnet build-pipeline.yml** template YAML file can be found in the **Pipeline\\YAML_Files** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository.

## Design of extensions

The fiscal printer integration sample for Poland is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Retail SDK. The sample is located in the **src\\FiscalIntegration\\Posnet** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository (for example, [the sample in release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33/src/FiscalIntegration/Posnet)). The sample [consists](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) of a fiscal document provider, which is an extension of CRT, and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Retail SDK, see [Retail SDK architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the fiscal printer integration sample for Poland (legacy)](emea-pol-fpi-sample-sdk.md). Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

### Commerce runtime extension design

The purpose of the extension that is a fiscal document provider is to generate printer-specific documents and handle responses from the fiscal printer. This extension generates a set of printer-specific commands in JavaScript Object Notation (JSON) format that are defined by POSNET specification 19-3678.

#### Request handler

The **DocumentProviderPosnetProtocol** request handler is the entry point for the request to generate documents from the fiscal printer.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Commerce headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a printer-specific document that should be registered in the fiscal printer.
- **GetSupportedRegistrableEventsDocumentProviderRequest** – This request returns the list of events to subscribe to. Currently, the following events are supported: sales, printing X report, and printing Z report.

#### Configuration

The configuration file for the fiscal document provider is located at **src\\FiscalIntegration\\Posnet\\CommerceRuntime\\DocumentProvider.PosnetSample\\Configuration\\DocumentProviderPosnetSample.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings of the fiscal document provider to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal printer. This extension calls the functions of the POSNET driver to submit commands that the CRT extension generates to the fiscal printer. It also handles device errors.

#### Request handler

The **FiscalPrinterHandler** request handler is the entry point for handling the request to the fiscal peripheral device.

The handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Commerce headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to printers and returns the response from the fiscal printer.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the device.
- **InitializeFiscalDeviceRequest** – This request is used for printer initialization.

#### Configuration

The configuration file for the fiscal connector is located at **src\\FiscalIntegration\\Posnet\\HardwareStation\\ThermalDeviceSample\\Configuration\\ConnectorPosnetThermalFVEJ.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings of the fiscal connector to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
