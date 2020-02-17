# Quality check

With this functionality, you can perform rapid quality checks on the spot at the time of receiving to the inbound dock area. These spot checks are beneficial when inspecting packaging or any other easily recognizable part of the item. It serves as a quick look to see if anything is standing out as faulty before stocking the inventory to its location.

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

This section provides an example of how to set up and use this feature.

### Enable sample data

To work through this example using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

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

Navigate to _Warehouse management - Setup - Location directives_ and change the Work order type to Quality In Quality Check. Create a new record:

- Name: 51 To Quality
- Work type: Put
- Site: 5
- Warehouse: 51

Create a line:

- From quantity: 1
- To quantity: 1000000

Create a Location Directive Action:

- Name: Quality

Open the edit query for the action and add a range for Locations – Location = QMS

### Set up mobile device menu items

Navigate to _Warehouse management -  Setup - Mobile device  - Mobile device menu items_. Select Purchase Put-away.

In the Work classes grid, add a new record for QC Check

### Try out the feature

Navigate to _Procurement and sourcing - Purchase orders - All purchase orders_ and create a new order. Specify Vendor account = 104 and Warehouse = 51.

Add a line for item M9203, quantity 3 PL.

Open the mobile device and navigate to _Inbound - Purchase Line Receive_. Enter your purchase order number and LineNum 1. Receive 1 PL.

Click on Work details from the purchase order line action bar. Copy the Target license plate from the created putaway work.

On the mobile device navigate to _Inbound -  Purchase Put-away_. Enter the license plate you copied. Confirm the pick from RECV.

On the quality check screen, choose &#39;Reject&#39;.

The original purchase order putaway work will be completed (the put location will be overridden to RECV) and you will now be directed to complete the put of the newly created Quality in quality check work. Confirm the Put to QMS.

A quality order has been created, and can be processed using normal quality procedures.
