---
title: Fiscal registration service integration sample for Germany
description: This article provides an overview of the fiscal integration sample for Germany in Microsoft Dynamics 365 Commerce.
author: EvgenyPopovMBS
ms.date: 10/04/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-05-29

---
# Fiscal registration service integration sample for Germany

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article provides an overview of the fiscal integration sample for Germany in Microsoft Dynamics 365 Commerce.

To meet local fiscal requirements for cash registers in Germany, the Dynamics 365 Commerce functionality for Germany includes a sample integration of the point of sale (POS) with an external fiscal registration service. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It's based on the [EFR (Electronic Fiscal Register)](https://www.efsta.eu/de/fiskalloesungen/deutschland) solution from [EFSTA](https://www.efsta.eu/de/) and enables communication with the EFR service via the HTTPS protocol. The EFR service should be hosted on either the Retail Hardware station or a separate computer that can be connected to from the Hardware station. The sample is provided in the form of source code and is part of the Commerce software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from EFSTA. For information about how to get the EFR solution and operate it, contact [EFSTA](https://www.efsta.eu/de/kontakt/kontakt).

## Scenarios

The following scenarios are covered by the fiscal registration service integration sample for Germany.

### Sales operations

- **Registration of cash-and-carry sales and returns in the fiscal registration service:**

    Registration of sales operations includes the following steps:

    1. Registration of the transaction start

        The start of each transaction is registered in a technical security element (TSE) that is connected to the EFR service. As a result of registration, a TSE assigns a transaction ID (TID).

    2. Registration of the transaction end

        When a transaction is concluded at the POS, it's registered by using the same TID that was assigned during registration of the transaction start. At that moment, detailed transaction data is sent to the fiscal registration service. This data includes sales line information, and information about discounts, payments, and taxes.

    3. Capturing a response from the fiscal registration service

        Security data is received from a TSE as a part of a response and is saved in the transaction in the channel database. The security data consists of the following information:

        - TID
        - Date and time of the transaction start
        - Date and time of the transaction end
        - Signature counter
        - Check value
        - Serial number of the TSE

- **Registration of customer orders in the fiscal registration service:** The registration process is the same as the process for cash-and-carry sales and returns.
- **Registration of operations that involve gift cards and deposits:** The registration process is the same as the process for cash-and-carry sales and returns.

#### Notifying users about fiscal registration failures

There are two ways that the fiscal registration service can notify users about failures that occurred during the fiscal registration:

- Print additional information from the response in the **Info message** field on receipts.
- Show notifications from the fiscal service as user messages at the POS.

    > [!NOTE]
    > This notification mechanism requires that the **Show fiscal registration notifications** parameter on the **Connector technical profiles** page be turned on.

#### Printing receipts

Receipt printing is mandatory in Germany. All receipts must contain at least the following information:

- Name and address of the company
- Information about goods, including their prices and quantities
- Information about payments that were received
- Information about taxes, including total amounts per tax rate
- Security data:

    - TID
    - Date and time of the transaction start
    - Date and time of the transaction end
    - Signature counter
    - Check value
    - Serial number of the TSE

- Informational message

> [!NOTE]
> A QR code can also be printed on receipts. Although the QR code is optional, it's highly recommended. For more information about how to get QR code as a part of a response from the fiscal registration service, see the "EFR Guide \[DE\]" document that is published on the [EFSTA documentation](https://public.efsta.net/efr/) website.
>
> The **Info message** field on receipts shows a notification from the fiscal registration service. For example, if a signature device is broken, special text can be printed on a receipt.

#### Voided, suspended, and recalled transactions

- A voided transaction is registered as a request to terminate a transaction in the fiscal registration service.
- A suspended transaction is registered as a request to terminate a transaction in the fiscal registration service.
- Recall of a suspended transaction is registered as the start of a new transaction in the fiscal registration service.

### Non-sales transactions and shift closing

The following non-sales transactions are registered as non-fiscal operations in the fiscal registration service by using the **NFS** tag:

- Declare start amount
- Float entry
- Tender removal
- Safe drop
- Bank drop
- Income accounts
- Expense accounts

