---
title: Process over/under transactions
description: Learn how to set up the details of policies for over/under transactions, so that the system can determine how to manage over-processing of goods.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: ITMOverUnderTrans, ITMOverUnderToleranceTable, ITMOverUnderReasonTable, ITMOverUnderToleranceGroup
ms.topic: how-to
ms.date: 04/04/2025
ms.custom: 
  - bap-template
---

# Process over/under transactions

[!include [banner](../../includes/banner.md)]

When the orders in a voyage are processed, the system expects the item quantity that is received in the final destination warehouse for consumption to match the quantity that is specified on the purchase order lines that are associated with the voyage. However, because the exact quantity on the purchase order lines isn't always received in the warehouse, the **Landed cost** module defines a set of rules that are used to handle over-receiving and under-receiving of goods. These rules are especially important because the original purchase order has been invoiced and can no longer be modified.

By setting up the details of over/under transaction policies, you enable the system to determine how to manage the over-processing and under-processing of goods at the time of receipt. An over or under transaction will in some cases trigger an automatic action, and other times require manual action to resolve. You can also manually manage over and under inventory by using the **Over/under transactions** page.

We recommend handling over and under deliveries with a goods-in-transit order.

## Over/under transaction process flow and examples

The following diagram shows a flowchart of the process the system uses to determine whether over/under transactions should be created.

:::image type="content" source="media/over-under-flowchart-all.svg" alt-text="Over/under transaction process flowchart." lightbox="media/over-under-flowchart-all.svg":::

The diagram highlights the following steps of the process:

1. When goods are received, the system first compares the total monetary amount of the received purchase with the original purchase order and checks whether this difference is within or outside of the configured amount tolerance.
1. If the difference is within the amount tolerance, the system then checks the percentage tolerance against the individual purchase order line.
1. The system checks whether the received amount or quantity is larger or smaller than the ordered amount or quantity.
1. Based on this analysis, the system determines whether there has been an over or under delivery and carries out the relevant tasks as needed.

Use the **Over and Under Transactions** page to keep track of whether the system created an over/under transaction, movement journal, and/or purchase order.

In some cases, a movement journal is automatically created as a response to the over/under delivery. This writes off or absorbs the difference between ordered and actual quantities.

In other cases, a purchase order is automatically created. This involves recording the additional quantity received under a new purchase order in case of an over delivery. In scenarios when the system doesn't take any automatic actions, the user must decide whether to create a movement journal or purchase order.

When a purchase order is created for an under-delivery, it shows a negative quantity for the vendor to pay for the missing goods. This works as a vendor return or as credit for a future order.

### Example scenarios

#### Setup used in these scenarios

Each of the scenarios described later use the setup described in this section.

The following over/under tolerances apply (required for all items to be used in the purchase order):

- Amount tolerance: $100 (applied to the order)
- Percentage tolerance: 10% (applied to the order line)

The following purchase order exists:

- Line 1: 10 pcs at $100/ea
- Line 2: 20 pcs at $50/ea
- Total monetary amount of original purchase order = $2000

In this example, any received purchase order with a total value outside of the $1900 to $2100 threshold will be processed as an over/under transaction. Any difference between the quantity of the original and received purchase order line will be considered as within the percentage tolerance if within the following thresholds:

- Line 1: 9-11
- Line 2: 18-22

#### Scenario 1

The following items are received and, as a result, the following actions are taken (as shown in the flowchart shown earlier in this article).

- Total order: Purchase order total value is $2050.
    - Step 1: Purchase order is *within* the amount tolerance.

- Line 1: 10 pcs ($1000)
    - Step 2: The exact quantity of the purchase order line was received, so the order line is *within* the percentage tolerance threshold.
    - Step 3: The received quantity of the purchase order line is *equal to* the original purchase order line.
    - Step 4: The exact quantity of the purchase order line was received. No action.

