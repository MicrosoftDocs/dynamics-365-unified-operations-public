---
title: Cycle counting example scenarios
description: This document provides a collection of scenarios for exploring the cycle counting features of Microsoft Dynamics 365 Supply Chain Management
author: GalynaFedorova
ms.date: 06/08/2021
ms.topic: article
ms.search.form: WHSCycleCountPlan, WHSCycleCountPlanListPage, WHSCycleCountThreshold, WHSWorkTableListPage, SalesShipmentDeviation, WHSRFMenuItemCycleCount, WHSWorkLineCycleCount
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-06-08
ms.dyn365.ops.version: 10.0.20
---

# Cycle counting example scenarios

[!include [banner](../includes/banner.md)]

This document provides a collection of scenarios for exploring the cycle counting features of Microsoft Dynamics 365 Supply Chain Management. It starts with requirements for your existing Supply Chain Management environment, then goes on to cycle counting configuration, and then goes through all cycle counting stages. At the end, you will have an understanding of cycle counting that includes guided cycle counting, blind cycle counting, spot cycle counting, cycle count thresholds and cycle count plans.

## Prerequisites

### Make demo data available

Each scenario in this topic references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.

### Turn on support for the Warehouse Management mobile app

Before you can use the new *Warehouse Management mobile app*, you must add support for it to your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *User settings, icons, and step titles for the new warehouse app*

<a name= "prepare-demo-data"></a>

### Prepare demo data for the scenarios

Work through the following procedure to confirm that all the demo data required for these scenarios is available in the USMF company on your system. Create any records or values that are missing.

1. Go to **Warehouse management \> Setup \> Worker**.

1. From the list pane, select **Julia Funderburk**.

1. On the **Users** FastTab Select the row with the following values (or create it if necessary):

    - **User ID:** *61*
    - **User name:** *WH61*
    - **Default warehouse:** *61*
    - **Menu name:** *Main*

1. On the **Work** FastTab, make the following settings for user *61* if they aren't set already:

    - **Is a cycle count supervisor:** *No*
    - **Maximum percentage limit:** *0*
    - **Maximum quantity limit:** *0*
    - **Maximum value limit:** *0*

1. Go to **Warehouse management \> Setup \> Work \> Work pools**.

1. Work pools are used to segregate warehouse work based on the type of work (in this case, cycle counting work). Make sure a record exists with the following settings:

    - **Work pool ID:** *CycleCount*
    - **Description:** *Cycle Count*

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.

1. From the list pane, select the record called *Cycle Count* (or create a new record with this name). Confirm or make the following settings for it:

    - **Menu item name:** *Cycle Count*
    - **Title:** *Cycle Count Guided*
    - **Mode:** *Work*
    - **Use existing work:** *Yes*
    - **Directed by:** *System directed* (This means that Supply Chain Management assigns a cycle counting work ID to the worker.)
    - **Display inventory status:** *Yes*

1. Select **Cycle counting** on the Action Pane.

1. Confirm or make the following settings in the **Mobile device cycle counting** dialog box:

    - **Display item number:** *Yes*
    - **Display license plate:** *Yes*
    - **Number of attempts:** *1*

1. Select **OK** to close the dialog box.

1. From the list pane, select the record called *Cycle Count Blind* (or create a new record with this name). Confirm or make the following settings for it:

- **Menu item name:** *Cycle Count Blind*
- **Title:** *Cycle Count Blind*
- **Mode:** *Work*
- **Use existing work:** *Yes*
- **Directed by:** *Cycle count grouping* (This means that the worker can group cycle counting work IDs that are specific to a particular location, zone, or work pool.)

1. Select **Cycle counting** on the Action Pane.

1. Confirm or make the following settings in the **Mobile device cycle counting** dialog box:

    - **Display item number:** *No*
    - **Display license plate:** *No*
    - **Number of attempts:** *0*

1. Select **OK** to close the dialog box.

1. From the list pane, select the record called *Spot Counting* (or create a new record with this name). Confirm or make the following settings for it:

    - **Menu item name:** *Spot Counting*
    - **Title:** *Spot Counting*
    - **Mode:** *Work*
    - **Use existing work:** *No*
    - **Work creation process:** *Spot cycle counting* (This means that the worker can count items in a warehouse location at any time, without creating cycle counting work. To perform spot cycle counting in a location, the worker enters the location ID.)

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.

1. From the list pane, select the record called *Inventory* (or create a new record with this name). It must have the following cycle counting menu items in its **Menu structure** column:

    - *Cycle Count*
    - *Cycle Count Blind*
    - *Spot counting*

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.

