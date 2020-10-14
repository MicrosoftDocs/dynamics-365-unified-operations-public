---
# required metadata

title: Putaway clusters
description: Putaway clusters are a way to pick multiple license plates at once and take them for putaway at different locations. It can be very useful for retail businesses, where license plates typically aren't full pallets of inventory.
author: Mirzaab
manager: tfehr
ms.date: 07/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-18
ms.dyn365.ops.version: Release 10.0.7
---

# Putaway clusters

[!include [banner](../includes/banner.md)]

Putaway clusters are a way to pick multiple license plates at once and take them for putaway at different locations. It can be very useful for retail businesses, where license plates typically aren't full pallets of inventory. This process is often called a *Milk run*.

## Enable the Cluster Putaway feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Cluster Putaway Feature*

## Setup for the example scenario

### Cluster profiles

The Putaway cluster profile determines where the item will go based on the location assigned to the item at receipt. If different clusters are needed, different Putaway clusters should be created, one for each mobile device menu item.

1. Go to **Advanced Warehouse management \> Setup \> Mobile device \> Cluster profiles**.
1. Select **New** in the Action Pane.
1. In the **Header**, enter the following:

    - **Putaway Cluster profile ID** – *Cluster putaway*
    - **Putaway Cluster profile ID Name** – *Cluster putaway*
    - **Cluster type** – *Putaway*
    - **Sequence number** - *Accept default*

1. Select **Save** to enable the required fields on the **General** FastTab.
1. On the **General** FastTab, specify the following:

    - **Cluster assignment timing** - *At receipt*
        - Should the putaway cluster be assigned immediately when the inventory is being received, or sorted later?

    - **Cluster assignment rule** - *Manual*
        - Should the cluster assignment be determined automatically by the system, or manually by the user?

    - **Directive code** - *Leave blank*
    - **Putaway cluster locate** - *Receipt*
        - **Receipt**: Location found immediately during receipt.
        - **Cluster close**: Location found when cluster is closed.
        - **User directed**: Location found when LP is picked from cluster to putaway.
            - The putaway work is created without location and during the putaway itself, the user has to scan the LP or Work ID to initiate the Put step. The system finds the put location again and tells the user where to put the picked quantity.

    - **Putaway cluster per user** – *No*
        - When assigning clusters automatically, should each cluster be unique per user? Only enabled when **Cluster assignment rule** is set to *Automatic*.

    - **Unit restriction** - *Leave blank*
        - Unit that is required to be received for the profile to valid. If left blank, all units will be valid.

    - **Work unit break** – *Individual*
        - When closing a cluster, should all inventory be consolidated onto one license plate (using the cluster ID and the LP), and putaway as a single LP, or putaway separately on the LPs that were received? Disabled when **Putaway cluster locate** is set to *Receipt*.

    - **Cluster persists as Parent License Plate** – *No*
        - If *Yes*, when the Put step is complete, the Cluster ID will become a Parent License Plate and all items on the Cluster ID will be tied to that Parent license plate.

1. On the **Cluster sorting** FastTab, putaway sorting criteria can be determined. Select **New** in the Toolbar and enter the following:

    - **Sequence number** – *Accept default*
    - **Field name** – *WMSLocationId*
        - Determines what field this line will use for sorting criteria.

    - **Sorting** – *Ascending*
        - Determines whether sorting should be Ascending or Descending.

1. On the **Cluster work template** FastTab, select **New** in the Toolbar to add a line. Enter the following:
    - **Work order type** - *Purchase orders* : **Work template** - *61 PO Direct*

1. In the Action Pane, select **Save**, then select **Edit query**.
1. In the **Cluster putaway** dialog box, on the **Range** tab, select **Add** to add a second line to the query, then update the query lines as follows:

    | Table | Derived table | Field | Criteria |
    | -- | -- | -- | -- |
    | Work | Work | Warehouse | 61 |
    | Work | Work | Work ID | *Leave blank* |

10. Select **OK** to save the query and close the dialog box.
1. Select **Save** in the Action Pane and exit the form.

> [!IMPORTANT]
> Fields on the cluster profile that are greyed out when enabling *Generate cluster ID* are inactive and will not be considered when using the feature.

### Mobile device menu items

Two new mobile device menu items are available for this functionality. *Receive and Sort Cluster* is used to sort the received inventory to a putaway cluster upon receipt. *Cluster Putaway* is used to put away the cluster once it has been assigned.

#### Receive and Sort Cluster

Create new mobile device menu item for Receive and Sort Cluster, which will create Inbound Work after receiving the inventory. This where it is indicated that the receiving menu item will be used for Putaway clusters.

> [!NOTE]
> **Receive and Sort Cluster** can be used with the following menu items:
>
> - Purchase Order line receiving
> - Purchase Order item receiving
> - Load item receiving

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** in the Action Pane.
1. In the **Header**, enter the following:

    - **Menu item name** – *Receive and Sort Cluster*
    - **Title** – *Receive and Sort Cluster*
    - **Mode** – *Work*
    - **Use existing work** – *No*

1. In the **General** FastTab, enable the following settings:

    - **Work creation process** – *Purchase order item receiving*
    - **Generate license plate** – *Yes*
    - **Assign putaway cluster** – *Yes*
    - Accept the default values of the remaining parameters

1. Select **Save** in the Action Pane.

> [!NOTE]
> The **Assign putaway cluster** parameter is only available on one-step receiving **Work creation process** activity.

#### Cluster Putaway

