--- 
# required metadata 
 
title: Set up a location directive for purchase order put-away
description: This article explains how to set up a simple location directive. 
author: Weijiesa
ms.date: 08/08/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSInventFixedLocation
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up a location directive for purchase order put-away

[!include [banner](../../includes/banner.md)]

This article explains how to set up a simple location directive. The example that's shown creates a location directive to be used to determine where to put items that have been received for a purchase order. You can play this task guide with the data mentioned using demo data company USMF. Pre-conditions: You need to create a disposition code. In this procedure we use a disposition code called Relabel. If you're creating a location directive in your own data, you need to have set up warehouse management processes (WMS) for your warehouse and items. This procedure is intended for the warehouse manager.

1. Go to **Warehouse management > Setup > Location directives**.
2. In the **Work order type** field, select **Purchase orders**.

## Create a location directive header
1. Select **New**.
2. In the **Sequence number** field, enter a number. This is the sequence in which the location directive is processed for the selected work type. You can also modify the sequence, if needed.  
3. In the **Name** field, type a value. This is the unique identifier for this directive.  
4. In the **Work type** field, select **Put**. Select the type of work to be performed. For directive with work order type Purchase order, **Put** is the only supported value.  
5. In the **Site** field, type a value.
6. In the **Warehouse** field, type a value. Leave the Directive code blank.  Directive codes are used to link a work order line of type Put to a specific directive. For purchase orders, the location of the last work order line of type Put is resolved before the work template is determined. Therefore it is not possible to connect the last line of a work template to a specific directive.   
7. In the **Disposition code** field, type a value. The Disposition code limits the use of the location directive, so the location directive is only used if the warehouse worker enters this specific value during registration of the item using a mobile device.  
8. Select **Save**.

## Edit the query for directive
1. Select **Edit query**. The use of this directive is already limited to be used for items registered in the warehouse that you specified, and with the disposition code that you specified. You can add other constraints using the query.  
2. Select **OK**.

## Add directive lines
1. Select **New**. This is the sequence in which the location directive lines are processed for the selected work type. You can also modify the sequence, if needed.  
2. In the **From quantity** field, enter a number. This is the lowest quantity that this directive line is valid for.  
3. In the **To quantity** field, enter a number.
4. In the **Unit** field, type a value. The unit the From quantity and To quantity is expressed in. If you leave this field blank the inventory unit from the item is used.  
5. In the **Locate quantity** field, select an option.
    - None, or license plate quantity: The quantity registered on each license plate.  
    - Unitized quantity: The entire quantity that's been registered.  
    - Remaining quantity: The quantity that is yet to be registered from the purchase order line.  
    - Expected quantity: The total quantity that is specified on the purchase order line.  
6. Check or uncheck the **Restrict by unit** checkbox. If you select this option, and specify the unit on the **Restrict by unit** page, only items with that unit of measurement can be put into the location. For example, if the unit of measurement is PL (pallets), only items in pallets can be put into the specified location.  
7. Check or uncheck the **Allow split** checkbox. This allows the directive to split the quantity across multiple locations.  
8. Select **Save**.

## Restrict the directive line to a specific unit
1. Select **Restrict by unit**. This button is only available when you press **Save** after you have selected the **Restrict by unit** check box.  
2. In the **Unit** field, type a value.
3. Close the page.

## Add a location directive action line
1. Select **New**. This is the sequence in which the location directive action lines are processed for the selected work type. You can also modify the sequence, if needed.  
2. In the **Name** field, type a value. This is the unique identifier for this directive action.  
3. In the **Fixed location usage** field, select an option.
    - Fixed and non-fixed locations: All non-fixed locations are valid as well as the product's own fixed location, within the range specified in the query.  
    - Only fixed location for the product: Fixed locations for the product are valid, and all product variants share the same set of fixed locations.  
    - Only fixed location for the product variants: Only fixed locations specified for each product variant are valid.  
4. In the **Strategy** field, select an option. Work orders of type Purchase order support the following strategies: 
    - None: the item is placed at the first location that's found.  
    - Consolidate: The item is placed in a location where similar items are already available.  
    - Empty location with no incoming work: the item is placed in the first empty location that's found. A location is considered to be empty if it has no physical inventory and no expected incoming work.  
5. Select **Save**.

## Edit the query for directive action line
1. Select **Edit query**.
2. Select **Add**.
3. In the **Field** field, type `location profile ID`. In this example, we'll restrict the possible locations using a location profile ID.  
4. In the **Criteria** field, type a value.
5. Select **OK**. You can continue to add directive lines and directive actions until you have covered all the possible scenarios in your warehouse.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]