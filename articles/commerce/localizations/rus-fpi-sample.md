---
# required metadata

title: Fiscal printer integration sample for Russia
description: This topic provides an overview of the fiscal integration sample for Italy.
author: EvgenyPopovMBS
manager: annbe
ms.date: 09/02/2021
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
ms.search.region: Russia
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2021-8-2
ms.dyn365.ops.version: 10.0.21

---
# Fiscal printer integration sample for Russia

[!include [banner](../includes/banner.md)]

## Introduction

The Dynamics 365 Commerce functionality for Russia includes a sample integration of the point of sale (POS) with a fiscal printer. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and supports the application programming interface (API) of fiscal printers from [ATOL](http://integration.atol.ru/). The sample enables communication with a fiscal printer that is connected via a communication (COM) port by using a native software driver. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from ATOL. For information about how to get the fiscal printer and operate it, contact [ATOL](https://www.atol.ru/).

> [!NOTE]
> This sample code is intended to be used with certain cash register software from ATOL, a third party. You are responsible for your use of ATOL services, and any use is subject to a separate [end user agreement](http://integration.atol.ru/eula/) between you and ATOL. You understand that the data handling, compliance and security standards of ATOL may
not be the same as Microsoft Dynamics 365 Commerce. Your privacy is important to us. To learn more read our [Privacy statement](https://go.microsoft.com/fwlink/?LinkId=521839).

See [Commerce localization for Russia](rus-commerce-localization.md) for more information on Commerce features available to customers in Russia.

## Scenarios

The following scenarios are covered by the fiscal printer integration sample for Russia:

- Sales scenarios:

    - Print a fiscal receipt for cash-and-carry sales and returns.
    - Capture a response from the fiscal printer, and store it in the channel database.
    - Taxes:

        - Map tax rates to the fiscal printer's tax types.
        - Transfer mapped tax data to the fiscal printer.

    - Payments:

        - Map the store's payment methods to the fiscal printer's payment types.
        - Print payments on a fiscal receipt.
        - Print change information.

    - Print line discount information.
    - Send the [customer information](rus-customer-information.md) that is specified for a sales transaction with a fiscal receipt. An example of this information is the customer's email address.

- Daily reports (fiscal X and fiscal Z reports).
- Error handling, such as the following options:

    - Retry fiscal registration if a retry is possible, such as if the fiscal printer isn't connected, isn't ready, or isn't responding, the printer is out of paper, or there is a paper jam.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Check the availability of the fiscal printer before a new sales transaction is opened or a sales transaction is finalized.

### Limitations of the sample

- The fiscal printer supports only scenarios where sales tax is included in the price. Therefore, the **Price include sales tax** option must be set to **Yes** for both stores and customers.
- Printing of fiscal receipts for customer order operations (e.g., deposit, pick up, ship, etc.) is not currently supported. Support of customer order operations may be added in later versions.
- Printing of fiscal receipts for petty cash operations, such as tender declaration, float entry, tender removal, etc., is not currently supported. Support of petty cash operations may be added in later versions.
- Daily reports (fiscal X and fiscal Z) are printed by using the fiscal printer's embedded format.
- The fiscal printer doesn't support mixed transactions. The **Prohibit mixing sales and returns in one receipt** option should be set to **Yes** in POS functionality profiles.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample:

- Payment method mapping:
    ```json
    {
      "PaymentMethods": [
        {"StorePaymentMethod":"1", "AtolPaymentType":0},
        {"StorePaymentMethod":"2", "AtolPaymentType":4},
        {"StorePaymentMethod":"3", "AtolPaymentType":1},
        {"StorePaymentMethod":"4", "AtolPaymentType":3},
        {"StorePaymentMethod":"5", "AtolPaymentType":0},
        {"StorePaymentMethod":"6", "AtolPaymentType":0},
        {"StorePaymentMethod":"7", "AtolPaymentType":4},
        {"StorePaymentMethod":"8", "AtolPaymentType":4},
        {"StorePaymentMethod":"10", "AtolPaymentType":4},
        {"StorePaymentMethod":"11", "AtolPaymentType":4}
     ]
    }    
    ```

The default payment method mapping is based on the store payment method configuration in demo data. You may need to modify the mapping in the connector functional profile according to the settings of payment methods for your stores. See also the [ATOL integration documentation](http://integration.atol.ru/) for more information on payment types supported by ATOL fiscal printers.

## Set up fiscal integration for Russia

For more information on general Commerce settings for Russia, see [Set up Commerce localization for Russia](rus-commerce-setup.md).

To set up fiscal integration for Russia, complete the fiscal registration setup steps that are described in [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md):

1. [Set up a fiscal registration process](./setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Be sure to note the settings of the fiscal registration process that are [specific to Russia](#configure-the-fiscal-registration-process).
1. [Set error handling settings](./setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Set up fiscal X/Z reports from the POS](setting-up-fiscal-integration-for-retail-channel.md#set-up-fiscal-xz-reports-from-the-pos).
1. [Enable manual execution of postponed fiscal registration](./setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).
1. [Set up the functionality for management of customer information in POS](rus-customer-information.md#setup)

### Configure the fiscal registration process

To enable the fiscal registration process for Russia in Commerce headquarters, follow these steps.

1. Download configuration files for the fiscal document provider and the fiscal connector from the Commerce SDK:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    2. Open the last available release branch (for example, **[release/9.31](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.31)**).
    3. Open **src \> FiscalIntegration \> AtolFiscalPrinterSample**.
    4. Download the fiscal connector configuration file at **HardwareStation \> Connector.AtolSample \> ConfigurationTemplate \> ConnectorAtolSample.xml** (for example, [the file for release/9.31](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.31/src/FiscalIntegration/AtolFiscalPrinterSample/HardwareStation/Connector.AtolSample/ConfigurationTemplate/ConnectorAtolSample.xml)).
    5. Download the fiscal document provider configuration file at **CommerceRuntime \> DocumentProvider.AtolSample \> ConfigurationTemplate \> DocumentProviderAtolSample.xml** (for example, [the file for release/9.31](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.31/src/FiscalIntegration/AtolFiscalPrinterSample/CommerceRuntime/DocumentProvider.AtolSample/ConfigurationTemplate/DocumentProviderAtolSample.xml)).

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the fiscal connector configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the fiscal document provider configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile, and select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Set the connector type to **Internal**. Update the other connection settings as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**, and create a new fiscal connector group for the connector functional profile that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, create a fiscal registration process step, and select the fiscal connector group that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Open the functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the registration process that was created earlier.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Open the hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**. Open the distribution schedule, and select jobs **1070** and **1090** to transfer data to the channel database.

### Configure channel components

The fiscal printer integration sample for Russia is part of the Retail SDK. The sample is located in the **src \> FiscalIntegration \> AtolFiscalPrinterSample** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository (for example, [the sample in release/9.31](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.31/src/FiscalIntegration/AtolFiscalPrinterSample)). [The sample consists](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices) of a fiscal document provider, which is an extension of Commerce Runtime (CRT), and a fiscal connector, which is an extension of Hardware station. For more information about how to use the Retail SDK, see [Retail SDK architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).
