---
# required metadata

title: BOM calculations groups
description: This article provides information about calculation groups for bills of materials (BOMs) and how to set them up. To run a BOM calculation, you must either set up calculation groups and assign them to individual items, or set a default calculation group. The calculation settings from the calculation group are then used as default values on the BOM calculation page at the time of BOM calculation. 
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BOMCalcGroup, BOMCalcTable, BOMCalcTrans, InventItemPrice
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 63e1b7dc-c2c5-41b0-81ed-e3e02d1b39e0
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# BOM calculations groups

[!include [banner](../includes/banner.md)]

This article provides information about calculation groups for bills of materials (BOMs) and how to set them up. To run a BOM calculation, you must either set up calculation groups and assign them to individual items, or set a default calculation group. The calculation settings from the calculation group are then used as default values on the BOM calculation page at the time of BOM calculation. 

A default calculation group is required on the **Inventory and warehouse management parameters** page, or a product-specific calculation group is required on the **Released product details** page. The system first looks for the calculation group setup on the **Released product details** page. If it doesn't find a calculation group there, it looks on the **Inventory and warehouse management parameters** page. If the system can't find a calculation group, the user receives an error message during calculation. A calculation group contains policies for the cost price model, the sales price model, and the warnings checklist. The calculation settings from the calculation group are used as default values on the **BOM calculation** page at the time of BOM calculation.

## Purposes of BOM calculation groups
You assign a BOM calculation group to items for several reasons:

-   By setting the **Cost price model** field, you indicate the source of a purchased component’s cost contribution data during the calculation of the planned cost of a manufactured item. Some manufacturers calculate planned costs by using the purchase price trade agreements for purchased components or another basis, such as the purchase price records in a costing version.
-   By setting the **Sales price model** field, you indicate how the item’s data is used to calculate a suggested sales price. You can specify either the item sales price or the cost group. Some manufacturers want to calculate a suggested sales price for manufactured items. The calculated sales price can reflect a rolled-price approach that is based on the component’s sales price record. Alternatively, the calculated sales price can reflect a cost-plus-markup approach that is based on the component’s cost and applicable profit percentage, which is associated with the item’s cost group.
-   By using the **Stop explosion** field, you indicate that a manufactured item should be treated as a purchased item for cost roll-up purposes during BOM calculation. Typical scenarios include a purchased item that is occasionally manufactured or a manufactured item that is now being purchased. The item is first designated as a manufactured item to define BOM and route information, and to support production orders for the item. However, the **Stop explosion** flag prevents cost calculations from using the item’s BOM and route. Instead, the BOM calculation uses the item’s specified costs.

## Calculation groups
You define calculation groups under **Predetermined cost policies setup** in Cost management. Calculation groups that are assigned to items let you specify how the cost or sales price of components, as outlined by the calculation group, is sourced for the calculation. On the **Calculation groups** page, you can define a cost price model, an alternative cost price model, a sales price model, and warnings.

### Cost price model

There are four options for the **Cost price model** field:

-   **Item cost price** – The cost price from the **Released product** table is used, or the combination of item dimensions is used as the cost price.
-   **Item purchase price** – The purchase price from the **Cost price** field on the **Purchase** tab of the **Released product list** page is used.
-   **Trade agreements** – You can configure trade agreements for specific combinations of items and vendors, or for specific sites. Then, when you select the **Trade agreements** option here, the trade agreement that you created for the purchase price together with the item and site will be used.
-   **Inventory price** – The current inventory value for the item is used to calculate the unit cost in the BOM calculation. A unit cost price is calculated only if the posted quantity and the physical quantity are more than 0 (zero).

### Alternative cost price

The **Alternate cost price** field has the same options as the **Cost price model** field. However, this field is used only when a price can't be found in the primary cost price model.

### Sales price model

There are two options for the calculation of the **Sales prices** field:

-   **Cost group** – When this option is selected, the sales price is calculated based on the cost price and the profit setting percentage from the cost group.
-   **Item sales price** – When this option is selected, the sales price on the **Sell** FastTab from the Released product table is used.

### Stop explosion

