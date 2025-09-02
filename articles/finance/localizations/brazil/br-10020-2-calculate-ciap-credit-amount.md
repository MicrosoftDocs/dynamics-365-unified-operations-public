---
title: Calculate CIAP credit amount (Brazil)
description: This article describes how to calculate the CIAP credit amount in Brazil with Microsoft Dynamics 365 Finance.
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

# Calculate CIAP credit amount (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to calculate the Imposto Sobre Circulação de Mercadorias e Prestação de Serviços (ICMS) Credit Control of Fixed Assets (CIAP) credit amount in Brazil with Microsoft Dynamics 365 Finance.

Every month for each fiscal establishment, the tax credit amount is calculated for past fixed asset acquisitions for each fixed asset. This calculation occurs until the maximum number of tax credit installment payments is reached, or until the fixed asset no longer belongs to the legal entity. Each fixed asset tax credit installment payment is used to create a tax fiscal document that is part of the ICMS tax assessment for the legal entity. 

The following procedure uses the BRMF demo company.

To calculate the CIAP credit amount, follow these steps.

1. In Dynamics 365 Finance, go to **Fiscal books \> Common \> Booking period**.
1. Select **Create new booking period** to open the drop dialog.
1. In the **Fiscal establishment** field, enter or select a value.
1. In the **Month** field, select a month.
1. In the **Year** field, enter a year.
1. Select **OK**.
1. Select **Sync**.
1. Select **OK**.
1. Select **ICMS**.
1. Select **ICMS tax assessment** to open the drop dialog.
1. Select **OK**.
1. Select **CIAP assessment**.
1. Select **Calculate CIAP factor**.
1. Close the page.
1. Go to **General ledger \> Journal entries \> All tax fiscal documents**.
1. Select **New**.
1. In the **Tax fiscal document type** field, select an option.
1. In the **Fiscal establishment ID** field, enter or select a value.
1. In the **Account number** field, enter or select a value.
1. In the **Date** field, enter a date.
1. In the **Fiscal document type** field, enter or select a value.
1. Select **Save**.
1. Select **Add lin**.
1. In the **Item description** field, enter a value.
1. In the list, mark the selected row.
1. In the **CFOP** field, enter or select a value.
1. In the **Sales tax code** field, enter or select a value.
1. In the **Amount** field, enter a number.
1. Select **Post**.
1. Select **OK**.
1. Close the page.
1. Go to **Accounts receivable \> Fiscal documents \> Electronic fiscal documents \> Export/import NF-e process**.
1. Select **OK**.
1. Go to **Fiscal books \> Common \> Booking period**.
1. In the list, mark the selected row.
1. Select **Sync**.
1. Select **OK**.
1. Select **ICMS**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
