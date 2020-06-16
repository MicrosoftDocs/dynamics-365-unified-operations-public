---
# required metadata

title: Quality check
description: Use this feature to enable warehouse workers to perform quick quality spot checks while receiving items to the inbound dock area.
author: mirzaab
manager: AnnBe
ms.date: 02/18/2020
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
ms.search.validFrom: 2020-02-18
ms.dyn365.ops.version: Release 10.0.8
---

# Quality check

Use this feature to enable warehouse workers to perform quick quality spot checks while receiving items to the inbound dock area. These spot checks are beneficial when inspecting packaging or any other easily recognizable part of the item. The feature guides workers to take a quick look to see if anything is obviously faulty, or damaged, before stocking the inventory to its put away location.

This functionality offers an alternative to the existing quality check process, offering more flexibility and faster processing.

When using this feature, the arrival and quality check proceeds as follows:

1. When a shipment arrives, the warehouse worker registers the arrival, and also registers its location by scanning a license plate.
1. The worker does a quick quality check and records the result (pass or fail) for that license plate.
1. One of the following happens:
    - License plates containing accepted items are guided to a storage location as usual.
    - For the rejected license plates, existing put-away work is cancelled and a new *quality check* work order is created. The license plate is then diverted to a quality check location for further inspection.

<!-- The above wasn't entirely clear in the draft.  I tried to clarify with this revision. Please confirm it's still correct -->

This process can also be set to divert all scanned license plates to the quality check location immediately.

## Enable the Quality check feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Quality check

## Setup

This section provides guidelines and an example of how to set up and use this feature.

### Enable sample data