The **Close shift** operation is also registered as a non-fiscal operation in the fiscal registration service by using the **NFS** tag.

### Data export and audit

All transactions must be signed by a TSE to ensure their integrity, authenticity, and completeness, and to help prevent manipulation of recorded data.

> [!WARNING]
> Only a certified TSE can be used. For information about the types and models of TSEs that are supported in the EFR solution, see the "EFR Guide \[DE\]" document that is published on the [EFSTA documentation](https://public.efsta.net/efr/) website. For information about how to choose and obtain a TSE, contact [EFSTA](https://www.efsta.eu/at/kontakt).

Regulations in Germany require support for the DSFinV-K export. The DSFinV-K export can be triggered in the EFR solution. For more information about the DSFinV-K export, see the "EFR Guide \[DE\]" document that is published on the [EFSTA documentation](https://public.efsta.net/efr/) website.

### Limitations of the sample

The fiscal registration service supports only scenarios where sales tax is included in prices. Therefore, the **Prices include sales tax** option must be set to **Yes** for both stores and customers.

The fiscal service doesn't support situations where more than one sales tax code is applied to the same transaction line.

The fiscal integration framework doesn't support sales quotations. Therefore, those operations aren't registered in the fiscal service.

## Set up Commerce for Germany

This section describes the Commerce settings that are specific to and recommended for Germany. For more setup information, see [Commerce home page](../welcome.md).

To use the functionality that is specific to Germany, you must specify the following settings.

- In the primary address of the legal entity, set the **Country/region** field to **DEU** (Germany).
- In the POS functionality profile of every store that is located in Germany, set the **ISO code** field to **DE** (Germany).

You must also specify the following settings for Germany. Be sure to run appropriate distribution jobs after you complete the setup.

### Set up VAT per German requirements

You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax features, see [Sales tax overview](../../finance/general-ledger/indirect-taxes-overview.md).

On sales receipts, you can print an abbreviated code for a sales tax code (for example, "A" or "B"). To make this functionality available, set the **Code for printing** field on the **Sales tax codes** page.

### Set up stores

On the **All stores** page, update the store details. Specifically, set the following parameters:

- In the **Sales tax group** field, specify the sales tax group that should be used for sales to the default customer.
- Set the **Prices include sales tax** option to **Yes**.
- Set the **Name** field to the company name. This change helps ensure that the company name appears on a sales receipt. Alternatively, you can add the company name to the sales receipt layout as free-form text.
- Set the **Tax identification number (TIN)** field to the company identification number. This change helps ensure that the company identification number appears on a sales receipt. Alternatively, you can add the company identification number to the sales receipt layout as free-form text.

### Set up functionality profiles

Set up POS functionality profiles. On the **Receipt numbering** FastTab, set up receipt numbering by creating or updating records for the **Sale**, **Sales order**, and **Return** receipt transaction types.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

Add the following POS labels to the **POS** section of the **Language text** page.

| Language ID | Text ID | Text                                  |
|-------------|---------|---------------------------------------|
| en-US       | 900001  | QR code                               |
| en-US       | 900002  | Transaction ID                        |
| en-US       | 900003  | Tax Retail Print Code                 |
| en-US       | 900004  | Tax Amount (sales)                    |
| en-US       | 900005  | Tax Basis (sales)                     |
| en-US       | 900006  | Transaction start date time           |
| en-US       | 900007  | Transaction end date time             |
| en-US       | 900008  | Serial number of the security element |
| en-US       | 900009  | Signature counter                     |
| en-US       | 900010  | Check value                           |
| en-US       | 900011  | Info message                          |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that the **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                            | Type    | Caption text ID |
|---------------------------------|---------|-----------------|
| QRCODE\_DE                      | Receipt | 900001          |
| TRANSACTIONID\_DE               | Receipt | 900002          |
| RETAILPRINTCODE\_DE             | Receipt | 900003          |
| SALESTAXAMOUNT\_DE              | Receipt | 900004          |
| SALESTAXBASIS\_DE               | Receipt | 900005          |
| TRANSACTIONSTARTDATETIME\_DE    | Receipt | 900006          |
| TRANSACTIONENDDATETIME\_DE      | Receipt | 900007          |
| SECURITYELEMENTSERIALNUMBER\_DE | Receipt | 900008          |
| SIGNCOUNTER\_DE                 | Receipt | 900009          |
| SIGN\_DE                        | Receipt | 900010          |
| INFOMESSAGE\_DE                 | Receipt | 900011          |

> [!NOTE]
> It's important that you specify correct custom field names, as listed in the preceding table. An incorrect custom field name will cause missing data in receipts.

### Configure receipt formats

For every receipt format that is required, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Header:** Add the following fields:

    - **Store name** and **Tax Identification Number** fields, which are used to print the company name and identification number on receipts. Alternatively, you can add the company name and identification number to the layout as free-form text.
    - **Store address**, **Date**, **Time 24H**, **Receipt Number**, and **Register number** fields.

- **Lines:** Add the following fields:

    - **Item name** field
    - **Qty** field
    - **Total price with tax** field
    - **Tax Retail Print Code** field, which is used to print the abbreviated code that corresponds to the sales tax code that applies to the item

- **Footer:** Add the following fields:

    - Payment fields, so that the payment amounts for each payment method are printed. For example, add the **Tender name** and **Tender amount** fields to one line of the layout.
    - Fields in the **Tax break down** field group. All the fields in this field group must be printed on one separate line.

        - **Tax Id** field, which is a standard field that enables a sales tax summary to be printed for each sales tax code. The field must be added to a new line.
        - **Tax Percentage** field, which is a standard field that is used to print the effective tax rate for the sales tax code.
        - **Tax Basis (sales)** field, which is used to print the receipt's total cash sale amount for the sales tax code. Prepayments and gift card operations are excluded.
        - **Tax Amount (sales)** field, which is used to print the receipt's tax amount for cash sales for the sales tax code.
        - **Tax Retail Print Code** field, which is used to print the abbreviated code that corresponds to the sales tax code.

    - Fields that contain secured transaction data that is returned by the fiscal registration service:

        - **Transaction ID** field, which identifies the number of the cash transaction in the fiscal registration service
        - **Transaction start date time** field
        - **Transaction end date time** field
        - **Serial number of the security element** field
        - **Signature counter** field
        - **Check value** field
        - **QR Code** field, which is used to print the reference to the registered cash transaction in the form of a QR code

        > [!NOTE]
        > The **QR Code** value is retrieved from the fiscal register response. EFR returns a QR code in its response only if the value of the **Attributes** field in the EFR configuration is described in the EFSTA documentation. The QR code format in the **Attributes** field in the EFR configuration must be set to **BMP**.

    - **Info message** field, so that notification messages from the fiscal registration service can be shown on receipts. For example, if a signature device is broken, special text can be printed on a receipt.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

## Set up fiscal integration for Germany

The fiscal registration service integration sample for Germany is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Commerce SDK. The sample is located in the **src\\FiscalIntegration\\Efr** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The [sample](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) consists of a fiscal document provider, which is an extension of the Commerce runtime (CRT), and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Commerce SDK, see [Download Commerce SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!NOTE]
> The fiscal registration service integration sample for Germany is available in the Commerce SDK as of Commerce version 10.0.29. In Commerce version 10.0.28 or earlier, you must use the previous version of the Retail SDK on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Deployment guidelines for the fiscal integration sample for Germany (legacy)](emea-deu-fi-sample-sdk.md).

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md):

