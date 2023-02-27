---
title: Cycle counting example scenarios
description: This article provides a collection of scenarios that explore the cycle counting features of Microsoft Dynamics 365 Supply Chain Management.
author: GalynaFedorova
ms.date: 06/08/2021
ms.topic: article
ms.search.form: WHSCycleCountPlan, WHSCycleCountPlanListPage, WHSCycleCountThreshold, WHSWorkTableListPage, SalesShipmentDeviation, WHSRFMenuItemCycleCount, WHSWorkLineCycleCount
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: gfedorova
ms.search.validFrom: 2021-06-08
ms.dyn365.ops.version: 10.0.20
---

# Cycle counting example scenarios

[!include [banner](../includes/banner.md)]

This article provides a collection of scenarios that explore the cycle counting features of Microsoft Dynamics 365 Supply Chain Management. It first describes the requirements for your existing Supply Chain Management environment. It then explains how to configure cycle counting and describes all the cycle counting stages. When you've finished, you should have a good understanding of cycle counting, including guided cycle counting, blind cycle counting, spot cycle counting, cycle count thresholds, and cycle count plans.

## Prerequisites

### Make demo data available

Each scenario in this article references values and records that are included in the standard demo data that is provided for Supply Chain Management. If you want to use the values that are provided here as you work through the scenarios, be sure to work in an environment where the demo data is installed, and set the legal entity (company) to **USMF** before you begin.

### Turn on support for the Warehouse Management mobile app

To use the Warehouse Management mobile app, the *User settings, icons, and step titles for the new warehouse app* feature must be turned on for your system. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *User settings, icons, and step titles for the new warehouse app* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### <a name= "prepare-demo-data"></a>Prepare demo data for the scenarios

Follow these steps to confirm that all the demo data that is required for the scenarios is available in the USMF company in your system. Create any records or values that are missing.

1. Go to **Warehouse management \> Setup \> Worker**.
1. In the list pane, select **Julia Funderburk**.
1. On the **Users** FastTab, select the row that has the following values. If no existing row has these values, create it.

    - **User ID:** *61*
    - **User name:** *WH61*
    - **Default warehouse:** *61*
    - **Menu name:** *Main*

1. On the **Work** FastTab, set the following values for user *61* if they aren't already set:

    - **Is a cycle count supervisor:** *No*
    - **Maximum percentage limit:** *0*
    - **Maximum quantity limit:** *0*
    - **Maximum value limit:** *0*

1. Go to **Warehouse management \> Setup \> Work \> Work pools**.
1. Work pools are used to segregate warehouse work, based on the type of work (in this case, cycle counting work). Make sure that a record exists that has the following settings:

    - **Work pool ID:** *CycleCount*
    - **Description:** *Cycle Count*

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list pane, select the record that is named *Cycle Count*. If no existing record has this name, create it. Confirm or set the following values for the record:

    - **Menu item name:** *Cycle Count*
    - **Title:** *Cycle Count Guided*
    - **Mode:** *Work*
    - **Use existing work:** *Yes*
    - **Directed by:** *System directed* (This value indicates that Supply Chain Management will assign a cycle counting work ID to the worker.)
    - **Display inventory status:** *Yes*

1. On the Action Pane, select **Cycle counting**.
1. In the **Mobile device cycle counting** dialog box, confirm or set the following values:

    - **Display item number:** *Yes*
    - **Display license plate:** *Yes*
    - **Number of attempts:** *1*

1. Select **OK** to close the dialog box.
1. In the list pane, select the record that is named *Cycle Count Blind*. If no existing record has this name, create it. Confirm or set the following values for the record:

    - **Menu item name:** *Cycle Count Blind*
    - **Title:** *Cycle Count Blind*
    - **Mode:** *Work*
    - **Use existing work:** *Yes*
    - **Directed by:** *Cycle count grouping* (This value indicates that the worker can group cycle counting work IDs that are specific to a location, zone, or work pool.)

1. On the Action Pane, select **Cycle counting**.
1. In the **Mobile device cycle counting** dialog box, confirm or set the following values:

    - **Display item number:** *No*
    - **Display license plate:** *No*
    - **Number of attempts:** *0*

