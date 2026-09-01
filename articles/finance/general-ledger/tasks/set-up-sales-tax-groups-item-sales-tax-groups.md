--- 
title: Set up sales tax groups and item sales tax groups
description: Learn about how to set up sales tax and item sales tax groups, including a step-by-step process that outlines setting up tax groups for transactions. 
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/05/2026
ms.custom:
ms.reviewer: twheeloc   
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: TaxGroup,  TaxItemGroup 
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up sales tax groups and item sales tax groups

[!INCLUDE [banner](../../includes/banner.md)]

This task recording walks you through the setup of sales tax groups and item sales tax groups. Sales tax groups are groups of sales tax codes that you attach to customers and vendors. You also attach them to ledger accounts for transactions that aren't posted to a particular vendor or customer. Item sales tax groups are groups of sales tax codes that you attach to resources like products. The sales taxes that apply to a particular transaction are determined by the sales tax codes that are included both in the sales tax group and in the item sales tax group of the transaction. You can calculate sales tax only if you select a sales tax group and an item sales tax group for each transaction that requires sales tax calculation or recording.  

1. Go to **Tax > Indirect taxes > Sales tax > Sales tax groups**.
1. Select **New**.
1. In the **Sales tax group** field, enter a value.
1. In the **Description** field, enter a value.
1. Expand the **Setup** section.
1. Select **Add**.
1. In the list, select the row.
1. In the **Sales tax code** field, select the dropdown button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. Close the page.
1. Go to **Tax > Indirect taxes > Sales tax > Item sales tax groups**.
1. Select **New**.
1. In the **Item sales tax group** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Add**.
1. In the list, select the row.
1. In the **Sales tax code** field, select the dropdown button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
