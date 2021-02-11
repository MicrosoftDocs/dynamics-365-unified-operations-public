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

# Over/under transactions

[!include [banner](../includes/banner.md)]

When processing orders in a voyage, the system expects that the exact number of goods outlined on the purchase order lines associated with the voyage will be received into the final destination warehouse for the consumption. In reality, the exact number of items listed on the purchase order line is not always received into the warehouse. Therefore, the Landed cost module defines a set of rules on how to handle the over and under receiving of goods, particularly as the original purchase order has been invoiced and can no longer be modified. By setting up details regarding over and under transaction policies, the system will determine how to manage the over and under processing of goods at the time of receiving. You can also manage the over and under inventory manually using the **Over/under transactions** page.

## Over/under tolerances

Set over and under delivery tolerances to identify what level of over and under quantities or volumes are allowed to be processed on a voyage without error. If the voyage line receipt is outside of this tolerance, it must be modified and resolved before the voyage line can be closed for further processing.

To configure the tolerances, go to **Landed cost \> Over/under setup \> Over/under tolerances**. Here, you can view, edit, add, and remove tolerance records. The following table summarizes the settings available for each record.

| Setting | Description |
| --- | --- |
| **Account code** | <p>Set the scope of vendors to whom the tolerance applies by selecting one of the following</p><ul><li>**Table** - The over/under tolerance will only apply to the specific vendor selected for the row.</li><li>**Group** - The over/under tolerance will to all members of the tolerance group selected for the row.</li><li>**All** - The over/under tolerance will apply to all vendors.</li></ul> |
| **Account relation** | Select the vendor or vendor group for whom the over/under tolerance applies (depending on the **Account code** setting). |
| **Item code** | <p>Set the scope of items to which the tolerance applies by selecting one of the following</p><ul><li>**Table** - The over/under tolerance will only apply to the specific item selected for the row.</li><li>**Group** - The over/under tolerance will to all items in the item tolerance group selected for the row.</li><li>**All** - The over/under tolerance will apply to all items.</li></ul>|
| **Item relation** | Select the item or item group for whom the over/under tolerance applies (depending on the **Item code** setting). |
| **Amount tolerance** | Enter the amount tolerance applied to an entire purchase order. |
| **Percentage tolerance** | Enter the percentage tolerance applied to an individual purchase order line. |

## Over/Under reasons

When a voyage line is received and has an over or under quantity associated with it, you may be required to identify the reason for this over or under quantity. Do this by selecting the over/under reason on the receiving line at the time of receipt of the goods.

To set up over and under delivery reasons, go to **Landed cost \> Over/Under Setup \> Over/under reasons**. Here, you can view, edit, add, and remove the available over and under delivery reasons. The following table summarizes the settings available for each reason.

| Setting | Description |
| --- | --- |
| **Over/under reason** | Enter a unique name for the reason of the over or under receiving transaction. |
| **Description** | Enter a description of the over or under receiving reason. |
| **Movement** | Select the movement journal associated with the over/under reason. This drop-down list shows each of the available journals with the **Journal type** of *Movement* associated with it in the **Inventory journal names** page (**Inventory management Setup \> Journal names \> Inventory**). |

## Item over/under tolerance groups

Items with similar tolerances can be grouped together, which allows you set the over/under tolerance for all items in that group with just one setting.

To set up item over/under tolerance groups, go to **Landed cost \> Over/under setup \> Item over/under tolerance groups**. Here, you can view, edit, add, and remove over/under tolerance group records. The following table summarizes the settings available for each record.

| Setting | Description |
| --- | --- |
| **Over/under tolerance group** | Enter a unique name for the group. Choose a name that describes the tolerance, such as *1% Var*. |
| **Description** | Enter a description of the group. |

## Vendor over/under tolerance groups

You can group together vendors who regularly over or under deliver, and set the over/under tolerance per group.

To set up vendor over/under tolerance groups, go to **Landed cost \> Over/under setup \> Vendor over/under tolerance groups**. Here, you can view, edit, add, and remove over/under tolerance groups records. The following table summarizes the settings available for each record.

| Setting | Description |
| --- | --- |
| **Over/under groups** | Enter a unique name for the group. Choose a name that describes the type of vendors that would be part of this group. |
| **Description** | Enter a description of the group. |

## View and process over/under transactions

Over and under transactions are generated when the quantity of goods that are put away doesn't match the initialized quantity. The quantity on the arrival journal should only be updated with the put-away quantity.

When processing the receipt of voyage lines, over/under tolerances can be set for a vendor and the items will be reviewed and validated. The tolerance can be set as percent, local amount, or both.

