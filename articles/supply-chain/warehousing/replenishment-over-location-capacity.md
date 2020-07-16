---
# required metadata

title: Replenishment over location capacity
description: Some high-volume or space-constrained warehouses need to ship more quantity of an item in a day than what will fit in the picking location. Replenishment over location capacity allows all replenishment work to be created that will be needed for the day and manages availability of the replenishment work to ensure that the pick location doesn't run out of inventory, but also doesn't go above capacity.
author: mirzaab
manager: tfehr
ms.date: 07/16/2020
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
ms.search.validFrom: 2020-07-16
ms.dyn365.ops.version: Release 10.0.7
---

# Replenishment over location capacity

[!include [banner](../includes/banner.md)]

Some high-volume or space-constrained warehouses need to ship more quantity of an item in a day than what will fit in the picking location. *Replenishment over location capacity* allows all replenishment work to be created that will be needed for the day and manages availability of the replenishment work to ensure that the pick location doesn't run out of inventory, but also doesn't go above capacity.

The features allow more replenishment work to be created than will fit in a location and will block replenishment work from being completed once the location is full. As inventory in the pick location drops below a configurable threshold, more replenishment work will be made available.

## Enable the Replenishment over location capacity feature

To make this feature available, enable the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in order):

1. *Organization-wide work blocking*
1. *Replenishment over location capacity*

## Set up the feature for the example scenario

This section provides guidelines and an example of how to set up this feature and prepare sample data to be used with the example scenario given later in this topic.

### Enable sample data

