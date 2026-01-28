---
title: Issue customer fiscal documents (for end users) (Brazil)
description: This article describes how to issue a fiscal document to a customer who bought goods from a fiscal establishment in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Issue customer fiscal documents (for end users) (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to issue a fiscal document to a customer who bought goods from a fiscal establishment in Brazil with Microsoft Dynamics 365 Finance.

You can issue a fiscal document to a customer who bought goods from a fiscal establishment. The calculation of the ICMS tax base amount considers the IPI tax amount. 

The following procedure uses the BRMF demo company.

To issue a fiscal document to a customer who bought goods from the fiscal establishment, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. Use the Quick Filter to find records. For example, filter on the **Account** field with a value of "BRMF-000004".
1. In the list, select the link in the selected row.
1. Expand the **Fiscal information** section.
1. Select **Edit**.
1. In the **Final user** field, select **Yes**.
1. Select **Save**.
1. Close the page.
1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
1. Select **Add line**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Sit** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
1. Expand the **Line details** section.
1. Select the **Fiscal information** tab.
1. In the **Fiscal document type** field, enter or select a value.
1. Select **Save**.
1. Select **Invoice**.
1. In the **Quantity field**, select an option.
1. In the **Print invoice field**, select **Yes**.
1. Select **OK**.
1. Select **Yes**.
1. Close the page.
1. Go to **Accounts receivable \> Fiscal documents \> Electronic fiscal documents \> Export/import NF-e process**.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
