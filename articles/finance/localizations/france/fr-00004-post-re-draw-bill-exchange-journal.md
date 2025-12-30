--- 
title: FR-00004 Post a redraw bill of exchange journal
description: Learn how to post a redraw bill of exchange journal for legal entities whose primary address is in France in Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 04/04/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak    
ms.search.region: France
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransCustBillOfExchange, CustOpenTrans
---

# FR-00004 Post a redraw bill of exchange journal

[!include [banner](../../includes/banner.md)]

This article explains how to post a redraw bill of exchange journal for legal entities whose primary address is in France in Microsoft Dynamics 365 Finance.

The following procedure was created using the demo data company FRSI. 

The functionality described is available for legal entities whose primary address is in France. To complete this procedure you should have the role of accounts receivable clerk.

To post a redraw bill of exchange journal, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments \> Bill of exchange \> Redraw bill of exchange journal**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Name** field, enter or select a value.
1. In the list, select **ReemmEAR**.  
1. Select **Lines**.
1. In the list, mark the selected row.
1. In the **Account** field, enter "FR_SI_0001".
1. Select **Settle transactions**.
1. In the list, mark the most recently protested draw bill of exchange journal.  
1. Select the **Mark** checkbox.
1. Select **OK**.
1. Select **Post**.
1. Go to **Accounts receivable \> Inquiries and reports \> Payments \> Bill of exchange journal**.
1. Verify that the status for the newly posted journal is **Redrawn**. If it is, then the process is complete.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
