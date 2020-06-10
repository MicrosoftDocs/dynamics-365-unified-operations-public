---
# required metadata

title: Location license plate positioning
description: License plate location positioning lets you see where a license plate is located in a multi-pallet location, such as one using double-deep pallet racking.
author: Mirzaab
manager: tfehr
ms.date: 06/09/2020
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
ms.search.validFrom: 2020-06-09
ms.dyn365.ops.version: Release 10.0.9
---

# Location license plate positioning

[!include [banner](../includes/banner.md)]

License plate location positioning lets you see where a license plate is located in a multi-pallet location, such as one using double-deep pallet racking.

This functionality adds an sequence number to the license plate for each license plate that is put to a location. The sequence number orders the license plates within a storage location. This feature intelligently solves scenarios where customers are using gravity racking system and need to know which license plate is front facing for picking purposes.

This topic presents a scenario that illustrates how to set up and use this feature.

## Enable the location license plate positioning feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Location license plate positioning*

## Example scenario

### Enable sample data

To work through this scenario using the values suggested here, you must work on a system that has sample data installed, and select the **USMF** legal entity before starting.

### Set up the feature for this scenario

The feature must be enabled in **Location profiles** for all locations where license plate positioning is to be used. Follow the steps below to enable the feature for the scenario provided in this topic.

#### Location Profiles

1. Go to **Warehouse management > Setup > Warehouse > Location profiles**.
1. Select **BULK-06** from the location profiles list on the left.
1. In the **General** FastTab, two new options have been added by this feature. Enable both options:
    - **Enable license plate position** - *Yes*
        - When enabled, the license plate position will be maintained for license plates in the location.
    - **Display mobile device LP position** - *Yes*
        - Only editable when the functionality is enabled.
        - When enabled, the license plate position value will be shown to the user on the mobile device during adjustment in and during counting.

1. Select **Save**.

#### Location directives

1. Go to **Warehouse management > Setup > Location directives**.
1. Ensure **Work order type** is set to *Sales orders*.
1. Select **61 SO Pick order** from the list of location directives.
1. Select **Edit** on the Action Pane.
1. On the **Lines** FastTab, select the line with a **Sequence number** of *2*.
1. On the **Location Directive Actions** FastTab, select the line with a **Name** of *Pick for less than pallet* (this should be the only line) and change its **Sequence number** to *2*.

1. At top of the **Location Directive Actions** FastTab, select **New** and enter the following on the new line to add a new location directive action:
    - **Sequence number** - *1*
    - **Name** - *Pick position 1*

1. At top of the **Location Directive Actions** FastTab, with your new line still selected, select **Edit query**.
1. On the query form select the **Joins** tab.
1. Expand **Locations** table join to reveal the **Inventory dimensions** table.
1. Expand **Inventory dimensions** to reveal the join to the **On-hand inventory** table.
1. Select **Inventory dimensions** then select **Add table join**.
1. In the list of tables displayed, select **License plate (License plate)** in the **Relation** column and then, in the header, select **Select**  to add **License plate** to the **Inventory dimensions** table join.
1. Next, with the focus still on **License plate**, select **Add table join** in the header.
1. In the list of tables displayed, select **Location license plate positioning (License plate)** in the **Relation** column and then, in the header, select **Select**  to add **Location license plate positioning** to the **Inventory dimensions** table join.

    ![Table joins](media/LpTableJoin.png "Table joins")

1. Select **OK** to confirm the updated joined tables and close the query editor.
1. At top of the **Location Directive Actions** FastTab, select **Edit query** again to return to the query editor.
1. On the **Range** tab, select **Add** to create a new line and enter the following:
    - **Table** - *Location license plate positioning*
    - **Derived table** - *Location license plate positioning*
    - **Field** - *LP Position*
    - **Criteria** - *1*

    ![Criteria](media/LpPositionCriteria.png "Criteria")

1. Select **OK** to confirm the changes and close the query editor.

### Set up sample data for this scenario

The following scenario requires the user to sign in to the warehousing mobile app with a *worker* setup for *Warehouse 61* to perform work, and to complete transactions.

Because this feature adds a new identifier for license plate positions within a location, we must first create some data to support the scenario.

#### Spot count the first location

1. Open the warehousing mobile app and sign in to **Warehouse** *61*.
1. Go to **Inventory > Spot Counting**.
1. on the **Spot Counting** screen, set **Location** to *01A01R1S1B*.

1. Select **OK**.
1. The screen displays the **Location** that was entered and the message: "Location complete, add new LP or Item?"
1. Select the **Refresh** button.
1. The **Cycle Count: Add New LP or Item** screen opens, which includes the **Item** field.
1. Select **Item** and then enter the value *A0001*.
1. Select **OK**.
1. The **Cycle Count: Add New LP or Item** screen opens, which includes the **LP** field.
1. Select **LP** to enter a **License Plate** number and then enter the value *LP1001* (or one of your choosing).

1. **License Plate Position 1** will be displayed on the **Cycle Count: Add New LP or Item** screen.
1. Select **OK**.
1. Now you must specify quantity of the item counted on the license plate.
Set **Qty** to *10*.

