---
title: Issue fiscal documents for vendors (Brazil)
description: You can create and post vendor invoices on behalf of nontaxpayer vendors.
author: AdamTrukawka
ms.date: 06/26/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
ms.search.industry: Manufacturing;Distribution;Service industries
---
# Issue fiscal documents for vendors (Brazil)

[!include [banner](../../includes/banner.md)]

You can create and post vendor invoices on behalf of nontaxpayer vendors. You must assign a fiscal establishment to a site. You must also set up a fiscal document type for purchase orders that you create and post on behalf of nontaxpayer vendors. Before you can create and post vendor invoices on behalf of a nontaxpayer vendor, you must specify the vendor as a nontaxpayer vendor. This task uses the BRMF demo company.

1. Go to Accounts payable > Vendors > All vendors.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Expand the Fiscal information section.
5. Click Edit.
6. Select Yes in the Generate incoming fiscal document field.
    * Select this option to indicate that the vendor is a nontaxpayer.  
7. Select Yes in the Use and consumption field.
8. Select No in the ICMS contributor field.
9. Click Save.
10. Close the page.
11. Close the page.
12. Go to Procurement and sourcing > Purchase orders > All purchase orders.
13. Click New.
14. In the Vendor account field, enter or select a value.
    * Select a vendor account that is classified as a nontaxpayer.  
15. Click OK.
16. In the Item number field, enter or select a value.
17. In the CFOP field, enter or select a value.
18. In the Site field, enter or select a value.
19. In the Warehouse field, enter or select a value.
20. In the Quantity field, enter a number.
21. Click Save.
22. On the Action Pane, click Purchase.
23. Click Confirm.
24. Close the page.
25. Close the page.
26. Go to Accounts payable > Purchase orders > All purchase orders.
27. In the list, click the link in the selected row.
28. On the Action Pane, click Invoice.
29. Click Invoice.
30. Click Default from: Product receipt quantity to open the drop dialog.
31. In the Default quantity for lines field, select an option.
32. Click OK.
33. Click Post.
34. Close the page.
35. Close the page.
36. Go to Accounts receivable > Fiscal documents > Electronic fiscal documents > Export/import NF-e process.
37. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
