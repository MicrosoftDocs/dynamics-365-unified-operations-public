---
# required metadata

title: Goods-in-transit processing
description: This article describes how to work with goods-in-transit orders. When an order or voyage is set up to use goods-in-transit processing, goods can be invoiced before they have been received in the warehouse for consumption.
author: Weijiesa
ms.date: 01/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DeliveryTerms, InventLocation, InventPosting, ITMGoodsInTransitOrder, ITMTableListPage, ITMTable, ITMContainersListPage, ITMContainers, ITMFolioTableListPage, ITMFolioTable, ITMGoodsInTransitOrderEditLines, SysOperationTemplateForm, WHSRFMenuItem, WHSLocDirTable, WHSWorkTemplateTable
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac

# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: weijiesa
ms.search.validFrom: 2021-01-13
ms.dyn365.ops.version: 10.0.17
---

# Goods-in-transit processing

[!include [banner](../../includes/banner.md)]

This article describes how to work with goods-in-transit orders. This type of order is used only by the **Landed cost** module. When an order or voyage is set up to use goods-in-transit processing, you don't have to wait until goods are received in the warehouse before you can invoice them. Instead, the goods are invoiced when they leave the vendor's warehouse or port of origin, and the financial costs are recognized when the voyage begins. This functionality lets you correctly take ownership of inventory, because goods often become the property of your organization when they leave the shipping port.

When goods-in-transit orders are used, the financially updated items are received in an interim warehouse that is known as a goods-in-transit warehouse. The goods then stay in this warehouse until they can be received at the final destination warehouse (that is, the warehouse that is defined on the purchase line). They can't be manually removed.

As long as the items are in transit, they aren't available in inventory and can't be picked from inventory for a delivery. However, you can view the goods-in-transit inventory. You can also use the goods for master planning. In this case, use the confirmed delivery date on the purchase order line as the expected date when the inventory will be available for consumption.

The following sections describe the setup that is required to process inventory and voyages by using the goods-in-transit concept and functionality.

## Terms of delivery

When you enable the **Landed cost** module, the standard *terms of delivery* entity is enhanced to support the goods-in-transit feature.

When the **Goods in transit management** option is set to *Yes* for the applicable terms of delivery record, the goods are put into the goods-in-transit warehouse. This action is triggered only if the inventory receipt isn't processed before an invoice is processed. When the delivery terms for an order are set to use goods in transit, users can no longer post a product receipt for the purchase order. If they try, an error occurs. The error message states that they must use the goods-in-transit functionality to proceed.

