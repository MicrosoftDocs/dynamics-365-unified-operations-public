---
# required metadata

title: Import format for consolidation
description: This topic provides detailed information about the import format that is used when you consolidate financial data from multiple legal entities.
author: jinniew
ms.date: 10/09/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2018-5-31
ms.dyn365.ops.version: 8.0.1

---

# Import format for consolidation

[!include [banner](../includes/banner.md)]

This topic provides detailed information about the import format that is used when you consolidate financial data from multiple legal entities. The import format must be saved as a text (.txt) file.

## Import format

The following table lists the import format that you should use when you do a consolidation during an import.

| Record table | Format | Notes |
|--------------|---------|-------|
| 1            | 170150, Goodwill, 4 | <ul><li>The record table</li><li>The source main account ID</li><li>The main account line</li><li>The main account type</li></ul> |
| 2            | 110130, 2015/01/01, 1, USD, 0,0,80699.39,0,1 | <ul><li>The main account ID</li><li>The transaction date</li><li>The fiscal period type (**0** = Opening, **1** = Operating, and **2** = Closing)</li><li>The transaction currency</li><li>Debit or credit (**0** = Debit and **1** = Credit)</li><li>The posting layer</li><li>Transaction amounts</li><li>Quantity</li><li>The local RecID (ambiguous, unique int64 value for the transaction)</li></ul> |
| 3            | USMF0000009, 2017/01/01, FY2017, 1, 2017,01,01, 602200, USD, 6053.6.0 | <ul><li>The entry number (budget header transaction number)</li><li>The default date of the budget header</li><li>The budget model ID</li><li>Budget type (**1** - Original Budget, **2** - Transfer, **3** - Revision, **4** - Encumbrance, **5** - Pre-encumberance, **6** - Carry-forward budget, **7** - Project, **8** - Fixed Assets, **9** - Demand forecast, **10** - Supply forecast, **11** - Apportionments, **12** - Preliminary budget.)</li><li>The date of the line</li><li>The main account ID for the line</li><li>The currency code for the line</li><li>The amount for the line, in the transaction currency</li><li>The enumeration integer value for the budget type for the line (expense or revenue)</li></ul> |
| 4            | DEMF | RecordCompany is the Source legal entity. |
| 5            | 110130, 2015/01/01, 1, USD, 0,0,80699.39,0,1 | <ul><li>Main account ID</li><li>Transaction date</li><li>Fiscal period type (0 Opening, 1 Operating, 2 Closing)</li><li>Transaction currency</li><li>Debit or Credit (0 for Debit, 1 for Credit)</li><li>Posting layer</li><li>Transaction amount</li><li>Quantity</li><li>Local recid (ambiguous unique int64 value for the transaction)</li></ul>  |
| 6            | BusinessUnit, 1 Department, 2 | The financial dimension attributes that are defined in the segment order.<p>You can use the **Export** page to verify how the attributes are defined.</p> |
| 7            | 002,1,658 | <ul><li>The financial dimension value</li><li>The financial dimension, as the index that is provided in RecordDimensions</li><li>An ambiguous, unique record ID that is associated with the unique record ID from RecordTrans or RecordTrans2</li></ul> |
| 8            | 002,1,1 | <ul><li>Dimension values that are associated with the transaction from RecordBudget</li><li>The financial dimension, as the index that is provided in RecordDimensions</li><li>An ambiguous line record ID that is aligned with the order of the transaction lines in the file</li></ul> |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