1. Open the **Cycle counting** tab and make the following settings:

    - **Default cycle counting adjustment type:** *Cycle Count* (This is the journal type that is posted when cycle counting is executed.)
    - **Default cycle counting work class ID:** *CCount* (This is the work class that is used for cycle counting.)
    - **Default cycle count work priority** – *50* (This sets the priority of cycle counting work compared to other types of work in the warehouse. By entering a number that is lower than the number for other types of work, you raise the priority of the cycle counting work.)

1. Go to **Warehouse management \> Setup \> Inventory \> Adjustment types**.

1. This page lets you create various codes to designate the in and out adjustments that might occur. Make sure there is a record here with the following values:

    - **Inventory adjustment type:** *Cycle Count*
    - **Description:** *Cycle Count*
    - **Name:** *ICnt*

1. Go to **Warehouse management \> Setup \> Warehouse setup \> Warehouses**.

1. From the list pane, select warehouse *61* (or create a new record with this name).

1. Expand the **Warehouse** FastTab and make the following settings:

    - **Use warehouse management process:** *Yes* (This enables the warehouse for warehouse management processes.)
    - **Allow license plate moves during cycle counting:** *Yes* (This enables workers to move license plates during a cycle count.)

## Scenario 1: Guided cycle counting

Before guided cycle counting can take place, work must first be created. It will guide the assigned person through the warehouse from location to location to complete the counts set up in work.

### Create cycle counting work for scenario 1

Create cycle counting work for **Item location** *01A02R2S2B* (BULK-06) in **Warehouse** *61* by following these steps:

1. Go to **Warehouse management \> Cycle counting \> Cycle count work by location**. The **Create cycle count work by location** dialog box opens.

1. Set the **Work pool ID** field to *CycleCount*.

1. Expand the **Records to include** FastTab and select the **Filter** button.

1. In the query editor dialog box, on the **Range** tab, do the following:

    - For the row where **Field** is set to *Warehouse*, set**Criteria** to *61*.
    - For the row where **Field** is set to *Location,* set**Criteria** to *01A02R2S2B*.

1. Select **OK** to close the query editor dialog box.

1. Select **OK** to close the **Create cycle count work by location** dialog box. A message appears in your **Action center** when the work creation process is finished.

1. Go to **Warehouse management \> Work \> Work details**.

1. Find the newly created work by setting the filter on the **Work pool ID** column to find records with a value of *CycleCount*.

### Perform cycle counting work for scenario 1

After cycle counting work is created, you do the cycle counting work by counting items in a warehouse location and then using a mobile device to enter the result into Supply Chain Management. Now, you will perform the cycle counting work in the Warehouse Management mobile app:

