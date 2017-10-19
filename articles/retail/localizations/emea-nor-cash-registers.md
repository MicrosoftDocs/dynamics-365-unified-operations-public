---
# required metadata

title: Cash registers for Norway
description: This topic provides an overview of the cash register functionality that is available for Norway. 
author: EvgenyPopovMBS
manager: vastrup
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailPosPermissionGroup, RetailFunctionalityProfile, RetailFormLayout, RetailHardwareProfile, RetailFiscalPrinterConfigTable
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Retail, Operations, Core, UnifiedOperations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Norway
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Application update 4
---
# Cash registers for Norway

This topic provides an overview of the cash register functionality that is available for Norway in Microsoft Dynamics 365 for Retail. It also provides guidelines for setting up the functionality. The functionality consists of the following parts:

- Common point-of-sale (POS) features that are made available to customers in all countries or regions, such as an option to prevent printing a copy of a receipt more than one time

- Norway-specific features, such as digital signature for sales transactions

## Overview of cash register functionality for Norway

### Common POS features

To learn about common POS features that are available to customers in all countries or regions, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

The following POS localization features implemented previously and available to customers in all countries or regions may be used for Norway specifically:

- **Print text fields on a receipt in a large font size.** You can use the **Font size** parameter in the Receipt format designer to specify that the large font size should be used for a field in the receipt format. (The large font size is approximately double the usual font size.) For example, you can use this parameter to print the "Copy" indicator on a receipt copy in large characters.

- **Register the printing of receipt copies in the POS audit event log.** You can use the **Audit** parameter in the POS functionality profile to enable the printing of receipt copies and other POS audit events to be registered. The audit events are registered in the channel database and in Retail Headquarters. You can view the audit events on the **Audit events** page.

- **Prevent a copy of a receipt from being printed more than one time.** When the parameter **Audit** in the POS functionality profile is enabled, the **Allow printing receipt copies** POS permission controls whether receipt copies can be printed. There is also an option to prevent a copy of a receipt from being printed more than one time. 

Additionally, the following POS feature that was implemented for Norway has been made available to customers in all countries or regions:

- **Register additional events in the POS audit event log.** If the **Audit** parameter is enabled in the POS functionality profile, the following events are registered in the POS audit event log:

  - Price checks

  - Tax overrides

  - Line quantity corrections

  - Clearing transactions from the channel database

### Norway-specific POS features

The following Norway-specific POS features are enabled when the **ISO code** parameter in the POS functionality profile is set to **NO**.

#### Digitally signing sales transactions

Each sales transaction is digitally signed. The signature is created and recorded in the POS transaction journal in parallel with finalizing the transaction, and is further available in the journal exported for audit purposes.

Only cash sales transactions are signed. Excluded from the signing process are, for example:

- Prepayments (customer account deposit)

- Prepayments for sales orders (customer order deposit)

- Issuing a gift card

- Non-sale transactions (float entry, tender removal, etc.)

The data being signed is a text string consisting of the following data fields separated by semicolons:

- Previous signature for the same POS (“0” for the first transaction)

- Transaction date

- Transaction time

- Sequential signed transaction number

- Transaction amount including tax

- Transaction amount excluding tax

The digitally signing process uses an RSA 1024 bit key with a SHA-1 hash function (RSA-SHA1-1024). A certificate installed on the Retail Server is used for signing. The unique identifier of the certificate (footprint) is recorded together with the signature.

The signature is stored in the Store DB and HQ DB together with the transaction data. You can view the transaction signature, together with the transaction data used to generate the signature, on the **Retail store transactions** page, the fast tab **Fiscal transactions**. 

#### Receipts

Receipts for Norway may include additional information that was implemented using custom fields.

- **Receipt title**. It is possible to add a field to a receipt format layout that identifies the type of receipt. For example, a sales receipt will include the text "Sales receipt". 

- **Signed transaction sequential number**. The signed transaction sequential number may be listed on the receipt in order to associate a printed receipt with a digital signature in the database.

- **Receipt totals**. Custom receipt total fields exclude non-sales amounts from total transaction amounts. Non-sales amounts include:

  - Prepayments (customer account deposit)

  - Prepayments for sales orders (customer order deposit)

  - Issuing a gift card
  
  - Adding funds to a gift card

#### X and Z reports

X and Z reports include information according to Norwegian requirements. For example, total cash sales amounts include only cash sales transaction amount and exclude issue gift card operations, as well as prepayments; total cash sales are also listed per item group and per payment method. In addition, cumulative Grand total sales and Grand total return amounts are maintained and printed.

#### SAF-T Cash Register audit file

