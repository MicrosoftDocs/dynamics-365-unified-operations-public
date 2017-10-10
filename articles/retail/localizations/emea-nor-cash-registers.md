---
# required metadata

title: Cash registers for Norway
description: This topic provides an overview of the cash register functionality that is available for Norway. 
author: EvgenyPopovMBS
manager: annbe
ms.date: 10/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:
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

This topic provides an overview of the cash register functionality that is available for Norway in Microsoft Dynamics 365 for Retail. It also provides guidelines for setting up the functionality.

To learn about common POS features that are available to customers in all countries or regions, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

## Overview of cash register functionality for Norway

### Receipt changes
The following additions to receipts are implemented using custom fields.

#### Header texts
Receipt headers include text that identifies the type of receipt. For example, a sales receipt will include the text "Salskvittering". 

This following receipt types will include header text: 
- sales receipt
- return receipt
- copy receipt
- pro forma receipt
- training receipt
- delivery receipt

#### Signed transaction sequential number
The signed transaction sequential number is listed on the receipt in order to identify a link between the printed receipt and the digital signature in the database.

#### Receipt totals
Additional fields are added to receipt totals, in order to exclude non-sales transactions from receipt totals. Non-sales transactions include:
- Issuing a gift card
- Adding funds to a gift card
- Deposits
- Prepayments

### POS Transaction journal
The following events are registered in the POS transaction journal/POS Fiscal event log: 
- Price look-up
- Tax overrides
- Quantity corrections
- Clearing the transactions from the channel database. This information is also included in the exported journal and/or X/Z-reports.

### X and Z reports
X and Z reports now include more information than the core retail documents. For example, the name and organization number of the enterprise as well as the number of price look-ups specified by product group and amount are both included in the reports.

### Digitally signing sales data
Each sales transaction should  be digitally signed. The signature should be recorded in the POS transaction journal/POS Fiscal event log and should be further available in the exported journal.

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



