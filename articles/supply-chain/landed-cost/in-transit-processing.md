---
# required metadata

title: In-transit processing
description: This topic describes how to work with in-transit orders, which are a type of order only used by the Landed cost module. When an order or voyage is set to use goods in transit processing, items can be invoiced before the goods have been received into the warehouse for consumption.
author: RichardLuan
manager: tfehr
ms.date: 01/13/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ITMContainerActivityTable
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: riluan
ms.search.validFrom: 2021-01-13
ms.dyn365.ops.version: Release 10.0.17
---

# In-transit processing

[!include [banner](../includes/banner.md)]

This topic describes how to work with in-transit orders, which are a type of order only used by the Landed cost module. When an order or voyage is set to use goods in transit processing, you don't need to wait for goods to be received into the warehouse before you can invoice them. Instead, the goods are invoiced at the time they leave the vendor's warehouse or port of origin and the financial costs are recognized at the time the voyage begins. This lets you take ownership of inventory correctly, as goods are often the property of your organization from the time they leave the shipping port. With goods in transit orders, the financially updated items are received into an in-transit warehouse. The goods will stay in this warehouse until they can be received at the final destination warehouse, and can't be removed manually.

As long as the items are in transit, they are not available in inventory and can't be picked from inventory for a delivery. However, you can view the goods in transit inventory and can those goods for master planning, using the confirmed delivery date on the purchase order line as the expected date the inventory will be available for consumption.

The following subsections describe the setup required to process inventory and voyages using the goods in transit concept and functionality.

## Terms of delivery

When you enable the Landed cost module, the standard *terms of delivery* entity is enhanced to support the goods in transit feature.

When **Goods in transit management** option is set to *Yes* for the applicable terms of delivery record, the goods are placed into the in-transit warehouse. This is only triggered when an invoice is processed without the inventory receipt being processed first. When an order has the delivery terms set to use goods in transit, users can no longer post a product receipt for the purchase order. If they try, an error will show stating that they must use the goods in transit functionality to proceed.

