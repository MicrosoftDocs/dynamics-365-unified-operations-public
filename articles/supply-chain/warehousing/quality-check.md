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

Use this feature to enable warehouse workers to perform quick quality spot checks while receiving items to the inbound dock area. These spot checks are beneficial when inspecting packaging or any other easily recognizable part of the item. The feature guides workers to take a quick look to see if anything is obviously faulty before stocking the inventory to its location.

This functionality offers an alternative to the existing quality check process, offering more flexibility and faster processing. <!-- can we link to documentation for that existing functionality? How can we tell this feature apart from that functionality? Should this feature be called "quality spot check" "flexible quality check" or "advanced quality check" or something like that? -->

When you use this feature, arrival and quality check proceeds as follows:

1. When a shipment arrives, the warehouse worker registers the arrival, and also registers its location by scanning a license plate.
1. The worker does a quick quality check and records the result (pass or fail) for that license plate.
1. One of the following happens:
    - License plates containing accepted items are guided to a storage location as usual.
    - For the rejected license plates, existing put-away work is cancelled and a new *quality check* work order is created. The license plate is then diverted to a quality check location for further inspection.

<!-- The above wasn't entirely clear in the draft. I tried to clarify with this revision. Please confirm it's still correct -->

This process can also be set to divert all scanned license plates to the quality check location immediately.

## Enable the quality check feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Quality check

## Set up and try out this feature

This section provides guidelines and an example of how to set up and use this feature.

### Enable sample data