- Line 2: 21 pcs ($1050)
    - Step 2: The difference between the quantity of the original and received purchase order line is *within* the percentage tolerance threshold.
    - Step 3: The received quantity of the purchase order line is *greater than* the original purchase order line.
    - Step 4: It's an over-delivery,so the system creates:
        - An over transaction
        - A movement journal

#### Scenario 2

The following items are received and, as a result, the following actions are taken (as shown in the flowchart shown earlier in this article).

- Total order: Purchase order total value is $2050.
    - Step 1: Purchase order is *within* the amount tolerance.

- Line 1: 9 pcs ($900)
    - Step 2: The difference between the quantity of the original and received purchase order line is *within* the percentage threshold.
    - Step 3: The received quantity of the purchase order line is *less than* the original purchase order line.
    - Step 4: It's an under-delivery, so the system creates:
        - An under transaction
        - A movement journal

- Line 2: 23 pcs ($1150)
    - Step 2: The difference between the quantity of the original and received purchase order line is *outside of* the percentage threshold.
    - Step 3: The received quantity of the purchase order line is *greater than* the original purchase order line.
    - Step 4: It's an over-delivery, so the system creates:
        - An over transaction
        - A purchase order

#### Scenario 3

The following items are received and, as a result, the following actions are taken (as shown in the flowchart shown earlier in this article).

- Total order: Purchase order total value is $1900.
    - Step 1: Purchase order is *within* the amount tolerance.

- Line 1: 7 pcs ($700)
    - Step 2: The difference between the quantity of the original and received purchase order line is *outside of* the percentage threshold.
    - Step 3: The received quantity of the purchase order line is *less than* the original purchase order line.
    - Step 4: It's an under-delivery, so the system creates:
        - An under transaction

- Line 2: 24 pcs ($1200)
    - Step 2: The difference between the quantity of the original and received purchase order line is *outside of* the percentage threshold.
    - Step 3: The received quantity of the purchase order line is *greater than* the original purchase order line.
    - Step 4: It's an over-delivery, so the system creates:
        - An over transaction
        - A purchase order

#### Scenario 4

The following items are received and, as a result, the following actions are taken (as shown in the flowchart shown earlier in this article).

- Total order: Purchase order total value is $2950.
    - Step 1: Purchase order is *outside of* the amount tolerance. This means that Step 2 is skipped.

- Line 1: 20 pcs ($2000)
    - Step 3: The received quantity of the purchase order line is *greater than* the original purchase order line.
    - Step 4: It's an over-delivery, so the system creates:
        - An over transaction
        - A purchase order

- Line 2: 19 pcs ($950)
    - Step 3: The received quantity of the purchase order line is *less than* the original purchase order line.
    - Step 4: It's an under-delivery, so the system creates:
        - An under transaction
        - A movement journal

> [!NOTE]
> When an over-delivery automatically triggers the creation of a purchase order, the system also posts a product receipt. However, invoices must always be posted manually for these purchase orders.
>
> Under- and over-delivery quantities don't impact the estimated landed costs. This means that auto costs calculated for a voyage or container won't be redistributed across the actual quantities that are received.
>
> When receiving with the Warehouse Management mobile app, workers aren't notified when an over- or under-delivery occurs.

## Set up over/under transactions

To allow over/under transactions for goods-in-transit orders, you must set up the following:

- Set up the good-in-transit feature as described in [Goods-in-transit processing and receiving](in-transit-processing.md).
- Ensure that a movement journal has been set up and specified for the over/under delivery including an offset account defined (**Landed cost** \> **Setup** \> **Landed cost parameters** \> **General** \> **Defaults** \> **Over/Under Delivery**).
- Set up over/under tolerances, over/under reasons, and tolerance groups if applicable (**Landed Cost** \> **Setup** \> **Over/under setup**).

### Over/under tolerances

Over/under tolerances define when a difference between the actual and purchased quantity of goods creates an over/under delivery transaction. You set over-delivery and under-delivery tolerances to specify the over and under quantities or volumes that can be processed on a voyage without causing an error. If the voyage line receipt is outside these tolerances, it must be modified and resolved before the voyage line can be closed for further processing.

