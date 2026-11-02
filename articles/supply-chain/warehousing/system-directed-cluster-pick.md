---
title: System-directed cluster picking
description: Access an overview of system-directed cluster picking in Microsoft Dynamics 365 Supply Chain Management with an enabling the cluster picking feature.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 10/30/2026
ai-usage: ai-assisted
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSWorkCluster, WHSClusterProfile
---

# System-directed cluster picking

[!INCLUDE [banner](../includes/banner.md)]

Cluster picking is a piece picking process that you use to pick items for multiple orders at the same time by clustering them into pick clusters. You only need to visit the pick location once. Typically, use this functionality with small order picking or quantities that are less than case quantities.

When you set up system-directed cluster picking, you can cluster-pick work headers based on a system-generated cluster. The system cluster-picks orders up to the number of positions that you specify in the cluster profile. You can pick multiple orders at the same time without having to manually create a cluster.

System-directed cluster picking offers an alternative to manual cluster building, where you use a cluster profile to create a cluster. Define several setup-related lines in the cluster profile before you use it:

- **Number of positions** corresponds to the number of orders that you put on a cluster. Therefore, it corresponds to the number of totes.
- **Break cluster** determines when the cluster should be broken.
- **Generate cluster ID** controls whether the system generates the cluster ID or you enter it.
- **Sort verification type** determines whether position verification is required.

Use a new mobile device menu item for system-directed cluster picking. Specify the **Cluster profile ID** for the selected **Directed by** option. The system-directed work sequence queries can group orders based on company-specific criteria. Therefore, you can further optimize the assignment of work orders by specifying customized sorting criteria by using the system-directed work sequence queries.

When you enable system-directed cluster picking, warehouse workers see a cluster where the system preassigns picking orders to cluster positions. Workers can start to pick an item for multiple work orders by visiting the pick location only one time. The picking process for system-directed cluster picking is the same as the process for user-directed cluster picking.

## Set up system-directed cluster picking

### Create cluster profiles

Cluster profiles control how the system creates each cluster. If you need different clusters, create a different cluster profile for each mobile device menu item.

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Cluster profiles**.
2. Select **New**.
3. In the **Cluster profile ID** field, enter *2 Position*.
4. In the **Name** field, enter *2 Position*.
5. On the **General** FastTab, enter the following information:

    - **Generate cluster ID** - Select *Yes*. This option determines whether the system automatically creates the cluster ID or whether you create it at the start of picking.
    - **Activate positions** - Select *Yes*. This option determines whether the system automatically generates the position names based on the position name setup. If you set this option to *No*, the system uses the license plate ID for the position.
    - **Number of positions** - Select *2*. This field determines the maximum number of positions that the cluster can have (that is, the maximum number of boxes, totes, and so on).
    - **Position name** - Select *Numeric* so that the system names positions by using continuous numbers. If you select *Alphabetical*, the system names the positions in alphabetical order.
    - **Break cluster at** - Select *Put*. This field determines when the cluster breaks.
    - **Sort verification type** - Select *Position scan*. This field determines whether the system verifies the put-to-position step.

6. On the **Cluster sorting** FastTab, define sorting criteria by creating a new line and entering the following information:

    - **Sequence number** - Select *1*. This field determines the sequence that the system sorts by. The system enters a value automatically, but you can change it if needed.
    - **Field name** - Enter *WMSLocationId*. This field determines the field that the line uses for sorting criteria.
    - **Sorting** - Select *Ascending*. This field defines whether the sorting is done in ascending or descending order.

### Handle insufficient work for a cluster

If system-directed cluster picking can't find enough work for the configured number of positions, you might receive the following error message:

> Not enough work can be found for cluster.

To pick when fewer positions have work, edit the cluster profile and set **Activate positions** to *No*. With this setting, the license plate ID for the position is used instead of an automatically generated position name.

### Create a mobile device menu item

To create a new mobile device menu item for system-directed cluster picking and link the cluster profile ID to the mobile device menu item, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**.
1. Select **New**.
1. In the header section, enter the following information:
    - **Menu item name** - *SD Cluster*
    - **Title** - *SD Cluster*
    - **Mode** - *Work*
    - **Use existing work** - *Yes*

1. On the **General** FastTab, enter the following information:
    - **Directed by** - *System directed cluster picking*
    - **Generate license plate** - *Yes*
    - **Cluster profile ID** - *2 Position*

1. On the **Work classes** FastTab, set up the valid work class for this mobile device menu item by setting the following fields:
    - **Work class ID** - *Sales*
    - **Work order type** - *Sales orders*

1. In the **Mobile device menu items** Action Pane, select **System directed work sequence queries** and follow these steps to specify a new system-directed work sequence query:
    - Select **New** in the Action Pane.
    - **Sequence number** - *1*
    - **Description** - *Work priority – Work ID*

1. On the Action Pane select **Edit query**
1. Select the **Sorting** tab
1. Select **Add** to add a new line, then enter the following:
    - **Table** - *Work*
    - **Derived table** - *Work*
    - **Field** - *Work priority*
    - **Search direction** - *Ascending*
1. Select **Add** to add a second line, then enter the following:
    - **Table** - *Work*
    - **Derived table** - *Work*
    - **Field** - *Work ID*
    - **Search direction** - *Ascending*

1. The system sorts work IDs in the cluster, first by work priority and then by work ID.