To work through the [example scenario](#example-scenario) using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

### Location profile

Enable the replenish over capacity functionality on the location profile.

1. Go to **Warehouse management > Setup > Warehouse > Locations profiles**
1. On the list pane, select **PICK-06**
1. In the Action Pane, select **Edit**
1. In the **Replenishment** FastTab, make the following settings:
    - **Exceed Location Capacity** - *Yes*
        - This parameter dictates whether the replenishment overflow functionality is turned on or off.
        - When enabled, the maximum capacity of the location will be allowed to be exceeded by replenishment work.
    - **Work availability threshold type** - *Quantity*
        - What method is used for determining when to release more work. You can release by either *Quantity* or *Percent*
            - Percent uses a percentage capacity based on stocking limits or volumetrics.
            - Quantity uses a specific quantity value.
    - **Overflow quantity** - *0.65*
        - Quantity at which the location overflows. Work will be available whenever the sum of *location on hand* and *work quantity* is below this value.
        - Any replenishment work above this value will be blocked, and will have to be unblocked manually.
        - Any location stocking limits will be taken into consideration when calculating the work quantity.

    - **Overflow unit** - *PL*
        - Unit associated with the overflow quantity.
        - This will make more replenishment work available when the location gets down to 0.65 PL.

    - **Overflow percentage**
        - This field is only enabled when the **Work availability threshold type** - *Percent* is selected.
            - Percentage at which the location overflows. Work will be available whenever the sum of *location on hand* and *work quantity* is below this percentage.
            - Any replenishment work quantity percentage above this value will be blocked, and will have to be unblocked manually.
            - Any location stocking limits will be taken into consideration when calculating the work quantity percentage.
            - If no location stocking limits are defined, work quantity percentage will be calculated by volume if volume constraints are defined on location profile.

> [!IMPORTANT]
> If you are using the demo data for USMF and have previously enabled the feature *Location license plate positioning*, you must disable the setting **Enable license plate positioning** on the **BULK-06** location profile to complete the mobile steps given later in th example scenario.

>[!TIP]
>
>**Work available threshold type: Quantity**
>
>Use this option when you aren't using volumetric for the locations being replenished, or you have consistent quantities at which you want to let more inventory be brought to the location.
>
>If this option is selected, populate the **Overflow quantity** and **Overflow unit** fields with the quantity and unit that will be used to control when more replenishment work is made available.
>
>**Work available threshold type: Percent**
>
>If the picking locations use volumetric, then you can use the *Percent* option.
>
>Set the **Overflow percentage** field to the percentage at which more replenishment work will be made available.

### Wave step code

> [!NOTE]
> To set up a wave step code as described here, you may first need to use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable the feature called *Organization wide wave step code*.

1. Go to **Warehouse Management > Setup > Waves > Wave step codes**
1. Select **New** and enter the following:
    - **Wave step code** – *Replen*
    - **Wave step description** – *Replenishment*
    - **Wave step type** - *Replenishment*

1. Select **Save**

### Replenishment template

Replenishment templates are a set of rules that control when and how to replenish a location.

1. Go to **Warehouse management > Setup > Replenishment > Replenishment templates**
1. Select **Edit** in the Action Pane.
1. In the **Overview** section, focus on the line with **Replenish template** - *Demand replenish*
1. Make the following settings:
    - **Wave step code** - *Replen*
    - **Allow wave demand to use unreserved quantities** - *Yes* (selected)

1. Select **Save**

### Wave template

When **Automate replenishment work release** is set to *Yes*, it will create demand-based replenishment work and release it automatically. You must add the replenishment wave method to the wave template and create a replenishment template of the type *Wave demand*.

1. Go to **Warehouse management > Setup > Waves > Wave templates**.
1. On this list pane, set **Wave template type**  to *Shipping*.
1. Select template **61 Shipping** in the list.
1. Select **Edit** on the Action Pane.
1. On the **General** FastTab, make the following setting:
    - **Automate replenishment work release** - *Yes*  
        Select this option to create demand-based replenishment work and release it automatically. You must add the replenishment wave method to the wave template, and create a replenishment template of the type Wave demand. Set up a replenishment template in the Replenishment templates page. This requires that you add the replenish method to the wave template.

1. On the **Methods** FastTab, in the **Selected methods** column, edit the **Wave step code** on the following line:
    - **Method name** - *replenish*
    - **Name** - *Replenishment*
    - **Wave step code** - *Replen*

1. Select **Save**.

## Example Scenario

Once you have enabled and set up all the sample data described previously in this topic, work through this scenario to try out the feature. The values shown in this scenario assume you are working with the standard demo data, have selected the **USMF** legal entity, and have prepared the sample records described earlier in this topic. This scenario also serves as an example of how to use the feature in a production setting.

### Create replenishment work

#### Create sales order 1

1. Go to **Sales and Marketing > Sales orders > All sales orders**
1. Select **New** in the Action Pane to open a dialog box for creating a new sales order.
1. In the dialog box, enter the following:
    - **Customer account** - *US-007*
    - **Warehouse** - *61*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It includes a new empty line on the **Sales order lines** FastTab. On this line, enter the following:
    - **Item number** - *T0100*
    - **Quantity** - *40*

1. On the **Sales order lines** toolbar, select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**.
1. Close the page.
1. On the Action Pane, open the **Warehouse** tab and then select **Release to warehouse**.
1. Informational messages will be displayed indicating wave and shipment IDs created, a replenishment wave is also created.
    - Note a Warning message is also displayed indicating that: "Work ID XXXX cannot be unblocked because it has unfinished replenishment work."

#### Create sales order 2

1. Remain at **Sales and Marketing > Sales orders > All sales orders**
1. Select **New** in the Action Pane to open a dialog box for creating a new sales order.
1. In the dialog box, enter the following:
    - **Customer account** - *US-001*
    - **Warehouse** - *61*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It includes a new empty line on the **Sales order lines** FastTab. On this line, set the following values:
    - **Item number** - *T0100*
    - **Quantity** - *60*

1. On the **Sales order lines** toolbar, select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**.
1. Close the page.
1. On the Action Pane, open the **Warehouse** tab and then select **Release to warehouse**.
1. Informational messages will be displayed indicating wave and shipment IDs created, a replenishment wave is also created.
    - Note a Warning message is also displayed indicating that: "Work ID XXXX cannot be unblocked because it has unfinished replenishment work."

#### Create sales order 3

1. Remain at **Sales and Marketing > Sales orders > All sales orders**
1. Select **New** in the Action Pane to open a dialog box for creating a new sales order.
1. In the dialog box, enter the following:
    - **Customer account** - *US-004*
    - **Warehouse** - *61*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It includes a new empty line on the **Sales order lines** FastTab. On this line, set the following values:
    - **Item number** - *T0100*
    - **Quantity** - *30*
1. On the **Sales order lines** toolbar, select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**.
1. Close the page.
1. On the Action Pane, open the **Warehouse** tab and then select **Release to warehouse**.
1. Informational messages will be displayed indicating wave and shipment IDs created, a replenishment wave is also created.
    - Note a Warning message is also displayed indicating that: "Work ID XXXX cannot be unblocked because it has unfinished replenishment work."

#### View work details

1. Go to **Warehouse management > Work > Work details**.
1. In the **Overview** section, filter the **Warehouse** column for *61*.
1. You should see that seven work IDs were created for the three demand sales orders, three with a **Work order type** of *Replenishment* and four  with a **Work order type** of *Sales orders*.
    - Sales order 1 will have two work IDs created.
    - Make note of the **Work ID** for the sales orders.
1. All three work IDs with a **Work order type** of *Replenishment* should have the same *Pick* and *Put* locations in the **Lines** section:
    - **Pick** - *02A01R5S1B*
    - **Put** - *06A01R2S1B*

Depending on your on-hand quantities, the created **Work quantities** might vary slightly from case to case, but overall the created work headers should match this scenario example.

#### On-hand inventory license plate ID

Later in this scenario, you will work using the warehouse app (or an emulator), where you'll need to identify the *License plates* to complete the picking and replenishment scenarios.

To find the license plate IDs you'll need later:

1. Go to **Inventory management > Inquiries and reports > On-hand list**.
1. Select the **Show filters** button to open the filter pane. Enter the following filter criteria to get the license plates for the scenario (use the *begins with* filter):
    - **Item number** - *T0100*
    - **Warehouse** - *61*

1. Select **Apply**.

1. On the Action Pane, select **Dimensions** to open the **Dimensions display** dialog box. In the **Storage Dimensions** section of the dialog box, select all the values. In the **Transactions** section, select **Item number** and **Quantity <> 0**. Select **OK** when done.

1. In the **On-hand** grid, note the license plate numbers for item *T0100* in each of the locations. Note which license plate is in each location, you will need this later.

1. Close the page.

### Process steps

Perform the warehouse location replenishment for the first two work IDs. Work on the third replenishment work will be blocked until the picking location inventory level falls below the threshold.

#### Replenishment

1. Sign in to the warehouse app as a user in warehouse **61** (**User ID** *61*, **Password** *1*).
1. Go to **Inventory > Replenishment**.
1. You will be prompted to complete the first replenishment work. The item number, quantity, and location to pick from are displayed.

1. In the **LP** field, enter the *License plate* number for the item in the location that is displayed.
1. Select the **OK** button ( ✔ ).
1. A system generated **Target LP** number is generated for the new license plate for the picked item.
1. Select **OK** to confirm.
1. Put work is displayed to put the target license plate into the replenishment location.
    - The Put location should be **06A01R2S1B**.

1. Confirm the put details and select **OK**.
1. A message **Work Completed** is displayed along with the details of the next replenishment pick task.
    - The item number, quantity, and location to pick from are displayed.
    - The pick location will be the same as the first replenishment location, therefore, the license plate will be the same license plate ID used for the first replenishment work task.

1. Complete the replenishment work for the second work task as you did for the first.
    - The quantity and Target LP will be different.

After the completion of the second replenishment work, the mobile device will display a message that is **Work Completed** and there is **No Work Available**, even though some replenishment work is remaining. This is because the replenishment work has an availability status of *Held* and is therefore marked as **Blocked**.

This status was triggered because the picking location's location profile (which the work is being assigned to) has an **Overflow quantity** of *0.65 PL* (Pallet). The previous two replenishment work tasks filled the location near its overflow limit for the Item T0100 (the unit conversion for the item is *1 PL = 100 ea*). The remaining replenishment work would put the location over the over flow quantity.

Until inventory is picked from the location that brings it below the work release threshold on the mobile device menu item, this replenishment will remain **Blocked**.

#### Sales order pick

Before the remaining replenishment work task can be completed, the picking location must be depleted of inventory to a level that supports unblocking the remaining replenishment work. This means that the quantity of the inventory on-hand in the location plus the replenishment quantity cannot exceed the **Overflow quantity**. When the combination is less than the overflow, the remaining replenishment will be unblocked.

1. Sign in to the warehouse app as a user in warehouse **61** (**User ID** *61*, **Password** *1*).
1. Go to **Outbound > Sales Picking**.
1. Enter the first **Work ID** for sales order 1.
    - Refer to the work IDs for sales orders from the **Work details** page.
    - This work ID will generate pick work from two separate locations, a quantity of 10 ea.

1. Select **OK**.
1. The **Sales orders: Pick** task screen opens.
    - The item number, quantity, and location to pick from the first location are displayed.

1. In the **LP** field, enter the *License plate* number for the item in the location that is displayed.
1. Select the **OK** button ( ✔ ).
1. The **Sales orders: Pick** task screen opens.
    - The item number, quantity, and location to pick the next location from are displayed.

1. In the **LP** field, enter the *License plate* number for the item in the location that is displayed.
1. Select the **OK** button ( ✔ ).
1. The **Sales orders: Put** screen is displayed with the instructions to put away to the outbound staging location both of the picking work completed.
1. Select **OK**.
1. A message **Work Completed** is displayed on the screen.
1. Enter the second **Work ID** for sales order 1.
    - There is only one pick task for this work ID.

1. Select **OK**.
1. The **Sales orders: Pick** task screen opens.
    - The item number, quantity, and location to pick from are displayed.

1. In the **LP** field, enter the license plate number for the item in the location that is displayed.
    - The license plate to enter will be one of the system-generated license plates from the replenishment work tasks. Check the **On-hand list** inventory for the item, location, and quantity to capture the correct license plate ID.

1. Select the **OK** button ( ✔ ).
1. Confirm the instructions for the put task to the outbound staging location.
1. Select **OK**.
1. A message **Work Completed** is displayed on the screen.

Sales order 2 is blocked from picking because the replenishment task it is linked to isn't complete. At this time, there is still a quantity of 30 ea in the picking location, the replenishment quantity for sales order 2 is 60 ea. The combination of the on-hand inventory and the replenishment inventory (90 ea) is greater than the overflow quantity of 0.65 PL (or 65 ea). Before the replenishment work can be completed, sales order 3 must be picked.

1. Enter the **Work ID** for sales order 3.
    - There is only one pick task for this work ID.

1. Select **OK**.
1. The **Sales orders: Pick** task screen opens.
    - The item number, quantity, and location to pick from are displayed.

1. In the **LP** field, enter the license plate number for the item in the location that is displayed.
    - The license plate to enter will be  one of the system-generated license plates from the replenishment work tasks. Check the **On-hand list** inventory for the item, location, and quantity to capture the correct license plate ID.

1. Select the **OK** button ( ✔ ).
1. Confirm the instructions for the put task to the outbound staging location.
1. Select **OK**.
1. A message **Work Completed** is displayed on the screen.

As soon as the pick location on-hand quantity plus the replenishment quantity is below the threshold, you will be able to process the remaining replenishment work.

View **Work details** again, and the replenishment work availability for the final piece of replenishment (for sales order 2) will be *Open*, as there is now enough space in the location to accept the replenishment.

You can now process this replenishment work via the mobile device.

1. Go to **Inventory > Replenishment**.
1. You will be prompted to complete the remaining replenishment work.
    - The item number, quantity, and location to pick from are displayed.

1. In the **LP** field, enter the *License plate* number for the item in the location that is displayed.
1. Select the **OK** button ( ✔ ).
1. A system-generated **Target LP** number is generated for the new license plate for the picked item.
1. Select **OK** to confirm.
1. Put work is displayed to put the Target LP into the replenishment location.
    - The Put location should be **06A01R2S1B**.

1. Confirm the Put details, select **OK*.
1. The messages **Work Completed** and **No Work Available** are displayed.

Now it is possible to pick sales order 2, it became unblocked once the replenishment work linked to the sales order was completed.

1. Enter the **Work ID** for sales order 2.
    - There is only one pick task for this work ID.

1. Select **OK**.
1. The **Sales orders: Pick** task screen opens.
    - The item number, quantity, and location to pick from are displayed.

1. In the **LP** field, enter the *License plate* number for the item in the location that is displayed.
    - The license plate to enter will be the system-generated license plate from the replenishment work task. Check the **On-hand list** inventory for the item, location, and quantity to capture the correct license plate ID.

1. Select the **OK** button ( ✔ ).
1. Confirm the instructions for the Put task to the outbound staging location.
1. Select **OK**.
1. A message **Work Completed** is displayed on the screen.

## Notes and tips

- This functionality works with all types of replenishment (wave demand, min/max, load demand, and slotting)
- The replenishment work availability for each work header can be manually overridden from the work details screen if desired
- The system will take any inventory already in the location before any work is completed into account when setting the replenishment work availability.
- Each piece of sales order work is linked to a specific replenishment work, there is no corresponding *Sales work availability* functionality.
