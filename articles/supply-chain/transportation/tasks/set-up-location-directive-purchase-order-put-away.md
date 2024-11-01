---
title: Set up a location directive for purchase order putaway
description: Learn how to set up a simple location directive, including pre-conditions and a step-by-step process for creating a location directive header. 
author: lisascholz
ms.author: lisascholz
ms.topic: how-to
ms.date: 06/07/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: WHSInventFixedLocation
---

# Set up a location directive for purchase order putaway

[!include [banner](../../includes/banner.md)]

This article explains how to set up a simple location directive. The example that's shown creates a location directive to be used to determine where to put items that have been received for a purchase order.

**Pre-conditions**: You must create a disposition code. In this procedure, we use a disposition code called *Relabel*. If you're creating a location directive in your own data, you need to have set up warehouse management processes (WMS) for your warehouse and items.

This procedure is intended for the warehouse manager.

## Create a location directive header

1. Go to **Warehouse management > Setup > Location directives**.
1. In the **Work order type** field, select **Purchase orders**.
1. Select **New**.
1. In the **Sequence number** field, enter a number. This is the sequence in which the location directive is processed for the selected work type. You can also modify the sequence, if needed.  
1. In the **Name** field, type a value. This is the unique identifier for this directive.  
1. In the **Work type** field, select **Put**. Select the type of work to be performed. For directive with work order type Purchase order, **Put** is the only supported value.  
1. In the **Site** field, type a value.
1. In the **Warehouse** field, type a value. Leave the Directive code blank.  Directive codes are used to link a work order line of type Put to a specific directive. For purchase orders, the location of the last work order line of type Put is resolved before the work template is determined. Therefore it isn't possible to connect the last line of a work template to a specific directive.
1. In the **Disposition code** field, type a value. The Disposition code limits the use of the location directive, so the location directive is only used if the warehouse worker enters this specific value during registration of the item using a mobile device.  
1. Select **Save**.

## Edit the query for directive

1. Select **Edit query**. The use of this directive is already limited to items registered in the warehouse that you specified, and with the disposition code that you specified. You can add other constraints using the query.  
1. Select **OK**.

## Add directive lines

1. Select **New**. This is the sequence in which the location directive lines are processed for the selected work type. You can also modify the sequence, if needed.  
1. In the **From quantity** field, enter a number. This is the lowest quantity that this directive line is valid for.  
1. In the **To quantity** field, enter a number.
1. In the **Unit** field, type a value. The unit the From quantity and To quantity is expressed in. If you leave this field blank the inventory unit from the item is used.  
1. In the **Locate quantity** field, select an option.
    - None, or license plate quantity: The quantity registered on each license plate.  
    - Unitized quantity: The entire quantity that's been registered.  
    - Remaining quantity: The quantity that is yet to be registered from the purchase order line.  
    - Expected quantity: The total quantity that is specified on the purchase order line.  
1. Check or uncheck the **Restrict by unit** checkbox. If you select this option, and specify the unit on the **Restrict by unit** page, only items with that unit of measurement can be put into the location. For example, if the unit of measurement is PL (pallets), only items in pallets can be put into the specified location.  
1. Check or uncheck the **Allow split** checkbox. This allows the directive to split the quantity across multiple locations.  
1. Select **Save**.

## Restrict the directive line to a specific unit

1. Select **Restrict by unit**. This button is only available when you press **Save** after you have selected the **Restrict by unit** check box.  
1. In the **Unit** field, type a value.
1. Close the page.

## Add a location directive action line

1. Select **New**. This is the sequence in which the location directive action lines are processed for the selected work type. You can also modify the sequence, if needed.  
1. In the **Name** field, type a value. This is the unique identifier for this directive action.  
1. In the **Fixed location usage** field, select an option.
    - *Fixed and non-fixed locations*: All non-fixed locations, including the product's own fixed location, are valid within the range specified in the query.  
    - *Only fixed location for the product*: Fixed locations for the product are valid, and all product variants share the same set of fixed locations.  
    - *Only fixed location for the product variants*: Only fixed locations specified for each product variant are valid.  
1. In the **Strategy** field, select an option. Work orders of type *Purchase order* support the following strategies:
    - *None*: the item is placed at the first location that's found.  
    - *Consolidate*: The item is placed in a location where similar items are already available.  
    - *Empty location with no incoming work*: the item is placed in the first empty location that's found. A location is considered to be empty if it has no physical inventory and no expected incoming work.  
1. Select **Save**.

## Edit the query for directive action line

1. Select **Edit query**.
1. Select **Add**.
1. In the **Field** field, type *location profile ID*. In this example, we'll restrict the possible locations using a location profile ID.  
1. In the **Criteria** field, type a value.
1. Select **OK**. You can continue to add directive lines and directive actions until you have covered all the possible scenarios in your warehouse.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