### Set up a mobile device menu

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu**.
1. Add the *SD Cluster* menu item that you just created to a mobile device menu.
1. Select the *Outbound* menu.
1. Select **Edit** from the Action Pane.
1. Scroll until you find *SD Cluster*.
1. Select *SD Cluster*. The arrow pointing to the **Menu Structure** list is enabled.
1. Select the **arrow** button to move the *SD Cluster* menu item into the **Outbound** menu structure.
1. Select *SD Cluster* from the **Menu Structure** list, and then select the **Up** or **Down** arrows to move the menu item into the desired position on the mobile device menu.

## Scenario

### Create picking work

Before you can set up system-directed cluster picking, you must create eligible outbound work. The cluster profile that you created earlier specifies two cluster positions. Therefore, you must create at least two work IDs. In this scenario, you create two sales orders, reserve inventory, release the sales orders to the warehouse, and then manually process the wave.

1. Go to **Sales and Marketing** > **Sales orders** > **All sales orders**.
1. Select **New** in the Action Pane to create the first sales order.
    - The **Create sales order** menu opens. Enter the following information:
        - On the **Customer** FastTab, enter **Customer account** - *US-004*.
        - On the **General** FastTab, enter **Warehouse** - *62*.
        - Select **OK** to close the menu and create the sales order.
    - On the **Sales order lines** FastTab, select **Add line** if a new line isn't automatically added and enter the following information:
        - **Item number** - *A0001*
        - **Quantity** - *1*
        - Select **Add line** to add a second line.
        - **Item number** - *A0002*
        - **Quantity** - *3*
    - Reserve inventory for both of the lines that you just created.
        - Select *Line 1*.
        - On the **Sales order lines** Action Pane, select **Inventory**, and then select **Reservation** from the list.
        - On the **Reservation** form, select **Reserve lot** to reserve the inventory.
        - Close the **Reservation** form when the reservation is completed.
        - Repeat these steps to reserve inventory for *Line 2*.
1. Select **New** in the Action Pane to create the second sales order.
    - The **Create sales order** menu opens. Enter the following information:
        - On the **Customer** FastTab, enter **Customer account** - *US-005*.
        - On the **General** FastTab, enter **Warehouse** - *62*.
        - Select **OK** to close the menu and create the sales order
    - On the **Sales order lines** FastTab, select **Add line** if a new line isn't automatically added and enter the following information:
        - **Item number** - *A0001*
        - **Quantity** - *4*
        - Select **Add line** to add a second line.
        - **Item number** - *A0002*
        - **Quantity** - *2*
    - Reserve inventory for both lines that you just created.
        - Select *Line 1*.
        - On the **Sales order lines** Action Pane, select **Inventory**, and then select **Reservation** from the list.
        - On the **Reservation** form, select **Reserve lot** to reserve the inventory.
        - Close the **Reservation** form when the reservation is completed.
        - Repeat these steps to reserve inventory for *Line 2*.
    - Close the sales order and return to the **All sales orders** list page.
1. Find the two sales orders you just created (you might need to refresh the page). In the table, select both sales orders using the section check mark.
    - In the **All sales orders** Action Pane, select the **Warehouse** tab.
    - In the **Actions** group, select **Release to warehouse** to release both sales orders to the warehouse.
1. When the release to warehouse process finishes, an informational message is displayed.
    - Shipments are created for each sales order.
    - A wave is created and both shipments are assigned to the wave. Make note of the **Wave ID**.
1. Go to **Warehouse management** > **Outbound waves** > **Shipment waves** > **All waves**.
    - In the **All waves** list, find and select the **Wave ID** that you created in the previous step.
    - In the Action Pane, select the **Wave** tab.
    - In the **Wave** group, select **Process** to process the wave and create **Work**.
    - Informational messages are generated when processing finishes, indicating that work is created and the wave is posted.
1. **Optional**: Go to **Warehouse management** > **Work** > **Work details** to view the work created. Two different work IDs are created. Each work ID has two pick lines.

### Run the mobile device flow

1. Sign in to the mobile device for a user in warehouse *62*.
1. On the **Main Menu**, select **Outbound**.
1. On the **Outbound** menu, select *SD Cluster* to initiate the pick.
    - The system creates a cluster and attaches the two work IDs that you created earlier. If you created more than two work IDs, the system adds only the first two to the cluster. The system adds the work IDs to the cluster in ascending order, as you specified in the query setup.

    > [!NOTE]
    > The system automatically creates the new cluster only if you previously created enough additional work IDs. Otherwise, the system shows the following message: "Not enough work can be found for cluster."

    - After you select the menu, the first pick screen appears. The system aggregates all matching pick lines from the two work IDs and directs you to visit the pick location one time, so that you can satisfy both orders by using one pick. This process is done in the same way as the process for user-directed cluster picking.

1. Confirm the first picking location and item by selecting **OK**.
    - The quantity of the pick is the total of the item displayed on the sales orders in the cluster.
1. Enter the position name (numeric or alphabetical) to confirm that the item quantity picked for the position is in the correct position.
1. Repeat this process until you pick all item quantities and put them in the correct position.
1. The last step on the mobile device is to **Put** the cluster in the final location. Select **OK**.
    - When you confirm the put operation, the system closes and breaks the cluster based on the value that you set for the **Break cluster at** field in the cluster profile. The system also closes work IDs.
1. The mobile device shows a "Cluster complete" message.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
