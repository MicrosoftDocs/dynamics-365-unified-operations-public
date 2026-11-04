---
title: Set up a location directive for purchase order putaway
description: Learn how to set up a location directive that determines where warehouse workers put items that have been received against a purchase order.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSLocDirTable
ms.topic: how-to
ms.date: 10/30/2026
ms.custom:
  - bap-template
---

# Set up a location directive for purchase order putaway

[!INCLUDE [banner](../../includes/banner.md)]

This article provides an example of how to set up a location directive that determines where received items are put away.

A location directive is a rule that finds a location. When a worker registers a receipt against a purchase order, the work template creates the putaway work, but it doesn't decide where the items go. The location directive that matches the work makes that decision. Location directives consist of a header, one or more lines, and one or more actions for each line. The header controls when the directive applies, the lines set quantity conditions, and the actions find the location.

The example in this article creates a single directive that puts received items away in one warehouse. For a full description of every field on the **Location directives** page, learn more in [Work with location directives](../create-location-directive.md).

This procedure is intended for the warehouse manager.

## Prerequisites

Before you begin, set up warehouse management processes for the warehouse and items that you want to use. Learn more in [Configure locations in a WMS-enabled warehouse](configure-locations-wms-enabled-warehouse.md).

Optionally, create a disposition code. Disposition codes aren't required, but they let you send received items to different locations based on what the worker selects during registration. (In the standard demo data, *Relabel* is one of the available disposition codes.)

## Create a location directive header

The header determines when the directive is used.

1. Go to **Warehouse management** > **Setup** > **Location directives**.
1. In the **Work order type** field, select *Purchase orders*.
1. On the Action Pane, select **New**.
1. In the **Sequence number** field, enter a number. This number determines the order that the directives for this work order type are evaluated in. Low numbers are evaluated first, so give specific directives a low sequence number.
1. In the **Name** field, enter a descriptive name that identifies the purpose of the directive.
1. In the **Work type** field, select *Put*. Purchase order putaway finds a location to place received items in, so *Put* is the applicable work type. The field isn't filtered by work order type, so other values appear even though they aren't relevant here.
1. Leave the **Directive code** field blank. The next section explains why.
1. Leave the **Locate by** field set to *Item*. This field controls whether the directive evaluates the putaway quantity item by item or as a whole license plate. It also restricts the directive to a particular kind of receipt. The following options are available for purchase orders:

    - *Item* – The directive is evaluated line by line, and the quantity range on the **Lines** FastTab determines which line applies. This option is the one that's used in the example later in this article.
    - *ASN* – The directive is used only when the license plate that is being put away was received against an advance shipping notice (ASN). The whole quantity on the license plate is evaluated together, so the system doesn't suggest splitting the contents across several locations. Learn more in [License plate receiving via the Warehouse Management mobile app](../warehousing-mobile-device-app-license-plate-receiving.md).
    - *Mixed license plate* – The directive is used only when several items were registered to a single license plate at the receiving dock. As with *ASN*, the license plate is kept together. Learn more in [Mixed license plate receiving](../mixed-license-plate-receiving.md).
    - *Cluster* – The directive is used for putaway cluster work, where a worker collects several license plates in one trip and then puts them away in different locations. Learn more in [Putaway clusters](../putaway-clusters.md).

    Because the quantity comes from the license plate when you select *ASN* or *Mixed license plate*, the **From quantity**, **To quantity**, and **Unit** fields on the **Lines** FastTab aren't editable for those two options. Those fields are editable for *Item* and *Cluster*.

    The options that you can select depend on the work order type. For example, *Mixed license plate* is available only for purchase orders and inbound shipment orders.

1. On the **Warehouse selection** FastTab, in the **Warehouse selection** field, select *Warehouse*. Then select the **Site** and **Warehouse** that the directive applies to. If you select the warehouse first, the site is filled in automatically.
1. Optional: In the **Disposition code** field, select a disposition code. The directive is then used only when a worker selects that disposition code while registering the item. If you use disposition codes, also check the **Applicable disposition code** field. If it's set to *Exact match* while **Disposition code** is blank, the directive is considered only for blank disposition codes.
1. Select **Save**.

