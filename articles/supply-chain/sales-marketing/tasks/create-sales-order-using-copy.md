---
title: Create sales orders using Copy `From all` 
description: Learn how to create a sales order, using Copy | 'From all'  and 'From journal'
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, InventDimParmFixed, InventProductDimensionLookup, SalesTotals, SalesTableDelete, SalesTableListPagePreviewPage, SalesUpdateRemain
---

# Create Sales Order using Copy from All

[!include [banner](../../includes/banner.md)]

The "Copy from All" feature in Dynamics 365 Sales Order allows users to copy lines from one sales order to another. This feature is particularly useful for creating similar orders without manually re-entering all the details. 
You can use the procedure in demo data company USMF. Sales orders are typically created by a sales order processor.

## Enter sales order header details

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
2. Select **Sales order**.
3. Select Copy | From all 
4. Identify and select the sales order from which you want to copy lines.
5. Select the sales order lines.
6. Select **OK**.
---

#### **Parameters:**

1. **Copy Precisely**
   - **Description:** This parameter determines whether the copied lines should be an exact copy of the selected lines, including all order information such as GST, ledger accounts, and dimensions.
   - **Usage:** Enable this option if you want the copied lines to retain all the original details without any modifications.

2. **Recalculate Price**
   - **Description:** This parameter specifies whether the net amount of the copied lines should be recalculated based on current prices and trade agreements.
   - **Usage:** Enable this option if you want the prices of the copied lines to be updated according to the latest pricing rules and agreements.

3. **Copy Charges**
   - **Description:** This parameter determines whether order line charges should be copied. If the "Copy order header" option is also selected, order header charges will be copied as well.
   - **Usage:** Enable this option if you want to include any additional charges from the original order lines in the copied lines.

4. **Delete Order Lines**
   - **Description:** This parameter specifies whether previously entered order lines for the current order should be deleted before copying the new lines.
   - **Usage:** Enable this option if you want to replace the existing order lines with the copied lines.

5. **Copy Order Header**
   - **Description:** This parameter determines whether information from the selected order header should be copied to the current order.
   - **Usage:** Enable this option if you want to include header information such as customer details, delivery terms, and payment terms from the original order.

6. **Invert Sign**
   - **Description:** This parameter specifies whether the sign of the copied lines for the order quantity should be reversed in relation to the sign of the selected lines.
   - **Usage:** Enable this option if you want to create a return order or a negative quantity order by reversing the sign of the copied lines.

---



> [!TIP]
> For procedure that shows the standard sales order creation, see [Create Sales order](create-sales-orders.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