To work through the [example scenario](#example-scenario) using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use this example as guidance for how to use this feature when working on a production system, but then you must substitute your own values for each setting described here.

<a name="quality-template"></a>

### Quality check template

The quality check template defines the rules to perform quick quality spot checks at the time of receiving.

1. Go to **Warehouse management > Setup > Work > Quality check template**.
1. Select **New** to add a new template to the table.
1. Enter the following to define a new template:
    - **Quality check template name** - *Dock check*
        - Enter a name that identifies this policy

    - **Acceptance policy** - *Prompt user*
        - Should the user be prompted to accept or reject the inventory quality while processing the work or will it be automatically rejected? Available options:
            - *Auto reject*
            - *Prompt user*

    - **Quality processing policy** - *Create quality order*
        - Select the policy that should be used when rejecting the quality of the inventory. Available options:
        - *Create work only*
            - Only work is created to facilitate inventory movement.
        - *Create quality order*
            - A quality order will be created to facilitate quality tests.

    - **Test group** - *Enclosure*
        - Test group to use in the created quality order. These are setup in the *Inventory management* module.
        - *Destructive test* - Not enabled for *Enclosure*.
            - This option signifies if the sample will be destroyed as part of the tests in the test group. By using a destructive test, creating a quality order for an item will give you a system-generated inventory transaction. The new inventory transaction predicts the inventory reduction for the test quantity. Completion of the quality order through the validation step will result in the inventory reduction. The inventory transaction is identified as a quality order.

<a name="work-class"></a>

### Work class - Quality Check

Work classes are used to direct and/or limit the type of work order lines that a warehouse worker can process on a mobile device.

1. Go to **Warehouse management > Setup > Work > Work classes**.
1. Select **New** to create a new work class.
1. In the header, enter the following for your new work class:
    - **Work class ID** - *QC Check*
        - Enter a name that identifies this work class.

    - **Description** - *QC Check*
        - Enter a short description of what this work class is for.

    - **Work order type** - *Quality in quality check*
        - Identify the type of work order created by this work class.
        - When setting up quality control work, always select *Quality in quality check*.

1. In the **Valid put location types** FastTab you have the option to define a **Location type**. Leave this blank.
    - If you select a **Location type**, this sets a restriction on where items can be put after they've been picked.
    - This setting is used when a location directive tries to resolve the location, or if a warehouse worker manually provides the location for the mobile device menu item.

For more information about work classes and how to create them, see [Create a work class](tasks/create-work-class.md).

### Work template

Work templates lets you define the work operations that must be performed in the warehouse. Typically, warehouse work operations consist of a pair of actions: a warehouse worker picks up on-hand inventory in one location and then puts the picked inventory down in another location. A work template for quality control defines the work operations for performing the quality checks.

#### Purchase orders

1. Go to **Warehouse management > Setup > Work > Work templates**.
1. Ensure the **Work order type** is set to *Purchase orders*.
1. Select **Edit** in the Action Pane.
1. Select a work template that should include a quality-check step. In the **Overview** section, select the following template:
    - **Work template** - *51 PO Receipt*

1. Note in the **Work template details** section there are two existing lines for **Pick** and **Put**.
1. Select **New** in the Toolbar to add a new row to the table for quality control. **Line number** *3* is added.
1. Enter the following in the new row:
    - **Work type** - *Quality check*
    - **Work class ID** - *Purchase*
    - **Quality check template name** - *Dock check*
        - Select the unique ID for the work class. You use this value to configure the menu items on the mobile device and the types of work that those menu items can process.
    - Accept the default values of the remaining fields.

1. Select **Save** in the Action Pane to save your work so far.
1. An informational message will be displayed: **Invalid - Quality check must come directly after a pick**.
1. After saving, the **Line number** for the **Work type** of the *Quality check* row that you just added must be changed. Perform the following steps:
    - Select the line for **Work type** - *Quality check*
    - In the **Work Template Details** Toolbar, select the **Move up** or **Move down** buttons to move the *Quality check* line behind the *Pick* line.

1. Select **Save** in the Action Pane.

#### Quality in quality check

Next create a new work template for the quality check.

1. In the header, change the **Work order type** to *Quality in quality check*.
1. Select **New** in the Action Pane to add a row to **Overview** section.
1. Enter the following in the new row:
    - **Work template** - *51 Quality Check*
        - Enter a name for the template.

    - **Work template description** - *51 Quality Check*

1. Select **Save** in the Action Pane to enable the **Work Template Details** section.
1. With the new template still selected in the *Overview* section, select **New** in the **Work Template Details** Toolbar to add a new row there. Then enter the following values for the new row:
    - **Work type** - *Pick*
    - **Work class ID** - *QC Check*
        - Select the name of the [work class](#work-class) that you created earlier for quality-control work.

1. Select **New** in the **Work Template Details** Toolbar to add a new row, then enter the following values for this row:
    - **Work type** - *Put*
    - **Work class ID** - *QC Check*
        - Select the name of the [work class](#work-class) that you created earlier for quality-control work.

1. Select **Save** in the Action Pane.

For more information about work templates, see [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md)

### Location directive - Quality Failures

Location directives are rules that help identify pick and put locations for inventory movement. For example, in a sales order transaction, a location directive determines where the items will be picked, and where the picked items will be put. A location directive rule must be configured to determine how to handle failed quality checks.

1. Go to **Warehouse management > Setup > Location directives**.
1. In the *Location directives* list, select **Work order type** and change it to *Purchase orders* to start working with location directives of that type.
1. Select **New** in the Action Pane to create a new location directive for quality check. Enter the following in the Header:
    - **Sequence number** - Accept default value
    - **Name** - *51 To Quality*

1. In the **Location directives** FastTab, enter the following:
    - **Work type** - *Put**
    - **Site** - *5*
    - **Warehouse** - *51*
    - Accept the defaults for remaining fields.

1. Select **Save** to save your directive and enable the **Lines** FastTab.
1. In the **Lines** Toolbar, select **New** and enter the following:
    - **From quantity** - *1*
    - **To quantity** - *1000000*
    - Accept the defaults for remaining fields.

1. Select **Save** in the Action Pane to save the new line and enable the **Location Directive Actions** FastTab.
1. With the line still selected in the **Lines** grid, select **New**in the **Location directive actions** FastTab to set up actions for the line. Enter the following:
    - **Name** - "Quality"
    - Accept the defaults for remaining fields.

1. Select **Save** in the Action Pane to enable **Edit query** in the **Location Directive Actions** Toolbar.
1. In the **Location directive actions** grid, ensure that the *Quality* line you just added is selected.
1. In the **Location directive actions** Toolbar, select **Edit query** to open a dialog box where you can edit the query for the selected action.
1. On the **Range** tab, select **Add** to add a new row to the query. Enter the following:
    - **Table** - *Locations*
    - **Derived table** - *Locations*
    - **Field** - *Location*
    - **Criteria** - *QMS*
        - The *QMS* location is a warehouse location for quality.
    - Select **OK** to close the dialog box.

### Mobile Device Menu Items

Configure a menu item for mobile devices to perform the Quality Check function.

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. In the list, select the **Purchase Put-away** menu item.
1. Select **Edit** in the Action Pane.
1. In the **Work classes** Toolbar, select **New** to add a row to the grid and enter the following:
    - **Work class ID** - *QC Check*
        - Enter the name of the [work class](#work-class) that you created earlier for quality-control work.
    - **Work order type** - *Quality in quality check*

1. Select **Save** in the Action Pane.

<a name="example-scenario"></a>

### Scenario

#### Create a purchase order

Once you have enabled and set up all of the sample data described previously in this topic, do the following to try out this feature. Create a purchase order:

1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**.
1. Select **New** in the Action Pane.
1. The **Create purchase order** dialog box opens. Enter the following:
    - **Vendor account** - "104"
    - **Warehouse** - "51"

1. Select **OK** to close the dialog box and open a new purchase order.
1. The **Purchase order lines** FastTab grid contains a new, blank line. Enter the following:
    - **Item number** - *M9203*
    - **Quantity** - *3*
    - **Unit** - *PL*

1. Select **Save** in the Action Pane.

#### Process Quality check receiving

Once the Purchase Order has been created it can be received utilizing PO Line Receiving and the Quality Check functionality.

##### Receive pallet 1

1. Login to the Mobile app with a user for warehouse 51.
1. Go to **Inbound > PO line receiving**.
1. Enter the purchase order number in the **PONUM** field.
1. Confirm the purchase order number.
1. Next, enter the line number of the purchase order being received. Since this scenario only has a single line on the order, you will enter *1* in the **LINENUM** field for each receiving step.
    - **LINENUM** - *1*

1. Confirm the line number.
1. Next, enter the quantity to be received. Since this scenario's purchase order was for 3 pallets (*PL*), you will enter a quantity of *1* in the **QTY** field for each receiving step.
    - **QTY** - *1*

1. Confirm the quantity.
1. Next the **Quality check** screen is displayed. There are no entry fields on this screen except for, the confirm button at the bottom of the screen, and the menu button (**≡**) at the top of the screen.

:::image type="content" source="media/Quality check.png" alt-text="Quality check screen":::

10. To expedite the quality check process, when the pallet passes the quality check the user simply confirms the **Quality check** screen.
1. Select confirm to Pass the quality check for the first pallet from line 1.
1. The next screen is **Purchase orders: Put**. Details of Put work are displayed:
    - **LOC** - *BULK-007*
        - This is the designated put away location for purchase order receiving.
    - **LP** - *License plate ID generated by the system*
    - **Item** - *M9203*
    - **Qty** - *1 PL:    100 ea*
    - The item description is also displayed.

1. Confirm the put away work.
1. A **Work Completed** message is displayed on the PO Line Receiving **Task** screen. The **LINENUM** field is available to begin the receiving of the next pallet.

##### Receive pallet 2

1. For this scenario, the pallet will be rejected.
1. Enter *1* and confirm the line number.
1. The **Qty** field is now available, enter *1* and confirm.
1. Next the **Quality check** screen is displayed.
    - For this receipt, the pallet will be rejected for quality and the pallet will be put into the QMS quality location.

1. Select the menu button (**≡**) at the top of the screen.
1. A menu list drop-down opens.
1. Select **Reject** from the list.
1. Next, the **Task** screen appears for a **LOCATION**. Enter the *Put* location to send the pallet for further inspection.
1. Enter **QMS**.
1. The next screen is **Quality in quality check: Put**. Details of Put work are displayed:
    - **LOC** - *QMS*
        - This is the designated put away location for rejected quality receiving.
    - **LP** - *License plate ID generated by the system*
    - **Item** - *M9203*
    - **Qty** - *1 PL:    100 ea*
    - The item description is also displayed.

1. Confirm the put away work.
1. A **Work Completed** message is displayed on the PO Line Receiving **Task** screen. The **LINENUM** field is available to begin the receiving of the next pallet.

##### Receive pallet 3

1. For this scenario, pallet 3 will be accepted.
1. Enter *1* and confirm the line number.
1. The **Qty** field is now available, enter *1* and confirm.
1. Next the **Quality check** screen is displayed.
    - For this receipt, the pallet will be accepted for quality and the pallet will be put into the *BULK-007* put away location.

1. Select confirm to Pass the quality check.
1. The next screen is **Purchase orders: Put**. Details of Put work are displayed:
    - **LOC** - *QMS*
        - This is the quality location from the pallet 2 receipt. The put away location must be overridden.
    - **LP** - *License plate ID generated by the system*
    - **Item** - *M9203*
    - **Qty** - *1 PL:    100 ea*
    - The item description is also displayed.
1. Select the menu button (**≡**) at the top of the screen.
1. A menu list drop-down opens.
1. Select **Override Loc** from the list.
1. A **Work exceptions** message *Staging lane changed* is displayed. Confirm the message.
1. Next, the **Task** screen appears for a **LOCATION**. Enter the *Put* location to send the pallet for further inspection.
1. Enter **BULK-007** and confirm.
1. The next screen is **Purchase orders: Put**. Details of Put work are displayed:
    - **LOC** - *BULK-007*
    - **LP** - *License plate ID generated by the system*
    - **Item** - *M9203*
    - **Qty** - *1 PL:    100 ea*
    - The item description is also displayed.

1. Confirm the put away work.
1. A **Work Completed** message is displayed on the PO Line Receiving **Task** screen. The **LINENUM** field is available to begin the receiving of the next pallet.
1. Select the menu button (**≡**) at the top of the screen.
1. A menu list drop-down opens.
1. Select **Cancel** from the list to return to the menu. You may now exit the mobile app.

When you have finished this procedure, you will have created a quality order for the rejected pallet.
Go to **Inventory management > Periodic tasks > Quality management > Quality orders** to view the orders created. Quality order testing can now be processed.