1. Select **OK** to close the dialog box.
1. In the list pane, select the record that is named *Spot Counting*. If no existing record has this name, create it. Confirm or set the following values for the record:

    - **Menu item name:** *Spot Counting*
    - **Title:** *Spot Counting*
    - **Mode:** *Work*
    - **Use existing work:** *No*
    - **Work creation process:** *Spot cycle counting* (This value indicates that the worker can count items in a warehouse location at any time, without creating cycle counting work. To do spot cycle counting in a location, the worker enters the location ID.)

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**.
1. In the list pane, select the record that is named *Inventory*. If no existing record has this name, create it. Confirm that the following cycle counting menu items appear in the **Menu structure** column:

    - Cycle Count
    - Cycle Count Blind
    - Spot counting

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. On the **Cycle counting** tab, set the following values:

    - **Default cycle counting adjustment type:** *Cycle Count* (This field specifies the journal type that is posted when cycle counting is done.)
    - **Default cycle counting work class ID:** *CCount* (This field specifies the work class that is used for cycle counting.)
    - **Default cycle count work priority:** *50* (This field sets the priority that cycle counting work has relative to other types of work in the warehouse. By entering a number that is lower than the number that is entered for other types of work, you raise the priority of the cycle counting work.)

1. Go to **Warehouse management \> Setup \> Inventory \> Adjustment types**.
1. The **Adjustment types** page lets you create codes for the different in and out adjustments that might occur. Confirm that a record exists that has the following settings:

    - **Inventory adjustment type:** *Cycle Count*
    - **Description:** *Cycle Count*
    - **Name:** *ICnt*

1. Go to **Warehouse management \> Setup \> Warehouse setup \> Warehouses**.
1. In the list pane, select warehouse *61*. If no existing record has this name, create it.
1. On the **Warehouse** FastTab, set the following values:

    - **Use warehouse management process:** *Yes* (This value enables the warehouse for warehouse management processes (WMS).)
    - **Allow license plate moves during cycle counting:** *Yes* (This value enables workers to move license plates during a cycle count.)

## Scenario 1: Guided cycle counting

Before guided cycle counting can occur, you must create some work. This work will guide the assigned person through the warehouse, from location to location, to complete the counts that are set up in the work.

### Create cycle counting work for scenario 1

Follow these steps to create cycle counting work for item location *01A02R2S2B* (BULK-06) in warehouse *61*.

1. Go to **Warehouse management \> Cycle counting \> Cycle count work by location**.
1. In the **Create cycle count work by location** dialog box, set the **Work pool ID** field to *CycleCount*.
1. On the **Records to include** FastTab, select **Filter**.
1. In the query editor dialog box, on the **Range** tab, follow these steps:

    - For the row where the **Field** field is set to *Warehouse*, set the **Criteria** field to *61*.
    - For the row where the **Field** field is set to *Location,* set the **Criteria** field to *01A02R2S2B*.

1. Select **OK** to close the query editor dialog box.
1. Select **OK** to close the **Create cycle count work by location** dialog box.

    When the work creation process is completed, a message appears in the Action center.

1. Go to **Warehouse management \> Work \> Work details**.
1. Find the newly created work by setting a filter on the **Work pool ID** column to find records that have a value of *CycleCount*.

### Do cycle counting work for scenario 1

After you've created the cycle counting work, you do the work by counting items in a warehouse location and then using a mobile device to enter the results in Supply Chain Management. Follow these steps to do the cycle counting work in the Warehouse Management mobile app.

