---
# required metadata

title: Planned cross docking
description: XXXX
author: XXXX
manager: tfehr
ms.date: mm/dd/yyyy
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
ms.author: XXXX
ms.search.validFrom: yyyy-mm-dd
ms.dyn365.ops.version: Release 10.0.xx
---

# Planned cross docking

[!include [banner](../includes/banner.md)]

This functionality introduces advanced planned cross docking where the inventory quantity required to satisfy an order will be directed to the correct outbound dock or staging area straight from receipt or creation. All remaining inventory from the inbound source will be directed to the correct storage location through regular put away process. This warehouse process is called cross docking.

Cross docking therefore allows the worker to skip inbound put away and outbound picking of inventory that is already marked to an outbound order. The result is minimized number of touches of inventory where possible, together with greater time and space savings on the warehouse shop floor due to less interaction with the system.

Prior to execution, the user must configure new cross dock template where the supply source as well as other sets of requirements for cross docking are specified. As the outbound order is created, the line must be marked against an inbound order containing identical item.

At the time of inbound order receiving, cross docking setup will automatically identify the need for a cross dock and create the movement work for required quantity based on location directive setup.

> [!NOTE]
> The inventory transactions will *not* get unregistered when cancelling cross-dock work, even though the setting to do so has been enabled under the warehouse management parameters.

## Enable the Planned cross feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Planned cross docking*

## Setup

### Regenerate Load Posting Methods

Planned cross docking is implemented as a **Load posting method**. After enabling the feature you need to regenerate the methods.

1. Go to **Warehouse management > Setup > Load posting methods**.
1. Select **Regenerate methods** from the Toolbar.
1. When regeneration is completed you will see a **Method name** of **planCrossDocking**.
1. Close the form.

### Cross Dock Template

1. Go to **Warehouse management > Setup > Work > Cross docking templates**.
1. On the Action Pane select **New** to create a new template.
1. Enter the following in the header:
    - **Sequence** – *1* (Sets the order in which the templates will evaluated.)
    - **Cross docking template ID** – *51*
    - **Description** – *Warehouse 51*
    - **Demand release policy** – *Before supply receipt*
    - **Warehouse** – *51*

1. The setups in the **Planning** FastTab controls how the template will work.
1. Enter the following:
    - **Demand requirements** – *None*  
        Requirements of the demand inventory. Use *Marking* if the demand is required to be linked to the supply prior to release. Use *Order reservation* if the demand is required to be order reserved against the supply prior to release.
    - **Locating type** – *Shipment locations*  
        Should the cross dock work use the staging/load locations from the shipment, or use location directives to find its own.
    - **Work template** – *Blank*  
        Work template that will be used when creating cross dock work.
    - **Revalidate on supply receipt** - *No*  
        Should the supply be revalidated during receipt? If enabled, both the maximum window and expiration days range will be checked.
    - **Validate time window** – *Yes*  
        Should the maximum time window be evaluated when selecting a supply source? If enabled the Maximum  Window and Minimum Window fields are enabled.
    - **Maximum time window** – *5*  
        Maximum time period between the supply arrival and demand departure that is allowed.
    - **Maximum time window unit** – *Days*
    - **Minimum time window** – *0*  
        Minimum time period between the supply arrival and demand departure that is allowed.
    - **Minimum time window unit** – *Days*
    - **Expiration days range** – *0*  
        *FEFO Criteria*: Maximum number of days between the expiration date of the first expiring batch currently in the warehouse and the batch being received.

1. In the **Supply sources** FastTab you specify what types of supply are valid for this template.
1. Select **New** from the Toolbar and enter the following:
    - **Sequence number** - *1*
    - **Supply source** - *Purchase order*

### Work Class

1. Go to **Warehouse management > Setup > Work > Work classes**.
1. In the Action Pane select **New** to create a new work class.
1. Enter the following:
    - **Work class ID** – *CrossDock*
    - **Description** – *Cross Dock*
    - **Work order type** – *Cross docking*

### Work template

1. Go to **Warehouse management > Setup > Work > Work templates**.
1. In the header, set **Work order type** - *Cross docking*.
1. Select **New** on the Action Pane.
1. On the **Overview** tab enter the following on the new line:
    - **Sequence number** – *1*
    - **Work template** – *51 Cross Dock*
    - **Work template description** – *51 Cross Dock*
1. Select **Save** to enable the *Work Template Details* section.

1. In the **Work Template Details** Toolbar, select **New** to add a line and enter the following:
    - **Work type** – *Pick*
    - **Work class ID** – *CrossDock*

1. Select **New** to add another line and enter the following:
    - **Work type** – *Put*
    - **Work class ID** – *CrossDock*

1. Select **Save** and confirm that the **Valid** field on the *51 Cross Dock* template is selected.

> [!NOTE]
> The **Work class ID**'s for the *Pick* and *Put* Work type's must be the same.

### Location directives

1. Go to **Warehouse management > Setup > Location directives**.
1. In the left side column, set **Work order type** to *Cross docking*.
1. In the Action Pane, select **New** and enter the following:
    - **Sequence number** – *1*
    - **Name** - *51 Cross Dock Put*
    - **Work type** - *Put*
    - **Site** - *5*
    - **Warehouse** - *51*
1. Select **Save** to enable the **Lines** FastTab.

