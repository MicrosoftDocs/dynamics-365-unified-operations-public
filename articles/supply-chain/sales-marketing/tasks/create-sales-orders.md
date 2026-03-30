---
title: Create sales orders
description: Learn how to create a sales order, including outlines and step-by-step processes for entering sales order header details and entering sales order line details.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: how-to
ms.date: 10/24/2025
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, InventDimParmFixed, InventProductDimensionLookup, SalesTotals, SalesTableDelete, SalesTableListPagePreviewPage, SalesUpdateRemain
---

# Create sales orders

[!include [banner](../../includes/banner.md)]

This article describes how to create a sales order. You can use the step-by-step process in demo data company *USMF*. Typically, a sales order processor creates sales orders.

You can create a new sales order either from the **All sales orders** page or directly from the **Sales and marketing** module in the navigator. The second option offers a quicker way to create sales orders without opening the **All sales orders** page. This article describes both methods.

## Enter sales order header details

1. Open the **Create sales order** dialog by doing one of the following steps:
    - Go to **Sales and marketing** \> **Sales orders** \> **Create sales order**.
    - Go to **Sales and marketing** \> **Sales orders** \> **All sales orders** and, on the Action Pane, select **New**.

1. In the **Customer account** field, select the customer you want to create a sales order for. If you're working with *USMF* demo data, select customer *US-004*.
1. Select **OK**.

## Enter sales order line details

The products your organization sells might come in variants differentiated by dimensions, such as configuration, color, size, and style. Also, you might set up products to use storage dimensions, such as site, warehouse, and pallet, and tracking dimensions, such as batch and serial numbers. When you assign these dimensions, you must select the values for those dimensions on the order line. To improve order entry efficiency, consider adding the respective dimension fields to the order grid.

1. Under the **Sales order lines** section, select the **Sales order line**.
1. Select **Dimensions**.

    If you're working with *USMF* demo data, select the *Color*, *Site*, and *Warehouse* dimensions. The dimensions you select here appear in the sales order grid. To save your selections, set the **Save setup** option to *Yes*.

1. Select **OK**.
1. In the **Item number** field, select the drop-down button to open the lookup. If you're working with *USMF* demo data, select item number *T0004*.

    - If the item is part of a sales category, the item name automatically appears in the Sales category field.
    - If product dimension fields already contain a value, the value was copied from the product record where it's defined as a default product dimension. You can change the default value at any time.

1. In the **Color** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the **Quantity** field, enter a number.

    - If you sell the item in different units than when you purchase, produce, and store it, and you set a sales unit of measure on the product record, this value appears in the **Unit** field. You can change the value at any time.
    - If the **Site** field already contains a value, the value was copied from the order header or from the order settings that are associated with the product. You can change the value at any time. If the field is empty, select a value.
    - If the **Unit price** field already contains a value, the value was copied from a valid trade agreement, or from the product record. (The unit price can also come from a sales agreement, but the process for creating sales orders from sales agreements is different from the one shown here.) If the field is empty, enter a value.
    - The **Discount** field contains a discount amount per product unit. To calculate the total line discount amount, the discount value is multiplied by line quantity. If the **Discount** field already contains a value, the value was copied from a valid trade agreement. If the field is empty, and you want to give the customer a line discount, enter a value.
    - The **Discount percent** field contains a percentage value by which the total line gross amount is reduced. If the **Discount percent** field already contains a value, it was copied from a valid trade agreement. If the field is empty, and you want to give the customer a line discount, enter a value.
    - The **Net** amount field contains a value that's calculated based on the line's quantity and unit price adjusted by discounts. You can override the calculated value to a different one.

## Review the order totals

1. On the Action Pane, select **Sales order**.
1. Select **Totals**.

    The **Totals** dialog box displays details about the entire order. This information includes the subtotal amount, which is a sum of all line net amounts adjusted for any line discounts, the total invoice amount, which is a subtotal amount adjusted for any order-level discount, charges, and sales tax, the customer credit limit situation, and more. The invoice amount is the amount that appears on the customer's invoice document.

1. Select **OK**.

> [!TIP]
> For examples that show how sales totals and discounts are calculated when prices include and exclude sales tax, including information about how related values are shown in the **Totals** dialog box, see [Calculate sales totals when prices include sales tax](../sales-tax-calculation.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
