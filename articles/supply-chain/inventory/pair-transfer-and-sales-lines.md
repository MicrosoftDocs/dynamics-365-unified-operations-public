---
title: Link transfer order lines with sales order lines (preview)
description: Learn how to link transfer order lines to the sales order lines from which they were created. You can also add new transfer order lines to open transfer orders provided they are for the same warehouses.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/31/2024
ms.custom: 
  - bap-template
---

# Link transfer order lines with sales order lines (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!--KFM: Preview until further notice. -->

This feature lets you create transfer order lines from sales order lines and links the related lines together. You can choose to create a new transfer order or select an existing one to add the new lines to. <!--KFM: Can we briefly describe the business value of doing this? What are the benefits? What problems does this solve? Maybe use an example scenario. -->

Automatic marking is supported for non-settled item model groups, but catch-weight items aren't supported for automatic marking. <!--KFM: It's not clear what this does and how it's related. Explain what "marking" is what "automatic marking" means. Maybe this relates to https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/marking.  Add some context around what "non-settled" is. Later we mention "standard moving average items"; maybe explain that here too and tell what it means. -->

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *(Preview) Pair transfer order lines with sales order lines* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Add and link lines to a new or existing transfer order from a sales order

<!--KFM: Introduce this procedure. Explain when/why we would want to do this and what the result will be. -->

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order for which you want to add lines to a transfer order.
1. On the **Sales order lines** FastTab, select the lines that you want to add to the transfer order.
1. From the **Sales order lines** FastTab toolbar, select **Product and supply** \> **New** \> **Transfer order**.
1. The **Transfer order** dialog opens. Make the following settings:
    - **From warehouse** - Select warehouse from which the items will be transferred.
    - **To warehouse** - Select warehouse to which the items will be transferred. This is the warehouse that is associated with the sales order line and should already be selected.
    - **Add to an existing transfer order** - If you want to add the items to an existing transfer order, select the transfer order from the list. The list only shows open transfer orders that use the **From warehouse** and **To warehouse** selected in this dialog. If you want to create a new transfer order, leave this field blank.
    - **Ship date** - The date on which the items should be shipped.
    - **Reserve items automatically** - If you want the items to be reserved automatically, set this to *Yes*. <!--KFM: A little more info would be nice. What does this actually do? What if and why would I set this to *No*? -->
1. Select **OK**.
1. The new or selected transfer order opens. You can now view the transfer order lines and other details.

## View transfer order lines related to a sales order

<!--KFM: Introduce this procedure. Explain when/why we would want to do this and what the result will be. -->

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order that you want to check.
1. On the **Sales order lines** FastTab, select the line you want to view the related transfer order for. <!--KFM: Does it actually matter whether I pick a line here? Seems like we search for the all lines in this order; is that true? -->
1. From the **Sales order lines** FastTab toolbar, select **Product and supply** \> **View** \> **Related transfer orders**.
1. The **Paired transfer order and sales order lines** page opens. <!--KFM: Explain what this page is showing me and what I can do here. I think I am seeing all transfer order lines related to the previously shown sales order, regardless of what sales lines were selected before I came here. I think this only shows transfer orders that were created using this feature (I guess this is the "link" added by this feature). Looks like I can open the related item details, sales order and transfer order for each line by clicking in the grid. We have two Action Pane buttons, **Sales order line transactions** and **Transfer order line transactions**; we should describe what these are for. -->

## View sales orders related to a transfer order line

<!--KFM: Introduce this procedure. Explain when/why we would want to do this and what the result will be. -->

1. Go to one of the following pages: <!--KFM: Which should I pick? Is there any difference at all? -->
    - **Inventory management** \> **Inbound orders** \> **Transfer order**.
    - **Inventory management** \> **Outbound orders** \> **Transfer order**.
1. Open the transfer order that you want to check.
1. On the **Transfer order lines** FastTab, select the line you want to view the related sales order for.
1. From the **Transfer order lines** FastTab toolbar, select **Inventory** \> **Related sales order**.
1. The **Paired transfer order and sales order lines** page opens. <!--KFM: Explain what this page is showing me and what I can do here. I think I am seeing all sales order lines related to the transfer order line I had selected before coming here (selection seems to matter). I think this only shows sales orders that created the selected transfer order line using this feature (I guess this is the "link" added by this feature). Looks like I can open the related item details, sales order and transfer order for each line by clicking in the grid. We have two Action Pane buttons, **Sales order line transactions** and **Transfer order line transactions**; we should describe what these are for. -->

## Automatic marking between sales and transfer order lines

Automatic marking is only supported for standard moving average items. Non-settled item model group and catch-weight items aren't supported for automatic marking. <!--KFM: This seems to contradict the intro. Please confirm. Explain what makes an item a "standard moving average item" (this isn't mentioned in the intro); is this something to do with costing? -->

<!--KFM: What are we doing here? Just looking for "markings" or also editing them somehow?-->

The system automatically creates a marking when you create a transfer order line from from sales order line.

To view markings from a sale order line, follow these steps:

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order that you want to check.
1. On the **Sales order lines** FastTab, select the line you want to view the marking for.
1. On the **Sales order lines** FastTab toolbar, select **Inventory** \> **Maintain** \> **Marking**.
1. The **Marking** dialog opens, showing the marked quantities. <!--KFM: What am I looking at and what can I do here? -->

To view markings for a specific inventory transaction, follow these steps: <!--KFM: I wasn't sure where what **Inventory transactions** page you were referring to. I found the following one. Please confirm this is what you meant.  -->

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Open the sales order that you want to check.
1. On the **Sales order lines** FastTab, select the line you want to view transactions for.
1. On the **Sales order lines** FastTab toolbar, select **Inventory** \> **View** \> **Transactions**.
1. The **Inventory transactions** page opens. Select the transaction you want to inspect.
1. On the Action Pane, open the **Inventory** tab and, from the **View** group, select **Marking**.
1. The **Marking** dialog opens, showing the marked quantities. <!--KFM: What am I looking at and what can I do here? -->

To view markings from a transfer order line, follow these steps:

1. Go to one of the following pages: <!--KFM: Which should I pick? Is there any difference at all? -->
    - **Inventory management** \> **Inbound orders** \> **Transfer order**.
    - **Inventory management** \> **Outbound orders** \> **Transfer order**.
1. Open the transfer order that you want to check.
1. On the **Transfer order lines** FastTab, select the line you want to view the related sales order for.
1. From the **Transfer order lines** FastTab toolbar, select **Inventory** \> **Transactions**.
1. The **Inventory transactions** page opens. Select the transaction you want to inspect.
1. On the Action Pane, open the **Inventory** tab and, from the **View** group, select **Marking**.
1. The **Marking** dialog opens, showing the marked quantities. <!--KFM: What am I looking at and what can I do here? -->
