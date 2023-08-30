---
title: Set up mobile devices for warehouse work
description: This article describes how to configure the menu items that warehouse workers use to perform work on a mobile device.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSRFMenuItem, WHSRFSysDirSort, WHSWorkUserDisplaySettings
ms.topic: how-to
ms.date: 10/14/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up mobile devices for warehouse work

[!include [banner](../includes/banner.md)]

This article describes how to configure the menu items that warehouse workers use to perform work on a mobile device.

> [!NOTE]
> This article applies to features in Warehouse management. It doesn't apply to features in Inventory management. The menu items that appear on the menus on a warehouse mobile device are configured on the **Mobile device menu items** page. Because the menu items can be put onto different menus, it's easy to configure menu structures so that only specific types of work are exposed to specific users. You can configure menu items to perform the following tasks:

- Process an inquiry or perform an activity, such as printing a label, generating license plate numbers, starting a production order, or quickly looking up information about items in a location.
- Create work that will be performed through another process. For example, receiving an item for a purchase order can create putaway work for another worker.
- Perform work that was created by another process (existing work), such as putaway work that was created when an item was received for a purchase order.

To create a menu item for an activity or inquiry, set the **Mode** field to **Indirect**. A list of **Activity code** options then becomes available, so that you can select the type of inquiry or activity that the menu item is for. To create a menu item to generate warehouse work, set the **Mode** field to **Work**. A list of **Work creation process** options then becomes available. To create a menu item to process existing warehouse work, set the **Mode** field to **Work**, and then set the **Use existing work** option to **Yes**.

> [!NOTE]
> Additional fields might be available for menu items, depending on the mode that you select for the menu item, and whether the menu item is used to perform existing work. For information about the additional field selections, see the "Additional menu item options" section later in this article.

## Configure menu items for activities and inquiries

If the **Mode** field for a menu item is set to **Indirect**, you can create a menu item to perform a general activity or inquiry that doesn't create work. Examples include reprinting license plate labels and an inquiry about the items in a location. The following table lists the options that are available.

