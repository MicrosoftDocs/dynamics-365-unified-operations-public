---
title: Set up interest and fines for vendor payments (Brazil)
description: You must set up accounts for financial interest and fines, default codes for interest and fines, and interest codes and fine codes for vendors and purchase orders.
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
# Set up interest and fines for vendor payments (Brazil)

[!include [banner](../../includes/banner.md)]

You must set up accounts for financial interest and fines, default codes for interest and fines, and interest codes and fine codes for vendors and purchase orders. You must also define the holidays or non-business days during a financial year that aren't considered when interest and fines are calculated.  This task uses the BRMF demo company.

1. Go to Accounts payable > Setup > Vendor posting profiles.
2. Use the Quick Filter to find records. For example, filter on the Posting profile field with a value of '010'.
3. In the list, find and select the desired record.
4. Click Edit.
5. In the Financial interest field, specify the desired values.
6. In the Fine field, specify the desired values.
7. Click Save.
8. Close the page.
9. Go to Accounts payable > Payment setup > Payment calendar.
10. Use the Quick Filter to find records. For example, filter on the Payment calendar field with a value of 'Brazil'.
11. Click State/province holidays.
12. Use the Quick Filter to find records. For example, filter on the State/province field with a value of 'SP'.
13. Click New.
14. In the Date field, enter a date.
15. In the Description field, type a value.
16. Click Save.
17. Click City holidays.
18. Use the Quick Filter to find records. For example, filter on the City field with a value of 'São Paulo'.
19. Click Add.
20. In the Date field, enter a date.
21. In the Description field, type a value.
22. Click Save.
23. Close the page.
24. Close the page.
25. Close the page.
26. Go to Accounts payable > Payment setup > Fine codes.
27. Click New.
28. In the Fine code field, type a value.
29. In the Description field, type a value.
30. In the Fine % field, enter a number.
31. Click Save.
32. Close the page.
33. Go to Accounts payable > Payment setup > Interest codes.
34. Click New.
35. In the Interest code field, type a value.
36. In the Description field, type a value.
37. In the Interest % field, enter a number.
38. In the Interest calculation per field, enter a number.
39. Click Save.
40. Close the page.
41. Go to Accounts payable > Vendors > All vendors.
42. Use the Quick Filter to find records. For example, filter on the Vendor account field with a value of 'BRMF-000001'.
43. In the list, click the link in the selected row.
44. Expand the Payment section.
45. Click Edit.
46. In the Fine code field, enter or select a value.
47. In the Interest code field, enter or select a value.
48. Click Save.
49. Close the page.
50. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
