---
title: GB-00002 Create a sales order that includes items subject to reverse charge VAT
description: Learn how to create a sales order that includes items subject to reverse charge VAT for the United Kingdom in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/04/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - SalesTableListPage, SalesCreateOrder, SalesTable, TaxTmpWorkTrans
  - DefaultDashboard
---

# GB-00002 Create a sales order that includes items subject to reverse charge VAT

[!include [banner](../../includes/banner.md)]

This article explains how to create a sales order that includes items subject to reverse charge VAT for the United Kingdom in Microsoft Dynamics 365 Finance.

Before you complete the following procedure, you must complete the procedures in [Set up reverse charge VAT item groups, rules, and parameters](gb-00002-reverse-charge-vat-item-groups.md).

The procedure uses the demo company GBSI.

## Create a sales order that includes items subject to reverse charge VAT

To create a sales order that includes items subject to reverse charge VAT, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Select **New**.
1. In the **Customer account** field, select the drop-down, and then select **GB_SI_002**.  
1. In the list, find and select **GB_SI_002**.  
1. In the list, select **GB_SI_002** in the selected row. 
1. Select **OK**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter "S0020".  
1. In the **Quantity** field, enter "10".
1. In the **Unit price** field, enter "1000".  
1. Select **Save**.
1. Select or clear the **Don't show this dialog for current document again** checkbox.
1. Select **OK**.
1. Expand or collapse the **Line details** section.
1. Select the **Setup** tab.
1. Ensure that the sales tax group is set to **Reverse charge VAT: RC-VAT-AR**.  
1. On the Action Pane, select **Sell**.
1. Select **Sales tax**.
1. Ensure that the reverse charge VAT is calculated in the sales tax transactions.  
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