| Option | Description |
|---|---|
| None | This default value doesn't enable an activity or inquiry. |
| About | View information about the system, such as the version number, the warehouse ID, and the worker who is currently logged on. |
| Change warehouse | Change the warehouse that a worker is logged on to. |
| Location inquiry | View information about all items and quantities for a location. |
| License plate inquiry | View the quantity of items on a license plate and the location of the license plate. |
| Start production order | Start a production order. |
| Production scrap | Enter the quantity of scrap that was created during production for each bill of materials (BOM) line. |
| Production last pallet | Indicate that the last pallet of items has been produced for a production order, and that the status of the production order must be updated to **Reported as finished**. The status of the raw materials that were not consumed during production is changed back from **Picked** to **On order**, and the items can be returned to inventory. |
| Item inquiry | Scan an item to determine where it is in the warehouse. The inquiry returns all locations and quantities for the scanned item. |
| Reprint label | Reprint a license plate label. |
| License plate build | <p>Create a parent license plate by combining multiple license plates in the same location. This option is useful if you move multiple license plates at the same time. After the parent license plate is moved, you must perform a license plate break before you can pick items from each license plate.</p><p>**Tip:** To move a parent license plate, you must use a mobile device that is configured to create work for movements.</p> |
| License plate break | Break up a license plate build so that you can pick items from the license plates that were in the build. |
| Driver check in | If you're using Transportation management, register the arrival of a driver by scanning the outbound load ID, appointment ID, or shipment ID. For this option, a load must be assigned to the appointment, and the status of the load must be **Loaded**. |
| Driver check out | Register that a driver has completed their appointment. |
| Flush number sequence cache | Delete number sequence numbers from the number sequence cache. This activity is typically performed by a system administrator to resolve caching issues when mobile devices are used. |
| Change batch disposition | Allow a worker to specify a batch disposition code for an item and batch. This selection updates the disposition code that is specified for the batch. |
| Display open work list | Show a list of available work to a particular user. The user can then select work to perform and will be directed to it. This list is intended to be viewed on tablet devices that have a screen size of 7 inches or more. When you select this option, the **Edit query** and **Field list** menu items become available. The **Edit query** page lets you set up criteria for the work that appears in the list. The **Field list** page lets you select what fields appear in the work list. For example, you can reduce the number of fields that appear, so that the user can more quickly select the most appropriate work item. On the **General** FastTab, in the **Records per page** field, you can also select how many work records are shown per page. If the **Allow users to filter work by transaction type** option is selected, the work list will include a **Filter work** control that the user can use to filter by transaction type. In the work list, users will see only work that they have permission to access. You must make sure that users have permission for one or more user-directed menu items that support the specific work class types that they should be able to access. Permissions are verified when a user tries to perform work from the list.|
| Create transfer order from license plates | Allow warehouse workers to create and process transfer orders directly from the Warehouse Management mobile app. A worker starts by selecting the destination warehouse. The worker can then scan one or more license plates by using the app. After the warehouse worker selects **Complete order**, a batch job will create the required transfer order and order lines, based on the on-hand inventory that is registered for those license plates. For more information, see [Create transfer orders from the warehouse app](create-transfer-order-from-warehouse-app.md). |
| Data inquiry | Enable the creation of warehouse app menu items that can be used to look up data from the mobile device as an inquiry list. For more information, see [Warehouse app data inquiry](warehouse-app-data-inquiry.md). |
| Pack inventory into containers | Enable support for warehouse workers as they pack inventory items into containers. A worker starts by scanning a shipment to identify the inventory items that must be packed. The worker then identifies the destination shipping container by entering its ID or scanning its bar code. Finally, when the container is fully packed, the worker registers it as closed. This step makes the container ready for further processing by Microsoft Dynamics 365 Supply Chain Management. For more information, see [Packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md). |
| Container creation | Enable the container creation process. This process is typically part of the process of [packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md). |
| Container closing | Enable the container closing process. This process is typically part of the process of [packing containers by using the Warehouse Management mobile app](warehouse-app-packing-containers.md). |
| Print container label | Enable container label printing. This process is typically part of the process of [packing containers by using the Warehouse Management mobile app](warehouse-app-packing-containers.md). For more information, see [Container label layouts and printing](print-container-labels.md). |
| Receiving completed confirmation | Enable support for receiving clerks to indicate *Receiving completed* for a load. |

## Configure menu items to create work for another worker or process

You can set up a menu item that creates work for another worker after an initial action is performed on the mobile device. For example, when one worker uses a mobile device to receive an item, putaway work is created for another worker. To set up a menu item that creates work, on the **Mobile device menu items** page, in the **Mode** field, select **Work**. In the following table, the options in the **Work creation process** field are arranged by work order type.