By setting tolerance levels, businesses can avoid unexpected expenses that can arise when they receive a lower quantity of goods than expected. At the same time, if the business receives a higher quantity of goods than expected, they can benefit from the savings and adjust the landed cost calculation accordingly.

To configure the tolerances, go to **Landed cost** \> **Over/under setup** \> **Over/under tolerances**. There, you can view, edit, add, and remove tolerance records. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Account code | Define the scope of vendors that the tolerance applies to by selecting one of the following values: <ul><li>**Table** – The over/under tolerance applies only to the vendor that is selected for the row.</li><li>**Group** – The over/under tolerance applies to all vendors in the vendor tolerance group that is selected for the row.</li><li>**All** – The over/under tolerance applies to all vendors.</li></ul> |
| Account relation | Select the vendor or vendor group that the over/under tolerance applies to, depending on the value that you selected in the **Account code** field. |
| Item code | Define the scope of items that the tolerance applies to by selecting one of the following values: <ul><li>**Table** – The over/under tolerance applies only to the item that is selected for the row.</li><li>**Group** – The over/under tolerance applies to all items in the item tolerance group that is selected for the row.</li><li>**All** – The over/under tolerance applies to all items.</li></ul> |
| Item relation | Select the item or item group that the over/under tolerance applies to, depending on the value that you selected in the **Item code** field. |
| Amount tolerance | Enter the amount tolerance that should be applied to a whole purchase order. This is a monetary amount. This is an optional field. |
| Percentage tolerance | Enter the percentage tolerance that should be applied to an individual purchase order line quantity. This is an optional field. |

> [!NOTE]
> The system will first check whether the total amount of the received purchase order falls within the amount tolerance. If it does, the system will then check the percentage tolerance to manage over/under delivery scenarios.

### Over/under reasons

When an over or under quantity is associated with a voyage line that is received, you might have to identify the reason for the over or under quantity. In this case, you can select the over-delivery or under-delivery reason on the receiving line when the goods are received.

To set up over-delivery and under-delivery reasons, go to **Landed cost** \> **Over/under setup** \> **Over/under reasons**. There, you can view, edit, add, and remove the available over-delivery and under-delivery reasons. The following table describes the fields that are available for each reason.

| Field | Description |
|---|---|
| Over/under reason | Enter a unique name for the reason for the over-receiving or under-receiving transaction. |
| Description | Enter a description of the over/under reason. |
| Movement | Select the movement journal that is associated with the over/under reason. This field lists all available journals that a journal type of *Movement* is associated with on the **Inventory journal names** page (**Inventory management** \> **Setup** \> **Journal names** \> **Inventory**). |

### Item over/under tolerance groups

Items that have similar tolerances can be grouped together. In this way, you can set the over/under tolerance for all items in that group at the same time.

To set up item over/under tolerance groups, go to **Landed cost** \> **Over/under setup** \> **Item over/under tolerance groups**. There, you can view, edit, add, and remove over/under tolerance group records. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Over/under tolerance group | Enter a unique name for the group. Choose a name that describes the tolerance, such as *1% Var*. |
| Description | Enter a description of the group. |

> [!NOTE]
> Configure an item to be part of an over/under tolerance group using the **Released Product** \> **Purchase** \> **Over/under tolerance group** field drop-down.

### Vendor over/under tolerance groups

You can group together vendors that regularly over-deliver or under-deliver. You can then set the over/under tolerance per group.

To set up vendor over/under tolerance groups, go to **Landed cost** \> **Over/under setup** \> **Vendor over/under tolerance groups**. There, you can view, edit, add, and remove over/under tolerance group records. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Over/under groups | Enter a unique name for the group. Choose a name that describes the type of vendors that belong to the group. |
| Description | Enter a description of the group. |

