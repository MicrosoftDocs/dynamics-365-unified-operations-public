--- 
# required metadata 
 
title: FR-00004 Setup method of payment
description: The procedure walks you through setting up methods of payment so that you can create and post the bill of exchange after approving it from the draw bill of exchange journal. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustPaymMode, CustVendPaymFormat   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: France
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# FR-00004 Setup method of payment

[!include [banner](../../includes/banner.md)]

The procedure walks you through setting up methods of payment so that you can create and post the bill of exchange after approving it from the draw bill of exchange journal.

This procedure was created using the demo data company FRSI. 

This functionality is available for legal entities whose primary address is in France.

You should have a role of Accounts receivables manager to perform this procedure.





1. Go to Accounts receivable > Payments setup > Methods of payment.
2. Click New.
3. In the Method of payment field, type a value.
4. In the Description field, type a value.
5. In the Payment status field, select 'Approved'.
6. In the Payment type field, select 'Bill of exchange'.
7. Expand or collapse the General section.
8. In the Account type field, select 'Bank'.
9. In the Payment account field, specify the desired values.
    * For example: 'FRSI OPER'  
10. Expand or collapse the File formats section.
11. Click Setup.
12. In the list, find and select the desired record.
    * Find and select "French bill of exchange" and use the arrow to move it to the Selected list.  
13. Click Save.
14. Close the page.
15. In the Name field, click the drop-down button to open the lookup.
16. In the list, click the link in the selected row.
    * Select "EnmmEAR"  
17. In the Export format field, click the drop-down button to open the lookup.
18. In the list, click the link in the selected row.
    * For example: Select "French bill of exchange"  
19. Select or clear the Create and post draw journal automatically when posting invoices check box.
20. Select or clear the Run export script check box.
21. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]