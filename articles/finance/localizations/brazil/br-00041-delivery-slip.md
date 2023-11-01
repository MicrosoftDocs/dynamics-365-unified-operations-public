---
title: Delivery slips (Brazil)
description: You can post a delivery slip for a sales order that has multiple sales order lines that have a delivery Código Fiscal de Operações e Prestações (CFOP) code.
author: AdamTrukawka
ms.date: 06/24/2017
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
# Delivery slips (Brazil)

[!include [banner](../../includes/banner.md)]

You can post a delivery slip for a sales order that has multiple sales order lines that have a delivery Código Fiscal de Operações e Prestações (CFOP) code. For each sales order line, you must specify the CFOP code that has a delivery CFOP code assigned to it. A delivery slip is used when the customer that you deliver items to differs from the customer that is invoiced. (In other words, the customer account and invoice account differ.) Delivery slips are posted in chronological order. You must attach fiscal references to delivery slips before you post them. This task uses the BRMF demo company.

1. Go to Sales and marketing > Sales orders > All sales orders.
2. Click New.
3. In the Customer account field, enter or select a value.
4. Click OK.
5. In the Lines or header field, select an option.
6. In the Invoice account field, enter or select a value.
    * Select the customer that ordered the goods.  
7. In the Lines or header field, select an option.
8. Click Add line.
9. In the list, mark the selected row.
10. In the Item number field, enter or select a value.
11. In the Quantity field, enter a number.
12. In the Site field, enter or select a value.
13. In the Warehouse field, enter or select a value.
14. In the CFOP field, enter or select a value.
    * The CFOP codes that are available depend on the fiscal establishment of the site, order type, operation type, location of the customer, and delivery address of the customer.  
15. Expand the Line details section.
16. Click the Setup tab.
17. In the Delivery item sales tax group field, enter or select a value.
    * Enter the item sales tax group for the delivery fiscal document.  
18. In the Delivery sales tax group field, enter or select a value.
    * Enter the sales tax group for the delivery fiscal document.  
19. Click Save.
20. On the Action Pane, click Pick and pack.
21. Click Delivery slip.
22. Click Fiscal reference.
23. In the Document model field, enter or select a value.
24. In the Access key field, type a value.
    * Enter the access key from the NF-e that was issued by the customer that ordered to goods and that the sales must be invoiced to.  
25. In the Date field, enter a date.
26. In the Direction field, select an option.
27. In the Account field, enter or select a value.
    * Select the customer account that generated the fiscal document.  
28. Click Save.
29. Close the page.
30. Click OK.
31. Click OK.
32. Close the page.
33. Close the page.
34. Go to Accounts receivable > Fiscal documents > Electronic fiscal documents > Export/import NF-e process.
35. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