1. In the **Lines** Toolbar, select **New** to add a line. Enter the following:
    - **From quantity** - *1*
    - **To quantity** - *1,000,000*
    - Select **Save** to enable the **Location Directive Actions** FastTab.

1. In the **Location Directive Actions** Toolbar, select **New** to add a line. Enter the following:
    - **Name** - *Baydoor*
    - **Fixed location usage** - *Fixed and non-fixed locations*
1. Select **Save** to enable **Edit query**.

1. On the **Range** tab in the query, ensure the following is configured:
    - Line 1
        - **Table** - *Locations*
        - **Derived Table** - *Locations*
        - **Field** - *Warehouse*
        - **Criteria** - *51*

    - Line 2
        - **Table** - *Locations*
        - **Derived Table** - *Locations*
        - **Field** - *Location*
        - **Criteria** - *Baydoor*
1. Select **OK**.

### Mobile device menu item

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **Purchase Put-away** from the list of menu items in the left column.
1. Select **Edit**.
1. In the **Work classes** FastTab, select **New** on the Toolbar to add a new line and enter the following:
    - **Work class ID** - *CrossDock*
    - **Work order type** - *Cross docking*

1. Select **Save**.

## Scenario

### Purchase order

Create a purchase order as a source of supply.

1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**.
1. Select **New** from the Action Pane.
1. On the **Create purchase order** pane, enter the following:
    - **Vendor account** - *104*
    - **Warehouse** - *51*
1. Select **OK** and make note of the order number.

1. A new line is added to the **Purchase order lines** FastTab. Enter the following:
    - **Item number** - *A0001*
    - **Quantity** - *5*

### Sales order

Create a sales order as a source of demand.

1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select **New** from the Action Pane.
1. On the **Create sales order** pane, enter the following:
    - **Customer account** - *US-002*
    - **Warehouse** - *51*
1. Select **OK**.

1. A new line is added to the **Sales order lines** FastTab. Enter the following:
    - **Item number** - *A0001*
    - **Quantity** - *3*

### Create planned cross dock

Create the planned cross docking from the sales order.

1. On the Action Pane of the sales order you just created, select the **Warehouse** tab then, in the **Actions** group, select **Release to warehouse**.
1. An informational messages is displayed.
    - This will create a shipment and load line for the sales order line and attempt to allocate inventory.
    - You will also see a warning message: "No work was created for wave XXXX. See the work creation history log for details." This is expected because there is no inventory in the warehouse.

1. On the **Sales order lines** FastTab, open the **Warehouse** menu and select **Shipment details** from the menu list.
1. The **Shipment details** page opens displaying the shipment created for the sales order.
1. In the **Load lines** FastTab, notice that the **Planned cross docking quantity** field is set to *3*. Because there was no inventory available in the warehouse, but there is a valid supply source arriving within the window defined on the cross docking template, the cross docking quantity was created.

1. At the top of the **Load lines** FastTab, select **Planned cross docking** to see the details of the cross docking that was created.

## Process the cross dock

### PO receiving on warehousing mobile app

The system will receive the quantity of 5 from the purchase order into the receiving location, and create two pieces of work.

The first **Work ID** created is with **Work order type** of *Cross docking* and is linked to the sales order. It has a quantity of 3 and is directed to the final shipping location to be immediately shipped out.

The second **Work ID** created is with **Work order type** of *Purchase orders* and is linked to the purchase order. It has the remaining quantity of 2 that was not cross docked and is directed to put away to storage.

1. Sign in to the mobile device as a user in **Warehouse** *51*.
1. Go to **Inbound > Purchase Receive**.
    - In the **PONum** field, enter your purchase order number.
    - In the **QTY** field, enter *5*.
    - Select **OK**.
    - On the next screen, set the **Item** to *A0001*.
    - Select **OK**.
    - On the next screen, confirm the **PONum**, **Item** and **Qty** by selecting **OK**.
    - The message "Work Completed" is displayed.

1. Select **Cancel** to exit.

### Put away to cross dock and bulk

Both work ID's currently have the same target license plate. You will need to get the work ID and target licence plate ID to complete the next steps. You can get this from the work details for the purchase order line and sales order line. Alternately, you can go to **Warehouse management > Work > Work details** and filter the work for where **Warehouse** is *51*.

1. On the mobile device, go to **Inbound > Purchase put-away** and enter the target license plate from the work.
1. In the **ID** field, enter the target license plate ID from the work details. <!-- KFM: Continue here --> The cross docking - Pick form will display the picking location (RECV), Target LP (License plate), Item (A0001) and quantity (3).

1. Select **OK**
1. Next enter a **Target LP** for the licence plate ID that will be put (cross docked) to the shipping location. Select a license plate ID of your choosing.

1. Select **OK**.
1. On the next screen, enter the *Target license plate ID* in the **ID** field and select **OK**.
1. Confirm the work for picking the remaining quantity of 2, select **OK**.
1. Select **Done** on the next screen to end the picking process and begin the put away process.
1. The screen will present you with the location and license plate to put the item.
1. Confirm the bulk storage **Put** by selecting **OK**.
1. Confirm the cross docking **Put** by selecting **OK** on the next screen. The message "Work Completed" is displayed.

1. Select **Cancel** to exit.

The following screen shot shows an example of how the completed cross-docking work might appear in Dynamics 365 Supply Chain Management.

![Cross docking work completed](media/PlannedCrossDockingWork.png "Cross docking work completed")
