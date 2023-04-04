---
# required metadata

title: Over/under transactions
description: This article provides information that will help you set up the details of policies for over/under transactions, so that the system can determine how to manage the over-processing and under-processing of goods at the time of receipt.
author: Weijiesa
ms.date: 01/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ITMOverUnderTrans, ITMOverUnderToleranceTable, ITMOverUnderReasonTable, ITMOverUnderToleranceGroup
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

# Over/under transactions

[!include [banner](../../includes/banner.md)]

When the orders in a voyage are processed, the system expects the item quantity that is received in the final destination warehouse for consumption to match the quantity that is specified on the purchase order lines that are associated with the voyage. However, because the exact quantity on the purchase order lines isn't always received in the warehouse, the **Landed cost** module defines a set of rules that are used to handle over-receiving and under-receiving of goods. These rules are especially important because the original purchase order has been invoiced and can no longer be modified. By setting up the details of over/under transaction policies, you enable the system to determine how to manage the over-processing and under-processing of goods at the time of receipt. You can also manually manage over and under inventory by using the **Over/under transactions** page.

## Over/under tolerances

You set over-delivery and under-delivery tolerances to specify the over and under quantities or volumes that can be processed on a voyage without causing an error. If the voyage line receipt is outside these tolerances, it must be modified and resolved before the voyage line can be closed for further processing.

To configure the tolerances, go to **Landed cost \> Over/under setup \> Over/under tolerances**. There, you can view, edit, add, and remove tolerance records. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Account code | <p>Define the scope of vendors that the tolerance applies to by selecting one of the following values:</p><ul><li>**Table** – The over/under tolerance applies only to the vendor that is selected for the row.</li><li>**Group** – The over/under tolerance applies to all vendors in the vendor tolerance group that is selected for the row.</li><li>**All** – The over/under tolerance applies to all vendors.</li></ul> |
| Account relation | Select the vendor or vendor group that the over/under tolerance applies to, depending on the value that you selected in the **Account code** field. |
| Item code | <p>Define the scope of items that the tolerance applies to by selecting one of the following values:</p><ul><li>**Table** – The over/under tolerance applies only to the item that is selected for the row.</li><li>**Group** – The over/under tolerance applies to all items in the item tolerance group that is selected for the row.</li><li>**All** – The over/under tolerance applies to all items.</li></ul> |
| Item relation | Select the item or item group that the over/under tolerance applies to, depending on the value that you selected in the **Item code** field. |
| Amount tolerance | Enter the amount tolerance that should be applied to a whole purchase order. |
| Percentage tolerance | Enter the percentage tolerance that should be applied to an individual purchase order line. |

> [!NOTE]
> The system will first check whether the total amount of the received purchase order falls within the amount tolerance. If it does, the system will then check the percentage tolerance to manage over/under delivery scenarios.

## Over/under reasons

When an over or under quantity is associated with a voyage line that is received, you might have to identify the reason for the over or under quantity. In this case, you can select the over-delivery or under-delivery reason on the receiving line when the goods are received.

To set up over-delivery and under-delivery reasons, go to **Landed cost \> Over/under setup \> Over/under reasons**. There, you can view, edit, add, and remove the available over-delivery and-under delivery reasons. The following table describes the fields that are available for each reason.

| Field | Description |
|---|---|
| Over/under reason | Enter a unique name for the reason for the over-receiving or under-receiving transaction. |
| Description | Enter a description of the over/under reason. |
| Movement | Select the movement journal that is associated with the over/under reason. This field lists all available journals that a journal type of *Movement* is associated with on the **Inventory journal names** page (**Inventory management Setup \> Journal names \> Inventory**). |

## Item over/under tolerance groups

Items that have similar tolerances can be grouped together. In this way, you can set the over/under tolerance for all items in that group at the same time.

To set up item over/under tolerance groups, go to **Landed cost \> Over/under setup \> Item over/under tolerance groups**. There, you can view, edit, add, and remove over/under tolerance group records. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Over/under tolerance group | Enter a unique name for the group. Choose a name that describes the tolerance, such as *1% Var*. |
| Description | Enter a description of the group. |

## Vendor over/under tolerance groups

You can group together vendors that regularly over-deliver or under-deliver. You can then set the over/under tolerance per group.

To set up vendor over/under tolerance groups, go to **Landed cost \> Over/under setup \> Vendor over/under tolerance groups**. There, you can view, edit, add, and remove over/under tolerance group records. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Over/under groups | Enter a unique name for the group. Choose a name that describes the type of vendors that belong to the group. |
| Description | Enter a description of the group. |

## View and process over/under transactions

Over and under transactions are generated when the quantity of goods that is put away doesn't match the initialized quantity. The quantity in the arrival journal should be updated only with the quantity that is put away.

