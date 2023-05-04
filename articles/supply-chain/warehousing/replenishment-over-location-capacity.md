---
# required metadata

title: Replenishment over location capacity
description: This article provides information about the Replenishment over location capacity feature. This feature enables all replenishment work that will be required for the day to be created and manages availability of that replenishment work to ensure that the picking location neither runs out of inventory nor goes above capacity. 
author: Mirzaab
ms.date: 07/16/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSReplenishmentTemplates, WHSLocationLimit
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-16
ms.dyn365.ops.version: 10.0.7
---

# Replenishment over location capacity

[!include [banner](../includes/banner.md)]

Some high-volume or space-constrained warehouses must ship more quantity of an item in a day than will fit in the picking location. The *Replenishment over location capacity* feature enables all replenishment work that will be required for the day to be created and manages availability of that replenishment work to ensure that the picking location neither runs out of inventory nor goes above capacity.

The feature enables more replenishment work to be created than will fit in a location, and it blocks replenishment work from being completed when the location is full. As inventory in the picking location drops below a configurable threshold, more replenishment work is made available.

## Turn on the Replenishment over location capacity feature

To make this feature available, turn on the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in this order):

1. *Organization-wide work blocking* (As of Supply Chain Management version 10.0.21, this feature is mandatory and can't be turned off again.)
1. *Replenishment over location capacity* (As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off again.)

## Set up the feature for the example scenario

This section provides guidelines and an example that shows how to set up this feature and prepare sample data for the example scenario that is provided later in this article.

### Enable sample data

To work through the [example scenario](#example-scenario) by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

### Location profile

Enable the replenish over capacity functionality on the location profile.

1. Go to **Warehouse management \> Setup \> Warehouse \> Locations profiles**.
1. In the left pane, select **PICK-06**.
1. On the Action Pane, select **Edit**.
1. On the **Replenishment** FastTab, set the following values:

    - **Exceed Location Capacity:** *Yes*

        When enabled, the maximum capacity of the location will be allowed to be exceeded by replenishment work. This also enables other fields on the **Replenishment** FastTab.

    - **Work availability threshold type:** *Quantity*

        This field defines the method that is used to determine when more work should be released. You can release by either quantity or a percentage:

        - *Percent* – Select this option to use percentage capacity that is based on stocking limits or volumetrics. Selecting this option enables the **Overflow percentage** field, and disables the two quantity related fields,  **Overflow quantity** and **Overflow unit**.

            You can use this option if the picking locations use volumetrics.

            If this option is selected, set the **Overflow percentage** field to the percentage at which more replenishment work will be made available.

        - *Quantity* – Select this option to use a specific quantity value. Selecting this option disables the **Overflow percentage** field and enables **Overflow quantity** and **Overflow unit** fields.

            Use this option when you aren't using volumetrics for the locations that are being replenished, or when you have consistent quantities at which you want more inventory to be brought to the location.

           If this option is selected, set the **Overflow quantity** and **Overflow unit** fields to the quantity and unit at which more replenishment work will be made available.

    - **Overflow quantity:** *0.65*

        This field defines the quantity at which the location overflows.

        Work will be available whenever the sum of the on-hand quantity in the location and the work quantity is below this value. Any replenishment work above this value will be blocked and must be manually unblocked.

        Location stocking limits are considered when the work quantity is calculated.

    - **Overflow unit:** *PL*

        This field defines the unit that is associated with the overflow quantity.

        In this case, more replenishment work will be made available when the location gets down to 0.65 pallet (PL).

    - **Overflow percentage**

        This field defines the percentage at which the location overflows.

        Work will be available whenever the sum of the on-hand quantity in the location and the work quantity is below this percentage. Any replenishment work quantity percentage above this value will be blocked and must be manually unblocked.

        Location stocking limits are considered when the work quantity percentage is calculated. If no location stocking limits are defined, the work quantity percentage is calculated by volume if volume constraints are defined for the location profile.

> [!IMPORTANT]
> If you're using the demo data for the **USMF** legal entity and previously turned on the *Location license plate positioning* feature, you must turn off the **Enable license plate positioning** setting for the **BULK-06** location profile to complete the mobile steps in the example scenario.

### Wave step code

> [!NOTE]
> To set up a wave step code as described here, you might first have to use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to turn on the feature that is named *Organization wide wave step code*. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off.

1. Go to **Warehouse Management \> Setup \> Waves \> Wave step codes**.
1. Select **New**, and set the following values:

    - **Wave step code:** *Replen*
    - **Wave step description:** *Replenishment*
    - **Wave step type:** *Replenishment*

1. Select **Save**.

### Replenishment template

Replenishment templates are a set of rules that control when and how a location is replenished.

1. Go to **Warehouse management \> Setup \> Replenishment \> Replenishment templates**.
1. On the Action Pane, select **Edit**.
1. In the **Overview** section, select the line where the **Replenish template** field is set to *Demand replenish*.
1. Set the following values:

    - **Wave step code:** *Replen*
    - **Allow wave demand to use unreserved quantities:** *Yes*

1. Select **Save**.

### Wave template

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. In the left pane, set the **Wave template type** field to *Shipping*.
1. Select template **61 Shipping** in the list.
1. On the Action Pane, select **Edit**.
1. On the **General** FastTab, set the **Automate replenishment work release** option to *Yes*.

    Set this option to *Yes* to create demand-based replenishment work and release it automatically. You must add the replenishment wave method to the wave template and create a replenishment template of the **Wave demand** type. Set up a replenishment template on the **Replenishment templates** page. To set up a replenishment template, you must add the replenish method to the wave template.

1. On the **Methods** FastTab, in the **Selected methods** column, find the following line:

    - **Method name:** *replenish*
    - **Name:** *Replenishment*

1. Set the **Wave step code** field for this line to *Replen*.
1. Select **Save**.

## Example scenario

After you've made all the previously described sample data available and set it up, you can work through this scenario to try out the *Replenishment over location capacity* feature. The values that are shown in this scenario assume that you're working with the standard demo data, that you selected the **USMF** legal entity, and that you prepared the sample records that are described earlier in this article. This scenario also serves as an example that shows how the feature can be used in a production setting.

### Create replenishment work

#### Create sales order 1

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New** to open a dialog box for creating a new sales order.
1. In the dialog box, set the following values:

    - **Customer account:** *US-007*
    - **Warehouse:** *61*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It includes a new, empty line on the **Sales order lines** FastTab. On this line, set the following values:

    - **Item number:** *T0100*
    - **Quantity:** *40*

1. On the **Sales order lines** FastTab, select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**.
1. Close the page.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    You receive informational messages that show the wave and shipment IDs that were created. A replenishment wave is also created.

    You also receive a warning message that states, "Work ID XXXX cannot be unblocked because it has unfinished replenishment work."

#### Create sales order 2

1. On the **All sales orders**, page, on the Action Pane, select **New** to open a dialog box for creating a new sales order.
1. In the dialog box, set the following value:

    - **Customer account:** *US-001*
    - **Warehouse:** *61*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It includes a new, empty line on the **Sales order lines** FastTab. On this line, set the following values:

    - **Item number:** *T0100*
    - **Quantity:** *60*

1. On the **Sales order lines** FastTab, select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**.
1. Close the page.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    You receive informational messages that show the wave and shipment IDs that were created. A replenishment wave is also created.

    You also receive a warning message that states, "Work ID XXXX cannot be unblocked because it has unfinished replenishment work."

#### Create sales order 3

1. On the **All sales orders** page, on the Action Pane, select **New** to open a dialog box for creating a new sales order.
1. In the dialog box, set the following values:

    - **Customer account:** *US-004*
    - **Warehouse:** *61*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It includes a new, empty line on the **Sales order lines** FastTab. On this line, set the following values:

    - **Item number:** *T0100*
    - **Quantity:** *30*

1. On the **Sales order lines** FastTab, select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot**.
1. Close the page.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    You receive informational messages that show the wave and shipment IDs that were created. A replenishment wave is also created.

    You also receive a warning message that states, "Work ID XXXX cannot be unblocked because it has unfinished replenishment work."

#### View work details

1. Go to **Warehouse management \> Work \> Work details**.
1. In the **Overview** section, filter the **Warehouse** column for warehouse *61*.
1. You should see that seven work IDs were created for the three demand sales orders.

    - Three of the seven work IDs have a **Work order type** value of *Replenishment*, and four have a **Work order type** value of *Sales orders*.
    - All three work IDs that have a **Work order type** value of *Replenishment* have the same *Pick* and *Put* locations in the **Lines** section:

        - **Pick:** *02A01R5S1B*
        - **Put:** *06A01R2S1B*

    - Two work IDs were created for sales order 1.

1. Make a note of the work IDs for the sales orders.

Depending on your on-hand quantities, the work quantities that are created might vary slightly. However, overall, the work headers that are created should match this scenario example.

#### On-hand inventory license plate ID

Later in this scenario, you will use the Warehouse Management mobile app (or an emulator), where you must identify the license plate to complete the picking and replenishment scenarios.

To find the license plate IDs that you will need later, follow these steps.

1. Go to **Inventory management \> Inquiries and reports \> On-hand list**.
1. Select the **Show filters** button to open the filter pane.
1. Enter the following filtering criteria to get the license plates for the scenario. Use the *begins with* filter.

    - **Item number:** *T0100*
    - **Warehouse:** *61*

1. Select **Apply**.
1. On the Action Pane, select **Dimensions**.
1. In the **Dimensions display** dialog box, in the **Storage Dimensions** section, select all the values.
1. In the **Transactions** section, select **Item number** and **Quantity \<\> 0**.
1. When you've finished, select **OK** to close the dialog box.
1. The **On-hand** grid shows the license plate numbers for item *T0100* in each location. Make a note of the license plate that is in each location, because you will need this information later.
1. Close the page.

### Process steps

You will perform the warehouse location replenishment for the first two work IDs. Work on the third replenishment work will be blocked until the inventory level in the picking location falls below the threshold.

#### Replenishment

1. Sign in to the Warehouse Management mobile app as a user in warehouse *61*. (Enter *61* as the user ID and *1* as the password.)
1. Go to **Inventory \> Replenishment**.

    You're prompted to complete the first replenishment work. The item number, quantity, and location to pick from are shown.

1. In the **LP** field, enter the license plate number for the item in the location that is shown.
1. Select the **OK** button (check mark symbol).

    The system generates a target license plate number for the new license plate for the picked item.

1. Select **OK** to confirm the value.

    Put work is shown that instructs the user to put the target license plate into the replenishment location. The *Put* location should be **06A01R2S1B**.

1. Confirm the put details, and select **OK**.

    You receive a "Work Completed" message, and the details of the next replenishment pick task are shown: the item number, quantity, and location to pick from. The picking location will be the same as the first replenishment location. Therefore, the license plate will have the same license plate ID that was used for the first replenishment work task.

1. Repeat the preceding steps to complete the replenishment work for the second work task. The quantity and target license plate will differ from the quantity and target license plate for the first work task.

After the second replenishment work is completed, you receive a "Work Completed" message. The mobile device also informs you that there is no work available, even though some replenishment work remains. This behavior occurs because the replenishment work has an availability status of *Held* and is therefore marked as **Blocked**.

The *Held* status was triggered because the location profile for the picking location that the work is being assigned to has an **Overflow quantity** value of *0.65 PL*. The two previous replenishment work tasks filled the location almost to its overflow limit for item *T0100*. (The unit conversion for the item is *1 PL = 100 ea*.) Therefore, the remaining replenishment work would cause the location to exceed its overflow limit.

Until enough inventory is picked from the location to bring it below the work release threshold on the mobile device menu item, this replenishment work will remain blocked.

#### Sales order pick

Before the remaining replenishment work task can be completed, the picking location must be depleted of inventory to a level where the remaining replenishment work can be unblocked. In other words, the sum of the quantity of on-hand inventory in the location and the replenishment quantity can't exceed the **Overflow quantity** value. When this sum is less than the overflow quantity, the remaining replenishment work will be unblocked.

1. Sign in to the Warehouse Management mobile app as a user in warehouse *61*. (Enter *61* as the user ID and *1* as the password.)
1. Go to **Outbound \> Sales Picking**.
1. Enter the first work ID for sales order 1.

    Refer to the work IDs for sales orders that you made a note of earlier, on the **Work details** page. The work ID that you enter here will generate pick work for a quantity of 10 ea from two separate locations.

1. Select **OK**.

    The **Sales orders: Pick** task page shows the item number, quantity, and location to pick from for the first location.

1. In the **LP** field, enter the license plate number for the item in the location that is shown.
1. Select the **OK** button (check mark symbol).

    The **Sales orders: Pick** task page shows the item number, quantity, and location to pick from for the next location.

1. In the **LP** field, enter the license plate number for the item in the location that is shown.
1. Select the **OK** button (check mark symbol).

    The **Sales orders: Put** page instructs you to put away both the completed picking works to the outbound staging location.

1. Select **OK**.

    You receive a "Work Completed" message.

1. Enter the second work ID for sales order 1.

    There is only one pick task for this work ID.

1. Select **OK**.

    The **Sales orders: Pick** task page shows the item number, quantity, and location to pick from.

1. In the **LP** field, enter the license plate number for the item in the location that is shown.

    The license plate that you specify will be one of the system-generated license plates from the replenishment work tasks. To make sure that you capture the correct license plate ID, check the inventory on the **On-hand list** page for the item, location, and quantity.

1. Select the **OK** button (check mark symbol).
1. Confirm the instructions for the put task to the outbound staging location.
1. Select **OK**.

    You receive a "Work Completed" message.

Sales order 2 is blocked from picking because the replenishment task that it's linked to isn't completed. Currently, there is still a quantity of 30 ea in the picking location, and the replenishment quantity for sales order 2 is 60 ea. The sum of the on-hand inventory and the replenishment inventory (90 ea) exceeds the overflow quantity of 0.65 PL (or 65 ea). Before the replenishment work can be completed, sales order 3 must be picked.

1. Enter the work ID for sales order 3.

    There is only one pick task for this work ID.

1. Select **OK**.

    The **Sales orders: Pick** task page shows the item number, quantity, and location to pick from.

1. In the **LP** field, enter the license plate number for the item in the location that is shown.

    The license plate that you specify will be one of the system-generated license plates from the replenishment work tasks. To make sure that you capture the correct license plate ID, check the inventory on the **On-hand list** page for the item, location, and quantity.

1. Select the **OK** button (check mark symbol).
1. Confirm the instructions for the put task to the outbound staging location.
1. Select **OK**.

    You receive a "Work Completed" message.

As soon as the sum of the on-hand quantity in the picking location and the replenishment quantity is below the threshold, you will be able to process the remaining replenishment work.

Return to the **Work details** page, and notice that the replenishment work availability for the final piece of replenishment (for sales order 2) is *Open*, because there is now enough space in the location to accept the replenishment.

You can now process this replenishment work via the mobile device.

1. Go to **Inventory \> Replenishment**.

    You're prompted to complete the remaining replenishment work. The item number, quantity, and location to pick from are shown.

1. In the **LP** field, enter the license plate number for the item in the location that is shown.
1. Select the **OK** button (check mark symbol).

    The system generates a target license plate number for the new license plate for the picked item.

1. Select **OK** to confirm the value.

    Put work is shown that instructs the user to put the target license plate into the replenishment location. The *Put* location should be **06A01R2S1B**.

1. Confirm the put details, and select **OK**.

    You receive "Work Completed" and "No Work Available" messages.

You can now pick sales order 2. It became unblocked when the replenishment work that is linked to the sales order was completed.

1. Enter the work ID for sales order 2.

    There is only one pick task for this work ID.

1. Select **OK**.

    The **Sales orders: Pick** task page shows the item number, quantity, and location to pick from.

1. In the **LP** field, enter the license plate number for the item in the location that is shown.

    The license plate that you specify will be the system-generated license plate from the replenishment work task. To make sure that you capture the correct license plate ID, check the inventory on the **On-hand list** page for the item, location, and quantity.

1. Select the **OK** button (check mark symbol).
1. Confirm the instructions for the put task to the outbound staging location.
1. Select **OK**.

    You receive a "Work Completed" message.

## Notes and tips

- This functionality works with all types of replenishment: wave demand, min/max, load demand, and slotting.
- You can manually override the replenishment work availability for each work header from the **Work details** page if you want.
- When the system sets the replenishment work availability, it considers any inventory that is already in the location before any work is completed
- Each piece of sales order work is linked to a specific replenishment work. There is no corresponding sales work availability functionality.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]