---
title: Calculate interest and fines on customer payments (Brazil)
description: You can apply interest and fines on customer payments that are delayed.
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
# Calculate interest and fines on customer payments (Brazil)

[!include [banner](../../includes/banner.md)]

You can apply interest and fines on customer payments that are delayed. The interest and fine amounts that apply to a payment can be calculated when you receive a payment from a customer. Before you calculate interest or fine codes for customer payments, you must set up a list of bank holidays and national/regional holidays. A holiday date that is set up on the Payment calendar page is considered a non-working day. If an invoice is due on a non-working day, the due date is moved to the next working day in the calendar, and the interest and fines are calculated accordingly. This task uses the BRMF demo company.



1. Go to Accounts receivable > Customers > All customers.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Expand the Payment defaults section.
5. Click Edit.
6. In the Payment schedule field, enter or select a value.
7. In the list, click the link in the selected row.
8. In the Fine code field, enter or select a value.
9. In the list, click the link in the selected row.
10. In the Interest code field, enter or select a value.
11. Click Save.
12. Close the page.
13. Close the page.
14. Go to Sales and marketing > Sales orders > All sales orders.
15. Click New.
16. In the Customer account field, enter or select a value.
17. Click OK.
18. Click Add line.
19. In the list, mark the selected row.
20. In the Item number field, enter or select a value.
21. In the Quantity field, enter a number.
22. In the CFOP field, enter or select a value.
23. Click Save.
24. Click Invoice.
25. In the Quantity field, select an option.
26. Select Yes in the Print invoice field.
27. Click OK.
28. Click Yes.
29. Close the page.
30. Close the page.
31. Close the page.
32. Go to Accounts receivable > Payments > Payment journal.
33. Click New.
34. In the list, mark the selected row.
35. In the Name field, enter or select a value.
36. Click Lines.
37. In the list, mark the selected row.
38. In the Date field, enter a date.
39. In the Account field, specify the desired values.
40. Click Settle transactions.
41. In the list, find and select the desired record.
42. Select the Mark check box.
43. Select the Mark check box.
44. Click OK.
45. In the list, mark the selected row.
46. In the Description field, enter or select a value.
47. In the Offset account field, specify the desired values.
48. Click Post.
49. Close the page.
50. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
