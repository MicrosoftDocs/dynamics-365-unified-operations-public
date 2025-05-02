---
title: Set up adjustment codes for PIS and COFINS taxes (Brazil)
description: This article describes how to make manual adjustment transactions to adjust the credit of reported PIS and COFINS amounts in various records in Brazil with Microsoft Dynamics 365 Finance.
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

# Set up adjustment codes for PIS and COFINS taxes (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to make manual adjustment transactions to adjust the credit of reported Program of Social Integration (PIS) and Contribution for the Financing of Social Security (COFINS) amounts in various records in Brazil with Microsoft Dynamics 365 Finance.

You can make manual adjustment transactions to adjust the credit or debit of PIS and COFINS amounts that are reported in records M220, M225, M620, M625, M110, M115, M510, and M515. You must first create the adjustment codes. The Brazilian government determines the adjustment codes, based on the adjustment criteria and the type of adjustment transaction. 

The following procedure uses the BRMF demo company.

To make manual adjustment transactions to adjust the credit of reported PIS and COFINS amounts, follow these steps.

1. In Dynamics 365 Finance, go to **Fiscal books \> Setup \> Tax adjustment codes \> PIS and COFINS adjustment code table**.
1. Expand the **Posting** section.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Company accounts** field, enter or select a value.
1. In the **Sales tax code** field, enter or select a value.
1. In the **Main account** field, specify the desired values.
1. Select **Save**.
1. Select **New**.
1. In the **Identification** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Tax type** field, select an option.
1. In the **Adjustment type** field, select an option.
1. In the **Adjustment code** field, enter a value.
1. In the **Valid From Date** field, enter a date.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
