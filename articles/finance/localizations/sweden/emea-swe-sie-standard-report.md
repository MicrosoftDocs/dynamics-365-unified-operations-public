---
title: Export financial information for auditors in Sweden
description: Learn about the SIE standard report for Sweden, including a step-by-step process for setting up a SRU code for each general ledger account.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.date: 11/25/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Sweden
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
---

# Export financial information for auditors in Sweden

[!include[banner](../../includes/banner.md)]

You can export financial data using the formats specified by the Standard Import Export Group (SIE), which is an organization in Sweden that develops standard formats. Before you export data, you must set up a Standardiserad Räkenskaps Utdrag (SRU) code for each general ledger account. 

1. Go to **General ledger** > **Periodic tasks** > **SIE export**. 
1. On the **Export to SIE file** page, enter the reporting date, budget model, and format mapping (SIE export format (SE). 
1. Select **OK**. 
1. On the **Electronic report parameters** page, select one of the following options in the **SIE type** field: 
  - Type 2 – Exports year-end balances and period balances. 
  - Type 3 – Exports dimension balances. 
  - Type 4I – Exports transactions. 
  - Type 4E – Exports year-end balances and transactions. 
1. Select **OK**. The export is found in your Downloads folder.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
