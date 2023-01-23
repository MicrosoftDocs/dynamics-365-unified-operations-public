---
title: Cash register functionality for Norway
description: This article provides an overview of the cash register functionality that is available for Norway in Microsoft Dynamics 365 Commerce, and provides guidelines for setting up the functionality.
author: EvgenyPopovMBS
ms.date: 01/03/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-10-31
---
# Cash register functionality for Norway

[!include[banner](../includes/banner.md)]

This article provides an overview of the cash register functionality that is available for Norway in Dynamics 365 Commerce. It also provides guidelines for setting up the functionality. The functionality consists of the following parts:

- Common point-of-sale (POS) features that are available to customers in all countries or regions. Examples include an option that lets you prevent a copy of a receipt from being printed more than one time.
- Norway-specific features, such as digital signatures for sales transactions.

## Overview of cash register functionality for Norway

### Common POS features

To learn about POS features that are available to customers in all countries or regions, see [Help resources for Dynamics 365 Retail](../index.md).

The following POS localization features that were previously implemented and made available to customers in all countries or regions can now be used specifically for Norway:

- **Print text fields on a receipt in a large font size.** You can use the **Font size** parameter in the Receipt format designer to specify that the large font size should be used for a field in the receipt format. (The large font size is approximately double the usual font size.) For example, you can use this parameter to print the "Copy" indicator on a copy of a receipt in large characters.
- **Register the printing of receipt copies in the POS audit event log.** You can use the **Audit** parameter in the POS functionality profile to enable copies of receipts to be printed and other POS audit events to be registered. The audit events are registered in the channel database and in Headquarters. You can view the audit events on the **Audit events** page.
- **Prevent a copy of a receipt from being printed more than one time.** When the **Audit** parameter in the POS functionality profile is enabled, the **Allow printing receipt copies** POS permission controls whether copies of receipts can be printed. There is also an option that lets you prevent a copy of a receipt from being printed more than one time.

Additionally, the following POS feature was implemented for Norway but made available to customers in all countries or regions:

- **Register additional events in the POS audit event log.** If the **Audit** parameter in the POS functionality profile is enabled, the following events are registered in the POS audit event log:

    - Price checks
    - Tax overrides
    - Corrections to line quantities
    - Clearing transactions from the channel database

### Norway-specific POS features

The following Norway-specific POS features are enabled when the **ISO code** parameter in the POS functionality profile is set to **No**.

#### Digital signing of sales transactions

Every sales transaction is digitally signed. The signature is created and recorded in the POS transaction journal at the same time that the transaction is finalized. The signature is also available in the journal that is exported for audit purposes.

Only transactions for cash sales are signed. Here are some examples of transactions that are excluded from the signing process:

- Prepayments (customer account deposit)
- Prepayments for sales orders (customer order deposit)
- Issuing a gift card
- Non-sales transactions (float entry, tender removal, and so on)

The data that is signed is a text string that consists of the following data fields. The data fields are separated by semicolons.

1. Previous signature for the same POS (A zero \[**0**\] is used for the first transaction.)
2. Transaction date
3. Transaction time
4. Sequential signed transaction number
5. Transaction amount including tax
6. Transaction amount excluding tax

The digital signing process uses an RSA 1024-bit key that has a SHA-1 hash function (RSA-SHA1-1024). A certificate that is installed on Commerce Scale Unit is used for signing. The unique identifier of the certificate (footprint) is recorded together with the signature.

The signature is stored in the store database and the headquarters (HQ) database together with the transaction data. You can view the transaction signature, together with the transaction data that was used to generate it, on the **Fiscal transactions** FastTab of the **Store transactions** page.

#### Receipts

Receipts for Norway can include additional information that was implemented by using custom fields:

- **Receipt title** – You can add a field to a receipt format layout to identify the type of receipt. For example, a sales receipt will include the text "Sales receipt".
- **Signed transaction sequential number** – The sequential number of a signed transaction can appear on the receipt to associate a printed receipt with a digital signature in the database.
- **Receipt totals** – Custom fields for receipt totals exclude non-sales amounts from total transaction amounts. Non-sales amounts include amounts for the following operations:

    - Prepayments (customer account deposit)
    - Prepayments for sales orders (customer order deposit)
    - Issuing a gift card
    - Adding funds to a gift card

#### X and Z reports

The information that is included on X and Z reports is based on Norwegian requirements. For example, **Total cash sales** amounts include only amounts for cash sales transactions and exclude issue gift card operations and prepayments. Total cash sales are also listed per item group and payment method. In addition, cumulative **Grand total sales** and **Grand total returns** amounts are maintained and printed.

#### SAF-T Cash Register audit file

You can export the POS transaction journal in the predefined Standard Audit File - Tax (SAF-T) Cash Register format. The audit file includes information about the organization, relevant master data (such as item groups, items, and tax codes), cash sales transaction data together with signatures for those transactions, non-sales event data, and end-of-date report data.

The audit file can be exported for the following scenarios:

- Per store
- All stores
- Per terminal
- All terminals