> [!NOTE]
> Configure a vendor to an over/under tolerance group using the **Vendor** \> **Miscellaneous details** \> **Over/under tolerance group** field drop-down.

## View and process over/under transactions on the Over/under transactions page

Over and under transactions are generated when the quantity of goods that is put away doesn't match the initialized quantity. The quantity in the arrival journal should be updated only with the quantity that is put away.

When the receipt of voyage lines is processed, over/under tolerances can be set for a vendor. The items will then be reviewed and validated.

If an item that is received is inside the tolerance, the system will generate a movement journal. This journal can be specified on the voyage parameters page. In addition, an over/under transaction will be created. For example, the order value is $100, the receipt value is $99, and these values satisfy the tolerance rules. In this case, a negative movement journal for the under-received quantity will be created.

If an item that is received is outside the tolerance, the system will generate an over/under transaction for the difference in quantity.

To view and process over/under transactions, go to **Landed cost** \> **Inquiries** \> **Over/under transactions**. There, an over/under transaction will be associated with all the items in a voyage that are over-received or under-received. We recommend that you use the **Over/under transactions** page to resolve all over/under transactions that are associated with voyages.

We also recommend *against* using movement or counting journals to manually resolve under-delivery warehouse transactions. Instead, you should use the **Over/under transactions** page to manage the under-delivery warehouse quantities.

### Upper Overview tab

To view your over/under transactions, select the **Overview** tab in the upper part of the **Over/under transactions** page. The following table describes the fields that are available in the grid.

| Field | Description |
|---|---|
| Over/under transaction number | The unique name of the over/under transaction record that was automatically created when the arrival journal was processed. |
| Voyage | The voyage that the purchase line was attached to. |
| Shipping container | The container that the purchase line was attached to. |
| Arrival journal | The arrival journal that the over/under line was generated from. |
| Reference | A reference to the purchase order that is associated with the over/under transaction. |
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
| Other inventory dimensions | You can show columns for additional dimensions in the grid as you require. These dimensions include batch number, inventory status, and warehouse. On the Action Pane, select **Inventory** \> **Display dimensions** to open a dialog box where you can select the dimensions to include. |

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

### Action Pane buttons for processing over/under transactions

The Action Pane on the **Over/under transactions** page provides the following commands for processing the transactions that are selected on the page. Each command lets you choose how to process each transaction.

- **Create** \> **Movement** – Create and post a movement journal for the selected transaction. For under transactions, a movement journal is automatically created and posted for the difference between the expected and actual received quantity. Select this command for over transactions if you want the vendor to realize the cost difference.
- **Create** \> **Purchase order** – Create a purchase order for the difference between the expected and actual received quantity of the selected transaction. Select this command for over transactions if your organization will realize the cost difference.
- **Create** \> **Transfer to destination** – This command applies only to transfer orders. Select it if you want to transfer the over or under quantity to the destination warehouse.
- **Create** \> **Transfer to origin** – This command applies only to transfer orders. Select it if you want to transfer the over or under quantity to the origin warehouse.

## Over and under-receive a goods-in-transit order with quality orders enabled

When under-receiving a goods-in-transit order, a quality order will be created for the actual quantity that has been received if the parameter **Per Updated Quantity** is enabled in **Inventory management** \> **Setup** \> **Quality control** \> **Item sampling**. If this parameter is disabled, a quality order will be created based on the order quantity of the goods-in-transit order.

When over-receiving a goods-in-transit order, the system may either automatically create a purchase order or a movement journal for the quantity that has been over-delivered. In this case, a quality order will be created based on the original quantity of the goods-in-transit order.

If a purchase order has been automatically generated and you want the over-delivered quantity to also go through the quality check process, you will need to add an additional quality association for this newly created purchase order.

If a movement journal has been automatically created, you can manually create a quality order for this over-delivered amount in the goods-in-transit order form.

To learn more about how to set up quality orders for landed cost, go to [Quality orders](../inventory/quality-orders.md).