1. Sign in to the Warehouse Management mobile app as the work user that you set up in the [Prepare demo data for the scenarios](#prepare-demo-data) section earlier in this article. For the example in this article, the user is named *Julia Funderburk* and is set up for warehouse *61*. (The USMF demo data should let you sign in as this work user by entering *61* as the user ID and *1* as the password.)
1. On the main menu, select **Inventory**.
1. On the **Inventory** menu, select **Cycle Count Guided**.
1. Select the **Qty** field, enter *9* by using the number pad, and then select **OK** (the check mark button).
1. The system was expecting you to enter a count of 10 pieces for this item, location, and license plate. Therefore, you're asked to recount. Select the **Qty** field, enter *9* again by using the number pad, and then select **OK** (the check mark button). On the second attempt, your count will be accepted.

    > [!NOTE]
    > When the system detected a difference between the expected on-hand quantity and the quantity that you entered, it asked you to count a second time because the **Number of attempts** field is set to *1* for the **Cycle Count Guided** mobile device menu item. You were guided to a specific item number and license plate number because both the **Display item number** option and the **Display license plate** option are set to *Yes* for the mobile device menu item.

1. Select **OK** (the check mark button).

### Review the cycle counting differences for scenario 1

Follow these steps to review the cycle counting differences.

1. Return to Supply Chain Management.
1. Go to **Warehouse management \> Work \> Work details**.
1. Find and select the cycle counting work that you looked at earlier. (For example, set a filter on the **Work pool ID** column to find records that have a value of *CycleCount*.) Notice that the **Work status** field for this work is now set to *Pending review*.

    > [!NOTE]
    > For the work user account that you used to do the counting work, the **Cycle count supervisor** option is set to *No*, and the **Maximum percentage limit**, **Maximum quantity limit**, and **Maximum value limit** fields are all set to *0* (zero). Therefore, all counting differences that this user reports must be manually approved, and the **Work status** field for the related work is set to *Pending review*. If the counted value were within the deviation limits (as specified in the **Maximum percentage limit** or **Maximum quantity limit** fields on the **Work users** page), or if the **Cycle count supervisor** option were set to *Yes* for the user, the work would have automatically been closed.

1. On the Action Pane, on the **Work** tab, select **Cycle counting**.
1. On the Action Pane, select **Accept count**.

    The difference is posted by using the standard counting journal, and a new work order is created.

1. On the **Cycle counting transactions** page, on the Action Pane, select **Derived work** to find the work that was created for the approved difference.

## Scenario 2: Blind cycle counting

This scenario requires that scenario 1 already be completed in your system.

### Create cycle counting work for scenario 2

Before blind cycle counting can occur, you must create some work. Follow these steps to create cycle counting work for item location *01A02R2S2B* (BULK-06) in warehouse *61*.

1. Go to **Warehouse management \> Cycle counting \> Cycle count work by item**.
1. In the **Create cycle count work by item** dialog box, set the **Work pool ID** field to *CycleCount*.
1. On the **Records to include** FastTab, select **Filter**.
1. In the query editor dialog box, on the **Range** tab, add three rows that have the following settings:

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

1. Select **OK** to close the query editor dialog box.
1. Select **OK** to close the **Create cycle count work by item** dialog box.

    When the work creation process is completed, you receive an informational message.

### Do cycle counting work for scenario 2

After you've created the cycle counting work, following these steps to do the work in the Warehouse Management mobile app.

1. Sign in to the Warehouse Management mobile app as the work user that you set up in the [Prepare demo data for the scenarios](#prepare-demo-data) section earlier in this article. For the example in this article, the user is named *Julia Funderburk* and is set up for warehouse *61*. (The USMF demo data should let you sign in as this work user by entering *61* as the user ID and *1* as the password.)
1. On the main menu, select **Inventory**.
1. On the **Inventory** menu, select **Cycle Count Blind**.
1. Select the **Zone ID** field, enter *BULK06*, and then select **OK** (the check mark button).
1. Select the **Item** field, enter *L0101*, and then select **OK** (the check mark button).
1. Select the **License plate** field, enter *LP\_BULK\_06\_01*, and then select **OK** (the check mark button).
1. Select the **Qty** field, enter *10*, and then select **OK** (the check mark button).

    > [!NOTE]
    > Even though the system detected a difference between the expected on-hand quantity and the quantity that you scanned, it didn't ask you to count a second time because the **Number of attempts** field is set to *0* (zero) for the **Cycle Count Blind** mobile device menu item. You were asked to scan the item number and license plate because both the **Display item number** option and the **Display license plate** option are set to *No* for the mobile device menu item.

1. Select **OK** (the check mark button).

### Review the cycle counting differences for scenario 2

Follow these steps to review the cycle counting differences.

1. Return to Supply Chain Management.
1. Go to **Warehouse management \> Common \> Work \> Cycle count work pending review**.
1. On the Action Pane, on the **Work** tab, select **Cycle counting**.
1. On the Action Pane, select **Reject count**.

    Because the counting difference was rejected, the work is closed.

## Scenario 3: Spot cycle counting

The on-hand record states that there is an on-hand quantity of item *L0101* at location *01A02R2S2B*. The warehouse worker is at location *01A02R2S1B*. Although this location should be empty, it's full. Therefore, the warehouse worker immediately does a spot count of this location.

### Do cycle counting work for scenario 3

Follow these steps to do the cycle counting work in the Warehouse Management mobile app.

1. Sign in to the Warehouse Management mobile app as the work user that you set up in the [Prepare demo data for the scenarios](#prepare-demo-data) section earlier in this article. For the example in this article, the user is named *Julia Funderburk* and is set up for warehouse *61*. (The USMF demo data should let you sign in as this work user by entering *61* as the user ID and *1* as the password.)
1. On the main menu, select **Inventory**.
1. On the **Inventory** menu, select **Spot counting**.
1. Select the **Location** field, enter *01A02R2S1B*, and then select **OK** (the check mark button).

    The system detects that the location is empty in Supply Chain Management.

1. Select **Add LP or Item**.
1. Select the **Item** field, enter *L0101*, and then select **OK** (the check mark button).
1. Select the **License plate** field, enter *LP\_BULK\_06\_01*, and then select **OK** (the check mark button).
1. Select the **Qty** field, enter *9*, and then select **OK** (the check mark button).

    Because the system detects that the specified license plate is already available at another location in Supply Chain Management, that license plate will be moved to the current location. Therefore, the system asks you to confirm the movement.

1. Select **OK** (the check mark button).

### Review the cycle counting differences for scenario 3

Follow these steps to review the counting results.

1. Return to Supply Chain Management.
1. Go to **Warehouse management \> Common \> Work details**.
1. Select the **Show closed** checkbox at the top of the grid.
1. Set the filter for the **Work order type** column to *Inventory movement*.

    The system automatically detected this count as an inventory movement. This movement is permitted because the **Allow license plate moves during cycle counting** option is set to *Yes* for warehouse *61* on the **Warehouses** page.

## Scenario 4: Define cycle count thresholds

One way to create cycle counting work is to use thresholds. A cycle count threshold indicates the quantity or percentage limit of inventory items. Cycle counting work is automatically created when the threshold is reached.

For example, there are 60 items in a location that has a cycle count threshold of 40. During a sales order transaction, 25 items are picked from the location and put in a staging location. Because the new item count, 35, is less than the threshold quantity, cycle counting work is automatically created for the location.

Follow these steps to set up cycle count thresholds.

1. Go to **Warehouse management \> Setup \> Cycle counting \> Cycle count thresholds**.
1. On the Action Pane, select **New** to create a threshold, and set the following values for it:

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
1. In the query editor dialog box, on the **Range** tab, find the row where the **Field** field is set to *Item number*. Set the **Criteria** field for that row to *L0101*.
1. Select **OK** to close the query editor dialog box.

    You've now defined a cycle count threshold for item *L0101*.

Cycle counting will now be created for item *L0101* at any location if the on-hand quantity is less than 2, and if the date of the last cycle count for the location isn't today.

## Scenario 5: Define cycle count plans

Cycle count plans let you automate the creation of cycle counting work. You can set up each cycle count plan with specific item and location queries. When the batch job runs, it will create cycle counting work for all locations that match the item and location criteria (up to the maximum number of counts that is specified for the plan). When cycle counting work is created, the counting work line includes information about the location that must be counted. The on-hand inventory that is associated with that location isn't blocked. Therefore, it's available for reservation and outbound processing, even though open counting work exists.

Follow these steps to set up a cycle count plan.

1. Go to **Warehouse management \> Setup \> Cycle counting \> Cycle count plans**.
1. On the Action Pane, select **New** to add a row to the grid, and set the following values for it:

    - **Cycle counting plan ID:** *BULK06*
    - **Description:** *Counting of location for BULK06*
    - **Work pool ID:** *CycleCount*
    - **Maximum number of cycle counts:** *10*
    - **Days between cycle counting:** *10*
    - **Empty locations:** *Exclude empty*
    - **Work template:** Leave this field blank.

1. On the Action Pane, select **Select locations**.
1. A standard query editor dialog box appears. On the **Range** tab, add a row, and set the following values for it:

    - **Table:** *Locations*
    - **Field:** *Zone ID*
    - **Criteria:** *BULK06*

1. Select **OK** to close the query editor dialog box.
1. On the Action Pane, select **Process cycle counting plan**.
1. In the **Cycle count plans** dialog box, on the **Run in the background** FastTab, set the **Batch processing** option to *Yes*.
1. Select **Recurrence**.
1. In the **Define recurrence** dialog box, set up the batch job so that it begins immediately and runs once every minute, and so that there is no end date.
1. Select **OK** to close the **Define recurrence** dialog box.
1. Select **OK** to close the **Cycle count plans** dialog box.

    A message informs you that the job was added to the batch queue.

1. Go to **Warehouse management \> Common \> Cycle count scheduling**. The plan begins immediately and creates counting work. Because counting work hasn't been completed, the **Status** field is set to *In process*. After one minute, the value in the **Total cycle counts** column changes to *1*.

    > [!NOTE]
    > Cycle count work won't be created if the number of days since the last cycle counting is less than value that you set for the **Days between cycle counting** field for the cycle counting plan. For example, if the **Days between cycle counting** field is set to *5*, cycle counting work will be created every five days. However, if cycle counting work is processed on day 3, the next cycle counting work will be created five days after the last cycle counting was processed, on day 8.

1. On Action Pane, select **Work** to view the counting work that was created.
