---
title: Calculate CIAP credit amount (Brazil)
description: Every month, for each fiscal establishment, the tax credit amount is calculated for past fixed asset acquisitions for each fixed asset.
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
# Calculate CIAP credit amount (Brazil)

[!include [banner](../../includes/banner.md)]

Every month, for each fiscal establishment, the tax credit amount is calculated for past fixed asset acquisitions for each fixed asset. This calculation occurs until the maximum number of tax credit installment payments is reached, or until the fixed asset no longer belongs to the legal entity. Each fixed asset tax credit installment payment is used to create a tax fiscal document that is part of the ICMS tax assessment for the legal entity. This task uses the BRMF demo company.

1. Go to Fiscal books > Common > Booking period.
2. Click Create new booking period to open the drop dialog.
3. In the Fiscal establishment field, enter or select a value.
4. In the Month field, select an option.
5. In the Year field, enter a number.
6. Click OK.
7. Click Sync.
8. Click OK.
9. Click ICMS.
10. Click ICMS tax assessment to open the drop dialog.
11. Click OK.
12. Click CIAP assessment.
13. Click Calculate CIAP factor.
14. Close the page.
15. Close the page.
16. Close the page.
17. Go to General ledger > Journal entries > All tax fiscal documents.
18. Click New.
19. In the Tax fiscal document type field, select an option.
20. In the Fiscal establishment ID field, enter or select a value.
21. In the Account number field, enter or select a value.
22. In the Date field, enter a date.
23. In the Fiscal document type field, enter or select a value.
24. Click Save.
25. Click Add line.
26. In the Item description field, type a value.
27. In the list, mark the selected row.
28. In the CFOP field, enter or select a value.
29. In the Sales tax code field, enter or select a value.
30. In the Amount field, enter a number.
31. Click Post.
32. Click OK.
33. Close the page.
34. Close the page.
35. Go to Accounts receivable > Fiscal documents > Electronic fiscal documents > Export/import NF-e process.
36. Click OK.
37. Go to Fiscal books > Common > Booking period.
38. In the list, mark the selected row.
39. Click Sync.
40. Click OK.
41. Click ICMS.
42. Close the page.
43. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
