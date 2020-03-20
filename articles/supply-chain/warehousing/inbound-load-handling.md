---
# required metadata

title: Warehouse handling of inbound loads for purchase orders
description: Describes the warehouse handling process of inbound loads for purchase orders.
author: omulvad
manager: AnnBe
ms.date: 03/21/2020
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
ms.author: omulvad
ms.search.validFrom: 2020-03-21
ms.dyn365.ops.version: Release 10.0.8
---

# Warehouse handling of inbound loads for purchase orders

This topic describes the warehouse handling process of inbound loads for purchase orders.

For each inbound load, your system should already include a related sales order, and may also contain a related load specification and/or transportation plan. For more information about how to create and manage inbound loads, see also [Business process: Planning transportation for inbound loads](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/business-process-planning-transportation-for-inbound-loads).

## Overview: How inbound loads are created, registered, and received

The following illustration shows the typical flow of handling inbound loads with purchase order quantities when they arrive at your warehouse.

![The inbound load handling process](media/inbound-process.png "The inbound load handling process")

1. **Vendor confirms the purchase order**  
    The process begins when a purchase order is entered into the system and then delivered to a vendor, who confirms the order. The purchase order must exist before you can create an inbound load record&mdash;however, you can create the inbound load even if the order hasn't been confirmed. More information: [Approve and confirm purchase orders](../procurement/purchase-order-approval-confirmation.md)

1. **An inbound load record is created to plan the arrival and its contents**  
    The inbound load record represents a vendor shipment of one or more purchase orders. The load is expected to arrive at the warehouse as one physical transportation unit (such as a truckload). The inbound load record is used for planning purposes and allows the logistics coordinator to track the load's progress from the vendor. It's also used to register order line quantities and to manage progress through warehouse operations, such as arrival and put-away work. Loads can be created automatically or manually; they can be based on a purchase order or on an advanced shipment notice (ASN) from the vendor. More information: [Create or modify an inbound load](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/create-or-modify-an-inbound-load)

1. **Vendor confirms load dispatch**  
    When the vendor dispatches the load, the logistics coordinator at the receiving warehouse confirms the load shipment. If the receiving company is using the Transportation Management module, inbound shipment confirmation will trigger other load management processes that are associated with the inbound loads.  More information: [Confirm a load for shipping](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/confirm-a-load-for-shipping)

