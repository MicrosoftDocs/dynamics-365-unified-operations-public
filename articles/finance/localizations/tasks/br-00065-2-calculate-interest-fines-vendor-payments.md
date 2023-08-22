---
title: Calculate interest and fines on vendor payments (Brazil)
description: You can apply interest and fines on vendor payments that are delayed.
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
---
# Calculate interest and fines on vendor payments (Brazil)

[!include [banner](../../includes/banner.md)]

You can apply interest and fines on vendor payments that are delayed. The interest and fine amounts that apply to a payment can be calculated when you make a payment to a vendor. Before you calculate interest or fine codes for vendor payments, you must set up a list of bank holidays and national/regional holidays. A holiday date that is set up on the Payment calendar page is considered a non-working day. If an invoice is due on a non-working day, the due date is moved to the next working day in the calendar, and the interest and fines are calculated accordingly. This task uses the BRMF demo company.

1. Go to Accounts payable > Vendors > All vendors.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Expand the Payment section.
5. Click Edit.
6. In the Payment schedule field, enter or select a value.
7. In the list, click the link in the selected row.
8. In the Fine code field, enter or select a value.
9. In the list, click the link in the selected row.
10. In the Interest code field, enter or select a value.
11. Click Save.
12. Close the page.
13. Close the page.
14. Go to Procurement and sourcing > Purchase orders > All purchase orders.
15. Click New.
16. In the Vendor account field, enter or select a value.
17. Click OK.
18. Click Add line.
19. In the list, mark the selected row.
20. In the Item number field, enter or select a value.
21. In the CFOP field, enter or select a value.
22. In the Quantity field, enter a number.
23. Click Save.
24. On the Action Pane, click Purchase.
25. Click Confirm.
26. Close the page.
27. Close the page.
28. Go to Accounts payable > Purchase orders > All purchase orders.
29. In the list, click the link in the selected row.
30. On the Action Pane, click Invoice.
31. Click Invoice.
32. Click Default from: Product receipt quantity to open the drop dialog.
33. In the Default quantity for lines field, select an option.
34. Click OK.
35. In the Access key field, type a value.
36. In the Invoice date field, enter a date.
37. Click Post.
38. Close the page.
39. Close the page.
40. Go to Accounts payable > Payments > Payment journal.
41. Click New.
42. In the list, mark the selected row.
43. In the Name field, enter or select a value.
44. Click Lines.
45. In the list, mark the selected row.
46. In the Date field, enter a date.
47. In the Account field, specify the desired values.
48. In the Description field, enter or select a value.
49. Click Settle transactions.
50. In the list, find and select the desired record.
51. Select the Mark check box.
52. Select the Mark check box.
53. Click OK.
54. In the list, mark the selected row.
55. In the Offset account field, specify the desired values.
56. Click Post.
57. Close the page.
58. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