1. Select **OK**.
1. The screen displays the **Location** that you entered and the message: "Location complete, add new LP or Item?"
1. Select the **Refresh** button to add another count in the location.
1. The **Cycle Count: Add New LP or Item** page opens, which includes the **Item** field.
1. Select **Item** and then enter the value *A0002*.
1. Select **OK**.
1. The **Cycle Count: Add New LP or Item** page opens, which includes the **LP** field.
1. Select **LP** and then enter the license plate number *LP1002* (or one of your choosing, so long as it's different from the first one you picked).
1. Change the license plate position (**LP Position**) to *2*.
1. Select **OK**.
1. Enter the quantity of the item counted on the license plate by setting **Qty** to *10*.
1. Select **OK**.
1. The screen displays the **Location** that you entered and the message: "Location complete, add new LP or Item?"
1. Select **OK**.
1. Work is completed.

#### Spot count the second location

1. On the **Spot Counting** screen, set the **Location** to *01A01R1S2B*.

1. Select **OK**.
1. The screen displays the **Location** that you entered and the message: "Location complete, add new LP or Item?"
1. Select **Refresh**.
1. The **Cycle Count: Add New LP or Item** screen opens, which includes the **Item** field.
1. Select **Item** and then set **Item** to *A0002*.
1. Select **OK**.
1. The **Cycle Count: Add New LP or Item** screen opens, which includes the **LP** field.
1. Select **LP** and then enter the license plate number *LP1003* (or one of your choosing, so long as it's different from the previous two).

1. **License Plate Position 1** is displayed on the **Cycle Count: Add New LP or Item** screen.
1. Select **OK**.
1. Enter the quantity of the item counted on the license plate by setting **Qty** to *10*.

1. Select **OK**.
1. The screen displays the **Location** that you entered and the message: "Location complete, add new LP or Item?"
1. Select **OK**.
1. Work is completed.

#### Work details

> [!NOTE]
> Spot counts from the mobile app will create *Cycle counting* work in Dynamics 365. The work requires that the counts be accepted before posting the counts into inventory.

Sign in to Dynamics 365 Supply Chain Management to complete the next steps.

1. Go to **Warehouse management > Work > Work details**
1. On the **Work** *Overview* section look for the following lines:
    - **Work order type** - *Cycle counting*
    - **Warehouse** - *61*
    - **Work status** - *Pending review*

1. There will be two **Work ID**'s created. The counts for both work ID's need to be accepted.
1. Select the first **Cycle counting** Work ID in the *Overview* section.
1. In the Action Pane **Work** tab select *Cycle counting*.
1. Two lines will be displayed, one for each *Item* and *License plate*.
    - The Counted quantity, Location, License plate and Item will match with count entries performed on the mobile device.
    - If all these fields are not visible, select *Display dimensions* in the Toolbar to add them to the grid.

1. Select both lines.
1. In the Toolbar, select **Accept count**.
1. A *Posting - Journal* message displays, select *Message details* to view the posted journal number.
1. Close the form.
1. Refresh the **Work** form.
1. The first **Work ID** has been closed and is no longer displayed.
    - Select **Show closed** to view closed *Work*.

1. Repeat the steps above to accept the work for the license plate in **Location** - *01A01R1S2B*.
1. Select the second **Cycle counting** Work ID in the *Overview* section.
1. In the Action Pane **Work** tab select *Cycle counting*.
1. One line will be displayed, for the *Item* and *License plate*.
    - The Counted quantity, Location, License plate and Item will match with count entries performed on the mobile device.

1. Select the line.
1. In the Toolbar, select **Accept count**.
1. A *Posting - Journal* message displays, select *Message details* to view the posted journal number.
1. Close the form.
1. Refresh the **Work** form.
1. The second **Work ID** has been closed and is no longer displayed.
    - Select **Show closed** to view closed *Work*.

#### On-hand by location

1. Go to **Warehouse management > Inquiries and reports > On-hand by location**.
1. Enter or select the following:
    - **Site**  - *6*
    - **Warehouse** - *61*
    - **Refresh across locations** - *Yes*

1. Note that **Location** *01A01R1S1B* has two License Plates:
    - **A0001** with **LP Position** *1*
    - **A0002** with **LP Position** *2*

1. Note that **Location** *01A01R1S2B* has one License Plate:
    - **A0002** with **LP Position** *1*

### Sales order scenario

Now that the feature has been setup and the inventory staged, we need to create a sales order to generate picking work that will guide the warehouse worker to pick item A0002 from the inventory location where the pallet ID is in position 1.

1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select **New** in the Action Pane.
1. In the **Create sales order** FlyOut enter the following:
    - **Customer account** - *US-004*
    - **Warehouse** - *61*

1. Select **OK**.
1. On the **Sales order lines** FastTab a new line is added. Enter the following:
    - **Item number** - *A0002*
    - **Quantity** - *1*

1. On the **Sales order lines** Toolbar, select **Inventory** then select *Reservation*.
1. On the **Reservation** form select *Reserve lot* in the Toolbar to reserve inventory to the order line.
1. Close the form.
1. In the Action Pane, select the **Warehouse** tab, then select *Release to warehouse*.
1. An informational message displays with the **Wave ID* and *Shipment ID* created for the order.
1. On the **Sales order lines** Toolbar select **Warehouse** then select *Work details*.
1. The **Work** form opens and displays the work created for the sales line. Make note of the work ID shown.

### Sales picking scenario

1. Open the mobile app and sign in to **Warehouse** *61*.
1. Go to **Outbound > Sales picking**.
1. On the **Scan a work ID / license plate ID** screen, select the **ID** field and enter the wrk ID from the sales line.
1. Note that the picking work has directed you to pick **Item** *A0002* from **Location** *01A01R1S2B*. This is because item A0002 is on a license plate in that location that is in position 1.

    ![Position 1 location](media/LocationLicensePlatePositioning.png "Position 1 location")

1. Enter the **License plate ID** you created for that location and complete the prompts to pick the sales order.