When the receipt of voyage lines is processed, over/under tolerances can be set for a vendor. The items will then be reviewed and validated. The tolerance can be set as a percentage, a local amount, or both.

If an item that is received is inside the tolerance, the system will generate a movement journal. This journal can be specified on the voyage parameters page. In addition, an over/under transaction will be created. For example, the order value is $100, the receipt value is $99, and these values satisfy the tolerance rules. In this case, a negative movement journal for the under-received quantity will be created.

If an item that is received is outside the tolerance, the system will generate an over/under transaction for the difference in quantity.

To view and process over/under transactions, go to **Landed cost \> Inquiries \> Over/under transactions**. There, an over/under transaction will be associated with all the items in a voyage that are over-received or under-received. We recommend that you use the **Over/under transactions** page to resolve all over/under transactions that are associated with voyages. We also recommend that you **not** use movement or counting journals to manually resolve under-delivery warehouse transactions. Instead, you should use the **Over/under transactions** page to manage the under-delivery warehouse quantities.

### Upper Overview tab

To view your over/under transactions, select the **Overview** tab in the upper part of the **Over/under transactions** page. The following table describes the fields that are available in the grid.

| Field | Description |
|---|---|
| Over/under transaction number | The unique name of the over/under transaction record that was automatically created when the arrival journal was processed. |
| Voyage | The voyage that the purchase line was attached to. |
| Shipping container | The container that the purchase line was attached to. |
| Arrival journal | The arrival journal that the over/under line was generated from. |
| Reference | A reference to either the purchase order or the transfer order that is associated with the over/under transaction. |
| Number | The purchase order that is referenced in the over/under transaction. |
| Vendor account | The vendor that the over or under is related to. |
| Goods in transit number | The goods-in-transit number, if applicable. |
| Item number | The item number that the over or under is related to. |
| Original quantity | The original quantity of the purchase order line that is attached to the shipment. |
| Received quantity | The quantity that was actually received. |
| Difference | The difference between the expected arrival journal amount and the amount that was posted in the arrival journal. A negative value indicates an over-delivery of goods. |
| Remaining quantity | The quantity that remains on the arrival journal line. |
| Over/under delivery | A value that indicates whether the quantity that was received is an over or an under. |
| Status | The status of the over/under transaction. Depending on the settings on the **[Landed cost parameters](landed-cost-parameters.md)** page, over-delivery can automatically create a movement journal for the over-delivery amount and post the journal. In this case, the over/under transaction will have a status of *Completed*. If action is required to move the goods out of the under-delivery warehouse, the record will have a status of *In process*. |
| Over/under reason | The reason that is associated with the over/under transaction. |
| Other inventory dimensions | You can show columns for additional dimensions in the grid as you require. These dimensions include batch number, inventory status, and warehouse. On the Action Pane, select **Inventory \> Display dimensions** to open a dialog box where you can select the dimensions to include. |

### Upper General tab

To view more information about the line that is currently selected on the upper **Overview** tab, select the **General** tab in the upper part of the **Over/under transactions** page. The information on this tab includes the values for all available dimensions. This information is pulled from the originating purchase order.

### Lower Overview tab

To view the document type for the row that is selected on the upper **Overview** tab, select the **Overview** tab in the lower part of the **Over/under transactions** page. The following table describes the fields that are available.

| Field | Description |
|---|---|
| New document type | This field is set to either *Movement journal* or *Purchase order*, depending on the action that is shown on the selected over/under transaction line. |
| Number | A reference and link to either the purchase order or the movement journal that is associated with the selected over/under transaction line. |
| Over/under reason | The reason that is associated with the selected over/under transaction line. |
| Quantity | The quantity that you selected for the purchase order or movement journal that is associated with the selected over/under transaction line. |

### Lower General tab

To view the over/under transaction number, lot ID, and dimension number that are associated with the selected over/under transaction line, select the **General** tab in the lower part of the **Over/under transactions** page. 

### Process over/under transactions

The Action Pane on the **Over/under transactions** page provides the following commands for processing the transactions that are selected on the page. Each command lets you choose how to process each transaction.

- **Create \> Movement** – Create and post a movement journal for the selected transaction. For under transactions, a movement journal is automatically created and posted for the difference between the expected and actual received quantity. Select this command for over transactions if you want the vendor to realize the cost difference.
- **Create \> Purchase order** – Create a purchase order for the difference between the expected and actual received quantity of the selected transaction. Select this command for over transactions if your organization will realize the cost difference.
- **Create \> Transfer to destination** – This command applies only to transfer orders. Select it if you want to transfer the over or under quantity to the destination warehouse.
- **Create \> Transfer to origin** – This command applies only to transfer orders. Select it if you want to transfer the over or under quantity to the origin warehouse.
