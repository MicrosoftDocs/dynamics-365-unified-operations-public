--- 
# required metadata 
 
title: Create a journal entry using a template
description: Posted journal vouchers can be saved as Voucher templates and applied in a new journal voucher. 
author: aprilolson
manager: AnnBe 
ms.date: 02/17/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a journal entry using a template

[!include[task guide banner](../../includes/task-guide-banner.md)]

Posted journal vouchers can be saved as Voucher templates and applied in a new journal voucher. This procedure uses the USMF demo company.

1. General ledger > Journal entries > General journals. Click New.
    * This procedure starts by creating and posting a journal voucher, but any previously posted journal voucher can be saved as a template.  
2. In the Name field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. Click Lines.
6. Enter an account for the Account type.
7. In the Description field, type a value.
8. Enter an amount in the Debit field.
9. Click New.
10. Enter a different account for the Account type.
11. In the Description field, type a value.
12. Enter an amount in the Debit field.
13. Click New.
14. In the Account field, specify the desired values.
15. In the Description field, type a value.
16. Enter an amount in the Credit field to balance the voucher.
17. Click Post.
18. Click Functions.
19. Click Save voucher template.
20. This procedure assumes a Percent Template type. Click OK.
    * • Percent: The amounts in the voucher are converted into percentage factors, which allows any amount to be applied when the Voucher template is selected.  • Amount: The actual amounts will be stored and applied.  
21. Click General journals.
22. Click New.
23. In the Name field, click the drop-down button to open the lookup.
24. In the list, click the link in the selected row.
25. Click Lines.
26. Click Functions.
27. Click Select voucher template.
28. Find the template that you created earlier. Click OK.
    * You may need to click Previous step and then select the correct template if other templates exist.  
29. In the Amount field, enter the amount to be applied to the voucher.
    * The amount field is only displayed if the voucher template is of type Percent.  
30. Click OK.

