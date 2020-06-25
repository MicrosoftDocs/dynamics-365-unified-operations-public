---
# required metadata

title: Change work pool on work
description: Learn how to use the "Change work pool" button for work items to change the work pool of existing work.
author: mirzaab
manager: AnnBe
ms.date: 02/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: global
# ms.search.industry:
ms.author: mirzaab
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Release 10.0.8
---

# Change work pool on work

Use work pools to organize work into groups. For example, you can create a work pool to classify work that occurs in a particular warehouse location.

This features adds a **Change work pool** button to the Action Pane for work items, which makes it easy for warehouse managers to change the work pool of existing work. It enables managers to react quickly to changes on the warehouse shop floor and improves their ability to adapt to changing situations and the need of transferring work to another work pool.

## Enable the change work pool feature

Before you begin trying to set up or use this feature, you must make sure it's available on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed listed as:

- **Module**: *Warehouse management*
- **Feature name**: *Change work pool on work*

## Set up the change work pool feature

To use this feature, you must have some work pools set up, and you might also set up your work templates to assign a pool automatically. If you'd like to work through the example scenario provided later in this topic, then set up your system as described in this section.

### Set up your work pools

Work pools enable you to organize work items by type. To work with the change work pool feature, you must have at least two work pools available. To view and add work pools setup the following:

1. Go to **Warehouse management > Setup > Work > Work pools**.
1. If you're working with the **USMF** company demo data and will work through the example scenario later in this topic, then add the following:
     - **Work pool ID** - *Webshop*, **Description** - *Web Shop*
     - **Work pool ID** - *CallCenter*, **Description** - *Call Center*

1. Select **Save** on the Action Pane.

### Set up your work templates

You can set a default work pool for each of your work templates as needed. All work items generated using a given template will automatically inherit the assigned work pool (if any). For each relevant template, assign a work pool in the **Work pool ID** column. If you're working with the **USMF** company demo data and will work through the example scenario later in this topic, then add the following:

1. Go to **Warehouse management > Setup > Work > Work templates**.
1. Select **Edit** on the Action Pane to put the page into edit mode.
1. Edit the template as follows:
    - **Work template** - *62 Pick to pack*
    - **Work pool ID** - *Webshop*

1. Select **Save**.

## Example scenario

This scenario provides a demonstration for how to change the stream of processing for an existing work item by changing its work pool. It uses the **USMF** company demo data and each of the settings suggested earlier in this topic.

### Create a sales order and release to warehouse

1. Confirm that there is enough quantity on-hand for **Item** *A0001* and **Item** *A0002* in **Warehouse** *62*.
1. To confirm quantities, go to **Inventory management > Inquiries and reports > On-hand list**. Edit the **Filters** as follows:
    - **Warehouse** begins with - *62*
    - **Item number** is one of - *A001*, *A002*

    Demo data should have a quantity of 10 each.

1. Create a sales order.
1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select **New** on the Action Pane.
1. The **Create sales order** dialog box opens, enter the following:
    - **Customer account** - *US-007*
    - **Warehouse** - *62*

1. Select **OK** to create the sales order and close the dialog box.
1. Your new sales order opens. It should include a new, empty line in the **Sales order lines** FastTab.
1. On this new line, enter the following:
    - **Item number** - *A0001*
    - **Quantity** - *2*

1. On the **Sales order lines** FastTab toolbar, select **Inventory** \> **Reservation**.
1. On the **Reservation** page select **Reserve lot** on the Action Pane to reserve the inventory.
1. Close the page.
1. On the **Sales order lines** FastTab toolbar, select **Add line** to add another line to your sales order. Enter the following:
    - **Item number** - *A0002*
    - **Quantity** - *2*

1. On the **Sales order lines** FastTab toolbar, select **Inventory** \> **Reservation**.
1. On the **Reservation** page select **Reserve lot** on the Action Pane to reserve the inventory.
1. Close the page.
1. On the Action Pane select the **Warehouse** tab.
1. Then select **Release to warehouse**.
1. Informational messages are displayed with the **Wave ID** and **Shipment ID** created from the release. Make note of the **Wave ID**.

### Outbound Wave

1. Go to **Warehouse management > Outbound waves > Shipment waves > All waves**.
1. In the table, search for the **Wave ID** created from the release of the sales order.
1. Select the wave ID you just created to view the details.
1. On the **Wave lines** FastTab, ensure there is a **Shipment ID** listed for the sales order.

    > [!TIP]
    > If **Process wave at release to warehouse** is set to *No* on the **Wave template** setup for the shipping wave template, then you will need to manually **Process** the wave from **Wave** in the Action Pane to create work.

1. Make sure that the wave has been processed. This creates the required work.

### View work details and change the work pool

To see the work created and to manage the work pool, go to to the **Work details** page.

1. Go to **Warehouse management > Work > Work details**.
1. Select the row for the work you just created.
    - The sales order number will be displayed in the **Order number** column.

1. The **Work pool ID** field will be populated the work pool ID setup on the work template.
    - If you do not see the **Work pool ID** field, add the column to the grid and refresh the page.

1. To change the work pool associated with this **Work ID**, select the **Work** tab on the Action Pane, and then select **Change Work pool ID**.
1. The **Change work pool** dialog box opens.
1. In the **Parameters** FastTab select the following:
    - **Work pool ID** - *CallCenter*

1. Select **OK** to apply the change.
1. Note that the **Work pool ID** has now been changed to *CallCenter*.

> [!IMPORTANT]
> The **Work pool ID** may default to blank when the dialog box opens. If you select **OK** to apply changes and the field is blank, you will remove the work pool completely from the work.
>
> In addition to switching work pools, you can also use this procedure to add a work pool to any work item that doesn't have one or remove a work pool from any work item that does have one.
