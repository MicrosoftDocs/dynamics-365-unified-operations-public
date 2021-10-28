---

# required metadata

title: Fiscal registration service integration sample for Austria
description: This topic provides an overview of the fiscal integration sample for Austria.
author: josaw
ms.date: 10/28/2021
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
ms.search.region: Austria
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-3-1
ms.dyn365.ops.version: 10.0.1

---
# Fiscal registration service integration sample for Austria

[!include[banner](../includes/banner.md)]

## Introduction

To meet local fiscal requirements for cash registers in Austria, the Dynamics 365 Retail functionality for Austria includes a sample integration of the point of sale (POS) with an external fiscal registration service. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It's based on the [EFR (Electronic Fiscal Register)](https://www.efsta.eu/at/fiskalloesungen/oesterreich) solution from [EFSTA](https://www.efsta.eu/at/) and enables communication with the EFR service via the HTTPS protocol. The EFR service should be hosted on either the Retail Hardware station or a separate machine that can be connected to from the Hardware station. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

Microsoft doesn't release any hardware, software, or documentation from EFSTA. For information about how to get the EFR solution and operate it, contact [EFSTA](https://www.efsta.eu/at/kontakt).


## Scenarios

The following scenarios are covered by the fiscal registration service integration sample for Austria:

- Registration of cash transactions in the fiscal registration service:

    - Send detailed transaction data to the fiscal registration service. This data includes sales line information, and information about discounts, payments, and taxes.
    - Capture a response from the fiscal registration service. This response includes a digital signature and a link to the registered transaction.
    - Register taxes, and map them to the fiscal registration service's tax codes.
    - Print the QR code for a registered transaction on the receipt.

- Registration of gift card operations and customer deposits as non-cash transactions in the fiscal registration service:

    - Issue or add money to a gift card.
    - Register a customer account deposit.
    - Register a customer order deposit.

- Registration of non-sales transactions and events as non-cash transactions in the fiscal registration service:

    - Open shift and Close shift
    - Start amount, Float entry, and Tender removal
    - Price override
    - Tax override
    - Print copy of receipt
    - Open drawer
    - Print X report
    - Print Z report

- Printing end-of-day statements (X/Z reports) that have Austria-specific fields:

    - Total number of products or services that were delivered to customers
    - Breakdown of sales by tax rate
    - Breakdown of payments by cashier/cash register operator
    - Price discounts and returns that reduce daily sales
    - Zero sales (giveaways)

- Error handling, such as the following options:

    - Retry fiscal registration if a retry is possible, such as if the fiscal registration service isn't available, isn't ready, or isn't responding.
    - Postpone fiscal registration.
    - Skip fiscal registration, or mark the transaction as registered, and include info codes to capture the reason for the failure and additional information.
    - Check the availability of the fiscal registration service before a new sales transaction is opened or a sales transaction is finalized.

### Default data mapping

The following default data mapping is included in the fiscal document provider configuration that is provided as part of the fiscal integration sample:

- Value-added tax (VAT) rates mapping:

    *A: 20.00; B: 10.00; C: 13.00; D: 0.00; E: 19.00; F: 7.00*

### Gift cards

The fiscal registration service integration sample implements the following rules that are related to gift cards:

- Exclude sales lines that are related to the *Issue gift card* and *Add to gift card* operations from a cash transaction. Instead of registering those lines as a part of a cash transaction, register them as a separate non-cash transaction in the fiscal registration service.
- Don't print a tax group breakdown and a QR code on a receipt if the receipt consists only of gift card lines.
- Print the total amount of gift cards that are issued or re-charged in a transaction separately from the cash transaction amount on the receipt.
- Save calculated adjustments of payment lines in the channel database with a reference to a corresponding fiscal transaction.
- Payment by gift card is considered a regular payment.

### Customer deposits and customer order deposits

The fiscal registration service integration sample implements the following rules that are related to customer deposits and customer order deposits:

- Register a non-cash transaction if a transaction is a customer deposit.
- Register a non-cash transaction if a transaction contains only a customer order deposit or a customer order deposit refund.
- Deduct the customer order deposit amount from payment lines when a hybrid customer order is created.
- Save calculated adjustments of payment lines in the channel database with a reference to a fiscal transaction for a hybrid customer order.