<table>
<thead>
<tr>
<th>Work order type</th>
<th>Option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td rowspan="8">Inbound shipment order</td>
<td>Inbound shipment order line receiving</td>
<td><p>Register the receipt of a quantity of an item by using the inbound shipment order number and line number, and create putaway work for another worker.</p>
<p>A load must exist for this process.</p>
</td>
</tr>
<tr>
<td>Inbound shipment order line receiving and put away</td>
<td><p>Register the receipt of a quantity of an item by using the inbound shipment order number and line number, and put the items away. The same worker performs both actions.</p>
<p>A load must exist for this process.</p>
</td>
</tr>
<tr>
<td>Inbound shipment order item receiving</td>
<td><p>Register the receipt of a quantity of an item for an inbound shipment order by registering the order number and item number, and create putaway work for another worker.</p>
<p>A load must exist for this process.</p>
</td>
</tr>
<tr>
<td>Inbound shipment order item receiving and put away</td>
<td><p>Register the receipt of a quantity of an item for an inbound shipment order by registering the order number, and put the item away. The same worker performs both actions.</p>
<p>A load must exist for this process.</p>
</td>
</tr>
<td>License plate receiving</td>
<td>Receive an inbound advance ship notice (ASN) by using the license plate ID.</td>
</tr>
<tr>
<td>License plate receiving and put away</td>
<td>Receive and put away an inbound ASN by using the license plate ID.</td>
</tr>
<tr>
<td>Load item receiving</td>
<td>Register the receipt of a quantity for a load by using the load ID, and create putaway work for another worker. The item number and product dimensions match the receipt to the order lines.</td>
</tr>
<tr>
<td>Load item receiving and put away</td>
<td>Register the receipt of a load by using the load ID, and put the items away. The item number and product dimensions match the receipt to the order lines. The same worker performs both actions.</td>
</tr>
<tr>
<td rowspan="8">Purchase order</td>
<td>Purchase order line receiving</td>
<td>Register the receipt of a quantity of an item by using the purchase order number and purchase order line number, and create putaway work for another worker.</td>
</tr>
<tr>
<td>Purchase order line receiving and put away</td>
<td>Register the receipt of a quantity of an item by using the purchase order number and purchase order line number, and put the items away. The same worker performs both actions.</td>
</tr>
<tr>
<td>Purchase order item receiving</td>
<td>Register the receipt of a quantity of an item for a purchase order by registering the purchase order number and item number, and create putaway work for another worker.</td>
</tr>
<tr>
<td>Purchase order item receiving and put away</td>
<td>Register the receipt of a quantity of an item for a purchase order by registering the purchase order number, and put the item away. The same worker performs both actions.</td>
</tr>
<tr>
<td>License plate receiving</td>
<td>Receive an inbound ASN by using the license plate ID.</td>
</tr>
<tr>
<td>License plate receiving and put away</td>
<td>Receive and put away an inbound ASN by using the license plate ID.</td>
</tr>
<tr>
<td>Load item receiving</td>
<td>Register the receipt of a quantity for a load by using the load ID, and create putaway work for another worker. The item number and product dimensions match the receipt to the purchase order lines.</td>
</tr>
<tr>
<td>Load item receiving and put away</td>
<td>Register the receipt of a load by using the load ID, and put the items away. The item number and product dimensions match the receipt to the purchase order lines. The same worker performs both actions.</td>
</tr>
<tr>
<td rowspan="2">Return order</td>
<td>Return order receiving</td>
<td>Register the receipt of a quantity of an item by registering the RMA number, and create putaway work for another worker.</td>
</tr>
<tr>
<td>Return order receiving and put away</td>
<td>Register the receipt of a quantity of an item by registering the RMA number, and put the items away. The same worker performs both actions.</td>
</tr>
<tr>
<td rowspan="6">Transfer order</td>
<td>Transfer order item receiving</td>
<td><p>Register the receipt of a quantity of an item, and create putaway work for another worker.</p>
<p><strong>Note:</strong> Use this option only if the items were shipped from a warehouse that isn't enabled for warehouse management processes (WMS).</p></td>
</tr>
<tr>
<td>Transfer order item receiving and put away</td>
<td><p>Register the receipt of a quantity of an item, and put the items away. The same worker performs both actions.</p>
<p><strong>Note:</strong> Use this option only if the items were shipped from a warehouse that isn't enabled for WMS.</p></td>
</tr>
<tr>
<td>Transfer order line receiving</td>
<td>Register the receipt of a quantity of an item, and create putaway work for another worker.</td>
</tr>
<tr>
<td>Transfer order line receiving and put away</td>
<td>Register the receipt of a quantity of an item, and put the items away. The same worker performs both actions.</td>
</tr>
<tr>
<td>License plate receiving</td>
<td>Receive an inbound ASN by using the license plate ID.</td>
</tr>
<tr>
<td>License plate receiving and put away</td>
<td>Receive and put away an inbound ASN by using the license plate ID.</td>
</tr>
<tr>
<td rowspan="4">Production</td>
<td>Report as finished</td>
<td>Register a quantity of a finished item that has been finished for a production, and create putaway work for another worker. The quantity can be some or all of the quantity that was planned for production.</td>
</tr>
<tr>
<td>Report as finished and put away</td>
<td>Register a quantity of a finished item that has been finished for a production, and put the items away. The quantity can be some or all of the quantity that was planned for production. The same worker performs both actions.</td>
</tr>
<tr>
<td>Kanban</td>
<td>Indicate that a kanban is completed, and create putaway work for another worker.</td>
</tr>
<tr>
<td>Kanban put away</td>
<td>Indicate that a kanban is completed, and put away the items. The same worker performs both actions.</td>
</tr>
<tr>
<td rowspan="5">Inventory</td>
<td>Movement</td>
<td>Register that items have been moved from one location to another. The worker specifies the location that the items are moved from and where they are moved to.</td>
</tr>
<tr>
<td>Quarantine</td>
<td>Change the status of the on-hand inventory for a license plate or location to make damaged or missing inventory items unavailable.</td>
</tr>
<tr>
<td>Movement by template</td>
<td>Move items from one location to another in a semi-automated manner. The worker selects the location to move items from, the system uses the location directive to determine where to move the items to.</td>
</tr>
<tr>
<td>Warehouse transfer</td>
<td><p>Register that items have been transferred from one warehouse to another. This option requires that the worker be allowed to perform work in both warehouses.</p>
<p><strong>Note:</strong> This menu item requires a default inventory transfer journal where the <strong>Voucher draw</strong> field is set to <strong>Posting</strong>.</p></td>
</tr>
<tr>
<td>License plate loading</td>
<td>Use this option when you're setting up your warehouse for the first time. Scan all the license plates in all locations in the warehouse. The locations must be license plate–controlled. You can't use this option if <strong>Serial number</strong> or <strong>Batch number</strong> is listed above <strong>Location</strong> in the inventory reservation hierarchy.</td>
</tr>
<tr>
<td rowspan="3">Cycle count</td>
<td>Adjustment in</td>
<td>Increase the quantity of items in inventory. Specify the location, license plate, item, quantity, unit of measure, and status.</td>
</tr>
<tr>
<td>Adjustment out</td>
<td>Reduce the quantity of items in inventory. Specify the location, license plate, item, quantity, unit of measure, and status of the inventory.</td>
</tr>
<tr>
<td>Spot cycle counting</td>
<td>Start a count for a location. The worker must count all items in the location. When the result of a count is less than the expected quantity, the missing quantity is considered a loss.</td>
</tr>
</tbody>
</table>