To work with delivery terms information for goods in transit, go to **Procurement and Sourcing \> Setup \> Distribution \> Terms of delivery**. The following table describes the settings that the Landed cost module adds to the **Terms of delivery** page to support the goods in transit functionality. Both settings are on the **General** FastTab. For more information about the other settings on this page, see [Terms of delivery (form)](https://technet.microsoft.com/library/aa575567.aspx).

| **Field** | **Description** |
| --- | --- |
| **Shipping port mandatory** | Set to *Yes* if a shipping port is mandatory where these delivery terms apply. |
| **Goods in transit management** | Set to *Yes* to use in-transit management where these delivery terms apply. |

## Warehouses for goods in transit and under delivery

When you enable the Landed cost module, the standard *warehouses* entity is enhanced to allows purchase orders to be invoiced while the goods are placed in an interim warehouse (or goods in transit warehouse).

The Landed cost module also adds a warehouse type called *goods in transit* to  warehouse setup. Your goods in transit warehouse will have this warehouse type associated with it and will be used as the warehouse for processing goods in transit orders before they are received at the final destination warehouse, which is the warehouse defined on the purchase line.

Generally speaking, one goods in transit warehouse is sufficient for each site if site and warehouse are the two inventory dimensions used for inventory management. If location is used, a goods in transit warehouse must be set up for each site/warehouse combination so that the default location can also be specified.

Two new types of warehouses have been added: *goods in transit* and *under-delivery*. These warehouses can then be selected as *default* warehouses. To successfully process goods in transit orders, both the goods in transit warehouse and the under-delivery warehouse must be configured on the **Warehouses** page. Then, for each default warehouse that will be used with Landed cost and goods in transit, the goods in transit warehouse and under-delivery warehouse must be selected from the drop-down menu of the available warehouses of each type.

To work with goods in transit settings for your warehouses, go to **Inventory Management \> Setup \> Inventory Breakdown \> Warehouses**. The following table describes the settings that the Landed cost module adds to the **Warehouses** page to support the goods in transit functionality. Both settings are on the **General** FastTab. For more information about the other settings on this page, see [Warehouses (form)](https://technet.microsoft.com/library/aa620570.aspx).

| **Field** | **Description** |
| --- | --- |
| **Goods in transit warehouse** | Identify the goods in transit warehouse that relates to the main warehouse |
| **Under delivery warehouse** | Identify the under-delivery warehouse that relates to the main warehouse |

## Posting rules for landed cost

Landed cost adds two new posting rules that you can configure. These posting rules are used to post the direct purchase order invoice amounts financially to identify ownership of the goods at the time the goods leave the point of origin. This process will replace the concept of *goods received not invoiced* because the goods are invoiced before they are received. <!-- KFM: Add a link to the related scenario when available. -->

To work with posting profiles, go to **Inventory Management \> Setup \> Posting \> Posting**. Then open the **Purchase Order** tab. The following new posting rules are now available here:

- **Landed cost, goods in transit** - Specify the posting rules for goods in transit management.
- **Landed cost, cost charge accrual** - Specify the posting rules for charge account accrual.

## Goods in transit orders

You can review and manage goods in transit orders directly within the Landed cost module. You can choose to process goods in transit orders directly from the **Goods in transit orders** page, or to process them by going to the voyage associated with the goods in transit orders and processing the voyage, shipping container, or folio as a whole. When you invoice a voyage and create goods in transit orders, a new goods in transit order is created for each inventory and inventory dimension combination associated with the purchase order line.

To manage goods in transit, Landed cost follows a two-step procedure:

1. An item is received when a stock invoice is processed and assigned a status of *in transit*.
1. The in-transit order is processed on the **Goods in transit orders** page and then received into the warehouse specified on the purchase order, which changes the status to *received*.

To work with goods in transit orders, go to **Landed cost \> Periodic tasks \> Goods in transit orders**.

## Receiving stock from the in-transit warehouse

You can receiving goods from an in-transit order in many ways, depending on how you have set up your system.

### Receive in-transit

You can receive in-transit from any of the following pages:

- On the **Goods in transit orders** page, select the line, and select **Receive** on the Action Pane.
- On the **All voyages** page, select or open a voyage. On the Action Pane, open the **Manage** tab and, from the **Goods in transit** group, select **Receive goods in transit**.
- On the **All shipping containers** page, select or open a shipping container. On the Action Pane, open the **Manage** tab and, from the **Goods in transit** group, select **Receive goods in transit**.
- On the **All folios** page, select or open a folio. On the Action Pane, open the **Manage** tab and, from the **Goods in transit** group, select **Receive goods in transit**.

> [!NOTE]
> Receive in-transit is generally used without using locations and batch/serial tracking.

### Arrival journal

Goods can additionally be received by creating an arrival journal. You can navigate to the arrival journal creation directly from the voyages form. Whether the arrival journal is used for receiving stock depends on the best practices established by your organization.

1. Open the voyage, container, or folio.
1. On the Action Pane, open the **Manage** tab and, from the **Functions** group, select **Create arrival journal**.
1. The **Create arrival journal** dialog box opens. Make the following settings:

    - **Initialize quantity** - Set to *Yes* to set the quantity from the in-transit quantity. If this is set to *No*, no default quantity is set from the goods in transit lines.
    - **Create from goods in transit** - Set to *Yes* to take quantities from the selected in-transit lines for the selected voyage, container, or folio.
    - **Create from order lines** - Set this to *Yes* to set the default quantity on the arrival journal from the purchase order lines. You can do this provided there are no differences between the purchase order line and the goods in transit order quantity.

1. Process the arrival journal as described in [Register item receipts with an item arrival journal](https://technet.microsoft.com/library/aa571129.aspx).

> [!NOTE]
> The arrival journal is generally used in situations where locations and batch/serial tracking are used but warehouse management isn't used.

> [!NOTE]
> Default receipt locations shouldn't be specified on the order lines if a putaway location is to be specified on the arrival journal.

## Warehouse management

When you enable the Landed cost module, several pages from the Warehouse management module are modified to be able to process orders through the Landed cost module, and more specifically goods in transit processing. This section outlines the new and added fields and processes within the Warehouse management module.

### Mobile device menu items

Goods can be received using a mobile device provided the mobile device menu and Warehouse management module have been set up to receive goods in a transit order. The setup associated with goods in transit receiving is outlined below.

To set up mobile devices for goods in transit processing, go to **Warehouse Management \> Setup \> Mobile device \> Mobile device menu items**.

Landed cost adds following work creation processes to the mobile device menu items to support in-transit processing:

- Goods in transit item receiving
- Goods in transit item receiving and putaway

The configuration settings for each of these are similar to those for the [purchase order receive and putaway work creation processes](https://technet.microsoft.com/library/dn553216.aspx). However, the *Goods in transit item receiving and putaway* process also adds the following setting:

- **Enable shipping container complete** – When set to *Yes*, at completion of the putaway work, the warehouse app will provide an additional option called **Shipping container complete**. When selected, the worker will be asked to confirm that the container is complete. At this point, all short receipts will be processed as an under transaction.

### Location directives

Landed cost adds a new **Work order type** called *Goods in transit* to the **Location directives** page, which should be configured in the same manner as the [purchase order work order types](https://technet.microsoft.com/library/dn553184.aspx).

### Work templates

Landed cost adds a new **Work order type** called *Goods in transit* to the **Work templates** page, which should be configured in the same manner as the [purchase order work templates](https://technet.microsoft.com/library/dn553184.aspx).