### Limitations of the sample

The fiscal registration service supports only scenarios where sales tax is included in the price. Therefore, the **Price include sales tax** option must be set to **Yes** for both stores and customers.

## Set up Commerce for Austria

This section describes the Commerce settings that are specific to and recommended for Austria. For more information set up information, see [Commerce home page](../index.md).

To use the Austria-specific functionality, you must specify the following settings:

- In the primary address of the legal entity, set the **Country/region** field to **AUT** (Austria).
- In the POS functionality profile of every store that is located in Austria, set the **ISO code** field to **AT** (Austria).

You must also specify the following settings for Austria. Note that you must run appropriate distribution jobs after you complete the setup.

### Set up VAT per Austrian requirements


You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax features, see [Sales tax overview](../../finance/general-ledger/indirect-taxes-overview.md).


On sales receipts, you can print an abbreviated code for a sales tax code (for example, "A" or "B"). To make this functionality available, set the **Print code** field on the **Sales tax codes** page.

### Set up stores

On the **All stores** page, update the store details. Specifically, set the following parameters:

- In the **Sales tax group** field, specify the sales tax group that should be used for sales to the default customer.
- Set the **Prices include sales tax** option to **Yes**.
- Set the **Name** field to the company name. This change helps guarantee that the company name appears on a sales receipt. Alternatively, you can add the company name to the sales receipt layout as free-form text.
- Set the **Tax identification number (TIN)** field to the company identification number. This change helps guarantee that the company identification number appears on a sales receipt. Alternatively, you can add the company identification number to the sales receipt layout as free-form text.

### Set up functionality profiles

Set up POS functionality profiles:

- On the **Receipt numbering** FastTab, set up receipt numbering by creating or updating records for the **Sale**, **Sales order**, and **Return** receipt transaction types.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

Add the following POS labels to the **POS** section of **Language text** from the table:

| Language ID | Text ID | Text                      |
|-------------|---------|---------------------------|
| en-US       | 900001  | QR Code                   |
| en-US       | 900002  | Continuous Number         |
| en-US       | 900003  | Tax Retail Print Code     |
| en-US       | 900004  | Total (sales)             |
| en-US       | 900005  | Total Tax (sales)         |
| en-US       | 900006  | Total Include Tax (sales) |
| en-US       | 900007  | Tax Amount (sales)        |
| en-US       | 900008  | Tax Basis (sales)         |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page:

| Name                 | Type    | Caption text ID |
|----------------------|---------|-----------------|
| QRCODE               | Receipt | 900001          |
| CONTINUOUSNUMBER     | Receipt | 900002          |
| RETAILPRINTCODE      | Receipt | 900003          |
| SALESTOTAL           | Receipt | 900004          |
| SALESTOTALTAX        | Receipt | 900005          |
| SALESTOTALINCLUDETAX | Receipt | 900006          |
| SALESTAXAMOUNT       | Receipt | 900007          |
| SALESTAXBASIS        | Receipt | 900008          |

### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Header:** Add the following fields:

    - **Store name** and **Tax Identification Number** fields, which are used to print the company name and identity number on receipts. Alternatively, you can add the company name and identity number to the layout as free-form text.
    - **Store address**, **Date**, **Time 24H**, **Receipt Number**, and **Register number** fields.
    - **Continuous Number** fields, to identify the number of the cash transaction in the fiscal registration service.

- **Lines:** Add the following fields:

    - **Item name**.
    - **Qty**.
    - **Total price with tax**.
    - **Tax Retail Print Code**, which is used to print the abbreviated code that corresponds to the sales tax code that applies to the item.

