---
# required metadata

title: Cash registers for Norway
description: This topic provides an overview of the cash register functionality that is available for Norway. 
author: EvgenyPopovMBS
manager: vastrup
ms.date: 09/22/2017
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
ms.search.region: Sweden
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2017-10-15
# ms.dyn365.ops.version: App update 4
---
# Cash registers for Norway

This topic provides an overview of the cash register functionality that is available for Norway in Microsoft Dynamics 365 for Retail. It also provides guidelines for setting up the functionality.

## Common POS features

To learn about common POS features that are available to customers in all countries or regions, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

## Overview of cash register functionality for Norway

### Receipt header texts
Receipt headers include text that identifies the type of receipt. For example, a sales receipt will include the text "Salskvittering". 

This following receipt types will include header text: 
- sales receipt
- return receipt
- copy receipt
- pro forma receipt
- training receipt
- delivery receipt

### Register additional events in POS Transaction journal
The following events should be registered in the POS transaction journal/POS Fiscal event log: price look-up; tax overrides; qty corrections; clearing the transactions from the channel database. This information is also available in the exported journal and/or X/Z-reports.

### Print local X/Z reports
X/Z reports include more information than the core retail documents. For example, the name and organization number of the enterprise as well as the number of price look-ups specified by product group and amount are both included in the reports.

### Digitally signing sales data
Each sales transaction should  be digitally signed. The signature should be recorded in the POS transaction journal/POS Fiscal event log and should be further available in the exported journal.

### AF-T Cash register export
It should be possible to export the POS transaction journal in the predefined SAF-T (Standard Audit File - Tax) Cash register format.

## Setting up Retail for Norway

This section describes the Retail settings that are specific to and recommended for Norway. For more information about how to set up Retail, see [Microsoft Dynamics 365 for Retail documentation](../index.md).

To use the Norway-specific functionality for Retail, you must complete these tasks:

|Set up task                                 | Information                                                                     |
|--------------------------------------------|---------------------------------------------------------------------------------|
|Select legal entity primary address         |Select a primary address for the legal entity that is located in Norway          |
|Set up functionality profiles               |You must enable auditing and set up receipt numbering.                           |
|Update POS permissions groups and individual permission settings for store workers                |Set the **Allow printing receipt copy** permission to an appropriate value: **Allow always** – The operator can print a copy of a receipt multiple times. **Allow only once** – The operator can print a copy of a receipt only one time. **Allow only once, and only if HQ DB is available** – The operator can print a copy of a receipt only one time, and only if the headquarters database is available through Real-Time service, so that the system can verify that no copies of the receipt have previously been printed in any store. **Never** – The operator can't print a copy of a receipt.            |
|Set up hardware profiles                    | Set the **Receipt profile ID** to be **Print** and you must enable the Microsoft XPS Document Writer printer.            |
|Set up sales tax            |You must create sales tax codes, sales tax groups, and item sales tax groups. You must also set up sales tax information for products and services.            |
|Set up receipt formats            |            |
|            |            |


