--- 
title: Create sales tax transactions on documents
description: Learn about how sales tax is calculated by providing a sales tax group and an item sales tax group on document lines, including a step-by-step process.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: twheeloc    
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, TaxTmpWorkTrans 
ms.dyn365.ops.version: Version 7.0.0 
---

# Create sales tax transactions on documents

[!include [banner](../../includes/banner.md)]

Sales tax on documents is calculated by providing a Sales tax group and an Item sales tax group on document lines. These default from master data but can be changed manually if necessary. The calculated sales tax can be checked on a line and document level. This task uses the USMF demo company.

1. Go to **Accounts receivable > Orders > All sales orders**.
2. Click **New**.
3. In the **Customer account** field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Click **OK**.
7. In the list, mark the selected row.
8. In the **Item number** field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
10. In the **Unit price** field, enter a number.
11. Expand or collapse the **Line details** section.
12. Click the **Setup** tab.
13. In the **Item sales tax group** field, click the drop-down button to open the lookup.
14. In the list, find and select the desired record.
15. In the list, click the link in the selected row.
16. Click **Financials**.
17. Click **Sales tax**.
18. Click **OK**.
19. Click **Add line**.
20. In the list, mark the selected row.
21. In the **Item number** field, click the drop-down button to open the lookup.
22. In the list, find and select the desired record.
23. In the list, click the link in the selected row.
24. In the **Unit price** field, enter a number.
25. In the **Item sales tax group** field, click the drop-down button to open the lookup.
26. In the list, find and select the desired record.
27. In the list, click the link in the selected row.
28. On the Action Pane, click **Sell**.
29. Click **Sales tax**.
30. Click **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
