---
title: Create and transfer transactions to the BLWI (Belgium)
description: This article describes how to create and transfer transactions to the BLWI in Belgium with Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/02/2026
ms.reviewer: johnmichalak
ms.search.region: Belgium
ms.search.validFrom: 2016-06-30
---

# Create and transfer transactions to the BLWI (Belgium)

[!include [banner](../../includes/banner.md)]

This article describes how to create and transfer transactions to the Belgisch Luxemburgs Wissel Instituut (BLWI) in Belgium by using Microsoft Dynamics 365 Finance.

The following procedure walks you through creating a BLWI report for Belgium. This procedure was created by using the demo data company USSI. The functionality is available for legal entities whose primary address is in Belgium. You must set up a registration ID for Belgium and fill in the registration number to create BLWI declaration.

To create and transfer transactions to the BLWI, you must first set up BLWI information.

BLWI report includes customer and vendor transactions that you mark with one of the chosen payment purpose codes when the customer or vendor primary address is in a country or region that's different from the country or region of the legal entity.

To create and transfer transactions to the BLWI, follow these steps:

1. In Dynamics 365 Finance, go to **Tax \> Declarations \> Foreign trade \> BLWI**.
1. Select **Transfer**.
1. In the **Survey code** field, enter or select a value.
1. In the **Date** field, enter a date.
1. Select **OK**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **BLWI transaction** field, select an option.
1. In the **Account number** field, enter or select a value.
1. In the **Amount in transaction currency** field, enter a number.
1. In the **Country/region** field, enter or select a value.
1. Select **Save**.
1. Select **Create XML file**.
1. In the **Survey code** field, enter or select a value.
1. In the **File name** field, type a value.
1. In the **Date field**, enter a date.
1. Select **OK**.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
