---
# required metadata

title: Over/under transactions
description: When processing orders in a voyage, the system expects that the exact number of goods outlined on the purchase order lines associated with the voyage will be received into the final destination warehouse for the consumption. In reality, the exact number of items listed on the purchase order line is not always received into the warehouse. Therefore, the Landed cost module defines a set of rules on how to handle the over and under receiving of goods.
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
<!-- KFM: Continue here -->
# Over/under transactions

[!include [banner](../includes/banner.md)]

When processing orders in a voyage, the system expects that the exact number of goods outlined on the purchase order lines associated with the voyage will be received into the final destination warehouse for the consumption. In reality, the exact number of items listed on the purchase order line is not always received into the warehouse. Therefore, the Landed cost module defines a set of rules on how to handle the over and under receiving of goods, particularly as the original purchase order has been invoiced and can no longer be modified. By setting up details regarding over and under transaction policies in Landed cost, the system will determine how to manage the over and under processing of goods at the time of receiving. You can also manage the over and under inventory manually using the **Over/under transactions** page.

## Over/under tolerances

Set over and under delivery tolerances to identify an over or under outside of this tolerance. These tolerances are used to identify what level of over and under quantities or volumes are allowed to process on a voyage without error. If the voyage line receipt is outside of this tolerance, it must be modified and resolved before the voyage line can be closed for further processing.

To configure the tolerances, go to **Landed cost \> Over/under setup \> Over/under tolerances**. Here, you can view, edit, add, and remove tolerance records. The following table summarizes the settings available for each record.

| **Field** | **Description** |
| --- | --- |
| **Account code** | Select table, group, or all. When set to table, a specific vendor is selected for the over/under tolerance. When group is selected, a tolerance group is selected for the record. When all is selected, the tolerance record holds true for all vendors. |
| **Account relation** | Select the vendor or vendor group where applicable. |
| **Item code** | Select table, group, or all. When table is selected, a specific item uses the tolerance record. When group is selected, a specific item tolerance group is used for the record. When all is selected, all items utilize this tolerance record. |
| **Item relation** | Select the item or item group where applicable. |
| **Amount tolerance** | Amount tolerance applied to an entire purchase order. |
| **Percentage tolerance** | Percentage tolerance applied to an individual purchase order line. |

## Over/Under reasons

When an voyage line is received and has an over or under quantity associated to it, it can be required to identify the reason for this over or under quantity. This is done by selecting the over/under reason on the receiving line at the time of receipt of the goods.

To set up over and under delivery reasons, go to **Landed cost \> Over/Under Setup \> Over/under reasons**. Here, you can view, edit, add, and remove the available over and under delivery reasons. The following table summarizes the settings available for each record.

| **Field** | **Description** |
| --- | --- |
| **Over/under reason** | The unique identifier of the reason for the over or under receiving transaction. |
| **Description** | The description of the over or under receiving reason. |
| **Movement** | The movement journal associated to the over/under reason. This movement journal will be selected from a drop-down of the available journals with the type of movement associated to it in the **Journals** page. |

## Item over/under tolerance groups

Items with similar value can be linked together, and the over/under tolerance set per group.

To set up item over/under tolerance groups, go to **Landed cost \> Over/under setup \> Item over/under tolerance groups**. Here, you can view, edit, add, and remove over/under tolerance group records. The following table summarizes the settings available for each record.

| **Field** | **Description** |
| --- | --- |
| **Over/under tolerance group** | The unique identifier of the over/under group associated to over and under transactions processing. This can be associated to a group of items with similar values. |
| **Description** | The description of the over/under tolerance group. |

## Vendor over/under tolerance groups

You can group together vendors who regularly over deliver, and set the over/under tolerance per group.

To set up vendor over/under tolerance groups, go to **Landed cost \> Over/under setup \> Vendor over/under tolerance groups**. Here, you can view, edit, add, and remove over/under tolerance groups records. The following table summarizes the settings available for each record.

| **Field** | **Description** |
| --- | --- |
| **Over/under groups** | The unique identifier of the over/under group associated to over and under transactions processing. This can be associated to a group of vendors who regularly process in the same way. |
| **Description** | The description of the over/under tolerance group. |

## Process over/under transactions

Over and under transactions are generated when the goods that are put away varies to the initialized quantity. The quantity on the arrival journal should just be updated with the put-away quantity.

When processing the receipt of voyage lines, over/under tolerances can be set by a vendor and item will be reviewed and validated. The tolerance can be set either as both % and local amount.

When an item is received that is inside the tolerance, Dynamics 365 Finance and Operations, Enterprise Edition will generate a movement journal which can be specified from the voyage parameters form. In addition, an over/under transaction will be created. i.e. Assume an order value of $100 and a receive value of $99 which means that it meets the tolerance rules. A negative movement journal for the under received will be created.

When an item is received that is outside of the tolerance, Dynamics 365 Finance and Operations, Enterprise Edition will generate an over/under transaction for the difference in quantity.

To process over/under transactions, go to **Landed cost \> Inquiries \> Over/under transactions**. The process of managing transactions for over and under are outlined in the Scenarios document.

All items in a voyage that are over or under received will have an over/under transaction associated to it on this page. We recommend that all over and under transactions associated to voyages be resolved by using the **Over/under transactions** page. We also recommend _against_ manually resolving under delivery warehouse transactions using movement or counting journals. Rather, the under delivery warehouse quantities should be managed through the **Over/under transactions** page.

To view your over/under transactions, open the **Overview** tab in the top section of the **Over/under transactions** page.

| **Field** | **Description** |
| --- | --- |
| **Over/under transaction number** | The unique identifier associated to the over/under transaction record that is created automatically during arrival journal processing. |
| **Voyage** | The voyage the purchase line was attached to is shown. |
| **Shipping container** | The container the purchase line was attached to is shown. |
| **Arrival journal** | The arrival journal the over/under line was generated from. |
| **Reference** | The reference to either the purchase order or transfer order associated to the over/under transaction |
| **Number** | The Goods in transit order number associated to the record. |
| **Purchase order** | The purchase order is also referenced on the over/under transaction. |
| **Vendor account** | The vendor that the over/under relates to is shown here. |
| **Goods in transit number** | The goods in transit number if applicable is shown here. |
| **Item number** | The Item number the O/U relates to. |
| **Warehouse** | The warehouse the original purchase order was created to deliver to. |
| **Original quantity** | The original quantity of the purchase order line attached to the shipment is shown here. |
| **Received quantity** | The quantity that was actually received. |
| **Difference** | The difference between the expected arrival journal amount and the amount that posted in the arrival journal. A negative value means there was an over delivery of goods. |
| **Remaining quantity** | The quantity remaining on the arrival journal line. |
| **Over/under delivery** | Displays whether the quantity received is an over or under. |
| **Status** | The status of the over/under transaction. Parameters in the Module Maple parameters form can allow over delivery to automatically create a movement journal for the over-delivery amount and post the journal. If this happens, the over/under transaction will be in a status of &#39;completed&#39;. If an action must taken to move the goods out of the Under delivery warehouse, the status of the record will be &#39;in process&#39;. |
| **Over/under reason** | The reason associated to the over/under delivery transaction |