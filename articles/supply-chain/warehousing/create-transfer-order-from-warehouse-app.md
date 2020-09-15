---
# required metadata

title: Create transfer order from the warehouse app
description: This topic describes the create and process transfer orders from the warehouse app feature 
author: perlynne
manager: tfehr
ms.date: 09/02/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSMobileDeviceQueueEvent 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-10-09
ms.dyn365.ops.version: 10.0.15

---

# Create transfer orders from the warehouse app

[!include [banner](../includes/banner.md)]

This feature lets warehouse workers create and process transfer orders directly from the warehouse app. The warehouse workers start by selecting the destination warehouse and can following scan one or more license plates using the app. When the warehouse worker selects the **Complete order** a batch job will create the required transfer order and order lines based on the on-hand inventory registered for those license plates.

## <a name="enable-create-transfer-order-from-warehouse-app"></a>Enable the create transfer orders from Warehouse app feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Create and process transfer orders from the warehouse app

The feature is dependent on having the feature [Process warehouse app events](warehouse-app-events.md) enabled.

## <a name="setup-warehouse-app-menu"></a>Set up a mobile device menu item to create transfer orders

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New** to add a new menu item. Then make the following settings to get started:
    - **Menu item name** - Assign a name as it should appear in Supply Chain Management
    - **Title** - Assign a menu name as it should be presented to workers in the warehouse app.
    - **Mode** - Set to *Indirect* (this warehouse app will not create work)
    - **Activity code** - Set to *Create transfer order from license plates* to enable the warehouse workers to create a transfer order based on one or more scanned license plates.
1. Use the **Order line creation policy** setting to control how transfer order lines will be created by this menu item. The lines will get created/updated based on the on-hand inventory registered for the scanned license plates. Choose one of the following values:
    - **No reservation** - The transfer order lines will not get reserved.
    - **License plate guided with line reservation** – The transfer order lines will get reserved and use the License plate guided strategy option, which stores the relevant license plate IDs associated with the order lines. Located license plate ID values can therefore be used as part of the work creation process for the transfer order lines.
1. Use the **Outbound shipment policy** setting to add more automation to the outbound transfer order shipment process, as needed. When a worker selects the **Complete order** button, the app creates the *Complete order* warehouse app event, which will save the value you choose here in the **Outbound shipment policy** field for each line in the current transfer order. Later, when the event queue is processed by a batch job to create the transfer order, the value stored in this field can be read by the batch job, and may therefore control how that job processes each line. Choose one of the following:
    - **None**
    - **Release to warehouse**
    - **Ship confirm**
    - **Release and ship confirm**
1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**
1. Select **Edit**.
1. Select a existing menu following selection of the new menu item under **Available menus and menu items**. Add the menu item by selecting the right-arrow button.

## Create a transfer order based on license plates

The warehouse app has a very simple process for creating transfer orders based on license plates. To do this, the worker does the following using the warehouse app:

1. Create the transfer order and identify the destination warehouse.
1. Identify each license plate to be shipped.
1. Select **Complete order**.

