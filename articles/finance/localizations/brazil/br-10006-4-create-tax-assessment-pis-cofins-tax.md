---
title: Create a tax assessment - PIS and COFINS tax (Brazil)
description: This article describes how to create the tax assessment for PIS/COFINS contributions for a given booking period in Brazil with Microsoft Dynamics 365 Finance.
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

# Create a tax assessment - PIS and COFINS tax (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to create the tax assessment for Program of Social Integration (PIS)/Contribution for the Financing of Social Security (COFINS) contributions for a given booking period in Brazil with Microsoft Dynamics 365 Finance.

You can create the tax assessment for PIS/COFINS contributions for a given booking period. The tax assessment considers the PIS/COFINS contribution amount to recover and the PIS/COFINS contribution amount to pay from the fiscal documents. For the amount due after the tax assessment, you can create the tax payment. 

The following procedure uses the BRMF demo company.

To create the tax assessment for PIS/COFINS contributions for a given booking period, follow these steps.

1. In Dynamics 365 Finance, go to **Fiscal books \> Common \> Booking period**.
1. Select **Create new booking period** to open the drop dialog.
1. In the **Fiscal establishment** field, enter or select a value.
1. In the **Month** field, select a month.
1. In the **Year** field, enter a year.
1. Select **OK**.
1. Select **Sync**.
1. Select **OK**.
1. Close the page.
1. Go to **Fiscal books \> Common \> Tax assessment \> PIS-COFINS**.
1. Select **PIS and COFINS tax assessment** to open the drop dialog.
1. In the **Booking period** field, enter or select a value.
1. Select **OK**.
1. Select **Tax payment**.
1. Select **reate from assessment**.
1. Select **Edit**.
1. In the **Receita Code** field, enter a value.
1. In the list, mark the selected row.
1. In the **Due date** field, enter a date.
1. Expand the **General** section.
1. In the **Authority** field, enter or select a value.
1. Select **Post**.
1. Close the page.
1. In the list, find and select the desired record.
1. Select **Tax payment**.
1. Select **Create from assessment**.
1. Select **Edit**.
1. In the **Receita Code** field, enter a value.
1. In the list, mark the selected row.
1. In the **Due date** field, enter a date.
1. In the **Authority** field, enter or select a value.
1. Select **Post**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