## Configure menu items to process existing work
In addition to setting up menu items to create warehouse work, you can set up menu items to process work that has already been created. Set the **Mode** field to **Work**, and select the **Use existing work** option. Some additional options then become available on the **General** tab. You can control access to the menu item by assigning one or more work classes on the **Work class** FastTab. The work classes define the work that the menu item can process. The work class can also be used to grant access to specific user roles or to separate processing for different types of operations. The following table describes the options that are available. The option can be chosen under the **Directed by** field in the **Mobile device menu items** page. 

<table>
<thead>
<tr class="header">
<th>Option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>None</td>
<td>This default value doesn't process work.</td>
</tr>
<tr class="even">
<td>System directed</td>
<td>Supply Chain Management controls the type of work that is assigned to a worker and the order that the worker performs the work in. When you select this option, you can select <strong>System-directed work</strong> on the Action Pane to open the <strong>System-directed sorting order</strong> page, where you can set up sorting criteria for the work. The sorting criteria control the order that the worker performs the work in. You can add as many criteria as you require.</td>
</tr>
<tr class="odd">
<td>User directed</td>
<td>The worker selects the work to perform and the order to perform it in.</td>
</tr>
<tr class="even">
<td>User grouping</td>
<td>The worker manually groups work. This option is useful when, for example, a worker can pick multiple items at the same time in a location. After the worker has finished picking all the required items, they can put the items away.</td>
</tr>
<tr class="odd">
<td>System grouping</td>
<td><p>Supply Chain Management groups work for the worker, based on a specified field. For example, picking work is grouped when a worker scans a shipment ID, load ID, or any value that can link each work unit. If you select this option, the following fields are required:</p>
<ul>
<li><strong>System grouping field</strong> – Select the field that the worker scans to group the work.</li>
<li><strong>System grouping label</strong> – Enter text to instruct the worker what to scan to group the work.</li>
</ul></td>
</tr>
<tr class="even">
<td>Validated user directed</td>
<td><p>The worker selects the work to perform when work is associated with a larger entity, such as a load or shipment. The worker determines the order that the items are picked in. If you select this option, the following fields are required:</p>
<ul>
<li><strong>Validated user directed field</strong> – Select the field that the worker scans to group the work.</li>
<li><strong>Validated user directed label</strong> – Enter text that instructs the worker what to scan when picking work is grouped by the system.</li>
</ul>
<p>This option is useful when, for example, multiple pallets are staged for a load. If you select <strong>LoadId</strong> in the <strong>Validated User Directed</strong> field, the worker can pick any pallet that is associated with the load. The worker receives an error message if they scan an item that isn't associated with the load.</p></td>
</tr>
<tr class="odd">
<td>Cluster picking</td>
<td>The worker groups work into clusters. Clusters lets workers pick items from a single location for multiple work orders at the same time.</td>
</tr>
<tr class="even">
<td>Cycle count grouping</td>
<td>The worker selects a zone, work pool, or location, and Supply Chain Management assigns work, based on the selection. If you select this option, you can click <strong>Cycle counting</strong> on the Action Pane to specify additional information to display, and you can also specify the number of times that the worker must repeat the count if a difference is found.</td>
</tr>
 <tr class="odd">
