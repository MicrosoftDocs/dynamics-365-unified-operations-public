# Replenishment over location capacity

## About

Some high volume or space constrained warehouses will need to ship more quantity of an item in a day than what will fit in the picking location. Replenishment over location capacity allows all replenishment work to be created that will be needed for the day and manages availability of the replenishment work to ensure that the pick location doesn't run out of inventory, but also doesn't go above capacity.

The features allow more replenishment work to be created than will fit in a location and will block replenishment work from being completed once the location is full. As inventory in the pick location drops below a configurable threshold, more replenishment work will be made available.

## Enable the Replenishment over location capacity feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Replenishment over location capacity*

## Setup

### Location profile

The replenish over capacity functionality is enabled on the location profile.

1. Go to **Warehouse management > Setup > Warehouse > Locations profiles**
1. In left side column, select **PICK-06**
1. In the Action Pane select **Edit**
1. In the **Replenishment** FastTab, select the following:
    - **Exceed Location Capacity** - *Yes*
        - This parameter dictates whether the replenishment overflow functionality is turned on or off.
        - When enabled, the maximum capacity of the location will be allowed to be exceeded by replenishment work.
    - **Work availability threshold type** - *Quantity*
        - What method is used for determining when to release more work. You can release by either *Quantity* or *Percent*
            - Percent uses a percentage capacity based on stocking limits or volumetrics.
            - Quantity uses a specific quantity value.
    - **Overflow quantity** - *0.50*
        - Quantity at which the location overflows. Work will be available whenever the location on hand + work quantity is below this value.
    - **Overflow unit** - *PL*
        - Unit associated with the overflow quantity.
1. This will make more replenishment work available when the location gets down to 0.50 PL.
    - **Overflow percentage**
        - This field is only enabled when the **Work availability threshold type** - *Percent* is selected.
            - Percentage at which the location overflows. Work will be available whenever the location on hand + work quantity is below this percentage.

>[!TIP]
>
>**Work available threshold type: Quantity**
>
>This option is used when you are not using volumetric for the locations being replenishment, or you have consistent quantities at which you want to let more inventory be brought to the location.
>
>If this option is selected, populate the *Overflow quantity* and *Overflow unit* fields with the quantity and unit that will be used to control when more replenishment work is made available.
>
>**Work available threshold type: Percent**
>
>If the picking locations use volumetric, then the Percent option can be used.
>
>Set the *Overflow percentage* field to the percentage at which more replenishment work will be made available.

### Wave step code

1. Go to **Warehouse Management > Setup > Waves > Wave Step Codes**
1. Select **New** and enter the following:
    - **Wave step code** – *Replen*
    - **Wave step description** – *Replenishment*
    - **Wave step type** - *Replenishment*

1. Select **Save**

### Replenishment template

Replenishment templates are a set of rules that control when and how to replenish a location.

1. Go to **Warehouse management > Setup > Replenishment >  Replenishment templates**
1. Select **Edit** in the Action Pane.
1. In the **Overview** section, focus on the line **Replenish template** - *Demand replenish*
1. Select the following:
    - **Wave step code** - *Replen*
    - **Allow wave demand to use unreserved quantities** - *Yes* (selected)

1. Select **Save**

### Wave template

When **Automate replenishment work release** is set to *Yes*, it will create demand-based replenishment work and release it automatically. You must add the replenishment wave method to the wave template and create a replenishment template of the type Wave demand.

1. Go to **Warehouse management > Setup > Waves > Wave templates**
1. On the left side pane, ensure **Wave template type** is set to *Shipping*
1. Select template **61 Shipping** in the pane.
1. Select **Edit** from the Action Pane.
1. On the **General** FastTab:
    - **Automate replenishment work release** - *Yes*

1. On the **Methods** FastTab, in the *SELECTED METHODS* area, edit the *Wave step code* on the following line:
    - **Method sequence** - *4* (may be different)
    - **Method name** - *replenish*
    - **Name** - *Replenishment*
    - **Wave step code** - *Replen*

1. Select **Save**.

## Scenario

### Create replenishment work

1. Go to **Sales and Marketing > Sales orders > All sales orders**
1. Select **New** in the Action Pane to open a flyout for creating a new sales order.
1. In the flyout, enter the following:
    - On the **Customer** section, set **Customer account** to *US-007*.
    - On the **General** section, set **Warehouse** to *61*.

1. Select **OK** to create the sales order and close the flyout.
1. The new sales order is opened. It includes a new empty line on the **Sales order lines** FastTab. On this line, set the following values:
    - **Item number** - *T0100*
    - **Quantity** - *40*
1. In the **Sales order lines** toolbar select **Inventory**, then select *Reservation*.
1. On the **Reservation** form select *Reserve lot*.
1. Close the form.
1. In the Action Pane, select **Warehouse** then *Release to warehouse*.
1. Informational messages will be displayed indicating *Wave* and *Shipment* ID's created, a *Replenishment wave* is also created.
    - Note a *Warning message* is also displayed indicating that: **Work IDXXXX** cannot be unblocked because it has unfinished replenishment work.

1. Create a second sales order.
1. Select **New** in the Action Pane to open a flyout for creating a new sales order.
1. In the flyout, enter the following:
    - On the **Customer** section, set **Customer account** to *US-001*.
    - On the **General** section, set **Warehouse** to *61*.