1. **Load arrives at the warehouse and workers register quantities**  
    When a truckload arrives at the warehouse receiving dock, warehouse workers register the load quantities. When the Warehouse Management module is used, registration is done by the workers using the mobile devices. More information: [Product receipt against purchase orders - registration](../procurement/product-receipt-against-purchase-orders.md#registration) and [Register quantities arrived on inbound load](#register-item-quantities-arriving)

1. **Registered load quantities are posted against purchase orders**  
    Once the load quantities have been registered as arrived, those quantities must be product-receipt posted to the company's inventory ledger to record the physical stock increase.  More information: [Product receipt against purchase orders - product receipt](../procurement/product-receipt-against-purchase-orders.md#product-receipt) and [Post registered product quantities against purchase orders](#post-registered-quantities).

<a name="register-item-quantities-arriving"></a>

## Register item quantities arriving with an inbound load

Dynamics 365 Supply Chain Management supports several operational approaches for recording the arrival of ordered products, so you can configure the system to match your specific business requirements. This section describes how to register incoming item quantities using a mobile device when advanced warehouse management is enabled in the system. An alternative flow based on using the item arrival journal, rather than a mobile device, is described in [Register items for an advanced warehousing enabled item using an item arrival journal](tasks/register-items-advanced-warehousing.md).

The first thing that happens when an inbound load arrives at the warehouse is that warehouse workers must register the item quantities included in the shipment&mdash;typically by using a handheld scanner. To enable this workflow, the following must be present in the system:

- **An inbound load record that describes the item quantities expected in the shipment**
Typically, the inbound load record will have been confirmed by the vender before the shipment arrives at the warehouse, which means it will have a status of _shipped_. However, warehouse workers can also register items quantities for loads with a status of _open_ or _received_. More information about this is provided later in this topic.

- **A mobile device menu configured to support load receiving**
The [Dynamics 365 for Finance and Operations – Warehousing app](install-configure-warehousing-app.md) for mobile devices supports the following work creation processes:
  - Load item receiving
  - Load item receiving and put away
  - Mixed license plate receiving (where the **Source document line identification method** field for the mobile device menu item is set to _Load item receiving_; see also [Mixed license plate receiving](mixed-license-plate-receiving.md))
  - Mixed license plate receiving and put away (where the **Source document line identification method** field for the mobile device menu item is set to _Load item receiving_; see also [Mixed license plate receiving](mixed-license-plate-receiving.md))
  > [!NOTE]
  > Regardless of the action, the system will generate work to take quantities registered into the receiving location and put them away into the regular storage location. When the _Load item receiving and put-away_ (or _Mixed license plate receiving and put away_) action is used, the worker who registered the load quantity will also be instructed by the device's screen to perform the put-away as part of the registration task, while the _Load item receiving_or the_Mixed license plate receiving_ flow assumes that put-away work will be done separately from the registration.

- **A work template to define pick and put work for incoming loads**
Related to the previous points, you must have at least one **Work template** for **Work order type** f _Purchase order_ containing a set of pick/put work types.

The mobile device guides the warehouse receiving clerk through the load quantity registration flow, which will, at minimum, include the following steps for each load ID:

1. Enter the load ID.
2. Enter the item number for a received item.
3. Enter the quantity of that item number received.
4. Enter the license plate number for the item's initial location (if not set to be generated automatically).
5. Tap **OK**.

Once the worker completes the above steps, the system makes the following updates on respective entities (provided that the purchase order line quantity arrived on one load and all load quantities have been registered):

| **Entity** | **Updates** | **Note** |
| --- | --- | --- |
| Load | Update the **Work created quantity** field on the load line to show the registered quantity. | The **Load status** remains _Shipped_ or _Open_ (if no shipment confirmation has been run for the load), or changes to _In process_, if at least one line of put-away work has started. |
| Inventory transaction of purchase order, whose associated load quantities have been registered |<p>The following are updated:</p><ul><li>The <b>Receipt</b> field is set to <i>Registered.</i></li><li>The <b>Location</b> field is updated with the receiving dock location code (the code is specified in the <b>Default receipt location</b> field for each warehouse).</li><li>The **License plate** field is updated with the license plate number entered or generated during the registration.</li><li>The **Load ID** field is updated with number of the load against which quantity has been registered. \* | \* The ability to link between the purchase order inventory transaction and the quantities registered against the load was introduced in version 10.0.9 as an optional feature called _Associate purchase order inventory transactions with load_. The feature is especially beneficial for operational flows when a single order of purchased goods is delivered as multiple loads, or when a load contains quantities for multiple purchase orders. |
| Warehouse put-away | Work is created based on a work template to instruct the worker to move the registered quantities from the receiving location to a regular storage location. | The choice of the storage location is controlled by the Put location directive. If no location directive has been defined, the put away location on the work is empty. |

Note that warehouse workers can register the receipt of a purchase order with one or more associated loads without using the _Load item receiving_ process. The available options are as follows:

- On the mobile device: use the _Purchase order line receiving_ and _Purchase order line receiving and put-away_ work processes. (If there exists more than one load for the purchase order line quantity, the worker won't be allowed to use the _Purchase order line receiving_ action and will instead be instructed to use the device action associated with the _Load item receiving_ work process.)
- On the client: use the **Item arrival journal**.
- On the client: use the **Registration** action accessible from the purchase order line.

> [!NOTE]
> If the purchase order receipt is registered using any of the above methods, no link is created between the purchase order inventory transaction and the load (even when the _Associate purchase order inventory transactions with load_ feature is enabled). One exception to this rule is when you use the **Purchase order line receiving** option and there exists only one load in any state other than _Received_ for the order line.

### Handle discrepancies while registering inbound load quantities

Warehouse workers can do a partial load quantity receipt registration. Each partial load quantity receipt then creates a separate inventory transaction with **Receipt** status _Registered_ for the respective registered quantity, with the same lot ID referring to the originating purchase order line.

#### Load under receiving

When a load arrives with item quantities that are less than the quantities stated on the load record, warehouse receiving personnel working directly in the client can acknowledge this by reducing the quantity on the load line to match the actual arrived and registered quantity.

<a name="load-over-receiving"></a>

#### Load over receiving

Over receiving occurs when a load arrives with item quantities that are greater than the expected load line quantity. You can control whether and to what degree this will be allowed during load registration.

Use the **Load over receipt** setting for the relevant mobile device menu item(s) to control what will happen when a warehouse work attempts to register an overdelivery. The setting is available for mobile device menu items that use the following work creation process types:

- Load item receiving
- Load item receiving and put away
- Mixed license plate receiving (when **Source document line identification method** = _Load item receiving_)
- Mixed license plate receiving and put-away (when **Source document line identification method** = _Load item receiving_)

The following table explains the options available for the **Load over receipt** setting.

|   |   |
| --- | --- |
| **Value** | **Description** |
| **Allow** | Allows workers to register the receipt of quantities greater than the remaining unregistered quantity for a selected load. This will only be permitted if the total registered quantity does not exceed the quantity of purchase order line associated with the load (adjusted for the overdelivery percentage).  |
| **Block** | <p>Prevents workers from registering the receipt of quantities greater than the remaining unregistered quantity for a selected load (adjusted for the overdelivery percentage). If a worker attempts to do this, the system will show an error and the worker will be prevented from continuing until they register a quantity that is equal to or lower than the remaining unregistered load quantity.<p></p>By default, the value of the overdelivery percentage on a load line is copied from the associated purchase order line. The system will use this value to calculate the total quantity allowed to be registered for a load line when **Load over receipt** is set to _Block_. However, this value can be overwritten as needed for individual loads. This becomes relevant during receiving flows where some or all of the excess quantity representing the order line overdelivery percentage is distributed disproportionally across multiple loads. For example, imagine the following situation:</p><ul><li>There are multiple loads for one purchase order line.</li><li>The purchase order line has an overdelivery percent that is higher than 0.</li><li>Quantities against one or more loads have already been registered without taking overdelivery percentage into account.</li><li>Overdelivery quantity arrives on the last load.</li></ul><p> To allow the excess quantity for the last load to be registered using a mobile device, the warehouse supervisor must increase the overdelivery percentage for the load line in question from the default to the value that would allow the full overdelivery to be registered with the final load.</p> |
| **Block&nbsp;for&nbsp;closed loads only** | Allows workers to over receive load line quantities for open loads but prevents it for loads with a status of _received_. |

> [!NOTE]
> The default value for **Load over receipt** is _Allow_, which matches the standard behavior available before the _Over receipt of load quantities_ feature was introduced in version 10.0.11.

### Put away the registered quantities

When registration is completed on the mobile device, the _quantity receipt registration_ action updates the inventory and warehouse records to indicate that those quantities are now located in the receiving dock location and are available for reservation. Typically, however, a company's warehouse operations would require the quantities to be moved from the receiving dock to the regular warehouse storage to enable the subsequent picking processes. Instructions for the put-away are captured in the put-away work that is created automatically when the inbound load was registered as received.

When the warehouse worker has completed the put-away work, the system records and tracks the result by updating updates several entities as summarized in the following table.

| **Entity** | **Updates** | **Note** |
| --- | --- | --- |
| Load | <p>The following are updated:</p><ul><li>The **Load status** changes to _In process._</li><li>The **Work status** changes to _100.00% of work completed._</li></ul> | The **Load status** changes to _In process_ when the worker starts the put-away task for at least one line of put-away work. |
| Inventory transactions of work, whose associated quantities have been put away | The **Receipt,**  **Location** and other relevant fields are updated to reflect the movement from the receiving location to the storage location. | The **Receipt state** of the purchase order inventory transaction remains _Registered_. |
| Warehouse put-away | **Work status** is changed to _Closed._ |   |

<a name="post-registered-quantities"></a>

## Post registered product quantities against purchase orders

Once inbound product quantities are registered in the system, those quantities become available for reservation in connection with sales and other outbound and internal operations. However, the system doesn't yet update the inventory (interim) account(s). To do this, the operations team must _post_ the registered product receipts.

The operation team can open a form for posting a product receipt by doing any _one_ of the following:

- Open the relevant **Load** record and then select the **Product receipt** action.
- Go to **Warehouse management > Periodic tasks > Update product receipts** and then specify the **Load ID** to  post.
- Open the relevant purchase order and select the **Product receipt** action.
- Go to **Procurement and sourcing > Purchase orders > Receiving products > Posting product receipt job.**

The **Product receipt** action available on the **Load** page (and its update-job equivalent, **Update product receipts** ) can only update product-receipt quantities on purchase order quantities that are in the _Registered_ state. However, the **Product receipt** action available on the **Purchase order** page can include quantities in both processing states (_Ordered_ and _Registered_), and can also control the product-receipt posting scope through additional parameters, such as _Receive now quantity_ and _Registered quantity and services_.

Only orders with a status of _Confirmed_ can be product-receipt posted. The **Product receipt** action will be shown as disabled for non-confirmed purchase orders.

### Post registered quantities from the Load page

To product-receipt post registered quantities from the **Load** page, the following prerequisites must be in place:

- The load must have at least one quantity unit with a status of _Registered._
- The load status must be _Shipped_.
- The purchase order associated with the load must have a status of _Confirmed_.

> [!NOTE]
> If the load hasn't been set to _Shipped_ (which happens when a user registers the load's inbound shipment), the system will automatically confirm the load before executing the product-receipt updating.

To product-receipt post the arrival registrations associated with a selected load, the worker selects the **Product receipt** action on the **Load** page, which opens a page with the following key details:

- The **Quantity** field under the **Parameters** section of the **Settings** tab shows the _Registered quantity._ No other options are available here.
- The grid on the **Overview** FastTab lists all the purchase orders included in the selected load.
- The grid on the **Lines** FastTab lists all the order lines that have a registered quantity.

> [!NOTE]
> Quantities for order lines shown on the **Line** tab are calculated differently depending on whether the _Allow multiple product receipt per load_ feature is available and enabled in your version of Dynamics 365 Supply Chain Management.
>
> <table><tr><td>In versions before 10.0.10, and in newer versions where the <i>Allow multiple product receipt per load</i> feature isn't enabled</td><td>The line quantity is the total of all registered quantities <i>for that purchase order line</i>, regardless of whether registration was done over multiple loads, independent of the load, from a mobile device, or from the client.</td></tr><tr><td>In version 10.0.10 and later, where the <i>Allow multiple product receipt per load</i> feature is enabled</td><td>The line quantity is the total of all registered quantities <i>for the load record</i> from which the <b>Product receipt posting</b> action was initiated.</td></tr></table>

Once the user selects **OK** to confirm the product-receipt post, the system does the following key updates on respective entities:

| **Entity** | **Updates** |
| --- | --- |
| Inventory transaction of purchase order, whose line quantities have been included in the posting scope | <p>The following are updated (but note that there are also multiple other updates):</p><ul><li>The <b>Receipt</b> field is set to <i>Received</i>.</li><li>The **Physical date** field is updated with the date of the posting</li></ul> |
| Load (from which the user posted the product receipt) | Updates to the loads will depend on the version used and on the setting of the **Allow multiple product receipt per load** field **.** The rules are described in the table provided later in this section. |

Options in the **Allow multiple product receipt per load** field offer companies a choice with regards to an inbound load receiving policy. Depending on their operational flows, they may choose to allow or disallow multiple product-receipt posts for the same load. The logistics manager is advised to set the **Allow multiple product receipt per load** field to one of the following:

- **No** - Select this if warehouse receiving clerks always register all order quantities arriving with each load within a designated time frame. If there are load quantities that haven't been registered, the system assumes that those quantities didn't arrive, or were not on the load, and hence shouldn't be regarded as part of the load. The product-receipt post, when executed from a load, then builds on the above-mentioned assumption and, in addition to its main function of product-receipt updating all the registered quantities, also declares the load complete and closed for additional processing. In this case, all load line quantities are automatically updated to the registered quantities, load lines with no registered quantities are deleted, and the load status is changed to _Received_.
- **Yes** - Select this if warehouse receiving clerks require more time to register all the quantities on the arrived load and, in the meantime, you need to product-receipt post the already registered quantities. In this case, the logistics manager would want to keep a load open even after running the product-receipt posting job, thereby allowing remaining load quantities to be registered and product-receipt updated to the ledger on an ongoing basis.
- **Prompt** _-_ Select this if your load receiving practices are mixed and a decision is required at each individual run of the product-receipt posting

| **Allow multiple product receipt per load** | **Load quantity** | **Load status** | **Note** |
| --- | --- | --- | --- |
| When this setting isn't available (versions before 10.0.10) | Set equal to registered quantity.<br><br>If load quantity is updated to zero (which means that no registration has been performed), the load line is deleted.<br><br>If there are no load lines on the load, the load is deleted. | _Received_ | If multiple loads exist for the order line's registered quantity, only the status of the load from which the receipt was posted will be updated to _Received_.   |
| No | Set equal to the registered quantity associated with the load ID.<br><br>If no load ID is recorded for the inventory transaction, then behavior is the same as in versions before 10.0.10. | _Received_ |   |
| Yes | No updates | _Received_<br><br>(Provided the total registered load quantity is equal or higher than the load quantity .) |   |
| Yes | No updates | _Shipped_ or _In&nbsp;process_<br><br>(Provided the total registered load quantity is lower than the load quantity.) |   |

Once the **Load status** is set to _Received_, no further product-receipt posts will be possible for that load. However, the worker is allowed to register the remaining order quantity against the received load under the following conditions (see also [Load over receiving](#load-over-receiving), earlier in this topic):

- For versions of Supply Chain Management older that version 10.0.11.
- When the _Over receipt of load quantities_ feature is enabled and the **Load line quantity over receipt** field on the mobile device menu item for load item receiving action is set to _Allow_.

To product-receipt post the additionally registered load quantities against the load with status _Received_, the user must run the posting action from the associated purchase order.

### Post registered quantities from the Purchase order page

To product-receipt post registered quantities from the **Purchase order** page, the user must do the following before selecting the **Product receipt** action:

- Set the **Quantity** field under **Parameters** section of the **Settings** tab to _Registered quantity_.
- Enter the number in the **Product receipt** field for the purchase order(s) included into the posting

> [!NOTE]
> The line quantity to be included in the postingscope is the total of all registered quantity for that order line, regardless of whether quantity registration has been performed over multiple loads, independent of the load, from a mobile device, or from the client. This same rule applies when executing the product-receipt post from a load, if performed where **Allow multiple product receipt per load** is either not available or not enabled.

Once the user selects **OK** to confirm the product-receipt post, the system does the following key updates on respective entities:

| **Entity** | **Updates** |
| --- | --- |
| Inventory transaction of purchase order, whose line quantities have been included in the posting scope | <p>The following are updated (but note that there are also multiple other updates):</p><ul><li>The <b>Receipt</b> field is set to <i>Received</i>.</li><li>The <b>Physical date</b> field is updated with the date of the product-receipt posting action. |
| Load | Updates to the loads will depend on whether the **Allow multiple product receipt per load** is available and enabled. The rules are described in the table following this one. |

The following table summarizes the effects of the **Allow multiple product receipt per load** setting.

| **Allow&nbsp;multiple product&nbsp;receipts per load** | **Load quantity** | **Load status** | **Note** |
| --- | --- | --- | --- |
| Either disabled or unavailable (in versions before 10.0.10)  | No updates  | No updates (remains in _Open_, _Shipped_ or _In process_ status) | Because the product-receipt post is initiated from a purchase order, the updating logic isn't aware of the association between the registered quantities within its scope and the loads against which registration was recorded, and hence cannot select the load for the status update. |
| Enabled | No updates  | <p>One of the following occurs:</p><ul><li>Change to <i>Received</i> (provided the <i>total received</i> and <i>purchased quantity</i> of the purchase order inventory transactions are greater than or equal to the quantity of the load with which they are associated).</li><li>Leave as <i>Open</i>, <i>Shipped</i>, or <i>In process</i> (if the previous conditions aren't met for all the lines in the load). |   |

### Choose the product-receipt posting option that's right for your logistics operations

As described previously, the system offers two product-receipt posting facilities, which are accessible from either of the following:

- The **Load** page or from the **Warehouse management > Periodic tasks** menu as an update job
- The **Purchase order** page or from the **Procurement and sourcing > Purchase orders > Receiving products** menu as an update job

Companies that use loads to plan and manage transportation and warehouse handling of their inbound orders are advised to utilize functions that are designed to work with loads, specifically:

- **Load item receiving** actions on their warehouse mobile devices to register the product quantity arrival against the load
- **Product receipt posting** initiated from a load to update the inventory ledger

> [!NOTE]
> While other quantity registration and product-receipt posting functions can be used to support the respective inbound operational processes, using them interchangeably with or instead of the dedicated load-focused functions may compromise data accuracy of the load records and hence the seamlessness of the load management flows.

## Example scenarios

### Prepare your system to run the sample scenarios

To work through the sample scenarios described in this section, you must first make sure all of the required features are enabled on your system and you must also work on a system that has the required demo data available.

#### Enable the required features

These scenarios require the _Multiple product receipt postings per load_ feature and its prerequisite feature. Administrators can enable these features by doing the following:

1. Go to the **Feature management** workspace. (See [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) for complete details about how to find and use this workspace.)

1. First enable the _Associate purchase order inventory transactions with load_ feature, which is listed as:
    - **Module** - Warehouse management
    - **Feature name** - Associate purchase order inventory transactions with load

1. Then enable the _Multiple product receipt postings per load_ feature, which is listed as:
    - **Module** - Warehouse management
    - **Feature name** - Multiple product receipt postings per load

#### Enable sample data

To work through these scenarios using the sample records and values specified here, you must be on a system with the standard demo data installed, and you must select the **USMF** legal entity before you begin.

#### Add a menu item for receiving load items when using a mobile device

To enable warehouse receiving clerks to use a mobile device to register inbound inventory linked to a load, you must create a mobile device menu item for this purpose.

In this section, you'll create a mobile device menu item and add it to an existing menu, making it possible for a warehouse worker to select it in the Warehousing app.

Go to **Warehouse management > Setup > Mobile device > Mobile device menu items** and make sure that your mobile device menu is set up to include a menu item with the following settings:

- **Mode** - _Work_
- **Work creation process** - _Load item receiving_
- **Generate license plate** - _Yes_

You can leave all other settings at their default values.

![Mobile device menu item settings](media/inbound-mobile-menu-items.png "Mobile device menu item settings")

For more information about how to set up mobile device menu items, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).

After you've set up the menu item, go to **Warehouse management > Setup > Mobile device > Mobile device menu** and add the new item to the menu structure for your mobile devices.

### Example scenario 1: Register a load where some items are missing

This scenario shows how to register quantities for an inbound load where not all expected quantities are present. It then shows how to post the product receipt for the purchase order.

#### Create a load to plan receipt of a purchase order

In this exercise, you'll manually create a purchase order and an associated load. Then you'll update the load to simulate that it has been shipped from the vendor. Warehouse planners can then use this to filter for expected incoming loads.

1. Go to  **Procurement and sourcing > Purchase orders > All Purchase orders**.

1. Select  **New**.

1. The **Create purchase order** pane opens. Set the  **Vendor account**  to _1001_.

1. Select **OK** to close the pane and create the purchase order.

1. The new purchase order already includes a line in the **Purchase order lines** area. Make the following settings for this line:
    - **Item number** - _A0001_
    - **Warehouse**  - _24_
    - **Quantity** - _10_

1. Open the **Purchase** tab on the action pane, and then select **Actions > Confirm**. The order status is now _Confirmed_.

1. Open the **Warehouse** tab on the action pane, and then select **Actions** > **Load planning workbench**.

1. Open the **Supply and demand** tab on the action pane, and then select **Add** > **To new load.**

1. The **Load template assignment** pane opens. Set **Load template ID** to _20' Container_.

1. Select **OK** to close the pane and return to the workbench.

1. In the **Loads** section of the workbench, select the **Load ID** link to open the newly created load.

1. Review the load header and line details and note the following:
    - On the **Load** FastTab, the **Load status** is set to _Open_.
    - In the **Load lines** section, there is a single line where the load **Quantity** is _10_ and the **Work created quantity** is _0_.

    ![Load details](media/inbound-load-details.png "Load details")

1. Open the **Ship and receive** tab on the action pane, and then select **Confirm** > **Inbound shipment.** Note that the **Load status** has now changed to _Shipped_.

1. Make a note of the **Load ID** value so you can use it in the next exercise.

#### Register receipt of the quantities that arrived on the load

When the load arrives at the warehouse receiving dock, a receiving clerk registers the load quantities on their mobile device. If you were the receiving clerk, you would proceed as follows using a mobile device:

1. Use your mobile device to sign in to warehouse 24 (in the standard demo data, sign in with **User ID** = _24_ and **Password** = _1_).

1. Select the_Load item receiving_ menu item that you created for this scenario.

1. Follow the data entry instructions on the screen to enter the following values (the order may vary depending on which mobile device or emulator you are using):
    - **Load** - Enter the load ID that you created in the previous exercise.
    - **Item** - Enter _A0001_, which is the item expected for this load.
    - **Qty** - Enter _9_ **,** which is less than the expected quantity, but for this scenario imagine that this is the actual quantity present on the load.

1. Continue going through the workflow, leaving all other fields at their empty or default values, until your device tells you that the work is completed.

The load receiving task is now completed, so the receiving clerk would move on to their next task. However, warehouse receiving personnel will eventually review the load record and will be able to see that the quantity received was less than the quantity expected. If you were this person, you would proceed as follows using the web client:

1. Go to  **Warehouse management > Loads > All loads**.

1. On the list, locate the load that you have just received (you may need to select the **Show closed** checkmark to include the inbound loads with a **Load status** of _Shipped_). Select the link in the **Load ID** column to open the load.

1. The load record opens. Note that the **Load status** remains _Shipped_, while the **Work created quantity** field on the load line has changed to _9_.

1. Go to  **Procurement and sourcing > Purchase orders > All Purchase orders**.

1. In the list, locate the purchase that you have just received, and select the link in the **Purchase order** column to open the order.

1. On the **Purchase order lines** FastTab, select **Inventory** > **View** > **Transactions.**

1. Review the details of the two purchase order transactions (you may need to personalize the **Inventory transactions** page if you want to see the **Load ID** field to the grid). You should see two transactions here:
    - The transaction with **Receipt** in status _Registered_ represents the registration **Quantity** of _9_, which was executed from the mobile device against a specific load. That **Load ID** is associated with the transaction in question.
    - The transaction with **Receipt** in status _Ordered_ represents the remaining unregistered order line **Quantity** of _1_.

#### Product-receipt post the registered load quantities against purchase orders

In this exercise, you'll product-receipt post the inventory that you registered for a load, which will add the received inventory and its related costs to the company's general ledger.

1. Go to  **Warehouse management > Loads > All loads**.

1. In the list, locate the load that you received (you may need to select the **Show closed** checkmark to include the inbound loads with a **Load status** of _Shipped_). Select the link in the **Load ID** column to open the load.

1. Open the **Ship and receive** tab on the action pane, and then select **Receive** > **Product receipt**. Select **Yes** if you're prompted to confirm the action.

1. The **Posting product receipt** pane opens. Inspect the table on the **Lines** FastTab, where you should see the purchase order line whose quantity has been registered against the selected load.

    > [!NOTE]
    > In versions where the _Multiple product receipt postings per load_ feature is not available or not enabled, the default quantity displayed on the **Load lines** grid would be the total quantity that has been registered across all loads that are associated with the purchase order line.

1. Inspect the **Product receipt** field in the grid on the **Overview** FastTab and note that it is to set to a number that includes the ID of the selected load.

1. Select **OK** to post the product receipt and close the **Posting product receipt** panel.

1. You return to the load details. Note the following:
    - The **Load status** now shows _Received._
    - On the load line, the load **Quantity** has now changed from 10 to 9 pcs, which matches the registered quantity, while the **Work created quantity** remains 9.

If the purchasing team doesn't expect the vendor to deliver the remaining order quantity of 1, they can close the order by updating the line's deliver remainder to 0. If, however, the missing piece is soon found to have arrived with the original load, then the warehouse personnel can choose to do one of the following:

- Register this quantity against the same load. In this case, the load status will be reset to _Shipped_ and the Work created quantity will be updated to 10. This choice is only available to the workers if the _Over receipt of load quantities_ feature is not available or not enabled; or, if available and enabled, if the **Load line quantity over receipt** field is set to _Allow_.
- Add the quantity to a new or existing load and process it as usual.
- Register and/or receive the quantity in a way that does not involve load handling.

### Example scenario 2: Register quantities arriving with multiple inbound loads where some items are missing

In this scenario, an inbound shipment related to a single purchase order line will get split into two loads. A typical example of when this might happen could be due to physical load constrains on weight and/or volume.

This scenario also demonstrates how to process multiple product-receipt posts for the same load. You will register quantities arriving on multiple inbound loads, and the quantities won't match the expected quantities. The cost updates via posting of the product receipt will be done multiple times for the same load.

#### Set up load receiving policies

Enable for allowing multiple product receipt posts from the same load.

1. Go to **Warehouse management** > **Setup** > **Warehouse management parameters**.
1. On the **Loads** tab, set **Allow multiple product receipts per load** to _Yes_.

#### Create two loads to plan receipt of a purchase order

In this exercise, you'll create a purchase order and two loads, and you'll update each load manually to simulate them being shipped by the vendor. This can be used by the inbound warehouse planner to filter for the expected incoming loads.

You will also see how to set the purchase order line to allow you to receive a quantity that is 20% higher than is specified for the line.

1. Go to  **Procurement and sourcing > Purchase orders > All Purchase orders**.

1. Select  **New**.

1. On the **Vendor** FastTab, set  **Vendor account**  to _1001_ and then select **OK**.
1. Your new purchase order opens and includes a blank line in the **Purchase order lines** table. Make the following settings for this order line:
    - **Item number** - _A0001_
    - **Warehouse** - _24_
    - **Quantity** - _10_

1. On the **Line details** FastTab, open the **Delivery** tab and set **Overdelivery** to _20._

1. On the action pane, open the **Purchase** tab and select **Actions** > **Confirm**. The order status is now _Confirmed_.

1. On the action pane, open the **Warehouse** tab and select   **Actions** > **Load planning workbench**.

1. The **Load planning workbench** page opens. On the action pane, open the **Supply and demand** tab and select **Add** > **To new load.**

1. The **Load template assignment** pane opens. Set the **Load template ID** to _20' Container_ **.** On the **Details** tab, change the **Quantity** from _10_ to _5_ to partly add the purchase order line quantity.

1. Select **OK** to apply your settings and close the pane.

1. Repeat steps 8 to 11 to create a second load (this time, the **Quantity** should already be set to _5_).

1. In the **Loads** table of the **Load planning workbench** , select the **Load ID** for the first load you created.
    - The **Load details** page opens, showing your selected load.
    - On the action pane, open the **Ship and receive** tab and select **Confirm** > **Inbound shipment.**
    - Note that the **Load status** has changed to _Shipped_.
    - Select the close button to return to the **Load planning workbench**.

1. Repeat the previous step for the second load.

1. Take note of the two **Load ID** s that you have just created (as listed in the **Loads** table).

#### Register partial receipt of the quantities that arrived on the first load and post the registered load quantities

When the loads arrive at the warehouse receiving dock, a receiving clerk registers the load quantities on their mobile device. After this the registered inventory linked to a load will get cost updated within the company's general ledger by posting the purchase order product receipt based on the load.

 If you were the receiving clerk, you would proceed as follows using a mobile device:

1. On your mobile device, sign in to warehouse 24 (in the standard demo data, sign in with **User ID** = _24_ and **Password** = _1_).

1. Select the_Load item receiving_ menu item that you created for this scenario.

1. Follow the data entry instructions on the screen to enter the following values (the order may vary depending on which mobile device or emulator you are using):
    - **Load** - Enter the first load ID that you have created in the previous procedure.
    - **Item** - Enter _A0001_, which is the item expected for this load.
    - **Qty** - Enter _3_ **,** which is less than the expected quantity, but for this scenario imagine that the work didn't have time to register all quantities for this load. (Later in this procedure, you'll register the remaining pieces by repeating this step with **Qty** set to _2_.)

1. Continue going through the workflow, leaving all other fields at their empty or default values, until your device tells you that the work is completed.

1. Return to your web client and go to  **Warehouse management > Loads > All loads**.

1. In the list, locate the load that you have just received and select the **Load ID** to open it. Note that the **Load status** remains _Shipped_, while the **Work created quantity** field on the load line has changed to _3_.

1. On the action pane, open the **Ship and receive** tab and select **Receive** > **Product receipt**. Select **Yes** if you're prompted to confirm the action.

1. The **Posting product receipt** pane opens. Review, but don't change, the values shown here and select **OK**.

1. You return to the **Load details** page for your selected load. Note the following:
    - The **Load status** remains set to _Shipped._
    - On the load line, the load **Quantity** remains equal to _5_ pcs, which is the original load quantity, while the **Work created quantity** remains set to _3_.

1. The warehouse personnel can now complete the registration of the remaining quantity on this load. To do so, repeat this procedure, but on step 3, set the **Qty** field to _2_.

The receiving task for the first load is now completed. Two product receipt journals have been created&mdash;one for each of the two product receipt updates that you executed.

#### Register receipt of the quantities arrived on the second load and account for the overdelivered quantity

In this scenario the receiving clerk will inbound register a higher quantity than exists on the load. This will be permitted because the system is set up to allow overdelivery.

1. On your mobile device, sign in to warehouse 24 (in the standard demo data, sign in with **User ID** = _24_ and **Password** = _1_).

1. Select the_Load item receiving_ menu item that you created for this scenario.

1. Follow the data entry instructions on the screen to enter the following values (the order may vary depending on which mobile device or emulator you are using):
    - **Load** - Enter the second load ID that you created earlier.
    - **Item** - Enter _A0001_, which is the item expected for this load.
    - **Qty** - Enter _7_ **.** This is the remaining quantity that the vendor is authorized to deliver as part of total purchase order quantity of 12, where 10 is the original order quantity and 2 is the allowed overdelivery quantity (based on 20 percent). Recall that 5 pcs have already been registered against the first load.

1. The second load has now been updated with the quantity 7 and can become product receipt updated based on this quantity.