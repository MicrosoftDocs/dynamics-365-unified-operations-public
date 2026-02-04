---
title: GB-00002 Create a purchase order that includes items subject to reverse charge VAT
description: Learn how to create a purchase order that includes items subject to reverse charge VAT for the United Kingdom in Microsoft Dynamics 365 Finance.
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
  - PurchTable, PurchCreateOrder, TaxTmpWorkTrans
  - DefaultDashboard
---

# GB-00002 Create a purchase order that includes items subject to reverse charge VAT

[!include [banner](../../includes/banner.md)]

This article explains how to create a purchase order that includes items subject to reverse charge VAT for the United Kingdom in Microsoft Dynamics 365 Finance.

The following procedure usies the demo company GBSI.

Before you complete the procedure, you must complete the procedures in [Set up reverse charge VAT item groups, rules, and parameters](gb-00002-reverse-charge-vat-item-groups.md).

## Create a purchase order

To create a purchase order, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, select the drop-down, and then select **GB_SI_000002**.  
1. In the list, find and select **GB_SI_000002**.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter "S0020".  
1. In the **Quantity** field, enter "4".  
1. In the **Unit price** field, enter "1000".  
1. Select **Add line**.
1. In the **Item number** field, enter "S0012".  
1. In the **Quantity** field, enter "6".  
1. In the **Unit price** field, enter "1000".  
1. Select **Save**.
1. Expand or collapse the **Line details** section.
1. For **Sales tax group** and **Item tax group**, validate that reverse charge VAT groups are set (**RC-VAT**).   
1. Select the **Setup** tab.
1. For **Sales tax group** and **Item tax group**, validate that reverse charge VAT groups are set (**RC-VAT**). 
1. In the list, select row 1.
1. For **Sales tax group** and **Item tax group**, validate that reverse charge VAT groups are set (**RC-VAT**). 
1. On the Action Pane, select **Purchase**.
1. Select **Sales tax**.
1. Validate that the calculated reverse charge VAT transactions are sales tax transactions with incoming and outgoing directions.  
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