1. Select **OK** to create the sales order and close the flyout.
1. The new sales order is opened. It includes a new empty line on the **Sales order lines** FastTab. On this line, set the following values:
    - **Item number** - *T0100*
    - **Quantity** - *60*
1. In the **Sales order lines** toolbar select **Inventory**, then select *Reservation*.
1. On the **Reservation** form select *Reserve lot*.
1. Close the form.
1. In the Action Pane, select **Warehouse** then *Release to warehouse*.
1. Informational messages will be displayed indicating *Wave* and *Shipment* ID's created, a *Replenishment wave* is also created.
    - Note a *Warning message* is also displayed indicating that: **Work IDXXXX** cannot be unblocked because it has unfinished replenishment work.

1. Create a third order.
1. Select **New** in the Action Pane to open a flyout for creating a new sales order.
1. In the flyout, enter the following:
    - On the **Customer** section, set **Customer account** to *US-004*.
    - On the **General** section, set **Warehouse** to *61*.

1. Select **OK** to create the sales order and close the flyout.
1. The new sales order is opened. It includes a new empty line on the **Sales order lines** FastTab. On this line, set the following values:
    - **Item number** - *T0100*
    - **Quantity** - *30*
1. In the **Sales order lines** toolbar select **Inventory**, then select *Reservation*.
1. On the **Reservation** form select *Reserve lot*.
1. Close the form.
1. In the Action Pane, select **Warehouse** then *Release to warehouse*.
1. Informational messages will be displayed indicating *Wave* and *Shipment* ID's created, a *Replenishment wave* is also created.
    - Note a *Warning message* is also displayed indicating that: **Work IDXXXX** cannot be unblocked because it has unfinished replenishment work.

1. Go to **Warehouse management > Work > Work details**.
1. In the **Overview** section, filter the **Warehouse** column for *61*.
1. You should have 7 total **Work order type** headers created:
    - **Replenishment** - *3*
    - **Sales orders** - *4* (Picking)
        - Make note of the **Work ID** for the Sales orders.
1. All 3 **Replenishment** Work order types should have the same *Pick* and *Put* locations in the **Lines** section:
    - **Pick** - *02A01R5S1B*
    - **Put** - *06A01R2S1B*

Depending on your on-hand quantities, the created **Work quantities** might vary slightly from case to case, but overall the created work headers should match this scenario example.

>[!IMPORTANT]
>You will complete the next steps using the mobile app, you will also need to identify the *License plates* to complete the Picking Scenario.

#### Picking License plate

1. Go to **Inventory management > Inquiries and reports > On-hand list**
1. Select  **Show filters**, enter the following to get the license plates for the scenario (use the *begins with* filter):
    - **Item number** - *T0100*
    - **Warehouse** - *61*
    - **Location** - *02A01R5S1B*
    - Click **Apply**

1. In the On-hand grid note the license plate number for item *T0100* in location *02A01R5S1B*.
    - Note, if license plate is not displayed on the grid, select *Dimensions* from the Action Pane and add it to the display.

1. Close the form.

### Process Steps

Perform the warehouse location replenishment for the first two work ID's. Work on the third replenishment work will be blocked until the picking location inventory level falls below the threshold.

#### Replenishment

1. Login to the mobile device for a user in warehouse **61**.
1. Go to **Inventory > Replenishment**.
1. You will be prompted to complete the first replenishment work created (qty = first Replenishment work quantity).
1. Enter a *License plate* number to Pick from:
    - **LP** - *LPREPL01*
1. Select **OK**
1. Confirm the Pick details, select **OK*.
1. Confirm the Put details.
    - The Put location should be **06A01R2S1B**.
1. Select **OK**.
1. Work completed for the first replenishment pick.
1. You will then be prompted to complete the second replenishment work.
1. Complete the pick and the put replenishment work just as you did for the first pick and put.

After the completion of the second Replenishment work order type, the mobile device will display a message that there is *No work available*, even though some replenishment work is remaining. This is because the replenishment work has a Replenishment Work Availability status of *Held* and is therefore **Blocked**.

This status was triggered because the picking location's *Location profile* the work is being put to has an *Overflow quantity* of 0.5 PL (Pallet), and the previous two work headers filled the location to its limit for the Item *T0100*.

Until inventory is picked from the location that brings it below the work release threshold on the mobile device menu item, this replenishment will remain *Blocked*.

#### Sales Order Pick

1. Login to the mobile device for a user in warehouse **61**.
1. Go to **Outbound > Sales Picking**.
1. Enter the **Work ID** for any of the Sales orders picking work created.
    - Refer to the Work ID's for Sales orders from the Work details form.

    Enter the LP to pick from and confirm the pick. Repeat this process for the possible picking work. This is to empty the pick location and bring it below the previously specified threshold of 0.5PL.

As soon as the pick location on-hand quantity is below the threshold, you will be able to process the remaining replenishment work.

Go back to work details, and the Replenishment work availability for the final piece of replenishment will be *Open*, as there is now enough space in the location to accept the replenishment.

You can now process this Replenishment work via the mobile device.

## Tips

- This functionality works with all types of replenishment (wave demand, min/max, load demand, and slotting)
- The Replenishment work availability for each work header can be manually overridden from the work details screen if desired
- The system will take any inventory already in the location before any work is completed into account when setting the replenishment work availability.
- Each piece of sales order work is linked to a specific replenishment work, there is no corresponding *Sales work availability* functionality.