To work through the [example scenario](#example-scenario) using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use this example as guidance for how to use this feature when working on a production system, but then you must substitute your own values for each setting described here.

<a name="quality-template"></a>

### Set up a quality check template

<!-- KFM: Briefly describe what this is and why we are doing this. -->

1. Go to **Warehouse management > Setup > Work > Quality check template**.

1. Select **New** to add a new template to the table.

1. Make the following settings for the new row:

    - **Quality check template name** - Enter a name that identifies this policy.<br>(If you're preparing USMF sample data, then enter "Dock check".)
    - **Acceptance policy** - <!-- KFM: Briefly what this setting is for -->Select one of the following (If you're preparing USMF sample data, then select "Prompt user".):
        - **Auto reject** - <!-- KFM: Briefly describe this option -->
        - **Prompt user** - <!-- KFM: Briefly describe this option -->
    - **Quality processing policy** - <!-- KFM: Briefly what this setting is for -->Select one of the following (If you're preparing USMF sample data, then select "Create quality order".):
        - **Create work only** - <!-- KFM: Briefly describe this option -->
        - **Create quality order** - <!-- KFM: Briefly describe this option -->
    - **Test group** - <!-- KFM: Briefly what this setting is for. Where do these values come from? What is "Destructive testing" for? --><br>(If you're preparing USMF sample data, then select "Enclosure".)

<a name="work-class"></a>

### Set up a work class for quality control

<!-- KFM: Briefly describe what this is and why we are doing this. -->

1. Go to **Warehouse management > Setup > Work > Work classes**.
1. Select **New** to create a new work class.
1. Make the following settings for your new work class:
    - **Work class ID** - Enter a name that identifies this work class.<br>(If you're preparing USMF sample data, then enter "QC Check".)
    - **Description** - Enter a short description of what this work class is for.<br>(If you're preparing USMF sample data, then enter "QC Check".)
    - **Work order type** - Identify the type of work order created by this work class. When setting up quality control work, always select "Quality in quality check" (also if you're preparing USMF sample data).

<!-- KFM: What about the lines here (Valid put location types). We should say whether and why we might need them. -->

For more information about work classes and how to create them, see [Create a work class](tasks/create-work-class.md).

### Set up a work template that includes quality control

<!-- KFM: Briefly describe what this is and why we are doing this. -->

1. Go to **Warehouse management > Setup > Work > Work templates**.
1. Set **Work order type** to "Purchase orders" to start working with templates of that type.
1. Create or select a work template that should include a quality-check step.<br>(If you're preparing USMF sample data, then select "51 PO Receipt".)
1. In the **Work template details** area, select **New** to add a new row to the table for quality control.
1. Make the following settings for the new row:
    - **Work type** - Set to "Quality check" to add a quality-check step (also if you're preparing USMF sample data).
    - **Work class ID**: Set to "Purchase" (also if you're preparing USMF sample data). <!-- KFM: Why, what does this setting do? -->
1. Select **Save** to save your work so far. After saving, make the following setting for the quality-check row that you just added:
    - **Quality check template name**: Select the name of the [quality check template](#quality-template) that you created earlier.<br>(If you're preparing USMF sample data, then select "Dock check".)
1. Select the new line and use the **Move up** and **Move down** buttons to position the new row to its desired position for this work process.<br>(If you're preparing USMF sample data, then place it in the second position, between the pick and put operations.)
1. Now change the **Work order type** to "Quality in quality check" to switch to working with templates of that type.
1. Select **New** to add a row to the top table and then make the following settings for the new row:
    - **Work template** - Enter a name for the template.<br>(If you're preparing USMF sample data, then select "51 Quality Check".)
    - **Work template description**: Enter a short description for the template.<br>(If you're preparing USMF sample data, then select "51 Quality Check".)
1. Select **Save** to store your new template.
1. With your new template still selected in the top table, select **New** in the Work template details area to add a new row there. Then enter the following values for the new row:
    - **Work type** - <!-- KFM Briefly describe what we should choose and why. Always "Pick"? --><br>(If you're preparing USMF sample data, then select "Pick".)
    - **Work class ID** - Select the name of the [work class](#work-class) that you created earlier for quality-control work.<br>(If you're preparing USMF sample data, then select "QC Check".)
1. Add a second row to your new template, then enter the following values for this row:
    - **Work type** - <!-- KFM Briefly describe what we should choose and why. Always "Put"? --><br>(If you're preparing USMF sample data, then select "Put".)
    - **Work class ID** - Select the name of the [work class](#work-class) that you created earlier for quality-control work.<br>(If you're preparing USMF sample data, then select "QC Check".)

For more information about work templates, see [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md)

### Set up a location directive to handle quality failures

<!-- KFM: Briefly describe what this is and why we are doing this. -->

1. Go to **Warehouse management > Setup > Location directives**.
1. Set **Work order type** to "Purchase orders" to start working with location directives of that type.
1. Create or select a location directive for handling quality failures.<br>If you're preparing USMF sample data, then select **New** to create a new location directive and enter the following settings for the new directive:
    - **Name** - "51 To Quality"
    - **Work type** - "Put"
    - **Site** - "5"
    - **Warehouse** - "51"
1. Select **Save** to save your directive.
1. In the **Lines** area, set up your lines as needed. <!-- KFM: what is this setting for, and why are we doing this? What affect will the recommended settings have? --><br>If you're preparing USMF sample data, then select **New** to add a new row to the table and enter the following settings for the new row:
    - **From quantity** - "1"
    - **To quantity** - "1000000"
1. Select **Save** to save the new line.
1. With a line still selected, in the **Location directive actions** area, set up actions for that line as needed. Repeat for each line. <!-- KFM: what is this setting for, and why are we doing this? What affect will the recommended settings have? --><br>If you're preparing USMF sample data, then select the line you just created, select **New** to add a new action for that line, and enter the following settings for the new action: <!-- What does this name mean? What about the other settings--can we link to more information about them? -->
    - **Name** - "Quality"
1. In the **Location directive actions** area, select an action and then select **Edit query** to open a pane where you can edit the query for the selected action.
1. On the **Range** tab, select **Add** to add a new row to the query. <!-- KFM: what is this setting for, and why are we doing this? What affect will the recommended settings have? -->Make the following settings for the new line:
    - **Table** - "Locations"
    - **Derived table** - "Locations"
    - **Field** - "Location"
    - **Criteria** - "QMS" <!-- KFM: what does this mean? What will it do? Is this for sample data, or always? -->

### Set up mobile device menu items

<!-- KFM: Briefly describe what this is and why we are doing this. -->

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Create or select the mobile device menu item where you'd like to include a quality check option.<br>If you're preparing USMF sample data, then select the 
"Purchase Put-away" item.
1. In the **Work classes** area, select **New** to add a row to the table.
1. For the new row set **Work class ID** to the name of the [work class](#work-class) that you created earlier for quality-control work.<br>(If you're preparing USMF sample data, then set **Work class ID** to "QC Check".)

<a name="example-scenario"></a>

### Example scenario

Once you have enabled and set up all of the sample data described previously in this topic, do the following to try out this feature:

1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**.
1. Select **New**. 
1. The **Create purchase order** pane opens. Enter the following settings here:
    - **Vendor account** - "104"
    - **Warehouse** - "51"
1. Select **OK** to close the pane and open your new order.
1. The **Purchase order lines** section already contains a new, blank line. Enter the following values for it:
    - **Item number** - "M9203"
    - **Quantity** - "3"
    - **Unit** - "PL"
1. Sign in to a mobile device and go to **Inbound > Purchase Line Receive**. Enter your purchase order number and LineNum 1. Receive 1 PL. <!-- KFM: We need to explain this more clearly. We also need to explain or link to how to run the emulator. I don't know how, so I couldn't confirm this. -->
1. Return to Supply Chain Management with your purchase order still open. In the **Purchase order lines** area, select **Work details**.
1. The **Work** page opens. Copy the **Target license plate ID** shown here for the created put-away work.
1. Sign in to a mobile device and go to **Inbound > Purchase Put-away**. EEnter the license plate you copied. Confirm the pick from RECV. <!-- KFM: We need to explain this more clearly. I couldn't confirm this. -->
1. On the quality check page, select **Reject**. <!-- KFM: We need to explain this more clearly. Where are we, still in the mobile device? -->

The original purchase order put-away work will be completed (the put location will be overridden to RECV) and you will now be directed to complete the put of the newly created Quality in quality check work. Confirm the Put to QMS. <!-- KFM: We need more detail here. I don't understand what is going on. Change from passive to active voice so we know who is doing what. -->

When you have finished this procedure, you will have created a quality order, which you can then process using normal quality procedures. <!-- KFM: What are "normal quality procedures"? Do we have a link for that? -->