The **Scope** field controls whether the directive applies to single items, multiple items, or both, and it also determines whether you can edit the query. It's worth understanding before you build a full set of directives. Learn more in [Work with location directives](../create-location-directive.md).

## Why the Directive code field stays blank

A directive code links a specific work template line to a specific location directive. When a work template line has a directive code, the system finds the location directive by that code instead of by sequence number.

For purchase orders, the location of the *last* put line is resolved before the work template is selected. As a result, the last put line of a purchase order work template can't carry a directive code, so there's nothing to link this directive to. Instead, the directive is matched by work order type, work type, and warehouse. Learn more in [Set up a work template for purchase orders](set-up-work-template-purchase-orders.md).

## Add a directive line

Lines set the quantity conditions that determine which actions are applied. A simple directive needs only one line that covers the full range of quantities.

1. On the **Lines** FastTab toolbar, select **New**.
1. In the **From quantity** and **To quantity** fields, enter the range of quantities that the line applies to.
1. Optional: In the **Unit** field, select the unit of measure that the quantity range is expressed in. If you leave this field blank, the inventory unit of the item is used.
1. In the **Locate quantity** field, select the quantity that should be compared against the range. For purchase order putaway, this value determines whether the license plate quantity, the transaction quantity, the quantity that remains to be received, or the full purchase order line quantity is evaluated. Learn more in [Work with location directives](../create-location-directive.md).
1. Optional: Select the **Restrict by unit** check box if the line should apply only to specific units of measure, such as pallets. After you select the check box and save, select **Restrict by unit** on the toolbar to specify the units. Learn more in [Work with location directives](../create-location-directive.md).
1. Optional: Select the **Allow split** check box to let the directive spread the quantity across several locations. Leave it cleared if the whole quantity must go to a single location.
1. On the Action Pane, select **Save**.

## Add a location directive action

Actions find a location. Each line can have several actions. The system evaluates them in sequence until one succeeds.

1. On the **Location directive actions** FastTab toolbar, select **New**.
1. In the **Name** field, enter a descriptive name for the action.
1. In the **Fixed location usage** field, select whether the action considers all locations, only fixed locations for the product, or only fixed locations for the product variant.
1. In the **Strategy** field, select a strategy. The following strategies apply to put actions:

    - *None* – No strategy is used. The first location that matches the query is selected.
    - *Consolidate* – The system places the items where similar items are already stored, which makes later picking more efficient.
    - *Consolidate including incoming work* – Works like *Consolidate*, but also considers locations that have incoming put work for the item. This strategy is useful when you receive several license plates of the same item, such as during advance shipping notice (ASN) receiving.
    - *Empty location with no incoming work* – The system places the items in the first location that has no physical inventory and no expected incoming work.

1. On the Action Pane, select **Save**.

A common setup is two actions: a first action that uses *Consolidate*, and a second action that uses *Empty location with no incoming work* for when consolidation isn't possible. If no action finds a location, the **Location directive failures** page determines whether the system still creates work or the work creation fails.

## Refine the query for the action

The query narrows the locations that an action can choose from. The following steps show an example of how to limit the action to locations that have a specific location profile.

1. Select the action, and then select **Edit query** on the Action Pane.
1. On the **Range** tab toolbar, select **Add**.
1. In the **Field** column of the new row, select **Location profile ID**.
1. In the **Criteria** column, select the location profile that identifies your storage locations.
1. Select **OK**.

Continue to add lines and actions until you cover the putaway scenarios in your warehouse.

## Related information

- [Work with location directives](../create-location-directive.md)
- [Control warehouse work by using work templates and location directives](../control-warehouse-location-directives.md)
- [Set up a work template for purchase orders](set-up-work-template-purchase-orders.md)
- [Configure locations in a WMS-enabled warehouse](configure-locations-wms-enabled-warehouse.md)