The **Stop explosion** check box is used to indicate when a manufactured item should be treated as a purchase item. Typically, you will leave the **Stop explosion** check box cleared. By selecting this check box, you indicate that a manufactured item must be treated as a purchase component instead of a manufactured component for the purpose of BOM calculation. Depending on the site, the item's cost can still be calculated by using BOM calculations. Explosion of planned purchase orders and production orders is stopped at the BOM whose components are associated with the calculation group that the **Stop explosion** check box is selected for. Master scheduling generates the planned orders on the BOM itself, not on the items that are included in the BOM. Basically, by selecting this check box, you specify that a cost won't be added into the BOM calculation for items that have this calculation group.

### Warnings

On the **Warnings** FastTab, you select the options for any warning messages that users should receive when they do BOM calculations. 

For example, if you select the **No BOM** check box, the user receives a warning if no active BOM version is found for one of the components or the parent item that the BOM calculation is run for. If you select the **No route** check box, the user receives a warning if no active route version is found. If you're using resources on your routes and operations, you can instruct the system to check for those resources. Then, if a resource isn't found on every line in the active route, the user receives a warning. 

You can also verify and check for consumption. Consumption is the quantity in a particular route. Typically, it represents the amount of time that is required in order to perform a specific operation for a production process. You can check whether an item has no cost price. If there is no active cost price for an item, no cost is added into the BOM calculation. 

You can also check and verify the age of the cost price. For example, enter **60** to indicate that the unit cost price must be reevaluated after 60 days. If this limit is reached, the system generates a warning. For example, a cost price was entered for an item in January of this year. If it's now August, which is more than 60 days after the cost price was entered, the user receives a warning when the BOM calculation is run. You can enter in a percentage in the **Minimum contribution margin** field. This value indicates the point at which the minimum contribution margin isn't being met. If the contribution margin for a particular component isn't met, the user receives a warning. Therefore, this field helps guarantee that you don't undercut the costs and the additional carrying costs that might be required for your items.

### Default setup in Inventory and warehouse management parameters

Because calculation groups are required in order to run calculations, you must set up a default calculation group in the Inventory management parameters. This setup enables companies to have a standard cost group and profit setting for all items. Then, if a particular item has special calculation requirements, the user can assign a different calculation group to that item. Typically, you can set calculation groups on BOM component items instead of BOM items. However, when warning messages are shown, calculation groups can be applied. A calculation group that is assigned to items overrides the default value that is set up in the Inventory management parameters. 

You can set up the default parameter at **Cost management** &gt; **Inventory accounting policies setup** &gt; **Parameters** &gt; **Inventory accounting** &gt; **Calculation group**. By setting up a default configuration group, you can also configure the warning conditions that prompt users during the BOM calculation process, if the selected components might cause calculation errors.

### View warning messages on the Complete page

A BOM calculation generates warning messages. You can view the warnings about a selected item. For example, in Sales and marketing, create a new sales order for item D0001. Then, on the sales order line, on the **Update line** menu, click **Calculate Based on BOM/Formula** to view the calculation details and warnings. You can also view BOM calculation results on the **Complete** page. For the warning messages, only two warning conditions apply to manufactured items, whereas four warning conditions apply to any item:
-   Identify when a manufactured item doesn't have an active BOM.
-   Identify when a manufactured item doesn't have an active route.
-   Identify when the item on a BOM line has a quantity of 0 (zero).
-   Identify when the item on a BOM line has a cost of 0 (zero), or when it doesn't have a cost record.
-   Identify when the item on a BOM line has an out-of-date cost. The warning reflects a comparison of the calculation date to the specified days for a maximum age of cost.
-   Identify when the item on a BOM line has a profitability percentage that is less than you want.

You can define multiple BOM calculation groups, depending on your requirements for variations in warning messages. For example, one BOM calculation group that has warning conditions about an active BOM, a component quantity of 0 (zero), and component cost of 0 (zero) might be enough. When you start a BOM calculation, you can override the warning conditions that are associated with the BOM calculation group. You can also add or remove warning conditions. For example, if the current situation doesn't involve routing data, you can remove the warning condition about an active route. **Note:** Time and attendance includes a **Calculation groups** page, but that page has no relationship to BOM calculation groups. In Time and attendance, workers can be assigned to calculation groups that reflect the grouping of workers who are associated with the same supervisor or manager. Calculation of worker registrations can be done either automatically or manually by a supervisor or manager.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]