<td>Transport loading</td>
<td>This feature allows several warehouse workers to load inventory from the same or different loads onto the same truck, with loads that are fully or partially shipped.</td>
</tr>
</tbody>
</table>

## Additional menu item options
Additional menu items options are available on the **Mobile device menu items** page. The options vary, depending on the process that you're configuring the menu item for. 

The following table describes these options.

<table>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Allow splitting of work</td>
<td>Select this option to let users put items for a work order into more than one target license plate. This option is useful when, for example, a target license plate is full, and the worker must add the remaining items to another license plate. The worker can select <strong>Full</strong> to indicate that the license plate is full and stop receiving picking work for it. The put location for the picked items is then displayed, and the picking work that has already been completed is moved to a new work order. The remaining picking work for the target license plate stays on the original work order.</td>
</tr>
<tr class="even">
<td>Anchoring</td>
<td>Select this option to let workers specify a location that overrides the suggested staging or loading location. All the remaining putaway work is directed to the new location. This option is useful when, for example, a worker who must put items for order 1 in a staging location by Dock 1 can't, because a previous load hasn't cleared the location. Instead of waiting for the Dock 1 staging location to become available, the worker can decide to use the staging location for Dock 2. In this case, the worker overrides the suggested staging location. The put location for all remaining items for the work order is then updated to the Dock 2 staging location. If you select this option, you must set the <strong>Anchor by</strong> field.</td>
</tr>
<tr class="odd">
<td>Anchor by</td>
<td>If you're using anchoring, you must specify whether to anchor by shipment or by load.</td>
</tr>
<tr class="even">
<td>Audit template ID</td>
<td>Select the work audit template that will interrupt the work process for this menu item so that another operation can be performed. For example, if this menu item is for inbound work, the audit template might require that the worker check the temperature in the delivery container. The point at which the process is interrupted is specified on the audit template. This point can be, for example, when work is started or completed, or when its status changes.</td>
</tr>
<tr class="odd">
<td>Cluster profile ID</td>
<td>Select the cluster profile to use for cluster picking. The cluster profile includes settings such as whether to create clusters automatically, the names of positions and the number of work units that they can be assigned, when to break clusters into individual units, and whether verification is required. This field is available only if <strong>Cluster picking</strong> is selected in the <strong>Directed by</strong> field.</td>
</tr>
<tr class="even">
<td>Count total item quantity first</td>
<td>Select this option to require that a worker count the total quantity first during a count. If a difference is found, the worker must provide additional information, such as the license plate number, batch number, and serial numbers.</td>
</tr>
<tr class="odd">
<td>Create movement</td>
<td>Select this option to let a worker create work for a movement, but without requiring that the worker perform the work immediately. This option is useful if, for example, a quality inspection has been completed, and the inspector wants the item to be moved from the quality inspection area.</td>
</tr>
<tr class="even">
<td>Directive code</td>
<td>To use a specific location directive, select the directive code that is associated with the location directive. This field is available when you create work and the work creation process is <strong>Movement by template</strong>.</td>
</tr>
<tr class="odd">
<td>Disable cycle count thresholds</td>
<td>Select this option to ignore the cycle count thresholds. If you select this option, cycle count work isn't created when threshold values are exceeded.</td>
</tr>
<tr class="even">
<td>Display batch disposition code</td>
<td><p>Select this option to display batch disposition codes. For example, you can display batch disposition codes when you receive a returned batch. Workers can then evaluate the status or quality of a batch, and select the appropriate code. The rules on the batch disposition code determine whether the batch will be available to other warehouse processes. If you don't select this option, one of the following batch disposition codes is used:</p>
<ul>
<li>If you receive a new batch number, the default batch disposition code that is specified on the item model group.</li>
<li>The batch disposition code that is already assigned to the batch.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Display disposition code</td>
<td>Select this option to display disposition codes. For example, you can display disposition codes when you receive return items. Workers can then evaluate the status or quality of the items, and select the appropriate code. The rules on the disposition code determine whether the items will be available to other warehouse processes.</td>
</tr>
<tr class="even">
<td>Display inventory status</td>
<td>Select this option to display the status of items in inventory. This option is available for all menu items that use existing work, except cycle counting.</td>
</tr>
<tr class="odd">
<td>Display summary of pick screen</td>
<td>Select this option to display a summary of picking work for the selected work order. The summary is displayed until the first work line is processed for the work order.</td>
</tr>
<tr class="even">
<td>Generate license plate</td>
<td>Select this option to generate a unique license plate number, based on the number sequence selection. For example, you can generate a license plate number for items that are received for purchase orders.</td>
</tr>
<tr class="odd">
<td>Group put away</td>
<td>Select this option to group the putaway work. This option is available when the work was grouped either by the worker or by Supply Chain Management. When the worker has finished all the picking work in the group, putaway work is created for the same group.</td>
</tr>
<tr class="even">
<td>Inventory adjustment types</td>
<td>Select the inventory adjustment type that determines the inventory counting journal that is used to post the adjustment, and whether to remove reservations. This field is available only for the <strong>Adjustment in</strong> or <strong>Adjustment out</strong> work creation process.</td>
</tr>
<tr class="odd">
<td>Override batch number</td>
<td>Select this option to let workers who are reporting a quantity as finished for a production order enter a batch number that differs from the batch number that is assigned to the production order.</td>
</tr>
<tr class="even">
<td>Override target license plate</td>
<td>Select this option to let workers specify a target license plate number that differs from the suggested target license plate. Use this option when the first pick for a work order is for the entire quantity of an item on a license plate. This option is useful when, for example, a pallet is reused.</td>
</tr>
<tr class="odd">
<td>Pick and pack</td>
<td><p>Select this option to let workers combine work for a sales order or load into a single work unit. A worker can perform work only for the sales order or load. This option is useful when, for example, you must increase a quantity for a sales order after the load, shipment, and work have been created for a sales order. This option is available when the menu item uses existing work, and the work is directed by the user or system.</p><p>Note that only work headers that contain a single initial pick work line can be combined by using this group picking concept.</p></td>
</tr>
<tr class="even">
<td>Pick oldest batch</td>
<td><p>Indicate whether the worker must pick the oldest batch in a location first. The following options are available:</p>
<ul>
<li><strong>None</strong> – The worker can pick any batch in the location. The worker receives no message.</li>
<li><strong>Warn</strong> – The worker can pick any batch in the location, but they receive a warning message if a batch isn't the oldest batch.</li>
<li><strong>Force</strong> – The worker must pick the oldest batch in the location. The worker receives an error message if a batch isn't the oldest batch. <strong>Note:</strong> This option is relevant only if <strong>Batch number</strong> is lower than <strong>Location</strong> in the reservation hierarchy that is assigned to the item.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Print label</td>
<td>Select this option to let workers print license plate labels.</td>
</tr>
<tr class="even">
<td>System grouping field</td>
<td>Select the field that determines how Supply Chain Management will group picking work for workers. For example, if you select the <strong>ShipmentId</strong> field, the worker will scan the shipment ID to group the picking work. All work for the shipment is then assigned to the worker. This field requires that you create a menu item to use existing work that is grouped by the system. You must also enter text in the <strong>System grouping label</strong> field to instruct the worker what to scan.</td>
</tr>
<tr class="odd">
<td>System grouping label</td>
<td>Enter the text that will instruct the worker what to scan when picking work is grouped by Supply Chain Management. For example, if you're using the <strong>ShipmentId</strong> field to group picking work by shipment, you might enter <strong>Shipment ID</strong> in the field. This field requires that you create a menu item to use existing work that is grouped by the system. You must also select the field to group by in the <strong>System grouping</strong> field.</td>
</tr>
<tr class="even">
<td>Use default data</td>
<td>Select this option to enable the <strong>Default data</strong> button on the Action Pane, where you can select fields to display data that a worker typically requires in their daily work. This option is useful if, for example, a worker often picks items from the same location. You can select the <strong>From location</strong> field to display the location by default.</td>
</tr>
<tr class="odd">
<td>Validated User Directed Field</td>
<td>Select the field that the worker will scan to group the work. For example, if you select <strong>LoadId</strong>, a worker can pick any work that is associated with a selected load. You must also enter text in the <strong>Validated User Directed Label</strong> field to instruct the worker what to scan.</td>
</tr>
<tr class="even">
<td>Validated User Directed Label</td>
<td>Enter the text that will instruct the worker what to scan when picking work is grouped by a validated user-directed field. For example, if you're using the <strong>LoadId</strong> field to group picking work for a load, you might enter <strong>Load ID</strong> in the field.</td>
</tr>
<tr class="odd">
<td>Work template code</td>
<td>Select the work template that will create the work for a process. For example, if you receive an item for a purchase order, the putaway work will be generated based on the work template. If you don't select a work template, Supply Chain Management assigns a template, based on query criteria. For more information about work templates, see <a href="control-warehouse-location-directives.md">Controlling warehouse work with work templates and location directives</a>.</td>
<tr class="even">
<td>Show work line list</td>
<td>Select an option for how workers will be able to view and interact with the lines for the currently selected picking work. For more information about this option, see <a href="pick-line-overview.md">Set up a mobile device menu item to provide a pick line overview</a>.</td>
</tr>
</tbody>
</table>