1. [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Also, make a note of the settings for the fiscal registration process that are [specific to this fiscal registration service integration sample](#set-up-the-registration-process).
1. [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).

    > [!WARNING]
    > The error handling capabilities of the fiscal integration framework might not be fully aligned with local fiscal regulations.
    >
    > - We recommend that you leave the **Continue on error** option on the **Fiscal registration process** page turned off, because all transactions must be correctly registered, even if the first attempt at fiscal registration wasn't successful.
    > - Before you turn on the **Skip** or **Mark as registered** option on the **Fiscal registration process** page, you should discuss these changes to the fiscal registration process with your tax consultant or the local tax office.

1. [Enable manual execution of deferred fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-deferred-fiscal-registration).
1. [Configure channel components](#configure-channel-components).

### Set up the registration process

To enable the registration process, follow these steps to set up Commerce headquarters. For more information, see [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Download configuration files for the fiscal document provider and the fiscal connector:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    1. Select a correct release branch version according to your SDK/application version.
    1. Open **src \> FiscalIntegration \> Efr**.
    1. Download the fiscal document provider configuration file at **Configurations \> DocumentProviders \> DocumentProviderFiscalEFRSampleGermany.xml**.
    1. Download the fiscal connector configuration file at **Configurations \> Connectors \> ConnectorEFRSample.xml**.

    > [!NOTE]
    > In Commerce version 10.0.28 or earlier, you must use the previous version of the Retail SDK on a developer VM in LCS. The configuration files for this fiscal integration sample are located in the following folders of the Retail SDK on a developer VM in LCS:
    >
    > - **Fiscal document provider configuration file:** RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.EFRSample\\Configuration\\DocumentProviderFiscalEFRSampleGermany.xml
    > - **Fiscal connector configuration file:** RetailSdk\\SampleExtensions\\HardwareStation\\Extension.EFRSample\\Configuration\\ConnectorEFRSample.xml

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the fiscal document provider configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the fiscal connector configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile. Select the document provider and the connector that you loaded earlier. Update the [data mapping settings](#default-data-mapping) as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the fiscal connector that you loaded earlier. Update the [connector settings](#fiscal-connector-settings) as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group for the connector functional profile that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process and a fiscal registration process step, and select the fiscal connector group that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the fiscal registration service will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
1. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

#### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample:

- **Tender type mapping** – The mapping of payment methods to values of the **PayG** (payment group) attribute in requests that are sent to the fiscal service. Here is the default mapping:

    ```
    1: 0; 2: 1; 3: 3; 4: 8; 5: 2; 6: 0; 7: 7; 8: 6; 9: 0; 10: 8; 11: 1
    ```

    The first component in each pair represents a payment method that is set up for the store. The second component represents the corresponding payment group that is supported by the EFR fiscal registration service. For more information about payment groups that EFR supports for Germany, see the [EFR reference](https://public.efsta.net/efr/).

    The sample mapping of payment methods corresponds to store payment methods that are configured in the standard demo data.

    | Payment method | Payment method name |
    |----------------|---------------------|
    | 1              | Cash                |
    | 2              | Check               |
    | 3              | Card                |
    | 4              | Customer account    |
    | 5              | Other               |
    | 6              | Currency            |
    | 7              | Voucher             |
    | 8              | Gift card           |
    | 9              | Tender Remove/Float |
    | 10             | Loyalty Cards       |
    | 11             | Non-local checks    |

    Therefore, you must modify the sample mapping according to the payment methods that are configured in your application.

- **Include customer data** – If this parameter is turned on, requests to the fiscal service will contain customer information, such as names and addresses, in cases where a customer is added to a transaction.
- **Value-added tax (VAT) rates mapping** – The mapping of tax percentage values that are set up for the sales tax codes to values of the **TaxG** (tax group) attribute in requests that are sent to the fiscal service. Here is the default mapping:

    ```
    A: 19.00; B: 7.00; C: 10.70; D: 5.50; E: 0.00
    ```

    The first component in each pair represents a VAT tax group that is supported by the EFR fiscal registration service. The second component represents the corresponding VAT rate. For more information about VAT tax groups that EFR supports for Germany, see the [EFR reference](https://public.efsta.net/efr/).

- **Tax group for gift cards and deposits** – The value of the **TaxG** attribute in requests that are sent to the fiscal service, based on operations that involve gift cards or deposits. Here is the default mapping:

    ```
    G
    ```

- **Tax group for VAT exempt** – The value of the **TaxG** attribute in requests that are sent to the fiscal service, based on operations that are exempt from tax obligations. Here is the default mapping:

    ```
    F
    ```

> [!NOTE]
> Tax settings in the default data mapping are responsible for matching tax settings in the system and tax groups in the EFR service. Tax groups can be printed on receipts only if the **Code for printing** field is set on the **Sales tax codes** page.

#### Fiscal connector settings

The following settings are included in the fiscal connector configuration that is provided as part of the fiscal integration sample:

- **Endpoint address** – The URL of the fiscal registration service.
- **Timeout** – The amount of time, in milliseconds, that the fiscal connector will wait for a response from the fiscal registration service.
- **Show fiscal registration notifications** – This flag controls whether notifications that the fiscal registration service returns should be shown to the operator.

### Configure channel components

> [!NOTE]
> - The fiscal registration service integration sample for Germany is available in the Commerce SDK as of Commerce version 10.0.29. In Commerce version 10.0.28 or earlier, you must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the fiscal integration sample for Germany (legacy)](emea-deu-fi-sample-sdk.md).
> - Commerce samples that are deployed in your environment aren't automatically updated when you apply service or quality updates to Commerce components. You must manually update the required samples.

#### Set up the development environment

To set up a development environment to test and extend the sample, follow these steps.

1. Clone or download the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository. Select a correct release branch version according to your SDK/application version. For more information, see [Download Commerce SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md).
1. Open the EFR solution at **Dynamics365Commerce.Solutions\\FiscalIntegration\\Efr\\EFR.sln**, and build it.
1. Install Commerce runtime extensions:

    1. Find the CRT extension installer:

        - **Commerce Scale Unit:** In the **Efr\\ScaleUnit\\ScaleUnit.EFR.Installer\\bin\\Debug\\net461** folder, find the **ScaleUnit.EFR.Installer** installer.
        - **Local CRT on Modern POS:** In the **Efr\\ModernPOS\\ModernPOS.EFR.Installer\\bin\\Debug\\net461** folder, find the **ModernPOS.EFR.Installer** installer.

    1. Start the CRT extension installer from the command line:

        - **Commerce Scale Unit:**

            ```Console
            ScaleUnit.EFR.Installer.exe install --verbosity 0
            ```

        - **Local CRT on Modern POS:**

            ```Console
            ModernPOS.EFR.Installer.exe install --verbosity 0
            ```

1. Install fiscal connector extensions:

    You can install fiscal connector extensions on the [Hardware station](fiscal-integration-for-retail-channel.md#fiscal-registration-is-done-via-a-device-connected-to-the-hardware-station) or the [POS register](fiscal-integration-for-retail-channel.md#fiscal-registration-is-done-via-a-device-or-service-in-the-local-network).

    1. Install Hardware station extensions:

        1. In the **Efr\\HardwareStation\\HardwareStation.EFR.Installer\\bin\\Debug\\net461** folder, find the **HardwareStation.EFR.Installer** installer.
        1. Start the extension installer from the command line by running the following command.

            ```Console
            HardwareStation.EFR.Installer.exe install --verbosity 0
            ```

    1. Install POS extensions:

        1. Open the POS fiscal connector sample solution at **Dynamics365Commerce.Solutions\\FiscalIntegration\\PosFiscalConnectorSample\\Contoso.PosFiscalConnectorSample.sln**, and build it.
        1. In the **PosFiscalConnectorSample\\StoreCommerce.Installer\\bin\\Debug\\net461** folder, find the **Contoso.PosFiscalConnectorSample.StoreCommerce.Installer** installer.
        1. Start the extension installer from the command line by running the following command.

            ```Console
            Contoso.PosFiscalConnectorSample.StoreCommerce.Installer.exe install --verbosity 0
            ```

#### Production environment

Follow the steps in [Set up a build pipeline for a fiscal integration sample](fiscal-integration-sample-build-pipeline.md) to generate and release the Cloud Scale Unit and self-service deployable packages for the fiscal integration sample. The **EFR build-pipeline.yml** template YAML file can be found in the **Pipeline\\YAML_Files** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository.

## Design of extensions

The fiscal registration service integration sample for Germany is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Commerce SDK. The sample is located in the **src\\FiscalIntegration\\Efr** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The [sample](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) consists of a fiscal document provider, which is an extension of CRT, and a fiscal connector, which is an extension of Commerce Hardware Station. For more information about how to use the Commerce SDK, see [Download Commerce SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

> [!NOTE]
> The fiscal registration service integration sample for Germany is available in the Commerce SDK as of Commerce version 10.0.29. In Commerce version 10.0.28 or earlier, you must use the previous version of the Retail SDK on a developer VM in LCS. For more information, see [Deployment guidelines for the fiscal integration sample for Germany (legacy)](emea-deu-fi-sample-sdk.md).

### CRT extension design

The purpose of the extension that is a fiscal document provider is to generate service-specific documents and handle responses from the fiscal registration service.

#### Request handler

There is one request handler for the document provider, **DocumentProviderEFRFiscalDEU**. This handler is used to generate fiscal documents for the fiscal registration service. It's inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the connector document provider name that is specified in Commerce headquarters.

The connector supports the following requests:

- **GetFiscalDocumentDocumentProviderRequest** – This request contains information about what document should be generated. It returns a service-specific document that should be registered in the fiscal registration service.
- **GetFiscalTransactionExtendedDataDocumentProviderRequest** – This request returns the response together with extended data.

#### Configuration

The configuration file for the fiscal document provider is located at **src\\FiscalIntegration\\Efr\\Configurations\\DocumentProviders\\DocumentProviderFiscalEFRSampleGermany.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings of the fiscal document provider to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

### Hardware station extension design

The purpose of the extension that is a fiscal connector is to communicate with the fiscal registration service.

The Hardware station extension is **HardwareStation.Extension.EFRSample**. It uses the HTTP protocol to submit documents that the CRT extension generates to the fiscal registration service. It also handles the responses that are received from the fiscal registration service.

#### Request handler

The **EFRHandler** request handler is the entry point for handling requests to the fiscal registration service. This handler is inherited from the **INamedRequestHandler** interface. The **HandlerName** method is responsible for returning the name of the handler. The handler name should match the fiscal connector name that is specified in Commerce headquarters.

The connector supports the following requests:

- **SubmitDocumentFiscalDeviceRequest** – This request sends documents to the fiscal registration service and returns a response from it.
- **IsReadyFiscalDeviceRequest** – This request is used for a health check of the fiscal registration service.
- **InitializeFiscalDeviceRequest** – This request is used to initialize the fiscal registration service.

#### Configuration

The configuration file for the fiscal connector is located at **src\\FiscalIntegration\\Efr\\Configurations\\Connectors\\ConnectorEFRSample.xml** in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings of the fiscal connector to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration.

### POS fiscal connector extension design

The purpose of the POS fiscal connector extension is to communicate with the fiscal registration service from POS. It uses the HTTPS protocol for communication.

#### Fiscal connector factory

The fiscal connector factory maps the connector name to the fiscal connector implementation and is located in the **Pos.Extension\\Connectors\\FiscalConnectorFactory.ts** file. The connector name should match the fiscal connector name that is specified in Commerce headquarters.

#### EFR fiscal connector

The EFR fiscal connector is located in the **Pos.Extension\\Connectors\\Efr\\EfrFiscalConnector.ts** file. It implements the **IFiscalConnector** interface that supports the following requests:

- **FiscalRegisterSubmitDocumentClientRequest** – This request sends documents to the fiscal registration service and returns a response from it.
- **FiscalRegisterIsReadyClientRequest** – This request is used for a health check of the fiscal registration service.
- **FiscalRegisterInitializeClientRequest** – This request is used to initialize the fiscal registration service.

#### Configuration

The configuration file is located in the **src\\FiscalIntegration\\Efr\\Configurations\\Connectors** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The purpose of the file is to enable settings for the fiscal connector to be configured from Commerce headquarters. The file format is aligned with the requirements for fiscal integration configuration. The following settings are added:

- **Endpoint address** – The URL of the fiscal registration service.
- **Timeout** – The amount of time, in milliseconds, that the connector will wait for a response from the fiscal registration service.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
