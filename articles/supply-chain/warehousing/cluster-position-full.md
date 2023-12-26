---
# required metadata

title: Cluster position full
description: This article provides information about the Cluster position full feature. This feature offers an alternative to more rigid enforcement of work break rules when cluster picking is used, because it enables a larger margin of error in the volumetric constraints of containers or totes.
author: Mirzaab
ms.date: 08/25/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  WHSClusterProfile
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: 10.0.8
---

# Cluster position full

[!include [banner](../includes/banner.md)]

The *Cluster position full* feature offers an alternative to more rigid enforcement of work break rules when cluster picking is used, because it enables a larger margin of error in the volumetric constraints of containers or totes. In a common scenario, not all items on a work order fit into a selected container. Warehouse workers who are cluster picking have few options in this scenario: they must either change to a larger container size or work with their supervisor to come up with a different solution.

This feature introduces the ability to run the **Full** button on one of the work units in a cluster. In older versions, this option was available only for regular order picking, not for cluster picking. However, this feature differs from the standard **Full** button in that it cancels the remaining work. It doesn't suggest that the user add another bin to the same cluster, and it doesn't automatically create new work.

## Turn the Cluster position full feature on or off

To use the functionality described in this article, the *Cluster position full* feature must be turned on for your system. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *Cluster position full* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Setup

This section provides guidelines, and an example that shows how to set up and use the *Cluster position full* feature.

### Make sample data available

