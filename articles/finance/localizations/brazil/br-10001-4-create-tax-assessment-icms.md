---
title: Create a tax assessment - ICMS (Brazil)
description: This article describes how to create a tax assessment for the ICMS tax for a selected booking period in Brazil with Microsoft Dynamics 365 Finance.
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

# Create a tax assessment - ICMS (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to create a tax assessment for the Imposto Sobre Circulação de Mercadorias e Prestação de Serviços (ICMS) tax for a selected booking period in Brazil with Microsoft Dynamics 365 Finance.

You can create a tax assessment for the ICMS tax for a selected booking period. This tax amount considers the amount of ICMS tax to recover and the amount of ICMS tax to pay from the fiscal documents. For the amount that is due after the tax assessment, you can make the tax payment to the tax authority. 

The following procedure uses the BRMF demo company.

To create a tax assessment for the ICMS tax for a selected booking period, follow these steps.

1. In Dynamics 365 Finance, go to **Fiscal books \> Common \> Booking period**.
1. Select **Create new booking period** to open the drop dialog.
1. In the **Fiscal establishment** field, enter or select a value.
1. In the **Month** field, select an option.
1. In the **Year** field, enter a number.
1. Select **OK**.
1. Select **Sync**.
1. Select **OK**.
1. Close the page.
1. Go to **Fiscal books \> Common \> Tax assessment \> ICMS**.
1. Select **ICMS tax assessment** to open the drop dialog.
1. In the **Booking period** field, enter or select a value.
1. Select **OK**.
1. Select **Tax payment**.
1. Select **Create from assessment**.
1. Select **Edit**.
1. In the **Receita Code** field, enter a value.
1. In the list, mark the selected row.
1. In the **Due date** field, enter a date.
1. Expand the **General** section.
1. In the **Authority** field, enter or select a value.
1. Select **Post**.
1. Close the page.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