1. Sign in to the Warehouse Management mobile app as the work user you set up in [Prepare demo data for the scenarios](#prepare-demo-data). This user is named Julia Funderburk and is set up for warehouse 61. (The USMF demo data should let you sign in as this work user by entering **User ID** *61*, **Password** *1*.)

1. On the main menu, select **Inventory**.

1. On the **Inventory** menu, select **Cycle Count Guided**.

1. Select the **Qty** field, enter *9* using the number pad, and then select **OK** (the check mark button)

1. The system was expecting you to enter a count of 10 pieces for this item, location, and license plate. Therefore, you are asked to recount. Select the **Qty** field, once again enter *9* using the number pad, and then select **OK** (the check mark button).

1. On the second attempt, your count is accepted.

    > [!NOTE]
    > When the system detected a difference between the expected on-hand quantity and the quantity you entered, it asked you to count an extra time. This occurred because **Number of attempts** is set to one for the **Cycle Count Guided** mobile device menu item. The reason you were guided to a specific item number and license plate number is because the **Cycle Count Guided** mobile device menu item is configured with both **Display item number** and **Display license plate** set to *Yes*.

1. Select **OK** (the check mark button).

### Review the cycle counting differences for scenario 1

To review the cycle counting differences, follow these steps:

1. Return to Supply Chain Management.

1. Go to **Warehouse management \> Work \> Work details**.

1. Find and select the counting work you looked at last time (for example, by setting the filter on the **Work pool ID** column to find records with a value of *CycleCount*). Notice that it now shows a**Work status** of *Pending review*.

    > [!NOTE]
    > The work user account you used to do the counting work has **Cycle count supervisor** set to *No* and**Maximum percentage limit**, **Maximum quantity limit**, and **Maximum value limit** all set to zero. Therefore, all counting differences reported by this user must be approved manually and the related work has its **Work status** set to *Pending review*. If the counted value were within the deviation limits (as specified in the **Maximum percentage limit** or **Maximum quantity limit** fields on the **Work users** page) or if the user had **Cycle count supervisor** set to *Yes*, the work would have been closed automatically.

1. On the Action Pane open the **Work** tab and select **Cycle counting**.

1. On the Action Pane, select **Accept count** button.

1. The difference is posted using the standard counting journal, and that action creates a new work order.

1. On the **Cycle counting transactions** page, select **Derived work** on the Action Pane to find the work created for the approved difference.

## Scenario 2: Blind cycle counting

This scenario requires that you have already completed scenario 1 on your system.

### Create cycle counting work for scenario 2

Before blind cycle counting can take place, you must create some work. Create cycle counting work for **Item location** *01A02R2S2B* (BULK-06) in **Warehouse** *61* by following these steps:

1. Go to **Warehouse management \> Cycle counting \> Cycle count work by item**.

1. Set the **Work pool ID** field to *CycleCount*.

1. Expand the **Records to include** FastTab and select the **Filter** button.

1. In the query editor dialog box, on the **Range** tab, add the following three rows:

    - Row 1:
        - **Table:** *Items*
        - **Field:** *Item number*
        - **Criteria:** *L0101*

    - Row 2:
        - **Table:** *Inventory dimensions*
        - **Field:** *Warehouse*
        - **Criteria:** *61*

    - Row 3:
        - **Table:** *Inventory dimensions*
        - **Field:** *Location*
        - **Criteria:** *01A02R2S2B*

1. Select **OK** to close the query editor dialog box.

1. Select **OK** to close the dialog box. An informational message appears when the work creation process is completed.

### Perform cycle counting work for scenario 2

After you created the cycle counting work, do the work in the Warehouse Management mobile app:

1. Sign in to the Warehouse Management mobile app as the work user you set up in [Prepare demo data for the scenarios](#prepare-demo-data). This user is named Julia Funderburk and is set up for warehouse 61. (The USMF demo data should let you sign in as this work user by entering **User ID** *61*, **Password** *1*.)

1. On the main menu, select **Inventory**.

1. On the **Inventory** menu, select **Cycle Count Blind**.

1. Select **Zone ID** field, enter *BULK06*, and then select**OK** (the check mark button).

1. Select the **Item** field, enter *L0101*, and then select**OK** (the check mark button).

1. Select the **License plate** field, enter *LP\_BULK\_06\_01*, and then select**OK** (the check mark button).

1. Select the **Qty** field, enter *10*, and then select**OK** (the check mark button).

    > [!NOTE]
    > Even though the system detected a difference between the expected quantity on-hand and the quantity scanned, you weren't asked to count an extra time. This occurred because **Number of attempts** is set to zero for the **Cycle Count Blind** mobile device menu item. The reason you were asked to scan the item number and license plate is because the **Cycle Count Blind** mobile device menu item is configured with both **Display item number** and **Display license plate** set to *No*.

1. Select **OK** (the check mark button).

### Review the cycle counting differences for scenario 2

To review the cycle counting differences, follow these steps:

1. Go to **Warehouse management \> Common \> Work \> Cycle count work pending review**.

1. On the Action Pane, open the **Work** tab and select **Cycle counting**.

1. On the Action Pane, select **Reject count** button.

1. The counting difference was rejected, so the work is closed.

## Scenario 3: Spot cycle counting

On-hand record states there is a quantity on-hand of L0101 at location 01A02R2S2B. The warehouse worker is at location 01A02R2S1B, which should have been empty, but instead it is full. Therefore, the warehouse worker performs a spot counting of this location immediately.

### Perform cycle counting work for scenario 3

Perform the cycle counting work in the Warehouse Management mobile app:

1. Sign in to the Warehouse Management mobile app as the work user you set up in [Prepare demo data for the scenarios](#prepare-demo-data). This user is named Julia Funderburk and is set up for warehouse 61. (The USMF demo data should let you sign in as this work user by entering **User ID** *61*, **Password** *1*.)

1. On the main menu, select **Inventory**.

1. On the **Inventory** menu, select **Spot counting**.

1. Select the **Location** field, enter *01A02R2S1B*, and then select**OK** (the check mark button).

The system detects that the location is empty in Supply Chain Management.

1. Select **Add LP or Item**.

1. Select the **Item** field, enter *L0101*, and then select**OK** (the check mark button).

1. Select the **License plate** field, enter *LP\_BULK\_06\_01*, and then select**OK** (the check mark button).

1. Select the **Qty** field, enter 9, and then select **OK** (the check mark button).

1. The system detects that the specified license plate is already available at another location in Supply Chain Management, which means that the license plate will be moved to the current location. It therefore asks you to confirm the movement.

1. Select **OK** (the check mark button).

### Review the cycle counting differences for scenario 3

Review the counting results by doing the steps:

1. Go to **Warehouse management \> Common \> Work details**.

1. Select the **Show closed** check box at the top of the grid.

1. Set the filter for the **Work order type** column to *Inventory movement*.

1. The system automatically detected this count as an inventory movement. This is permitted because **Allow license plate moves during cycle counting** is set to *Yes* for warehouse 61 on the**Warehouses** page.

## Scenario 4: Define cycle count thresholds

One way to create cycle count work is to use thresholds. A cycle counting threshold indicates the quantity or percentage limit of inventory items. Cycle counting work is automatically created when the threshold limit is reached.

For example, there are 60 items in a location that has a cycle counting threshold of 40. During a sales order transaction, 25 items are picked from the location and put in a staging location. Because the new item count, 35, is less than the threshold quantity, so cycle counting work is automatically created for the location.

To set up count thresholds:

1. Go to **Warehouse management \> Setup \> Cycle counting \> Cycle count thresholds**.

1. On the Action Pane, select **New** button to create a new threshold that has the following settings:

    - **Cycle counting threshold ID:** *L0101*
    - **Description:** *Threshold L0101*
    - **Threshold quantity:** *2*
    - **Unit:** *ea*
    - **Capacity threshold based on percentage:** *0.00*
    - **Cycle counting threshold type:** *Quantity*
    - **Process cycle count immediately:** *Yes*
    - **Days between cycle counting:** *1*
    - **Work pool ID:** *CycleCount*

1. On the Action Pane, select **Select items**.

1. In the query editor dialog box, on the **Range** tab, find the row where **Field**  is set to *Item number*, and set the **Criteria** field for that row to *L0101*.

1. Select **OK** to close the query editor.

1. You have now defined a cycle counting threshold for item L0101.

Cycle counting will be created for item L0101 at any location if the on-hand quantity is less than 2, and the last cycle count date on the location is not today.

## Scenario 5: Define cycle count plans

Cycle counting plans let you automate the creation of cycle count work. You can set up each cycle count plan with specific item and location queries. When the batch job runs, it will create cycle count work for all locations matching the item and location criteria (up to the maximum number of counts specified for the plan). When cycle counting work is created, the counting work line includes information about the location to count. The on-hand inventory that is associated with this location isn't blocked, and is therefore available for reservation and outbound processing, even though open counting work exists.

To set up a cycle count plan:

1. Go to **Warehouse management \> Setup \> Cycle counting \> Cycle count plans**.

1. On the Action Pane, select **New** to add a new row to the grid and make the following settings for it:

    - **Cycle counting plan ID:** *BULK06*
    - **Description:** *Counting of location for BULK06*
    - **Work pool ID:** *CycleCount*
    - **Maximum number of cycle counts:** *10*
    - **Days between cycle counting:** *10*
    - **Empty locations:** *Exclude empty*
    - **Work template:** *(Leave blank)*

1. On the Action Pane, select **Select locations**.

1. A standard query editor dialog box opens. On the **Range** tab, add a row with the following settings:

    - **Table:** *Locations*
    - **Field:** *Zone ID*
    - **Criteria:** *BULK06*

1. Select **OK** to close the query editor.

1. On the Action Pane, select **Process cycle counting plan**.

1. The **Cycle count plans** dialog box opens. Expand the **Run in the background** FastTab set **Batch processing** to *Yes*.

1. Select **Recurrence**.

1. The **Define recurrence** dialog box opens. Set it to run once every minute starting now, with no end date.

1. Select **OK** to close the **Define recurrence** dialog box.

1. Select **OK** to close the **Cycle count plans** dialog box.

1. An infolog message is shown to tell you that the job was added to the batch queue.

1. Go to **Warehouse management \> Common \> Cycle count scheduling**. The plan begins immediately and creates counting work. Counting work does not complete, therefore the **Status** is *In process*. After one minute, the **Total cycle counts** column changes to 1.

    > [!NOTE]
    > Cycle count work will not be created if the last cycle counting day is less than value set for **Days between cycle counting** for the cycle counting plan. For example, if **Days between cycle counting** is set to 5, cycle counting work will be created every five days. However, if cycle counting work is processed on day three, the next cycle counting work will be created five days after the last cycle counting was processed, on day 8.

1. Select **Work** on Action Pane to see the counting work created.
