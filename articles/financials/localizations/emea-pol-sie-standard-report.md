---
# required metadata

title: Export financial information for auditors for Sweden
description: This topic provides information about the SIE standard report for Poland.
author: ShylaThompson
manager: AnnBe
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Sweden
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Export financial information for auditors for Sweden

[!include[banner](../includes/banner.md)]

You can export financial data using the formats specified by the Standard Import Export Group (SIE), the organization in Sweden that develops standard formats. Before you export data, you must set up a three-digit Standardiserad Räkenskaps Utdrag (SRU) code for each general ledger account. 

1. Click General ledger > Periodic > SIE export. 
2. Enter the file name and location to create the SIE file. 
3. Using the From date and To date fields, select the range of financial information to include in the export file. 
4. Enter a budget model to include in the export file. 
5. In the SIE file type field, select one of the following options: 
  - SIE type 2 – Exports year-end balances and period balances. 
  - SIE type 3 – Exports dimension balances. 
  - SIE type 4I – Exports transactions. 
  - SIE type 4E – Exports period balances and transactions. 
6. To include the chart of accounts in the export file, select the Include chart of accounts check box. 
7. To include the whole account name in the export file, select the Full name of account check box. 
  > [!NOTE]
  > By default, only the first 30 characters of the account name are included in the export file. 
8. Click OK. 