Create new mobile device menu item to be used for putting away the Cluster once it has been assigned.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** in the Action Pane.
1. In the **Header**, enter the following:

    - **Menu item name** – *Cluster putaway*
    - **Title** – *Cluster putaway*
    - **Mode** – *Work*
    - **Use existing work** – *Yes*

1. In the **General** FastTab, enable the following settings:

    - **Directed by** – *Cluster Putaway*
    - Accept the default values of the remaining parameters

1. In the **Work classes** FastTab, set up the valid work class for this mobile device menu item:

    - **Work class ID** – *Purchase* : **Work order type** – *Purchase orders*

1. Select **Save** in the Action Pane.

### Mobile device menu

Add the menu items just created to the inbound menu of the mobile app.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu** to add the newly created menu items to the desired menu.
1. Select **Edit** in the Action Pane.
1. Select **Inbound** in the menu list.
1. Scroll in the **AVAILABLE MENUS AND MENU ITEMS** until you find **Receive and Sort Cluster**.
1. Select **Receive and Sort Cluster**, the move right arrow ( **→** ) is enabled.
1. Select the arrow button ( **→** ) to move the selected menu item into the **MENU STRUCTURE** list.
1. Use the UP ( **↑** ) or DOWN ( **↓** ) arrow buttons to move the menu item into the desired position in the menu.
1. Select **Save** in the Action Pane.
1. Repeat steps 4 through 8 above to add the remaining menu items:

    - **Assign Cluster**
    - **Cluster Putaway**

## Example scenario

This scenario simulates putaway cluster processing.

### Create Purchase order

1. Go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. Select **New** in the Action Pane.
1. In the **Create purchase order** dialog box, enter the following:

    - **Vendor account** - *1001*
    - **Warehouse** - *61*

1. Select **OK**.
1. The **All purchase orders** page opens.
1. In the **Purchase order lines FastTab** add the following lines (use **Add line** in the Toolbar to add lines):

    - **Item number** - *A0001* : **Quantity** - *10*
    - **Item number** - *A0002* : **Quantity** - *20*
    - **Item number** - *M9215* : **Quantity** - *30*

1. Select **Save** in the Action Pane.
1. Make note of the purchase order number.

### Receive and put away from the mobile device

#### Receive and sort the inventory into a cluster

1. Logon to the mobile device with a user setup for warehouse 61.
1. Select **Inbound** from the **MAIN MENU**.
1. Select **Receive and Sort Cluster** from the **INBOUND** menu.
1. In the **PONUM** field, enter the purchase order number.
1. Select **OK** (displayed as a checkmark **(✔)** on the mobile device.)
1. Select the **ITEM** field, enter the item number *A0001*, and select **OK**.
1. Select the **QTY** field, enter *10* in the number pad and select the checkmark.
1. Select **OK** **(✔)** on the **QTY** task screen to confirm the quantity entered.
1. Select **OK** on the **ITEM** task screen to confirm item *A0001* was entered.
1. Next assign an ID for the cluster being created. Select the **CLUSTER ID** field and enter a value.

    - The ID number you enter here will be used when receiving the remaining two items on the purchase order.

1. Select **OK**.
1. The task screen for **PONUM** opens with a message **WORK COMPLETED**.

    - Item *A0001* has been received into the RECV location and assigned to the cluster ID entered in step 10.

1. Repeat steps 4 through 11 to receive the remaining two items from the purchase order and assign them to the cluster ID.

    - Item **A0002** with a quantity of **20**
    - Item **M9215** with a quantity of **30**

#### Close cluster

Before the items in the cluster can be put away, the cluster must first be closed. The following steps will be completed in Supply Chain Management.

1. Go to **Warehouse management \> Work \> Outbound \> Work clusters**.
1. In the **Work cluster** section of the page, search the **Cluster ID** field for the cluster ID entered previously.
1. If the cluster is not displayed, it may have already been closed. To verify this, select the **Show closed work** check box, and search from the cluster ID entered previously.

    - If the cluster has been closed go to **Cluster putaway** section below.
    - If the cluster has not been closed, the following steps describe how to manually close the cluster.

1. From the **Work clusters** page, in the **Work cluster** section, select the cluster ID created previously.
1. In the Action Pane, select **Close cluster**.
1. When the cluster has been closed it will no longer be displayed in the **Work cluster** section (with **Show closed work** unselected).

#### Cluster putaway

The following steps will be performed on the mobile device.

1. Logon to the mobile device with a user setup for warehouse 61.
1. Select **Inbound** from the **MAIN MENU**.
1. Select **Cluster putaway** from the **INBOUND** menu.
1. Select **CLUSTER ID** and enter the closed cluster ID created previously.
1. Select **OK**.
1. The **Cluster putaway: Pick** screen is displayed.

    - The **Cluster ID** is displayed along with the picking location (**Loc**), items (**Multiple** will be displayed) and total quantity (**Total Qty**) in the cluster to be picked.

1. Select **OK**.
1. The **Cluster putaway: Put** screen is displayed.

    - The **Put** instructions identify the cluster ID, the put location, items, quantity as well as the license plate ID's for the items received on the cluster.
    - The user has the standard option to **Override** or **Pass** this step.

![Cluster Putaway-Put](media/Cluster_putaway-Put.png "Cluster Putaway-Put")

9. Select **OK** to confirm the putaway of the cluster.
1. The message **Cluster Completed** will be displayed.

## Notes and tips

- For the instances where the Cluster ID becomes the Parent LP for a nested pallet, when the Cluster ID is scanned, the Put position is automatically given and no further LP needs to be scanned, even if generating LP is set to be manual.
