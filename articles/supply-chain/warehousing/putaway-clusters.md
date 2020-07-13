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

Putaway clusters are a way to pick multiple license plates at once and take them for putaway at different locations. It can be very useful for retail businesses, where license plates typically aren't full pallets of inventory. This process is often called a _Milk run_.

## Setup for the example scenario

The setup does not include the standard warehouse configuration required for processing of the inbound flow. Make sure that is set up correctly before processing the example scenario.

### Putaway cluster profiles

Go to **Advanced Warehouse management \> Setup \> Mobile device \> Putaway clusters**. The Putaway cluster profile determines where the item will go based on the location assigned to the item at receipt. If different clusters are needed, different Putaway clusters should be created, one for each mobile device menu item.

In the **Header**, specify the following:

- **Putaway Cluster profile ID** – _Cluster putaway_
- **Putaway Cluster profile ID Name** – _Cluster putaway_
- **Cluster type** – _Putaway_

On the **General** FastTab, specify the following:

- **Assign putaway cluster at receipt** – _No_
  - If _Yes_ and if Putaway cluster assignment method is set to _Manual_, after the license plate is entered on the receiving screen, the cluster will be requested from the worker performing the receiving. This eliminates the Mobile device menu item step _Assign to Putaway cluster_
- **Generate Cluster ID** – _No_
- **Directive code** – _leave blank_
  - Restricts the Putaway cluster to a unique Location directive
- **Putaway Cluster locate** – _At receipt_
  - At Receipt - Location is found and held at the Receipt of the inventory
  - Cluster close - Location is found and held after closing the Cluster
  - User Directed - Location is found at receipt, the inventory is sorted, then the location is removed. Location Directives are run again when the LP is picked up from the Cluster for putaway
    - The putaway work is created without location and during the putaway itself, the user has to scan the LP or Work ID to initiate the Put step. The system finds the put location again and tells the user where to put the picked quantity.
- **Putaway cluster per user** – _No_
  - Restricts the putaway cluster per one user
- **Work unit break** – _Individual_
- **Work template** – _leave blank_
  - Restricts the Putaway cluster profile to a unique Work template
- **Cluster persists as Parent License Plate** – _No_
  - If _Yes_, when the Put step is complete, the Cluster ID will become a Parent License Plate and all items on the Cluster ID will be tied to that Parent license plate.

On the **Cluster sorting** FastTab, putaway sorting criteria can be determined by creating a new line:

- **Sequence number** – determines the sequence the system will sort by. It is added automatically but can be changed.
- **Field name** – _WMSLocationId_
  - Determines what field will this line use for sorting criteria
- **Sorting** – _Ascending_
  - Determines whether sorting should be Ascending or Descending

![Putaway cluster profiles page](media/putaway-clusters-profiles.png "Putaway cluster profiles page")

Additionally, continue with opening the Edit query form of the newly created line and add a desired value to the Range:

1. First line:

    - **Table** – _Work_
    - **Derived table** – _Work_
    - **Field** – _Warehouse_
    - **Criteria** – _61_

1. Second line:

    - **Table** – _Work_
    - **Derived table** – _Work_
    - **Field** – _Work ID_
    - **Criteria** – _leave__blank_

Save the new putaway cluster profile and exit the form.

### Mobile device menu items

Three new mobile device menu items are needed for this functionality. The first one is used to sort the received inventory to a putaway cluster upon receipt, the second one is used to assign multiple license plates to a cluster for putaway, and the third one, which is used to put away the cluster once it has been assigned.

#### MDMI – Receive and Sort Cluster

Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**

Create new mobile device menu item for Receive and Sort Cluster, which will create Inbound Work after receiving the inventory. This where it is indicated that the receiving menu item will be used for Putaway clusters.

> [!NOTE]
> **Sort & assign putaway cluster** can be used with the following menu items:

- PO line receiving,
- PO item receiving,
- Load item receiving.

In **Header** , specify the following:

- Menu item name – _Receive and Sort Cluster_
- Title – _Receive and Sort Cluster_
- Mode – _Work_
- Use existing work – _No_

In **General** FastTab, the following setting can be specified:

- **Work creation process** – _Purchase order item receiving_
- **Generate license plate** – _Yes_
- **Sort & assign putaway cluster** – _Yes_

> [!NOTE]
> The **Sort & assign putaway cluster** parameter is only available on the one-step item receiving.

#### MDMI – Assign cluster

This menu item must only be used if _Assign putaway cluster at receipt_ is not marked for use on the Putaway cluster profile.

Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**

Create new mobile device menu item to be used for Assigning received inventory to a Cluster.

In **Header** , specify the following:

