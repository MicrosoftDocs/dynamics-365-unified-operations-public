--- 
# required metadata 
 
title: Create a journal entry using template
description: Posted journal vouchers can be saved as Voucher templates and applied in a new journal voucher. 
author: aprilolson
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, LedgerJournalTransDaily, LedgerJournalTransVoucherTemplate   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a journal entry using template

[!include [banner](../../includes/banner.md)]

Posted journal vouchers can be saved as Voucher templates and applied in a new journal voucher. This procedure uses the USMF demo company.

1. Go to **General ledger > Journal entries > General journals**.
2. On the **Action pane**, click **New**. This procedure starts by creating and posting a journal voucher, but any previously posted journal voucher can be saved as a template.  
3. In the **Name** field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Click **Lines**.
7. In the **Account type** field, type a value.
8. In the **Description** field, type a value.
9. In the **Debit** field, type a value.
10. Click **New**.
11. In the **Account type** field, type a value.
12. In the **Description** field, type a value.
13. In the **Debit** field, type a value.
14. Click **New**.
14. In the **Account** field, specify the desired values.
15. In the **Description** field, type a value.
16. In the **Credit** field, type a value to balance the voucher.
17. On the **Action pane**, click **Post**.
18. Click **Functions**.
19. Click **Save voucher** template.
20. This procedure assumes a **Percent Template** type. Click **OK**.
    - Percent: The amounts in the voucher are converted into percentage factors, which allows any amount to be applied when the Voucher template is selected.
    - Amount: The actual amounts will be stored and applied.  
21. Click **General journals**.
22. Click **New**.
23. In the **Name** field, click the drop-down button to open the lookup.
24. In the list, click the link in the selected row.
25. Click **Lines**.
26. Click **Functions**.
27. Click **Select voucher template**.
28. Find the template that you created earlier. Click **OK**. You may need to click **Previous step** and then select the correct template if other templates exist.  
29. In the **Amount** field, enter the amount to be applied to the voucher. The **Amount** field is only displayed if the voucher template is of type Percent.  
30. Click **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
