---
title: Enter PIS and COFINS tax adjustment transactions (Brazil)
description: This article describes how to create and post a journal for manual PIS and COFINS tax adjustments by using the adjustment codes defined by the tax authority in Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Enter PIS and COFINS tax adjustment transactions (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to create and post a journal for manual Program of Social Integration (PIS) and Contribution for the Financing of Social Security (COFINS) tax adjustments by using the adjustment codes defined by the tax authority in Brazil with Microsoft Dynamics 365 Finance.

You can create and post a journal for manual PIS and COFINS tax adjustments by using the adjustment codes that are defined by the tax authority. After the adjustment is posted, it can be viewed in the tax assessment. 

The following procedure uses the BRMF demo company.

To create and post a journal for manual PIS and COFINS tax adjustments by using the adjustment codes defined by the tax authority, follow these steps:

1. In Dynamics 365 Finance, go to **Fiscal books \> Journals \> General tax adjustment/benefit/incentive**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Name** field, enter or select a value.
1. Select **Lines**.
1. In the list, mark the selected row.
1. In the **Date** field, enter a date.
1. In the **Fiscal establishment ID** field, enter or select a value.
1. In the **Tax type** field, enter or select a value.
1. In the **Adjustment code** field, enter or select a value.
1. In the **Description** field, enter or select a value.
1. In the **Amount** field, enter a number.
1. In the **Base amount** field, enter a number.
1. In the **Tax value** field, enter a number.
1. In the **Taxation code** field, enter or select a value.
1. Select **Post**.
1. Close the page.
1. Go to **Fiscal books \> Common \> Tax assessment \> PIS-COFINS**.
1. Select **Adjustment**.
1. Close the page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
