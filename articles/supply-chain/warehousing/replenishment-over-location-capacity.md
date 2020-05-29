# Replenishment over location capacity

## About

Some high volume or space constrained warehouses will need to ship more quantity of an item in a day than what will fit in the picking location. Replenishment over location capacity allows all replenishment work to be created that will be needed for the day and manages availability of the replenishment work to ensure that the pick location doesn't run out of inventory, but also doesn't go above capacity.

The features allow more replenishment work to be created than will fit in a location and will block replenishment work from being completed once the location is full. As inventory in the pick location drops below a configurable threshold, more replenishment work will be made available.

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

#### Work available threshold type: Quantity

This option is used when you are not using volumetric for the locations being replenishment, or you have consistent quantities at which you want to let more inventory be brought to the location.

If this option is selected, populate the *Overflow quantity* and *Overflow unit* fields with the quantity and unit that will be used to control when more replenishment work is made available.

#### Work available threshold type: Percent

If the picking locations use volumetric, then the Percent option can be used.

Set the *Overflow percentage* field to the percentage at which more replenishment work will be made available.

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

1. On the **Methods** FastTab, in the *SELECTED METHODS* area, edit the following line:
    - **Method sequence** - *4* (may be different)
    - **Method name** - *replenish*
    - **Name** - *Replenishment*
    - **Wave step code** - *Replen*

1. Select **Save**.

## Scenario

### Create work

Navigate to _Sales and Marketing - Sales orders - All sales orders_. Click New in the action bar to create a new sales order. Specify US-007 as the customer, and in the General section warehouse 61.

Create a new line for item T0100, and specify a quantity of 40 ea. Click on Inventory _-_  Reservation in the sales order lines actions bar, and click on &#39;Reserve lot&#39; to reserve the order line and click &#39;Release to warehouse&#39; from the WAREHOUSE _-_ ACTIONS section of the ribbon.

- --You will notice that the created Work cannot be unblocked because it has unfinished replenishment work.

Create another sales order, for customer US-001, warehouse 61. Create a line for item T0100, and specify a quantity of 60 ea. Release this order to the warehouse as well.

- --You will notice again that the created Work cannot be unblocked because it has unfinished replenishment work.

Create a third sales order, for customer US-004, warehouse 61. Create a line for item T0100 and specify a quantity of 30 ea. Release this order to the warehouse.

- --You will notice again that the created Work cannot be unblocked because it has unfinished replenishment work.

Navigate to _Warehouse management - Work - Work details._ You should have 7 total work headers created, 3 replenishment and 4 picking. All the replenishment puts and picking picks should be from the same locations (02A01R5S1B and 06A01R2S1B).

Depending on your on-hand quantities, the work created quantities might vary slightly from case to case, but overall the created work headers should match this demo example.

### Process

Open the warehouse mobile device app, log in to warehouse 61, and navigate to _Inventory - Replenishment_. You will be prompted to complete the first replenishment work created (qty 40). Confirm the pick and the put.

You will then be prompted to complete the second replenishment work (qty 40). Complete the pick and the put.

After the completion of the second Replenishment work header, the mobile device will now say that there is now work available, even though some replenishment work is remaining. This is because that replenishment work has a Replenishment Work Availability status of &#39;Held&#39; and is therefore blocked.

This status was triggered because the picking location the work is being put to has a location stocking limit of 1 pl, and the previous two work headers filled the location to its stocking limit. Until inventory is picked from the location that brings it below the work release threshold on the mobile device menu item, this replenishment will remain held.

On the mobile device, navigate to Outbound _-_ Sales picking. Enter the work id for the any piece of picking work created. Enter the LP to pick from and confirm the pick. Repeat this process for the possible picking work. This is to empty the pick location and bring it below the previously specified threshold of 0.5PL.

As soon as the pick location on-hand quantity is below the threshold, you will be able to process the remaining replenishment work.

Go back to work details, and the Replenishment work availability for the final piece of replenishment will be &#39;Open&#39;, as there is now enough space in the location to accept the replenishment.

You can now process this Replenishment work via the mobile device.

## Addendum

- This functionality works with all types of replenishment (wave demand, min/max, load demand, and slotting)
- The Replenishment work availability for each work header can be manually overridden from the work details screen if desired
- The system will take any inventory already in the location before any work is completed into account when setting the replenishment work availability.
- Each piece of sales order work is linked to a specific replenishment work, there is no corresponding &#39;Sales work availability&#39; functionality.