You can export the POS transaction journal in the predefined SAF-T (Standard Audit File - Tax) Cash Register format. The audit file includes information about the organizaton, relevant master data (such as item groups and items, tax codes, etc.), cash sales transaction data with their signatures, non-sales event data, and end-of-date report date.

The audit file can be exported for the following scenarios:

- Per company
- Per store
- All stores
- Per terminal
- All terminals

The SAF-T Cash Register format is implemented at Retail Headquarters using [Electronic reporting](../../dev-itpro/analytics/general-electronic-reporting.md). 

## Setting up Retail for Norway

This section describes the Retail settings that are specific to and recommended for Norway. For more information about how to set up Retail, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

To use the Norway-specific functionality for Retail, you must complete these tasks:

- Set the **Country/region** field to **NOR** (Norway) in the primary address of the legal entity.

- Set the **ISO code** field to **NO** (Norway) in the POS functionality profile of every store that is located in Norway.

You must specify the following settings for Norway.

### Set up legal entity

Make sure the legal entity name is specified. It will be printed in X and Z reports;
  
Specify the organization number in the **Routing number** field on the **Bank account information** fast tab.
  
### Set up value-added tax (VAT) per Norwegian requirements

You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and in Retail, see [Sales tax overview](../../financials/general-ledger/indirect-taxes-overview.md). You also need to specify sales tax groups and enable the **Prices include sales tax** option for stores located in Norway

### Set up functionality profiles

You must enable auditing and set up receipt numbering.

### Update POS permissions groups and individual permission settings for store workers

Set the **Allow printing receipt copy** permission to an appropriate value:

-  **Allow always** – The operator can print a copy of a receipt multiple times;
    
- **Allow only once** – The operator can print a copy of a receipt only one time;
    
- **Allow only once, and only if HQ DB is available** – The operator can print a copy of a receipt only one time, and only if the headquarters database is available through Real-Time service, so that the system can verify that no copies of the receipt have previously been printed in any store;
    
- **Never** – The operator can't print a copy of a receipt.
    
### Configure custom fields to be used in receipt formats for sales receipts

Make the following steps to configure custom fields:

1. On the **Language text** page, add the following records for the captions of the custom receipt layout fields. Note that the Language ID, Text ID and Text fields are provided for example, and can be changed according to your requirements.

|Language ID|Text|Text ID|
|-------|----------------------------------------|--------|
|en-US|Receipt title|**900011**|
|en-US|Is gift card|**900012**|
|en-US|Total (sales)|**900013**|
|en-US|Tax total (sales)|**900014**|
|en-US|Total with tax (sales)|**900015**|
|en-US|Tax amount (sales)|**900016**|
|en-US|Cash transaction ID|**900017**|

2. On the **Custom fields** page, add the following records for the custom receipt layout fields. Note that Caption text IDs must correspond to the Text IDs specified on the previous step:

|Name|Type|Caption text ID|
|-----------------|----------|--------|
|**ReceiptTitle**|Receipt|**900011**|
|**IsGiftCard**|Receipt|**900012**|
|**SalesTotalExt**|Receipt|**900013**|
|**TaxTotalExt**|Receipt|**900014**|
|**TotalWithTaxExt**|Receipt|**900015**|
|**AmountPerTaxExt**|Receipt|**900016**|
|**CashTransactionSequentialNumber**|Receipt|**900017**|
            
### Configure receipt formats

For all required receipt formats, change the value of the **Print behavior** field to **Always print** for the receipt format.

In the Receipt format designer, add the following custom fields to appropriate receipt sections (note that field names correspond to the language texts defined in the previous section):

1. Header:

    - **Receipt title**. This field identifies the type of receipt

    - **Cash transaction ID**. This field prints the sequential number of the signed cash transaction.

2. Lines

    - **Is gift card**. This field marks the receipt line as related to the Issue gift card or the Add to gift card operations.

3. Footer:

    - **Total (sales)**. This field prints the receipt's total cash sale amount excluding tax and excluding prepayments and gift card operations.

    - **Tax total (sales)**. This field prints the receipt's total tax amount for cash sale, excluding prepayments and gift card operations. 

    - **Total with tax (sales)**. This field prints the receipt's total cash sale amount including tax and  excluding prepayments and gift card operations.

    - **Tax amount (sales)**. This field prints the receipt's tax amount for cash sales, excluding prepayments and gift card operations, per tax code. 

See [Receipt templates and printing](../receipt-templates-printing.md) for more information on working with receipt formats.

### Configure SAF-T Cash Register export format

Set up...

The format configuration is available to download from Lifecycle Services. For more information, see [Import electronic reporting configurations](../../dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

### Configure Retail channel components

You must configure Retail channel component extensions to enable Norway-specific functionalty. For more information, see the [deployment guidelines](./emea-nor-loc-deployment-guidelines.md)
