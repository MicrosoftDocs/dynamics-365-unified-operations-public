---
title: PIS and COFINS fixed assets (Brazil)
description: When a legal entity purchases a fixed asset, the PIS and COFINS tax credit that is calculated on that transaction can be appropriated in a specific number of installments.
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
# PIS and COFINS fixed assets (Brazil)

[!include [banner](../../includes/banner.md)]

When a legal entity purchases a fixed asset, the PIS and COFINS tax credit that is calculated on that transaction can be appropriated in a specific number of installments. For the correct calculation for this tax refund, the legal entity must present a specific fiscal book or report for the information in the SPED EFD Contributions file to demonstrate correct appropriation of the PIS and COFINS tax credit amount. The control of credit that is appropriated in the tax assessment period is detailed in records F120 and F130 of SPED EFD Contributions. This task uses the BRMF demo company.

1. Go to Procurement and sourcing > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, enter or select a value.
4. Click OK.
5. Click Add line.
6. In the list, mark the selected row.
7. In the Item number field, enter or select a value.
8. In the CFOP field, enter or select a value.
9. In the Quantity field, enter a number.
10. In the Unit price field, enter a number.
11. Expand the Line details section.
12. Click the Fixed assets tab.
13. Select Yes in the New fixed asset? field.
14. In the Fixed asset group field, enter or select a value.
15. Click the Financial dimensions tab.
16. In the CostCenter field, enter or select a value.
17. In the Filial field, enter or select a value.
18. On the Action Pane, click Purchase.
19. Click Confirm.
20. Close the page.
21. Close the page.
22. Go to Accounts payable > Purchase orders > All purchase orders.
23. In the list, click the link in the selected row.
24. On the Action Pane, click Invoice.
25. Click Invoice.
26. Click Default from: Product receipt quantity to open the drop dialog.
27. In the Default quantity for lines field, select an option.
28. Click OK.
29. In the Document model field, enter or select a value.
30. In the Access key field, type a value.
31. In the Invoice date field, enter a date.
32. In the Posting date field, enter a date.
33. Click Post.
34. Close the page.
35. Close the page.
36. Go to Fiscal books > Common > Booking period.
37. Click Create new booking period to open the drop dialog.
38. In the Fiscal establishment field, enter or select a value.
39. In the Month field, select an option.
40. In the Year field, enter a number.
41. Click OK.
42. Click Sync.
43. Click OK.
44. Click PIS-COFINS.
45. Click PIS and COFINS tax assessment to open the drop dialog.
46. Click OK.
47. Close the page.
48. Close the page.
49. Go to Fiscal books > Common > Fixed assets > All PIS and COFINS fixed assets.
50. In the list, click the link in the selected row.
51. Expand the PIS and COFINS fixed asset transactions section.
52. Close the page.
53. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