You can also send a report from one legal entity on behalf of another legal entity. In this case, you must run the export from the operating legal entity and specify the reporting legal entity as the sender of the report.

The SAF-T Cash Register format is implemented at Headquarters by using [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md). 

## Setting up Commerce for Norway

This section describes the settings that are specific to and recommended for Norway. For more information, see [Help resources for Dynamics 365 Retail](../index.md).

To use the Norway-specific functionality, you must complete these tasks:

- Set the **Country/region** field to **NOR** (Norway) in the primary address of the legal entity.
- Set the **ISO code** field to **NO** (Norway) in the POS functionality profile of every store that is located in Norway.

You must also specify the following settings for Norway.

### Enable features for Norway

You must enable the following features in the **Feature management** workspace of Commerce headquarters:

- (Norway) Enable additional audit events in POS
- (Norway) Enable additional information in end-of-day statements in POS

### Set up the legal entity

Make sure that the name of the legal entity is specified. This name will be printed on X and Z reports.

Additionally, on the **Bank account information** FastTab, in the **Routing number** field, specify the organization number.

### Set up value-added tax (VAT) per Norwegian requirements


You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax, see [Sales tax overview](../../finance/general-ledger/indirect-taxes-overview.md).

You must also specify sales tax groups and enable the **Prices include sales tax** option for stores that are located in Norway.

### Set up functionality profiles

You must enable auditing and set up receipt numbering.

### Update POS permissions groups and individual permission settings for store workers

Set the **Allow printing receipt copy** permission to an appropriate value:

- **Allow always** – The operator can print a copy of a receipt multiple times.
- **Allow only once** – The operator can print a copy of a receipt only one time.
- **Allow only once, and only if HQ DB is available** – The operator can print a copy of a receipt only one time, and only if the HQ database is available through Commerce Data Exchange: Real-time Service, so that the system can verify that no copies of the receipt have previously been printed in any store.
- **Never** – The operator can't print a copy of a receipt.

### Configure custom fields so that they can be used in receipt formats for sales receipts

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet your requirements.

| Language ID | Text                   | Text ID |
|-------------|------------------------|---------|
| en-US       | Receipt title          | 900011  |
| en-US       | Is gift card           | 900012  |
| en-US       | Total (sales)          | 900013  |
| en-US       | Tax total (sales)      | 900014  |
| en-US       | Total with tax (sales) | 900015  |
| en-US       | Tax amount (sales)     | 900016  |
| en-US       | Cash transaction ID    | 900017  |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                               | Type    | Caption text ID |
|------------------------------------|---------|-----------------|
| ReceiptTitle_NO                    | Receipt | 900011          |
| IsGiftCard_NO                      | Receipt | 900012          |
| SalesTotalExt_NO                   | Receipt | 900013          |
| TaxTotalExt_NO                     | Receipt | 900014          |
| TotalWithTaxExt_NO                 | Receipt | 900015          |
| AmountPerTaxExt_NO                 | Receipt | 900016          |
| CashTransactionSequentialNumber_NO | Receipt | 900017          |

> [!NOTE]
> It's important that you specify correct custom field names, as listed in the above table. An incorrect custom field name will cause missing data in receipts.

### Configure receipt formats

For all required receipt formats, change the value of the **Print behavior** field to **Always print** for the receipt format.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

1. Header:

    - **Receipt title** – This field identifies the type of receipt.
    - **Cash transaction ID** – This field prints the sequential number of the signed cash transaction.

2. Lines:

    - **Is gift card** – This field marks the receipt line as related to the Issue gift card or Add to gift card operation.

3. Footer:

    - **Total (sales)** – This field prints the receipt's total cash sale amount. The amount excludes tax. Prepayments and gift card operations are excluded.
    - **Tax total (sales)** – This field prints the receipt's total tax amount for cash sales. Prepayments and gift card operations are excluded.
    - **Total with tax (sales)** – This field prints the receipt's total cash sale amount. The amount includes tax. Prepayments and gift card operations are excluded.
    - **Tax amount (sales)** – This field prints the receipt's tax amount for cash sales per tax code. Prepayments and gift card operations are excluded.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

### Configure the SAF-T Cash Register export format

The SAF-T Cash Register configuration is available for download from Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Import electronic reporting configurations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md). You must download the following configurations:

- **Retail channel data.version.1** – The data model configuration.
- **DMM Retail channel data.version.1.14** – The data model mapping configuration.
- **NO SAF T Cash Register.version.1.20** – The format configuration.

After you import the configurations, on the **Commerce parameters** page, on the **Electronic documents** tab, in the **SAF-T Cash register export format** field, select the name of the format configuration that was imported.

You must also map required master data to predefined SAF-T standard codes. For more information, see the SAF-T Cash register documentation that is provided by the Norwegian Tax Administration. To create the mapping, you must set the new **SAF-T Cash register code** field on the following pages:

- Item groups
- Payment methods
- Sales tax codes

### Configure channel components

To enable the Norway-specific functionality, you must configure channel components. For more information, see the [deployment guidelines](emea-nor-fi-deployment.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
