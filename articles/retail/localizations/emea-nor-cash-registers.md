---
# required metadata

title: Cash registers for Norway
description: This topic provides an overview of the cash register functionality that is available for Norway. 
author: EvgenyPopovMBS
manager: vastrup
ms.date: 10/17/2017
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

- **Print text fields on the receipt in a large font size.** You can use the **Font size** parameter in the Receipt format designer to specify that the large font size should be used for a field in a receipt format. (The large font size is approximately double the usual font size.) For example, you can use this parameter to print the "Copy" indicator on a receipt copy in large characters.

- **Register the printing of receipt copies in the POS audit event log.** You can use the **Audit** parameter in the POS functionality profile to enable the printing of receipt copies and other POS audit events to be registered. The audit events are registered in the channel database and in Retail headquarters. You can view the audit events on the **Audit events** page.

- **Prevent a copy of a receipt from being printed more than one time.** When the parameter **Audit** in the POS functionality profile is enabled, the **Allow printing receipt copies** POS permission controls whether receipt copies can be printed. There is also an option to prevent a copy of a receipt from being printed more than one time. 

Additionally, the following POS feature that was implemented for Norway has been made available to customers in all countries or regions:

- **Register additional events in the POS audit event log.** If the **Audit** parameter is enabled in the POS functionality profile, the following events are registered in the POS audit event log:

  - Price checks

  - Tax overrides

  - Line quantity corrections

  - Clearing the transactions from the channel database

### Norway-specific POS features

The following Norway-specific POS features are enabled when the **ISO code** parameter in the POS functionality profile is set to **NO**.

#### Digitally signing sales data

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

The signature is stored in the Store DB and HQ DB together with the transaction data

#### Receipts
Receipts for Norway may include additional information that was implemented using custom fields.

- **Receipt titles**. It is possible to add a field to a receipt format layout that identifies the type of receipt. For example, a sales receipt will include the text "Sales receipt". 

- **Signed transaction sequential number**
The signed transaction sequential number is listed on the receipt in order to associate a printed receipt with a digital signature in the database.

#### Receipt totals
The receipt totals section exclude non-sales transactions. Non-sales transactions include:
- Issuing a gift card
- Adding funds to a gift card
- Deposits
- Prepayments

### POS Transaction journal
The following events are registered in the POS transaction journal/POS Fiscal event log: 


### X and Z reports
X and Z reports include more information than the core retail documents. For example, the name and organization number of the enterprise as well as the number of price look-ups specified by product group and amount are both included in the reports.

### SAF-T Cash register audit file
You can export the POS transaction journal in the predefined SAF-T (Standard Audit File - Tax) Cash register format. This audit file can be exported for the following scenarios:
- Per company
- Per store
- All stores
- Per terminal
- All terminals

The SAF-T cash register format must be implemented at Retail HQ using Electronic reporting. The format configuration is available to download from Lifecycle Services. For more information, see [Import electronic reporting configurations](../../dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

## Setting up Retail for Norway

This section describes the Retail settings that are specific to and recommended for Norway. For more information about how to set up Retail, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

To use the Norway-specific functionality for Retail, you must complete these tasks:

|Set up task                                 | Information                                                                     |
|--------------------------------------------|---------------------------------------------------------------------------------|
|Select legal entity primary address         |Select a primary address for the legal entity that is located in Norway          |
|Set up functionality profiles               |You must enable auditing and set up receipt numbering.                           |
|Update POS permissions groups and individual permission settings for store workers  |Set the **Allow printing receipt copy** permission to an appropriate value: **Allow always** – The operator can print a copy of a receipt multiple times. **Allow only once** – The operator can print a copy of a receipt only one time. **Allow only once, and only if HQ DB is available** – The operator can print a copy of a receipt only one time, and only if the headquarters database is available through Real-Time service, so that the system can verify that no copies of the receipt have previously been printed in any store. **Never** – The operator can't print a copy of a receipt.            |
|Set up hardware profiles                    | Set the **Receipt profile ID** to be **Print**                                   |
|Set up sales tax            |You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services. For more information about how to set up and use sales tax in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and in Retail, see [Sales tax overview](../../financials/general-ledger/indirect-taxes-overview.md).           |
|Set up receipt formats            | [Receipt templates and printing](../receipt-templates-printing.md)           |



