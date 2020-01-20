# Change work pool on work

This features adds a **Change work pool** button to the action panel for work items, which makes it easy for warehouse managers to change the work pool of existing work. It enables managers to react quickly to changes on the shop floor and improves their ability to streamline physical processes by changing situations.

<!-- KFM: What do you mean by "improves their ability to streamline physical processes by changing situations"? -->

## Enable the change work pool feature

Before you begin trying to set up or use this feature, you must make sure it's available on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed listed as:

- **Module**: Warehouse management
- **Feature name**: Change work pool on work

<!-- KFM: Add this?: "If you don't see the feature listed here, then it may have become a standard part of the product since this documentation was written, in which case you can proceed with the remaining sections of this topic and all of the described features should be available to you." -->

## Set up the change work pool feature

To use this feature, you must have some work pools set up, and you might also set up your work templates to assign a pool automatically. If you'd like to work through the sample scenario provided later in this topic, then set up your system as described in this section.

### Set up your work pools

Work pools enable you to organize work items by type. To work with the change work pool feature, you must have at least two work pools available. To view and add work pools:

1. Go to **Warehouse management** > **Setup** > **Work** > **Work pools**.

1. If you don't see the work pools you need, then do the following:

    - Select **New** on the command bar to add a new row to the **Work pools** table.
    - Assign a **Work pool ID** to identify the new work pool.

    (If you're working with the **USMF** company demo data and will work through the sample scenario later in this topic, then set the **Work pool ID** to "Webshop" and also add a second work pool with a **Work pool ID** of "CallCenter".)

1. Continue adding work pools as needed.

1. Select **Save** on the command bar.

### Set up your work templates

You can set a default work pool for each of your work templates as needed. All work items generated using a given template will automatically inherit the assigned work pool (if any). To assign a work pool for each template:

1. Go to **Warehouse management** > **Setup** > **Work** > **Work templates**.

1. Select **Edit** on the command bar to put the page into edit mode.

1. For each relevant template, assign a work pool in the **Work pool ID** column.

    (If you're working with the **USMF** company demo data and will work through the sample scenario later in this topic, then set the **62 Pick to pack** template to use the "Webshop" work pool ID.)

1. Select **Save** on the command bar.

## Example scenario

This scenario provides a demo for how to change the stream of processing for an existing work item by changing its work pool. It uses the **USMF** company demo data and each of the settings suggested earlier in this topic.

1. Make sure there's enough quantity on-hand for items A0001 and A0002 in warehouse 62. <!-- KFM: Should we explain how to do this? I don't know how. Maybe just a link? -->

1. Go to **Sales and marketing** > **Sales orders** > **All sales orders**.

1. Select **New** on the command bar to open the **Create sales order** flyout.

1. In the flyout, make the following settings:

    - On the **Customer** FastTab, set **Customer account** to "US-007".
    - On the **General** FastTab, set **Warehouse** to "62".

1. Select **OK** to create the sales order and close the flyout.

1. Your new sales order opens. It should include a new, empty line in the **Sales order lines** table. For this new line, set the **Item number** to "A0001" and the **Quantity** to "2".

1. In the **Sales order lines** FastTab, select **Add line** to add another line to your sales order. This time add **Item number** "A0002" with a **Quantity** of "2".

1. Open the **Warehouse** tab on the action pane and then select **Actions** > **Release to warehouse** to create a new shipment and a new wave. <!-- KFM: when I did this, nothing happened. Do I need to reserve inventory first? -->

1. Go to **Warehouse management** > **Outbound waves** > **Shipment waves** > **All waves**.

1. Find and open the wave that you just created and make sure the shipment listed in teh **Wave lines** FastTab.

1. If you aren't using automatic wave processing, then process the wave to create a work item. <!-- KFM: How do I do this? -->

1. The system now creates a work item in the "Webshop" work pool.

1. Go to **Warehouse management** > **Work** > **Work details**.

1. Select the row for the work you just created.

1. Open the **Work** tab on the action pane and then select **Change Work pool ID** here.

1. The **Change work pool** flyout opens. Select a new work pool from the **Work pool ID** combo box (or, to remove the work item from all work pools, select and delete all the text in the combo box).

1. Select **OK** to apply your setting, close the flyout, and return to the work list. Note that the work item now shows your newly selected value in the **Work pool ID** column.

> [!NOTE]
> In addition to switching work pools, you can also use this procedure to add a work pool to any work item that doesn't have one or remove a work pool from any work item that does have one.