To work with delivery terms information for goods in transit, go to **Procurement and Sourcing \> Setup \> Distribution \> Terms of delivery**. The following table describes the fields that the **Landed cost** module adds to the **Terms of delivery** page to support the goods-in-transit functionality. Both fields are on the **General** FastTab. For more information about the other fields on this page, see [Terms of delivery (form)](/dynamicsax-2012//terms-of-delivery-form).

| Field | Description |
|---|---|
| Shipping port mandatory | Set this option to *Yes* if a shipping port is mandatory when the delivery terms apply. |
| Goods in transit management | Set this option to *Yes* to use goods-in-transit management when the delivery terms apply. |

## Warehouses for goods in transit and under-delivery

When you enable the **Landed cost** module, the standard *warehouses* entity is enhanced to enable purchase orders to be invoiced while the goods are in a goods-in-transit warehouse.

Landed cost adds two new types of warehouse: *goods in transit* and *under-delivery*. Warehouses of both types can be selected as default warehouses. Successful processing of goods-in-transit orders requires that both the goods-in-transit warehouse and the under-delivery warehouse be configured on the **Warehouses** page. Then, for each default warehouse that will be used with Landed cost and goods in transit, the goods-in-transit warehouse and under-delivery warehouse must be selected for the available warehouses of each type.

The *goods in transit* warehouse type will be associated with your goods-in-transit warehouse, and that warehouse will be used to process the goods on goods-in-transit orders before they are received at the final destination warehouse. In general, one goods-in-transit warehouse is enough for each site if Site and Warehouse are the only inventory dimensions that are used for inventory management. If the Location inventory dimension is also used, a goods-in-transit warehouse must be set up for each combination of a site and warehouse, so that the default location can also be specified.

To work with goods-in-transit settings for your warehouses, go to **Inventory management \> Setup \> Inventory breakdown \> Warehouses**. The following table describes the fields that the **Landed cost** module adds to the **Warehouses** page to support the goods-in-transit functionality. Both fields appear on the **General** FastTab. For information about the other fields on the page, see [Warehouses (form)](/dynamicsax-2012//warehouses-form).

| Field | Description |
|---|---|
| Goods in transit warehouse | Identify the goods-in-transit warehouse that is related to the main warehouse. |
| Under delivery warehouse | Identify the under-delivery warehouse that is related to the main warehouse. |

> [!NOTE]
> Error message "*Landed cost goods in transit warehouse and under warehouse should not use warehouse management processes. Please replace it with new warehouse if warehouse management processes parameter cannot be disabled.*" will throw out when **Goods in transit** or **Under** type warehouse try to enable **use warehouse management processes** parameter in the warehouse setting. 

## Posting rules for landed cost

Landed cost adds two new posting rules that you can configure. These posting rules are used to financially post the direct purchase order invoice amounts to identify ownership of the goods when they leave the point of origin. This process replaces the concept of *goods received not invoiced*, because the goods are invoiced before they are received.

To work with posting profiles, go to **Inventory management \> Setup \> Posting \> Posting**. On the **Purchase Order** tab, the following new posting rules are available:

- **Landed cost, goods in transit** – Specify the posting rules for goods-in-transit management.
- **Landed cost, cost charge accrual** – Specify the posting rules for charge account accrual.

## Goods-in-transit orders

You can review and manage goods-in-transit orders directly in the **Landed cost** module. You can process goods-in-transit orders directly from the **Goods in transit orders** page. Alternatively, you can go to the voyage that is associated with the goods-in-transit orders, and process the whole voyage, shipping container, or folio. When you invoice a voyage and create goods-in-transit orders, a new goods-in-transit order is created for each combination of inventory and inventory dimensions that is associated with the purchase order line.

To manage goods in transit, Landed cost uses a two-step procedure:

1. An item is received when a stock invoice is processed and assigned a status of *In transit*.
1. The goods-in-transit order is processed on the **Goods in transit orders** page and then received in the warehouse that is specified on the purchase order. At that point, the status is changed to *Received*.

To work with goods-in-transit orders, go to **Landed cost \> Periodic tasks \> Goods in transit orders**.

## Receiving stock from the goods-in-transit warehouse

You can receive goods from a goods-in-transit order in many ways, depending on the setup of your system.

### In-transit receiving

You can do in-transit receiving from any of the following pages:

- On the **Goods in transit orders** page, select the line, and then, on the Action Pane, select **Receive**.
- On the **All voyages** page, select or open a voyage. Then, on the Action Pane, on the **Manage** tab, in the **Goods in transit** group, select **Receive goods in transit**.
- On the **All shipping containers** page, select or open a shipping container. Then, on the Action Pane, on the **Manage** tab, in the **Goods in transit** group, select **Receive goods in transit**.
- On the **All folios** page, select or open a folio. Then, on the Action Pane, on the **Manage** tab, in the **Goods in transit** group, select **Receive goods in transit**.

> [!NOTE]
> In-transit receiving is generally used in situations where locations and batch/serial tracking aren't used.

### Arrival journal

You can also receive goods by creating an arrival journal. You can create an arrival journal directly from the voyage page. The best practices that your organization has established determine whether the arrival journal is used to receive goods.

1. Open the voyage, container, or folio.
1. On the Action Pane, on the **Manage** tab, in the **Functions** group, select **Create arrival journal**.
1. In the **Create arrival journal** dialog box, set the following values:

    - **Initialize quantity** – Set this option to *Yes* to set the quantity from the in-transit quantity. If this option is set to *No*, no default quantity is set from the goods-in-transit lines.
    - **Create from goods in transit** - Set this option to *Yes* to take quantities from the selected in-transit lines for the selected voyage, container, or folio.
    - **Create from order lines** – Set this option to *Yes* to set the default quantity in the arrival journal from the purchase order lines. The default quantity in the arrival journal can be set in this way only if the quantity on the purchase order line matches the quantity on the goods-in-transit order.

1. Process the arrival journal as described in [Register item receipts with an item arrival journal](/dynamicsax-2012/appuser-itpro/register-item-receipts-with-an-item-arrival-journal).

> [!NOTE]
> The arrival journal is generally used in situations where locations and batch/serial tracking are used, but warehouse management isn't used.
>
> Default receipt locations should not be specified on the order lines if a putaway location will be specified in the arrival journal.

## Warehouse management

When you enable the **Landed cost** module, several pages in the **Warehouse management** module are modified so that order processing (specifically, goods-in-transit processing) can be done through the **Landed cost** module. This section outlines the fields and processes that are added in the **Warehouse management** module.

### Mobile device menu items

Goods can be received by using a mobile device, provided that the mobile device menu and **Warehouse management** module have been set up to receive goods on a goods-in-transit order. This section describes the setup that is associated with goods-in-transit receiving.

To set up mobile devices for goods-in-transit processing, go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.

Landed cost adds the following work creation processes to the mobile device menu items to support goods-in-transit processing:

- Goods in transit item receiving
- Goods in transit item receiving and putaway

The configuration settings for these processes resemble the settings for the [purchase order receive and putaway work creation processes](/dynamicsax-2012/appuser-itpro/configure-mobile-devices-for-warehouse-work). However, the *Goods in transit item receiving and putaway* process also adds the following field.

- **Enable shipping container complete** – If this option is set to *Yes*, when the putaway work is completed, the Warehouse Management mobile app will provide an additional option that is named **Shipping container complete**. When that option is selected, the worker will be asked to confirm that the container is complete. At that point, all short receipts will be processed as an under transaction.

####  <a name="specify-GIT-order"></a> Specify goods in transit order when receiving via mobile device
This feature empowers users to manually determine the receiving of specific goods in transit order when multiple orders are associated with the same voyage, container, item number, and purchase order number. Users can effortlessly achieve this by inputting the Voyage, Container,Item and Order number, and subsequently selecting the desired Goods in Transit order from a dropdown list available in the 'Goods in transit number' field on their mobile devices.

![image](https://github.com/MicrosoftDocs/Dynamics-365-Operations/assets/102585421/4b0bd332-6442-4092-af1e-a11af7983229)

This functionality is available in two mobile device menu items:
- Goods in transit item receiving
- Goods in transit item receiving and putaway

Both options provide flexibility and control over the selection of goods in transit orders, ensuring accurate and efficient handling of incoming inventory.

#### Assign batch/serial number when receiving via mobile device
When receiving goods in transit order with batch/serial tracking enable items, user can assign batch/serial number during the receiving process. In the meanwhile,the mobile device GIT receiving process allow user define the goods quantity per batch/serial number being received.
System will conslidate the received quantity per batch/serial number into one work for process. The batch/serial number will be assigned to the received item automatically.

> [!NOTE]
> The under delivery receive scenario is not supported as user cannot specify batch/serial number manually due to the entrie under dlivery process is automatical without user interaction.

### Location directives

Landed cost adds a new work order type that is named *Goods in transit* to the **Location directives** page. This work order type should be configured in the same manner as the [purchase order work order types](/dynamicsax-2012/appuser-itpro/create-a-work-template).

### Work templates

This section describes features that the **Landed cost** module adds to work templates.

#### Goods in transit work order type

Landed cost adds a new work order type that is named *Goods in transit* to the **Work templates** page. This work order type should be configured in the same manner as the [purchase order work templates](/dynamicsax-2012/appuser-itpro/create-a-work-template).

#### Work header breaks

Work templates that have a work order type of *Goods in transit* can be configured to split work headers. On the **Work templates** page, follow one of these steps:

- On the **General** tab for the template, set work header maximums. These maximums work in the same way that they work for purchase order work templates. (For more information, see [purchase order work templates](/dynamicsax-2012/appuser-itpro/create-a-work-template).)
- Use the **Work header breaks** button to define when the system should create new work headers, based on fields that are used for sorting. For example, to create a work header for each container ID, select **Edit query** on the Action Pane, and then add the **Container ID** field to the **Sorting** tab of the query editor. Fields that are added to the **Sorting** tab are available for selection as *grouping fields*. To set up grouping fields, select **Work header breaks** on the Action Pane, and then, for each field that you want to use as a grouping field, select the checkbox in the **Group by this field** column.

Landed cost [creates an over transaction](over-under-transactions.md) if the registered quantity exceeds the original order quantity. When a work header is completed, the system updates the status of the inventory transactions for the principal order quantity. However, it first updates the quantity that is linked to the over transaction after the principal is completely purchased.

If you cancel a work header for an over transaction that has already been registered, the over transaction is first reduced by the canceled quantity. After the over transaction is reduced to a quantity of 0 (zero), the record is removed, and any additional quantities are unregistered against the principal order quantity.
