---
title: Create a purchase order governed by budget
description: Use this procedure to create a purchase order that is checked for available budget. 
author: JennySong-SH
ms.date: 06/15/2020
ms.topic: how-to 
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a purchase order governed by budget

[!include [banner](../../includes/banner.md)]

Use this procedure to create a purchase order that is checked for available budget.

## Review the budget control configuration

1. Go to **Budgeting > Setup > Budget control > Budget control configuration**.
1. Select the **Budget funds available** tab.
1. Select the **Documents and journals** tab.
1. Select the **Define budget control rules** tab.
1. Select the **Define budget groups** tab.
1. Close the page.

## Create a purchase order

1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, enter or select a value.
1. Expand the **General** FastTab.
1. In the **Accounting date** field, set the date.
1. Select **OK** to close the dialog and open your new purchase order.
1. On the **Purchase order lines** FastTab, select **Add line** from the toolbar to add a new line and then fill out the line as needed to add an item to the order.
1. On the **Purchase order lines** FastTab toolbar, select **Financials \> Distribute amounts**.
1. In the **Ledger account** field, specify an account.
1. Close the page.

## Perform budget checking

1. Continue working with the purchase order you just added a line to.
1. On the **Purchase order lines** FastTab toolbar, select **Financials \> Perform budget checking**.
1. On the **Purchase order lines** FastTab toolbar, select **Financials \> Budget check errors or warnings**.
1. The **Budget check errors or warnings** dialog opens. Check the results of the check and then select **Close** to close the dialog.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]