- **Footer:** Add the following fields:

    - Payment fields, so that the payment amounts for each payment method are printed. For example, add the **Tender name** and **Tender amount** fields to one line of the layout.
    - **Sales total** field group:

        - **Total (sales)** field, which is used to print the receipt's total cash sale amount. The amount excludes tax. Prepayments and gift card operations are excluded.
        - **Total Include Tax (sales)** field, which is used to print the receipt's total cash sale amount. The amount includes tax. Prepayments and gift card operations are excluded.
        - **Total Tax (sales)** field, which is used to print the receipt's total tax amount for cash sales. Prepayments and gift card operations are excluded.

    - **Tax break down** field group. The fields in this field group must be printed on a separate line.

        - **Tax Id** field, which is a standard field that enables a sales tax summary to be printed for each sales tax code. The field must be added to a new line.
        - **Tax Percentage** field, which is a standard field that is used to print the effective tax rate for the sales tax code.
        - **Tax Basis (sales)** field, which is used to print the receipt's total cash sale amount for the sales tax code. Prepayments and gift card operations are excluded.
        - **Tax Amount (sales)** field, which is used to print the receipt's tax amount for cash sales for the sales tax code.
        - **Tax Retail Print Code** field, which is used to print the abbreviated code that corresponds to the sales tax code.

    - **QR Code** field, which is used to print the reference to the registered cash transaction in the form of QR code.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Set up fiscal integration

Because of the introduction of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), the fiscal integration setup steps differ depending on the version of the Retail SDK that is used:

- For the version 10.0.21 and before, you must use the Retail SDK on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS).
- For the version 10.0.22 and later, you must use [sealed Commerce self-service components](../dev-itpro/enhanced-mass-deployment.md) and the fiscal integration sample published in the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) GitHub repository.

For more information, see [Retail SDK architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md).

> [!WARNING]
> Because of limitations of the new independent packaging and extension model, it can't currently be used for this fiscal integration sample. You must use the previous version of the Retail SDK on a developer VM in LCS. Supporting the new independent packaging and extension model for fiscal integration samples is planned for later versions.

Complete the fiscal integration setup steps as described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md):

1. [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Note also the settings for the fiscal registration process that are [specific to this fiscal registration service integration sample](#set-up-the-registration-process).
1. [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Enable manual execution of postponed fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).
1. [Configure channel components](#configure-channel-components)

#### Set up the registration process

To enable the registration process, follow these steps to set up Headquarters. For more details, see [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Download configuration files for the fiscal document provider and the fiscal connector:

    1. For the Retail SDK on a developer VM in LCS:
        1. Open **RetailSdk\\SampleExtensions\\CommerceRuntime\\Extensions.DocumentProvider.EFRSample\\Configuration** and download the fiscal document provider configuration files: **DocumentProviderEFRSampleAustria.xml** and **DocumentProviderNonFiscalEFRSampleAustria.xml**.
        1. Download the fiscal connector configuration file at **RetailSdk\\SampleExtensions\\HardwareStation\\Extension.EFRSample\\Configuration\\ConnectorEFRSample.xml**.
    1. For the fiscal integration sample published in the GitHub repository:
        1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
        1. Open the last available release branch (for example, **[release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33)**).
        1. Open **src \> FiscalIntegration \> Efr**.
        1. Open **Configurations \> DocumentProviders** and download the fiscal document provider configuration files: **DocumentProviderFiscalEFRSampleAustria.xml** and **DocumentProviderNonFiscalEFRSampleAustria.xml** (for example, [the location of the files for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.33/src/FiscalIntegration/Efr/Configurations/DocumentProviders)).
        1. Download the fiscal connector configuration file at **Configurations \> Connectors \> ConnectorEFRSample.xml** (for example, [the file for release/9.33](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.33/src/FiscalIntegration/Efr/Configurations/Connectors/ConnectorEFRSample.xml)).
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the fiscal document provider configuration files that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the fiscal connector configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create two new connector functional profiles, one for each document provider that you loaded earlier, and select the connector that you loaded earlier. Update the data mapping settings as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Update the connection settings as required.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create two new fiscal connector groups, one for each connector functional profile that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, two fiscal registration process steps, and select the fiscal connector groups that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier. To enable registration of non-fiscal events on the POS, on the **Functions** FastTab, under **POS**, set the **Audit** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**. Select a hardware profile that is linked to the Hardware station that the fiscal printer will be connected to. On the **Fiscal peripherals** FastTab, select the connector technical profile that you created earlier.
1. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

#### Configure channel components

The channel component configuration steps differ depending on the version of the Retail SDK that is used:

- For the Retail SDK on a developer VM in LCS, see [deployment guidelines for the sample from the Retail SDK](emea-aut-fi-sample-sdk.md).
- For the fiscal integration sample published in the GitHub repository, see [deployment guidelines for sample from GitHub](emea-aut-fi-sample-guthub.md).
 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
