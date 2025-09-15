---
title: Export financial information for auditors in Sweden
description: Learn how to export financial information for auditors in Sweden in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 07/21/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Sweden
ms.search.validFrom: 2016-05-31
---

# Export financial information for auditors in Sweden

[!include[banner](../../includes/banner.md)]

This article explains how to export financial information for auditors in Sweden in Microsoft Dynamics 365 Finance.

You can export financial data using the formats specified by the Standard Import Export Group (SIE), which is an organization in Sweden that develops standard formats. Before you export data, you must set up a Standardiserad Räkenskaps Utdrag (SRU) code for each general ledger account. 

To export financial data using the formats specified by the SIE, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Periodic tasks** \> **SIE export**. 
1. On the **Export to SIE file** page, enter the reporting date, budget model, and format mapping (SIE export format). 
1. Select **OK**. 
1. On the **Electronic report parameters** page, select one of the following options in the **SIE type** field: 
    - **Type 2**: Exports year-end balances and period balances. 
    - **Type 3**: Exports dimension balances. 
    - **Type 4I**: Exports transactions. 
    - **Type 4E**: Exports year-end balances and transactions. 
1. Select **OK**. The export is downloaded to your **Downloads** folder.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
