---
title: Create and transfer transactions to the BLWI (Belgium)
description: This article describes how to create and transfer transactions to the BLWI in Belgium with Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/11/2025
ms.reviewer: johnmichalak
ms.search.region: Belgium
ms.search.validFrom: 2016-06-30
---

# Create and transfer transactions to the BLWI (Belgium)

[!include [banner](../../includes/banner.md)]

This article describes how to create and transfer transactions to the Belgisch Luxemburgs Wissel Instituut (BLWI) in Belgium with Microsoft Dynamics 365 Finance.

The following procedure walks you through creating BLWI report for Belgium. This procedure was created using the demo data company USSI. The functionality is available for legal entities whose primary address is in the Belgium. You must set up a registration ID for Belgium and fill in the registration number in order to create BLWI declaration.

To create and transfer transaction to the BLWI, you must first set up BLWI information.

Customer/vendor transactions marked with one of the chosen payment purpose codes with customer/vendor primary address are in a country/region different from the country/region of the legal entity are included in BLWI report.

To create and transfer transaction to the BLWI, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Declarations \> Foreign trade \> BLWI**.
2. Select **Transfer**.
3. In the **Survey code** field, enter or select a value.
4. In the **Date** field, enter a date.
5. Select **OK**.
6. Select **New**.
7. In the list, mark the selected row.
8. In the **BLWI transaction** field, select an option.
9. In the **Account number** field, enter or select a value.
10. In the **Amount in transaction currency** field, enter a number.
11. In the **Country/region** field, enter or select a value.
12. Select **Save**.
13. Select **Create XML file**.
14. In the **Survey code** field, enter or select a value.
15. In the **File name** field, type a value.
16. In the **Date field**, enter a date.
17. Select **OK**.
18. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
