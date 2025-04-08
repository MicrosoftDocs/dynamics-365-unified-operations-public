--- 
title: Define shift and industry types for books (India)
description: Learn about defining a shift type and industry for a book and then assigning the book to a fixed asset, including a step-by-step process. 
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/21/2024
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0 
---

# Define shift and industry types for books (India)

[!include [banner](../../includes/banner.md)]

This procedure walks you through defining a shift type and industry for a book and then assigning the book to a fixed asset. The calculation of depreciation for a fixed asset is for a specific period and is based on the selected type of shift and industry. The calculation of depreciation is also based on the actual number of days in the calendar month when Day based is selected in the Calendar field on the Books page for the Straight line service life depreciation method or the Reducing balance depreciation method. The demo data company used to create this procedure is INMF.

1. Go to Fixed assets > Setup > Books.
2. Click New.
3. In the Book field, type a value.
4. Select Yes in the Calculate depreciation field.
5. In the Description field, type a value.
6. In the Depreciation profile field, enter or select a value.
7. In the Calendar field, enter or select a value.
8. Select Yes in the Override fixed asset calendar days? field.
9. In the Asset working days field, enter a number.
10. Click Shift depreciation.
11. In the From date field, enter a date.
12. In the To date field, enter a date.
13. Click Save.
14. Close the page.
15. Close the page.
16. Go to Fixed assets > Fixed assets > Fixed assets.
17. In the list, find and select the desired record.
18. In the list, click the link in the selected row.
19. Click Books.
20. Click New.
21. In the Book field, enter or select a value.
22. Click Shift depreciation.
23. Close the page.
24. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