## Require workers to confirm the product, location, or quantity when they pick items

You can set up work confirmations that require that a worker use a mobile device to register the location or quantity when they perform work in the warehouse. Work confirmations help ensure that the worker is at the correct location or is handling the correct quantity of items. You can also enable Supply Chain Management to automatically confirm the worker's registration. If you enable automatic confirmation, you can't also require confirmations for location or quantity. Work confirmations also include products and product variants. Additionally, you can register confirmations by scanning a bar code. To confirm products and product variants, you must enter an ID for the product or product variant. This ID can be a product ID, product search ID, external ID, GTIN, or bar code. After you enter the ID or scan the bar code, the dimensions for the product variant are displayed on the mobile device. 

The following table describes the various work types that you can use work confirmations with.

| Option | Description |
|------------------------|----------------------------------------------------------------------------|
| Pick | Require confirmation when items are picked. |
| Put | Require confirmation when items are put in a location. |
| Counting | Require confirmation during cycle counting. |
| Adjustments | Require confirmation when inventory quantities are adjusted. |
| Custom | Require confirmation for custom work. |
| Quarantine | Require confirmation when items are moved to quarantine. |
| License plate building | Require confirmation when items are consolidated to build a license plate. |
| Print | Require confirmation when license plate labels are printed. |
| Status change | Require confirmation when the status of inventory is changed. |

> [!NOTE]
> You can require product confirmation only for pick and put work types.

## Additional resources

- [Set up a mobile device menu item for completing work of type Purchase order](tasks/set-up-mobile-device-menu.md)
- [Set up a mobile device menu item to register received items](tasks/set-up-mobile-device-menu-item-register-received-items.md)
- [Inventory statuses](../inventory/inventory-statuses.md)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
