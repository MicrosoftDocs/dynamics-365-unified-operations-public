---
title: Create purchase orders from sales orders
description: Learn how to create a purchase order that is based on a sales order and set up related options. 
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, PurchCreateFromSalesOrder, VendAccountItemLookup, SalesTableReferences, PurchTable, PurchTablePart
ms.topic: how-to
ms.date: 12/03/2025
ms.custom: 
  - bap-template
---

# Create purchase orders from sales orders

[!include [banner](../../includes/banner.md)]

## Set options for how delivery mode and terms of delivery are set for purchase orders created from sales orders

You can configure the way that the system copies and synchronizes the delivery mode and terms of delivery between purchase orders created from sales orders and the originating sales orders. Set these options separately for sales order lines that are set up for *stocked delivery* and for sales order lines that are set up for *direct delivery*.

### Prerequisites

To use the options for delivery mode and terms of delivery described in this section, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.
- The feature that is named *Enable purch parameters to control delivery information sync on sales and purchase orders* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

> [!NOTE]
> When you turn on the *Enable purch parameters to control delivery information sync on sales and purchase orders* feature, its default settings match the behavior that was in place before the feature was introduced.

### Configure options for delivery mode and terms of delivery

To configure how the delivery mode and terms of delivery are set for purchase orders that you create from sales orders in various scenarios, follow these steps:

1. Go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing parameters**.
1. Open the **Delivery** tab.
1. On the **Synchronization of mode and terms of delivery** FastTab, make the following settings in the **For delivery type stock** field group. These settings apply to purchase orders that you create from *stocked delivery* sales order lines.
    - **Synchronize on creation** – Controls how the delivery mode and terms of delivery are set on purchase orders that you create from *stocked delivery* sales order lines. Choose one of the following options:
        - *No* – The system sets the delivery mode and terms of delivery for the *purchase order header and lines* to match the *vendor settings*.
        - *Yes* – The system sets the delivery mode and terms of delivery for the *purchase order header* from the *sales order header*. The system sets the delivery mode and terms of delivery for the *purchase order line* from the *sales order line*.
    - **Synchronize on update** – Controls whether the system synchronizes purchase orders that you create from *stocked delivery* sales order lines with the original sales order. Choose one of the following options:
        - *No* – The delivery mode and terms of delivery for the purchase order header and lines *aren't synchronized* with the original sales order. Therefore, changes you make to the purchase order don't affect the original sales order and changes you make to the original sales order don't affect the purchase order.
        - *Yes* – The delivery mode and terms of delivery for the purchase order header and lines *are synchronized* with the original sales order (in both directions). This setting only updates the *header* values when all lines on sales order are *stocked delivery*. At the *line* level, this setting applies to all *stocked delivery* sales lines (only).
    - **Copy from purchase header** – Controls whether changes you make to purchase orders that you create from *stocked delivery* sales order lines also apply to the original sales order. Unlike the **Synchronize on update** setting, this setting only applies changes in one direction—from the purchase order to the sales order. When you set **Synchronize on update** to *No*, the system sets **Copy from purchase header** to *No* and makes it read-only. When you set **Synchronize on update** to *Yes*, the **Copy from purchase header** setting takes precedence when you change the purchase order but has no effect when you change the sales order. Choose one of the following options:
        - *No* – Changes you make to the purchase order don't affect the original sales order.
        - *Yes* – Changes you make to the purchase order are also applied to the original sales order. This setting only updates the *header* values when all lines on sales order are *stocked delivery*. At the *line* level, this setting applies to all *stocked delivery* sales lines (only).

1. On the **Synchronization of mode and terms of delivery** FastTab, the **For delivery direct delivery** field group provides settings that are similar to (and named the same as) the settings provided in the **For delivery type stock** field group, except these settings apply to sales order lines that are set up for *direct delivery* instead of *stocked delivery*. Set these options as needed based on the descriptions provided in the previous step.

## Create a purchase order from a sales order

This procedure shows you how to create a purchase order that is based on a sales order. The product quantities on the purchase order are designated to fulfill the demand of the originating sales order. Fulfilling sales demand this way is an alternative to a more comprehensive and optimized method of distribution requirements planning. You can run this procedure by using demo data company *USMF* or your own data.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Select **New**.
1. In the **Customer account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. Select **OK**.
1. In the **Item number** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. If you're using USMF, you can select *D0001*.  
1. In the **Quantity** field, enter a number.
1. Select **Add line**.
1. In the **Item number** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. If you're using USMF, you can select *T0020*.  
1. In the list, select the link in the selected row.
1. In the **Quantity** field, enter a number.
1. Select **Save**.
1. On the Action Pane, select **Sales order**.
1. Select **Purchase order**. The **Create purchase order** page lists all the open sales order lines that the system copied from the sales order. You can review the order details, and if necessary, you can modify selected details such as purchase quantity and pricing terms, before you create the purchases.
1. Select the **Include all option**.
    - If you want to generate purchase orders for only a subset of the sales order lines, select these lines individually.  
    - The **Vendor account** field might or might already be populated with a vendor number. If the default vendor is set up for the product (on the associated Item coverage), then this vendor is copied to the line. Otherwise, you must enter a vendor manually. In this article, regardless of whether the **Vendor account** field already contains a value or not, the following steps instruct you to select a new vendor that's different for each line.  
1. In the **Vendor account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select the second order line.
1. In the **Vendor account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Validate**.
1. Select **OK**. The message informs you that one or more purchase orders are created. The system generates a separate purchase order for each vendor that you specified for the sales order lines. This means that if several sales order lines are to be supplied by the same vendor, a single purchase order with multiple lines is generated.  

## Review purchase orders created from sales orders

To review the purchase orders that you created from a sales order, follow these steps:

1. On the Action Pane, select **General**.
1. Select **Related orders**. The **Related orders** page lists all the orders that you created from the sales order. In this example, two purchase orders are generated for two different vendors.
1. Select the link in the **Purchase order** field. Each purchase order line is associated with the sales order line that led to the purchase. The **Product tab** in the **Line details** FastTab shows the relation to the sales order in the **Reference type**, **Reference number**, and **Reference lot** fields.  
1. Expand or collapse the **Line details** section.
1. Select the **Product** tab.
    - The **Reference lot** guarantees that the costs from the current purchase are charged on the attached sales order.  
    - You can navigate to the originating sales order by opening the link in the **Reference number** field.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