When an item is received that is inside the tolerance, the system will generate a movement journal, which can be specified from the voyage parameters form. In addition, an over/under transaction will be created. For example, suppose you have an order value of $100 and a receive value of $99, and that this satisfies the tolerance rules. In this case, negative movement journal for the under received quantity will be created.

When an item is received that is outside of the tolerance, the system will generate an over/under transaction for the difference in quantity.

To view and process over/under transactions, go to **Landed cost \> Inquiries \> Over/under transactions**. All items in a voyage that are over or under received will have an over/under transaction associated with it on this page. We recommend that all over and under transactions associated with voyages be resolved by using the **Over/under transactions** page. We also recommend *against* manually resolving under delivery warehouse transactions using movement or counting journals. Instead, you should manage the under delivery warehouse quantities through the **Over/under transactions** page.

### The upper Overview tab

To view your over/under transactions, open the **Overview** tab in the top section of the **Over/under transactions** page. The following table describes each column displayed in the grid.

| Setting | Description |
| --- | --- |
| **Over/under transaction number** | Shows the unique name for the over/under transaction record that was created automatically during arrival journal processing. |
| **Voyage** | Shows the voyage the purchase line was attached to. |
| **Shipping container** | Shows the container the purchase line was attached to. |
| **Arrival journal** | Shows the arrival journal the over/under line was generated from. |
| **Reference** | Shows a reference to either the purchase order or transfer order associated with the over/under transaction |
| **Number** | Shows the purchase order referenced on the over/under transaction. |
| **Vendor account** | Shows the vendor that the over/under relates to. |
| **Goods in transit number** | Shows the goods in transit number, if applicable. |
| **Item number** | Shows the item number the over/under relates to. |
| **Original quantity** | Shows the original quantity of the purchase order line attached to the shipment. |
| **Received quantity** | Shows the quantity that was actually received. |
| **Difference** | Shows the difference between the expected arrival journal amount and the amount that was posted in the arrival journal. A negative value means there was an over delivery of goods. |
| **Remaining quantity** | Shows the quantity remaining on the arrival journal line. |
| **Over/under delivery** | Shows whether the quantity received is an over or under. |
| **Status** | Shows the status of the over/under transaction. Settings on the **[Landed cost parameters](landed-cost-parameters.md)** page can allow over delivery to automatically create a movement journal for the over-delivery amount and post the journal. If this happens, the over/under transaction will be in a status of *Completed*. If an action must taken to move the goods out of the Under delivery warehouse, the status of the record will be *In process*. |
| **Over/under reason** | Shows the reason associated with the over/under delivery transaction |
| Other inventory dimensions | You can choose to show columns for additional dimensions as needed, such as batch number, inventory status, warehouse, and more. On the Action Pane, select **Inventory \> Display dimensions** to open a dialog box where you can choose which dimensions to include. |

### The General tab

Open the **General** tab in the top section of the **Over/under transactions** page to see more information about the line currently selected in the upper **Overview** tab. Here you can see values for all available dimensions and other information about the line. This information is pulled from the originating purchase order.

### The lower Overview tab

Use the **Overview** tab in the bottom section to view the document type for the row selected in the upper **Overview** tab. The following table describes the columns available here.

| Column | Description |
| --- | --- |
| **New document type** | Will show either *Movement journal* or *Purchase order*, depending on the action shown on the selected over/under transaction line. |
| **Number** | Provides a reference and link to either the purchase order or movement journal associated with the selected over/under transaction line. |
| **Over/under reason** | Shows the reason associated with the selected over/under transaction line. |
| **Quantity** | Shows the quantity that you have selected for the purchase order or movement journal associated with the selected over/under transaction line. |

### The lower General tab

Open the **General** tab in the bottom section of the **Over/under transactions** page to see the **Over/under transaction number**, **Lot ID** and **Dimension number** associated with the selected over/under transaction line. 

### Process over/under transactions

The Action Pane on the **Over/under transactions** page provides the following commands for processing the transactions selected on the page. Each action enables you choose how to process each of these transactions.

- **Create \> Movement** - Create and post a movement journal for the selected transaction. For under transactions, a movement journal is created and posted automatically for the difference between the expected and actual received quantity. You would select this option for over transactions if you want the vendor to realize the cost difference.
- **Create \> Purchase order** - Creates a purchase order for the difference between the expected and actual received quantity of the selected transaction. You would select this option for over transactions if your organization will realize the cost difference.
- **Create \> Transfer to destination** - This command only applies for transfer orders. If you'd like to transfer the over or under quantity to the destination warehouse.
- **Create \> Transfer to origin** - This command only applies for transfer orders. If you'd like to transfer the over or under quantity to the origin warehouse.