To work through the [example scenario](#example-scenario) by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use the example scenario as guidance for working with this feature on a production system. However, in that case, you must substitute your own values for the settings that are described here.

### Cluster profiles

You must specify whether cluster IDs are automatically generated, how many positions are used, when clusters are broken, and how the picking work is sequenced and verified.

1. Go to **Warehouse management \> Setup \> Mobile device \> Cluster profiles**.
1. In the list pane, select the **Create Cluster** record.
1. On the **General** FastTab, verify the following values:

    - **Generate cluster ID:** *Yes*
    - **Activate positions:** *Yes*
    - **Number of positions:** *2*
    - **Position name:** *Numeric*
    - **Break cluster at:** *Put*
    - **Sort verification type:** *Position scan*

1. In the **Cluster sorting** FastTab. The grid should be blank (that is, it should contain no lines).

### Work templates

You must define how the picking work for cluster picking is created.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. At the top of the page, set the **Work order type** field to *Sales orders*.
1. Make sure that the following work templates from the demo data are listed. If they aren't available, you won't be able to complete the scenario.

    - 61 SO Stage
    - 61 SO Cluster pick

### Location directives

You must specify where items are picked from and where they are put.

1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the list header, set the **Work order type** field to *Sales orders*.
1. Make sure that the following sales order directives from the demo data are listed. If they aren't available, you won't be able to complete the scenario.

    - 61 Cluster pick
    - 61 SO Pick order

### Mobile device menu items

You must configure a mobile device menu item to use existing work that is directed by cluster picking. In the mobile device menu item for cluster picking, the **Allow splitting of work** parameter must be turned on, and the *SO Pick* work class must be added.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list pane, select the **Cluster Pick Create** record.
1. Select **Edit** in the Action pane.
1. On the **General** FastTab, set the following values:

    - **Directed by:** *Cluster picking*
    - **Generate license plate:** *Yes*
    - **Allow splitting of work:** *Yes*
    - **Cluster profile ID:** *Create Cluster*

    Accept the default values for all other fields.

1. On the **Work classes** FastTab, add the following two lines, as required:

    - Line 1 (usually present in demo data):

        - **Work class ID:** *Sales* 
        - **Work order type:** *Sales orders*

    - Line 2 (probably not present in demo data):

        - **Work class ID:** *SO Pick*
        - **Work order type:** *Sales orders*

1. Go to **Work confirmation setup** in the Action pane.
1. Select **Edit**.
1. Enter the following values on the line in grid.
    - **Work type** - *Pick*
    - **Product confirmation** - *Select the check box*

1. Select **Save** in the Action pane and close the page.

## Create picking work

Before you can start cluster picking, you must create some outbound work. The cluster profile that you created earlier specifies two cluster positions. Therefore, at least two work IDs must be created for sales order picking. For this scenario, transactions will occur in warehouse *61*, and they will use items *L0101* and *T0100*. The demo data should have enough on-hand inventory of these items. Make sure that you have enough inventory to complete the transactions.

### Create sales order 1

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. Select **New** to create sales order 1.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-010*
    - **Warehouse:** *61*

1. Select **OK**.
1. The new sales order is opened. On the **Sales order lines** FastTab, add a line that has the following settings:

    - **Item number:** *T0100*
    - **Quantity:** *5*

1. On the **Line details** FastTab, on the **Delivery** tab, set the **Confirmed ship date** field to today's date.
1. On the **Sales order lines** FastTab, add a second line that has the following settings:

    - **Item number:** *L0101*
    - **Quantity:** *20*

1. On the **Line details** FastTab, on the **Delivery** tab, set the **Confirmed ship date** field to today's date.
1. For each line that you just added, follow these steps to reserve inventory:

    1. Select the line to reserve.
    2. On the **Sales order lines** FastTab, select **Inventory \> Reservation**.
    3. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the inventory.
    4. Close the **Reservation** page.

1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    When the release is completed, you receive informational messages that show the wave and load IDs that were created.

### Create sales order 2

1. Go to **Sales and Marketing \> Sales orders \> All sales orders**.
1. Select **New** to create sales order 2.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-011*
    - **Warehouse:** *61*

1. Select **OK**.
1. The new sales order is opened. On the **Sales order lines** FastTab, add a line that has the following settings:

    - **Item number:** *L0101*
    - **Quantity:** *20*

1. On the **Line details** FastTab, on the **Delivery** tab, set the **Confirmed ship date** field to today's date.
1. On the **Sales order lines** FastTab, add a second line that has the following settings:

    - **Item number:** *T0100*
    - **Quantity:** *2*

1. On the **Line details** FastTab, on the **Delivery** tab, set the **Confirmed ship date** field to today's date.
1. For each line that you just added, follow these steps to reserve inventory:

    1. Select the line to reserve.
    2. On the **Sales order lines** FastTab, select **Inventory \> Reservation**.
    3. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the inventory.
    4. Close the **Reservation** page.

1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    When the release is completed, you receive informational messages that show the wave and load IDs that were created.

### Get work IDs and license plate numbers

Two work IDs should have been created, each of which has two pick lines. Follow these steps to find the work IDs and license plate assignments.

1. Go to **Warehouse management \> Work \> Work details**.
1. In the **Overview** grid, search the **Order number** column for the two sales orders that you just created. For each sales order, make a note of the corresponding work ID.
1. Select the row for each sales order to show related information in the **Lines** grid. Make a note of the location that each item will be picked from.
1. Go to **Inventory management \> Inquiries and reports \> On-hand list**.
1. On the Action Pane, select **Dimensions** to open the **Dimension display** dialog box.
1. Make sure that the **License plate**, **Warehouse**, and **Item number** check boxes are selected, and then select **OK**.
1. In the **Filter** pane, set the following filters:

    - **Item number** – **is one of** – *L0101* and *T100*
    - **Warehouse** – **begins with** – *61*

1. Make a note of the **License plate** values that are shown.

## <a name="example-scenario"></a>Example scenario

### Mobile device flow execution – Work confirmation setup for the product

1. Sign in to the Warehouse Management mobile app as a user in warehouse *61*.
1. Go to **Outbound \> Cluster pick create**.

    The **TASK: Assign work to Cluster** page appears.

1. Enter the work ID for sales order 1 to assign it to cluster position 1.
1. Select **OK** (check mark symbol).
1. Enter the work ID for sales order 2 to assign it to cluster position 2.
1. Select **OK** (check mark symbol).

    The **TASK: Cluster Pick Create: Pick** page appears and shows *Item L0101 2 PL*.

Because the cluster profile set the number of positions to 2, the system automatically directs you to the first consolidate pick: two pallets (PL) of item *L0101*.

At any time during the following steps, you can select the **Details** tab to view additional information about the task, such as the picking location.

1. Set the **ITEM** field to *L0101*. This confirms the item number, which is required for this menu item (you configured this earlier by selecting **Work confirmation setup**  from the **Mobile device menu item** page when you created this menu item).
1. Enter the license plate number that is associated with the item in the location that is being picked. You will pick two pallets.
1. Set the **LP** field to *LP\_PICK\_01*.
1. Select **OK** (check mark symbol).

    The **TASK: Sort: Cluster Pick Create** page appears. Here, you will sort the two picked pallets into a pick position. This position might be a tote or container that is used to separate the picked inventory by sales order.

1. View the details that are shown for the item (*L0101*) and quantity (*20* ea) that will be sorted into position 1 (for sales order 1).
1. Set the **POSITION NA** field to *1*.
1. Select **OK** (check mark symbol).
1. View the details that are shown for the item (*L0101*) and quantity (*20* ea) that will be sorted into position 2 (for sales order 2).
1. Set the **POSITION NA** field to *2*.
1. Select **OK** (check mark symbol).

    The **TASK: Cluster Pick Create: Pick** page appears and shows *Item T0100 7 ea*.

In this scenario, position 1 can't accept the full quantity of items that must be picked to fulfill sales order 1. A position must be marked as full. In this scenario, you will do a partial pick of the second item. The second item will be partially picked for position 1, and new work will be created to pick the remaining quantity to fulfill the order.

1. Select the Menu button (sometimes referred to as the hamburger or the hamburger button), and then select **Position full**.
1. Identify the position that is full, and select *1*.
1. Select **OK** (check mark symbol).
1. Enter the pick quantity that can still be picked into position 1. The system can determine which item number is being picked.
1. Enter *2*.
1. Select **OK** (check mark symbol).
1. Confirm the item number to complete the pick of the remaining item into position 2.
1. Set the **ITEM** field to *T0100*.
1. Select **OK** (check mark symbol).
1. Enter the license plate that the item is being picked from by setting the **LP** field to *LPREPL04*.
1. Select **OK** (check mark symbol).
1. View the details that are shown for the item (*T0100*) and quantity (*2* ea) that will be sorted into position 2 (for sales order 2).
1. Set the **POSITION NA** field to *2*.
1. Select **OK** (check mark symbol).
1. View the details that are shown for the item (*T0100*) and quantity (*2* ea) that will be sorted into position 1 (for sales order 1).
1. Set the **POSITION NA** field to *1*.
1. Select **OK** (check mark symbol).

    The **TASK: Cluster Pick Create: Put** page appears.

In this scenario, the cluster pick has been completed, and the user is directed to put away the picked items from position 1 and position 2 into staging location *STAGE01*.

1. Review the information on the page. It shows that a total quantity of *44* will be put to the staging location.
1. Select **OK** (check mark symbol).

    You receive a "Cluster Completed" message.

You can now use the **Sales Picking** menu item to pick the remaining quantity. You can then use the **Sales loading** menu item to move the items from the staging location to the loading dock.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]