>[!Note]
> It is possible for multiple workers to assign license plates intended for the same transfer order by using the the **Select transfer order** button to select an existing, unprocessed, transfer order number from the warehouse app event queue. For information about how to find the transfer order number values, see [Inquire the warehouse app events](#inquire-the-warehouse-app-events).

## Example scenario

This scenario provides an overview of the process for getting transfer orders created and automatically processed based on the on-hand inventory registered on the selected license plates.

To work through this scenario using the values suggested, you must work on a system with demo data installed and select the *USMF* legal entity before you begin.

This scenario assumes that you have already enabled both the [Create and process transfer orders from the warehouse app feature](#enable-create-transfer-order-from-warehouse-app), and the [warehouse app event processing](warehouse-app-events.md) capability.

### Example Scenario blueprint

You are a retailer and have multiple license plates, each containing a mix of items placed at a specific location within one of your warehouses (*warehouse 51*). You would like to enable the process that allows workers to create a transfer order to another warehouse for a collection of scanned license plates and automatically ship update the transfer order as soon as the last license plate for the order has been identified.

![Automated transfer order process example](media/create-transfer-order-from-app-example.png "Automated transfer order process example")

### Create a mobile device menu item for creating transfer orders

This section explains how to create a new mobile device menu item for creating transfer orders. You must select the **Mode** _Indirect_ and select the **Activity code** _Create transfer order from license plates_.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select **New**.
1. In the **Menu item name** field, enter the name *Create TO*. In the **Title** field, enter the description *Create TO*.
1. In the **Mode** field select *Indirect*.
1. In the **Activity code** select *Create transfer order from license plates*
1. In the **Order line creation policy** select *License plate guided with line reservation*.
1. In the **Outbound shipment policy** select *Release and ship confirm*.
1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu**
1. Select **Edit**.
1. Select the existing **Inventory** menu and then select the new menu item under **Available menus and menu items**. Add the menu item into to **Inventory** menu by selecting the right-arrow button.

### Set up work templates to auto process and break work by located license plate

In this section it will be explained how to enable a work template to automatically process the work created by the template when a wave is released.

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. Select **Edit**.
1. Set **Work order type** to *Transfer issue*.
1. Select **New** to create a new work template with work template name *Auto process LP*.
1. Enable **Automatically process**.
1. Add two work template details lines for work type **Pick** and **Put**. Use *Work Class ID TransfOut* for both.
1. Update the second **Put** line set **Directive code** to *Baydoor*.
1. Make sure this new work template gets the lowest **Sequence number**.
1. Select **Edit query** to open the query editor and then go to **Sorting** tab.
1. Select **Add** and set **Field** to *Located license plate ID*.
1. Select **OK** followed by **Yes** to reset the grouping and return to the **Work templates** page.
1. Select **Work header breaks** and enable the **Group by this field** for the **Located license plate ID** and close.

> [!NOTE]
> Not all setup can get auto processed. E.g. catch weight items and the use of mixed tracking dimensions.

### Set up location directives for the license plate guided strategy

This section explains how to set up a location directive pick process to use the **License plate guided** strategy.

1. Go to **Warehouse management \> Setup \> Location directives**.
1. Select **Edit**.
1. Set the **Work order type** to *Transfer issue*.
1. Select the existing location directive **51 TO Pick** and enable the **Allow split** for the existing location directive line.
1. For the existing location directive action, set the **Strategy** to *License plate guided*.

> [!NOTE]
> The *License plate guided* strategy will try to reserve and create picking work against the locations holding the requested license plates that have been associated with the transfer order lines. But if this isn't possible and you still would like to create picking work, you should fall back to another location directive action strategy, and perhaps also search for inventory in another area of the warehouse, depending on your business process needs.

### Set up a batch job to process warehouse app events

This section explains how to set up a scheduled batch job to process warehouse app events.

1. Go to **Warehouse management \> Periodic tasks \> Process warehouse app events**.
2. Enable **Batch processing** under the **Run in background** section.
3. Select **Recurrence** and set up the batch job to process based on the interval needed for your business.
4. Select **OK** to return to the main dialog.
5. Select **OK** in the main dialog to add the job to the batch queue.

### Set up a batch job to release transfer orders automatically
<!-- KFM: Continue here. Check/improve steps around setting up a filer. -->
This section explains how to set up a scheduled batch job to release the transfer orders that have been marked as "ready to release".

1. Go to **Warehouse management \> Release to warehouse \> Automatic release of transfer orders**.
1. Select **Filter** under the **Records to include** section.
1. Insert a range for the table **Transfer line release to warehouse** , field **Outbound shipment policy** and select **Criteria** as **Release and ship confirm**.
1. Select **OK** to return to the main dialog.
1. Enable **Batch processing** under the **Run in background** section.
1. Select **Recurrence** and setup the batch job to process based on interval needed for your business.
1. Select **OK** to return to the main dialog.
1. Select **OK** in the main dialog to get the batch job added to the batch queue.

### Setup the Process outbound shipment batch job

In this section it will be explained how to setup a scheduled batch job going to run the outbound shipment confirmation for loads ready to ship related to transfer order lines which are "ready to ship".

1. Go to **Warehouse management \> Periodic tasks \> Process outbound shipments**.
1. Select **Filter** under the **Records to** include section.
1. Select the **Joins** button following a selection of the Loads table in the hierarchy list.
1. Select the **+Add table join** and mark the relation **Load details (Load ID)**. Then press the "Select" button.
1. Continue this process from the **Load details** to get the **Transfer order lines** joined, following the **Invent Transfer Additional Fields** table.
1. Select the **Range** section and insert a range for the table **Loads** , field **Load status** and select **Criteria** as **Loaded**.
1. Add another line for the table **Invent Transfer Additional Fields** , field **Outbound shipment policy** and select **Criteria** as **Release and ship confirm**.
1. Select **OK** to return to the main dialog.
1. Enable **Batch processing** under the **Run in background** section.
1. Select **Recurrence** and setup the batch job to process based on interval needed for your business.
1. Select **OK** to return to the main dialog.
1. Select **OK** in the main dialog to get the batch job added to the batch queue.

> [!Note]
> More information can be found at: [Confirm outbound shipments from batch jobs](confirm-outbound-shipments-from-batch-jobs.md).

## Processing the example for "Create transfer order from the warehouse app"

### Add on-hand on a license plate

As a starting point for this scenario you will need to have a license plate containing physical available inventory on hand.

| Item | Warehouse | Inventory status | Location | License plate | Quantity |
| --- | --- | --- | --- | --- | --- |
| A0001 | 51 | Available | LP-010 | LP10 | 1 |
| A0002 | 51 | Available | LP-010 | LP10 | 2 |

Add physical inventory on hand quantities by using the following values:

> [!NOTE]
> You will need to create the license plate and use locations which allows to carry mixed items, like LP-010.

### Create and process transfer orders from the warehouse app

1. Open the app and login as user *51*. Current user warehouse will be 51.
1. Select the menu item *Create TO*.
1. Create transfer order by selecting to-warehouse *61* in the **Warehouse** field. The new transfer order will be going from current warehouse 51 to destination warehouse 61.
1. Scan a license plate *LP10* into the **License plate** field to add the license plate to the transfer order.
1. Click on the menu button and select **Complete order** to finalize the warehouse app transfer order creation.

For the above-mentioned example two **Warehouse app events** (*Create transfer order* and *Complete transfer order*) gets used.

### <a name="#inquire-the-warehouse-app-events"></a>Inquire the warehouse app events

You can view the event queue and events messages generated by the warehouse app by going to **Warehouse management \> Inquiries and reports \> Mobile device logs \> Warehouse app events**.

The *Create transfer order* event messages will get created in the status **Waiting** which means that the **Process warehouse app events** batch job will not pick-up and process the event messages. As soon as the event messages gets updates to status **Queued** the batch job will process the events. This will happen at the same time as the creation of the *Complete transfer order* event (**Complete order** button click). When the *Create transfer order* event messages has been processed the status gets updated to **Completed** or **Failed**. When the *Complete transfer order* status gets updated to **Completed,** all the related events gets deleted from the queue.

Because the **Warehouse app events** for the creation of transfer order data will not get processed by the batch job before the messages gets updated into status **Queued** , you will need to look-up the requested transfer order numbers as part of the **Identifier** field.

As part of the warehouse event processing it might happen that the creation of the transfer order lines fails. In this case the state of the event message will get updated to **Failed** and you can use the **Batch log** information to read why and use take action to correct any problems.

Typical issues could be related to missing setup for the process, like e.g. a missing transit warehouse for the *Create transfer order* event. In an example like this this, you would simply add a transit warehouse to the shipping warehouse and change the status for all the warehouse app event messages via the **Reset** option from **Failed** into **Queued** which will mean that the batch job will process the event messages again after the correction of the setup data.

Within production environments, the exceptions would of cause be more process related, like e.g. having a requested license plate which at the batch job processing time is empty and thereby no transfer order lines can get created. This failed event message can either be removed by using the **Delete** option or you can add the needed physical on-hand on the license plate and use the **Reset** option for all the related event messages.

More information can be found here: [Warehouse app event processing](warehouse-app-events.md).

### Follow up on the example scenario processing

During this scenario, the following occurred:

1. Using the warehouse app, you selected a menu item that uses the activity code **Create transfer order from license plates**.
1. The app prompted you to select the destination warehouse for the transfer order. The source warehouse is always the one you currently are operating against.
1. On the selection of the destination warehouse, the system reserved an ID number for the upcoming transfer order (based on the transfer-order number sequence defined on your system) but did not create the transfer order yet.
1. When you scanned the license plate *LP10* containing on-hand inventory that should be moved to the new warehouse an **Warehouse app event** was added to the events queue to be processed later. The warehouse event contained message details about the scan, including the intended transfer-order number.
1. At warehouse app **Complete order** button click a new warehouse app event got created and the relate existing event changed status to **Queued**.
1. On the back end the **Process warehouse app events batch job** did now pick-up the **Queued** event and collected the on-hand related to the scanned license plate. Based on the on-hand the actual transfer order record and associated lines got created. The job also populated the **Outbound shipment policy** field for the transfer order with the value based to configured *Release and ship confirm* and linked the license plate against the lines for the **License plate guided** strategy.
1. Based on the transfer order line **Outbound shipment policy** field value the **Automatic release of transfer orders batch job** query now resulted in releasing the transfer order to the shipping warehouse. And due to the setup for the used **Wave template**, **Work template**, and **Location directives** the work got auto processes resulting on the **Load status** got updated to *Loaded*.
1. The **Process outbound shipment batch job** now got executed for the load resulting in the transfer order getting shipped and thereby the Advance Shipment Notice (ASN) to get generated.

## FAQ

### Mobile device menu item setup

>Q: Why can’t I see **Create transfer order from license plate** in the menu item work activity dropdown?
>
>A: The feature **Create and process transfer orders from the warehouse app** must be enabled, see: [Enable the create transfer orders from Warehouse app](#enable-create-transfer-order-from-warehouse-app).>

### Warehouse app processes

>Q: Why can’t I see the menu button **Complete order**?
>
>A: You must have at least one license plate assigned to the transfer order.

>Q: Can several warehouse app users add license plates to the same transfer order at the same time?
>
>A: Yes, several warehouse workers can scan license plates into the same transfer order."

>Q: Can the same license plate be added to different transfer orders?
>
>A: No, a license plate can only be added to one transfer order at the time.

>Q: After having selected the **Complete order** button, can I then add more license plates for that transfer order?
>A: No, you can't add more license plates to a transfer order that has a **Complete transfer order** warehouse app event.

>Q: How can I find existing transfer orders to be used via the **Select transfer order** button in the warehouse app, if the order has not yet been created in the backend system?
>
>A: Currently, you can't look up transfer orders in the app, but you can find the transfer order numbers in the **Warehouse app events** page, see: [Inquire the warehouse app events](#inquire-the-warehouse-app-events).

>Q: Can I manually select the transfer order number to be used from the warehouse app?
>
>A: Only auto-generated transfer order numbers via number sequences are supported.

### Background processing

>Q: How should I clean up records in my warehouse app events queue message tables?
>
>A: You can view and maintain this in the Warehouse app events page, see: Inspect the warehouse app events.

>Q: Why is the transfer order **Receipt date** not updated according to my **Delivery date control** setup?
>
>A: The transfer orders are created without using the **Delivery date control** capabilities.

>Q: Can I use a license plate having physical negative inventory on hand?
>
>A: The feature only supports positive physical on-hand quantities. You must make sure that you have positive physical on-hand quantities at the warehouse and inventory status level before assigning license plates to a transfer order.