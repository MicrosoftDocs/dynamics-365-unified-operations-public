---
title: Tax assessment for ISS tax (Brazil)
description: This article describes how to make a tax assessment for ISS tax for a given booking period that considers the amount of tax to recover and the amount of tax to pay in Brazil with Microsoft Dynamics 365 Finance.
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

# Tax assessment for ISS tax (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to make a tax assessment for Imposto Sobre Serviços (ISS) tax for a given booking period that considers the amount of tax to recover and the amount of tax to pay in Brazil with Microsoft Dynamics 365 Finance.

You can make the tax assessment for ISS tax for a given booking period, considering the amount of ISS tax to recover and the amount of ISS tax to pay from the fiscal documents. For the due amount after the tax assessment, you can make the payment of the amount for the tax authority. 

The following procedure uses the BRMF demo company.

To make a tax assessment for ISS tax for a given booking period, follow these steps:

1. In Dynamics 365 Finance, go to **Fiscal books \> Common \> Booking period**.
1. Select **Create new booking period** to open the drop dialog.
1. In the **Fiscal establishment** field, enter or select a value.
1. In the **Mont**h field, select a month.
1. In the **Year** field, enter a number.
1. Select **OK**.
1. Select **Sync**.
1. Select **OK**.
1. Close the page.
1. Go to **Fiscal books \> Common \> Tax assessment \> ISS**.
1. Select **ISS tax assessment** to open the drop dialog.
1. In the **Booking period** field, enter or select a value.
1. Select **OK**.
1. Select **Tax payment**.
1. Select **Create from assessment**.
1. In the list, mark the selected row.
1. Select **Edit**.
1. In the **Receita Code** field, enter a value.
1. In the **Due date** field, enter a date.
1. Expand the **General** section.
1. In the **Authority** field, enter or select a value.
1. Select **Post**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
