---
title: Miscellaneous charges on free text invoices (Brazil)
description: This article describes how to configure miscellaneous charges on free text invoices for Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
ms.search.industry: Manufacturing;Distribution;Service industries
---

# Miscellaneous charges on free text invoices (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to configure miscellaneous charges on free text invoices for Brazil with Microsoft Dynamics 365 Finance.

Brazilian legislation taxes miscellaneous charges such as freight. Miscellaneous charges can be used only on a free text invoice. 

The following procedure uses the BRMF demo company.

To configure miscellaneous charges on free text invoices, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select **New**.
1. In the **Fiscal establishment ID** field, enter or select a value.
1. In the **Customer account** field, enter or select a value.
1. In the **Lines or header** field, select an option.
1. Expand the **Fiscal information** section.
1. In the **Fiscal document type** field, enter or select a value.
1. In the **Lines or header** field, select an option.
1. Select **Save**.
1. Select **Add line**.
1. In the list, mark the selected row.
1. In the **Description** field, enter a value.
1. In the **Main account** field, enter the desired values.
1. In the **CFOP** field, enter or select a value.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
1. Expand the **Line details** section.
1. In the **Fixed asset number** field, enter or select a value.
1. Select **Charges**.
1. In the **Charges code** field, enter or select a value.
1. In the **Charges value** field, enter a number.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Select **Save**.
1. Close the page.
1. Select **Save**.
1. Select **Post**.
1. In the **Carrier name** field, enter or select a value.
1. In the **Volume type** field, enter a value.
1. In the **Volume quantity** field, enter a number.
1. In the **Net weight** field, enter a number.
1. In the **Gross weight** field, enter a number.
1. Select **OK**.
1. Close the page.
1. Go to **Accounts receivable \> Fiscal documents \> Electronic fiscal documents \> Export/import NF-e process**.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
