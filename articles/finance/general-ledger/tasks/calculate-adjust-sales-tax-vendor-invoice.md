--- 
# required metadata 
 
title: Calculate and adjust sales tax on a vendor invoice
description: This article explains how to adjust sales tax on a vendor invoice in Dynamics 365 Finance. 
author: twheeloc
ms.date: 07/31/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, LedgerJournalTransVendInvoice, VendTableLookup, TaxTmpWorkTrans   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Calculate and adjust sales tax on a vendor invoice

[!include [banner](../../includes/banner.md)]

This article explains how to adjust sales tax on a vendor invoice. If the original source document displays different tax amounts as calculated, you can adjust those amounts before posting. This task uses the DEMF demo company.

1. Go to **Accounts payable > Invoices > Invoice journal**.
2. Select **New**.
3. In the **Name** field of the new row, select an option in the drop-down menu.
4. In the Action Pane, select **Lines**.
5. In the **Account** field, specify the desired values.
6. In the **Invoice** field, type a value.
7. In the **Credit** field, enter a number.
8. In the **Offset account** field, specify the desired values.
9. Select **Sales tax**.
10. In the **Total actual sales tax amount** field, enter a number.
11. On the **Adjustment** tab, the sales tax amounts can be adjusted per sales tax code.
12. Select **Reset actual from calculated amounts**.
13. Select **OK**.
14. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