- **Menu item name** – _Assign Cluster_
- **Title** – _Assign Cluster_
- **Mode** – _Indirect_

In **General** FastTab, the following setting can be specified:

- **Activity Code** – _Assign to putaway cluster_

#### MDMI – Cluster Putaway

Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**

Create new mobile device menu item to be used for putting away the Cluster once it has been assigned.

In **Header** , specify the following:

- **Menu item name** – _Cluster putaway_
- **Title** – _Cluster putaway_
- **Mode** – _Work_
- **Use existing work** – _Yes_

In **General** FastTab, the following setting can be specified:

- Directed by – _Cluster Putaway_

In **Work classes** FastTab, set up the valid work class for this mobile device menu item:

- **Work class ID** – _Purchase_
- **Work order type** – _Purchase orders_

### Mobile device menu

Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu** and add the newly created menu items to the desired menu.

## Example scenario procedure

This scenario simulates putaway cluster processing. The setup did not include the standard warehouse configuration required for inbound flow.

### Create Purchase order

Before system directed cluster picking, some inbound orders must be created.

Go to **Accounts payable \> Purchase orders \> All purchase orders**. Select **New** to create a new sales order. Pick any vendor account. On the **General** FastTab, specify warehouse 61.

Sales order 1: Add a new line to the sales order, item A0001, quantity 10 pcs. Add a second line for item A0002, quantity 20 pcs; and a third line for item L0101, quantity 30 pcs.

### Mobile device flow execution

#### Receive the inventory

1. Enter mobile device menu where the _Receive and Sort_ menu item was added during the setup.

1. Select the _Receive and Sort_ menu and initiate the receiving. The mobile device will display the Putaway Cluster profile that the inventory is assigned to.

1. As each Purchase order line is processed, the user is presented with the _"Work completed"_ message on the mobile device and an indication that the _"Work has been sorted to Cluster Putaway"_.

    ![Warehouse app, work completed](media/putaway-clusters-work-completed.png "Warehouse app, work completed")

1. All created Work orders will have a Putaway Cluster Profile ID assigned.

    ![Putaway cluster profile IDs](media/putaway-clusters-work-cluster-profile-id.png "Putaway cluster profile IDs")

#### Assign to Putaway Cluster

Enter mobile device menu where the _Assign to cluster_ menu item was added during the setup.

Select the _Assign to cluster_ menu and initiate next flow.

1. Enter the Cluster ID (or have the system generate one automatically)
1. Add previously created Work IDs/License plates to the Cluster. Repeat for all Work IDs.
    - The user will see a message on the mobile device _"Work was assigned to cluster"_
1. After the last Work has been added to the Cluster, initiate the _Close Cluster._ The user will be presented with the message _"Cluster Close Succesfully"_.
    - Unlike outbound cluster picking, Putaway Clusters do not have maximum number of positions assigned. The user can decide when to close the Cluster manually.

This Cluster is now ready for putaway processing.

#### Cluster putaway

Enter mobile device menu where the _Cluster putaway_ menu item was added during the setup.

Select the _Cluster putaway_ menu and initiate next flow. Remember, the Cluster sorting criteria from the Putaway Cluster Profile setup will be used here to determine the putaway flow.

1. Enter the previously created Cluster ID

1. Pick screen will show the Pick location and under _Items_ field it will state _Multiple_, indicating that multiple items are being picked. Total quantity will reflect the sum of quantity from all Work IDs. At this time, all Work IDs' status will be updated to _In process_

    ![Work in process](media/putaway-clusters-work-in-process.png "Work in process")

1. The Put step will indicate which item(s) should be put to a specific location. The screen will also show which License plates this includes.

    ![Warehouse app, putaway step](media/putaway-clusters-put-step.png "Warehouse app, putaway step")

    The user has the standard option to **Override** or **Pass** this step.

1. Repeat the Put to location process as many times as required. Once finished, the user will be presented with the message _"Cluster completed"_ which indicates the flow has been completed successfully. The work is now _Closed_.

    ![Work closed](media/putaway-clusters-work-closed.png "Work closed")

## Notes and tips

- Another option for one-step receiving and cluster assignment is to set the _Assign Putaway Cluster at Receipt_ on the _Putaway cluster profile_ to _Yes_ and then set the _Putaway Cluster Assignment_ to _Manual_. After the license plate is entered on the receiving screen, the Cluster ID will be requested from the receiver. This eliminates the menu item step _Assign to Putaway Cluster_.
- For the instances where the Cluster ID becomes the Parent LP for a nested pallet, when the Cluster ID is scanned, the Put position is automatically given and no further LP needs to be scanned, even if generating LP is set to be manual.
