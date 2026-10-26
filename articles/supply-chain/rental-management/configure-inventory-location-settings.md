---
title: Configure inventory and location settings for rental management (preview)
description: Learn how to configure released products, dimension groups, fleet types, warehouses, rental locations, and transfer rules for rental management.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Configure inventory and location settings for rental management (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Rental management depends on inventory dimension and warehouse settings that you configure before you use it. Those settings are the required item dimension groups, fleet types and their value tracking methods, warehouse setup, and the rental location hierarchy that tracks where fleet items are physically located.

## Configure released products for rental

### Understand how inventory dimensions support the rental fleet

Rental management uses standard Dynamics 365 Supply Chain Management inventory dimensions to track fleet items through the fleet lifecycle.

The *Serial number (tracking dimension)* is critical for rentals because each fleet item is a unique serialized asset. Serial number tracking must be active on fleet items so that each item has a distinct inventory identity. This feature lets the system link a purchase order line directly to a specific fleet item record and track it through every movement.

The fleet type isn't an inventory dimension. Each fleet item carries its own fleet type (for example, *New*, *Rental*, *Lease*, or *Used*). A fleet transfer changes the fleet type without physically moving the fleet item. When a fleet item is in a fleet type whose **Value tracking method** is *Fixed asset*, such as *Rental* or *Lease*, the system doesn't track its physical location through an inventory warehouse and location. It uses the *fleet location* hierarchy instead. That hierarchy is described later in this article.

### Set up tracking dimension groups

A *tracking dimension group* defines which tracking dimensions (batch number, serial number, and owner) are active for a product, and how strictly each one is enforced. Rental management identifies every piece of equipment individually, so each fleet item needs a tracking dimension group that has the *Serial number* dimension active. Serial number tracking is what gives each fleet item a distinct inventory identity, so that the system can link a purchase order line to a specific fleet item and follow that item through every movement.

To set up tracking dimension groups, follow these steps:

1. Go to **Product information management** > **Setup** > **Dimension and variant groups** > **Tracking dimension groups**.
1. Create a tracking dimension group for fleet items.
1. On the **Tracking Dimension** FastTab, ensure that the *Serial number* dimension is active and set up as shown in the following table.

    | Name | Active | Primary stocking | Physical inventory | Financial inventory | Blank receipt allowed | Blank issue allowed |
    |---|---|---|---|---|---|---|
    | *Serial number* | *Yes* | *Yes* | *Yes* | *Yes* | *No* | *No* |

    Setting **Physical inventory** to *Yes* includes the serial number in on-hand inventory, and setting **Blank receipt allowed** and **Blank issue allowed** to *No* requires a serial number on every purchase order receipt and movement.

    Setting **Financial inventory** to *Yes* values each serial number separately, so that you can track costs, profit, and inventory valuation per fleet item.

1. On the **Serial numbers** FastTab, set **Serial number control** to *Yes*.
1. Make other settings as required for your business processes.

The serial number doesn't have to be on the purchase order line when you create the line. You can enter it when the fleet item arrives, before the product receipt. Learn more in [Enter serial numbers when fleet items arrive](add-equipment-to-rental-fleet.md#enter-serial-numbers-when-fleet-items-arrive).

> [!NOTE]
> Rental management doesn't require the **Batch number** dimension, because the fleet type is stored on the fleet item rather than on a batch. If the **Batch number** dimension is active for a fleet item product, you can't create or delete batches for that product on the **Batches** page.

### Set up storage dimension groups

A *storage dimension group* defines where inventory is tracked: by site, by warehouse, and optionally by warehouse location. Rental management uses these dimensions to record which branch holds each fleet item while the item is in an inventory fleet, and to move equipment between branches. Fleet items that are in a fleet type whose **Value tracking method** is *Fixed asset* are tracked through the fleet location hierarchy instead.

To set up storage dimension groups, go to **Product information management** > **Setup** > **Dimension and variant groups** > **Storage dimension groups**.

At the storage dimension group level, set **Primary stocking** to *Yes*. This setting applies to the warehouse; it isn't a separate setting on each dimension row.

Configure the dimension rows for fleet item inventory as follows:

| Name | Active | Coverage plan by dimension | Blank receipt allowed | Blank issue allowed |
|---|---|---|---|---|
| *Site* | *Yes* | *Yes* | *No* | *No* |
| *Warehouse* | *Yes* | *Yes* | *No* | *No* |
| *Location* | *Optional* | *As required* | *As required* | *As required* |

For the **Location** row, *As required* means that you choose the setting according to your inventory processes when the dimension is active. Configure the other standard dimension fields according to your business requirements.

Activate the **Location** dimension when you want to track fleet items in warehouse locations. It's what the **Update location** action on the fleet item master and on fleet item availability moves a fleet item between, and what a hub location's **Linked warehouse location** resolves to.

> [!NOTE]
> Advanced Warehouse Management (WMS) isn't supported for fleet item inventory. Set **Use warehouse management processes** to *No* on the storage dimension group and on warehouses that hold fleet item inventory. The system tracks fleet item physical location through the fleet location hierarchy described later in this article.

### Set up item model groups

An *item model group* is a reusable set of rules that controls how the system values, stocks, and reconciles a product. In rental management, the item model group that you assign to a fleet item decides how the item's inventory cost is calculated and whether its purchase, inventory, and sales transactions post to the ledger. Rental management doesn't add settings to the item model group, so fleet items behave like any other stocked, serialized product.

To set up item model groups, go to **Inventory management** > **Setup** > **Inventory** > **Item model groups**.

For fleet items, use an item model group configured as follows:

| Setting | Recommended value | Reason |
|---|---|---|
| **Inventory model** | *FIFO* | Use FIFO for inventory costing, with **Financial inventory** enabled for the serial-number tracking dimension to value each fleet item separately. |
| **Stocked product** | *Yes* | Fleet items are stocked inventory. A fleet item must be in stock before you can transfer it to a fleet type whose **Value tracking method** is *Fixed asset*. |

Rental management doesn't add settings to the item model group. The standard **Post physical inventory** and **Post financial inventory** settings decide whether the purchase, inventory, and sales transactions of fleet items post to the ledger, in the same way as for any other stocked item.

### Configure the released product

After you set up the dimension groups and item model group, assign them to the released products that you intend to use as fleet items.

To configure a released product for use as a fleet item, follow these steps:

1. Go to **Product information management** > **Products** > **Released products** and open the product record for the fleet item.
1. On the **General** FastTab, set the following fields:
   - **Item model group** – Assign the item model group that you set up for the fleet item.
   - **Storage dimension group** – Assign the storage dimension group with *Site* and *Warehouse* dimensions active.
   - **Tracking dimension group** – Assign the tracking dimension group with *Serial number* active.

1. On the **Purchase** FastTab, verify that **Unit** is set correctly (typically *each* for serialized fleet items).
1. On the Action Pane, open the **Manage inventory** tab and select **Default order settings**. On each of the **Purchase order**, **Inventory**, and **Sales order** FastTabs, set the **Default site** and **Default warehouse** where the fleet item is purchased, held, and sold.
1. On the Action Pane, select the **Back** button to return to the released product record.
1. If the storage dimension group has *Location* active, then on the Action Pane, open the **Manage inventory** tab and select **Warehouse items**. Create a record for each warehouse that holds the product, and set **Default receipt location** and **Default issue location** to the warehouse location that's linked to the fleet location. These defaults place purchase receipts and sales issues at the expected fleet location.
1. On the Action Pane, select the **Back** button to return to the released product record.
1. On the Action Pane, open the **Setup** tab and select **Rental class definition**. Then assign the product's default rental class for each configuration. In the **Rental class definition** grid, each row has an **Item number**, a **Configuration**, a **Rental class**, and a **Default** flag. For product masters, **Configuration** is required, and you can mark only one row per item and configuration as **Default**. Fleet items that you later create for the product get these rental classes, and the row marked **Default** becomes their default rental class.
1. On the Action Pane, select the **Back** button to return to the released product record.
1. On the **Fleet item** FastTab, make the following settings:
    - **Fleet item** – Set to *Yes* to identify the product as a fleet item.
    - **Fleet item type** – Select the type to assign to fleet items that you create from this product through a purchase order, an inventory journal, or on-hand inventory:
        - *Fleet item* – Use for an individual piece of equipment that you track separately, such as an excavator or loader. This is the main equipment item rather than an attachment or a quantity of bulk equipment.
        - *Attachment fleet item* – Use for equipment that attaches to a main fleet item, such as buckets, forks, or augers.
        - *Bulk fleet item* – Use for non-serialized equipment that you rent by quantity.
    - **Usage required** – Select the initial **Usage required** value for fleet items that you create from this product. You can change the value for an individual fleet item on its **Usage information** FastTab.

        For movements, this setting works with the **Fleet item movement status setup** page, which defines the requirements for each movement direction and processing step, such as shipping or receiving. Its **Service meter unit mandatory** and **Fuel mandatory** settings specify which readings the worker must record before posting that step. Choose how these requirements apply to fleet items created from this product:

        - *Default* – Apply the step's reading requirements to items whose **Fleet item type** is *Fleet item*. Attachments and bulk fleet items are exempt.
        - *Yes* – Apply the step's reading requirements to attachments as well as main fleet items. This value doesn't make a reading mandatory if the corresponding requirement is turned off for the movement step.
        - *No* – Exempt the fleet item from the step's mandatory service meter and fuel reading requirements, even when those requirements are turned on.

        Learn more in [Configure fleet item movement statuses](set-up-rental-reference-data.md#configure-fleet-item-movement-statuses).

    - **Model** – Select the fleet item model associated with this released product.

### Configure the location change transfer journal

When you update a fleet item's inventory location (the location dimension) by using the **Update location** action, the system posts a standard inventory transfer journal. You must specify which journal name to use for this process:

1. Go to **Rental management (Preview)** > **Setup** > **Rental parameters**.
1. Open the **Fleet items** tab.
1. On the **General** FastTab, set **Location update** to the name of the inventory transfer journal to use when updating a fleet item's location.

<a name="configure-fleet-types"></a>

## Configure fleet types

*Fleet types* show where a fleet item is in its ownership and rental lifecycle (for example, *New*, *Rental*, *Lease*, *Used*, *Re-rent*, *Customer*, and *Canceled*). Each fleet type has a **Value tracking method** that determines how the system tracks the fleet items of that type, which fleet transfers the system can process, and which rental processes include those fleet items.

To configure fleet types, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet types**.
1. Use the buttons on the Action Pane to add, edit, or remove fleet type rows as needed.
1. For each fleet type, set the following fields:
    - **Fleet type** – Enter a unique name for the fleet type. You can't change this ID after you save the record.
    - **Description** – Enter a description of the fleet type.
    - **Allow to replace attachment** – Choose whether to allow attachments in this fleet type to be used as replacements when you replace an attachment. Unless **Different fleet type on attachment replacement** is set to *Yes* on the **Rental parameters** page (on the **Fleet items** tab, **Replace attachment** FastTab), a replacement must be in the same fleet type as the attachment that it replaces.
    - **Value tracking method** – Select the category of fleet item that belongs to this fleet type. Choose one of the following values:
        - *Inventory* – Fleet items that the system tracks as inventory (for example, *New* and *Used*). When you create fleet items from inventory, you can only from among fleet types that have this tracking method.
        - *Fixed asset* – Fleet items that the system tracks as fixed assets (for example, *Rental* and *Lease*). A fleet transfer into this fleet type from an *Inventory* fleet type creates a fixed asset for the fleet item. You can't add these fleet items to a sales order or sales quotation until you transfer them to an *Inventory* fleet type.
        - *Manual* – Fleet items that you don't track as inventory or as fixed assets, such as *Re-rent*. When you create a fleet item manually, you can only from among fleet types that have this tracking method.
        - *Customer* – Fleet items that a customer owns. When you post a sales invoice for a fleet item, the system moves the fleet item to the fleet type that has this value. Only one fleet type can have this tracking method.
        - *Canceled* – Fleet items that are retired from the fleet. When you cancel or reverse the purchase of a fleet item, the system moves it to the fleet type that has this tracking method. Only one fleet type can have this tracking method.

Make sure that exactly one fleet type has the *Customer* tracking method and exactly one fleet type has the *Canceled* tracking method before you sell fleet items or cancel fleet item purchases.

### Supported fleet transfers

A fleet transfer needs a transfer rule that links in outgoing and incoming fleet types, as described in [Configure transfer rules](#configure-transfer-rules). The system can only process the transfer if the value tracking methods of the two fleet types form one of the following tracking method combinations:

| From | To | What the transfer does |
|---|---|---|
| *Inventory* | *Fixed asset* | Creates a fixed asset for the fleet item and posts its acquisition. |
| *Fixed asset* | *Inventory* | Disposes of the fixed asset and returns the fleet item to inventory. |
| *Fixed asset* | *Fixed asset* | Posts the fixed asset transactions that update the fixed asset group and book for the target fleet type. |

No other combination of value tracking methods can be transferred.

### Which processes use the value tracking method

The value tracking method determines which fleet items other rental processes include:

- **Fleet item availability summary** – The **Available for rent (including re-rent)** figure counts available fleet items in fleet types whose value tracking method is *Fixed asset* or *Manual*. The fleet type filter lists only fleet types whose value tracking method is *Inventory*, *Fixed asset*, or *Manual*.
- **Sales from fleet item availability** – **Sales order**, **Sales quotation**, and **Insert line** on the fleet item availability page only accept fleet items with fleet types whose value tracking method is *Inventory*.
- **Fleet item movements** – You can add a fleet item to a fleet item movement only if its fleet type has a value tracking method of *Inventory*, *Fixed asset*, or *Manual*.
- **Utilization** – The *Calculate fleet item utilization* job calculates utilization only for fleet items in fleet types whose value tracking method is *Fixed asset*. Learn more in [Track rental fleet utilization](track-rental-fleet-utilization.md).
- **Carrying cost and dynamic pricing** – The *Calculate carrying cost* job and the inventory level count that dynamic pricing uses include only fleet items in fleet types whose value tracking method is *Fixed asset*.

### Configure posting for fleet types

Use the **Posting configuration for fleet types** page to define fixed asset group and book assignments by fleet type and item group. Each posting configuration row applies to all item groups or to one specific item group. By using this configuration, you can use different asset classifications and depreciation settings for different kinds of equipment within the same fleet type.

Although you can assign fixed asset groups and books to any fleet type, the assignments supply fixed asset information, not general posting rules. Each fleet type that you track as a *Fixed asset* must have a posting configuration.

This page doesn't specify ledger accounts, journal names, or revenue posting rules. Inventory posting and fixed asset posting profiles determine the ledger accounts. Learn more in [Configure prerequisites for rental management](set-up-rental-prerequisites.md).

The following processes use these assignments:

- **Fleet transfers** – A transfer into a fleet type whose **Value tracking method** is *Fixed asset* requires a matching assignment with a fixed asset group and book. The transfer uses these values to create or update the fleet item's fixed asset. This requirement includes transfers between two fleet types tracked as fixed assets. Learn more in [Understand fleet transfer financial impact](understand-rental-financial-integration.md#understand-fleet-transfer-financial-impact).
- **Sales invoicing** – When the system needs a fixed asset book for an invoice line and can't find an open book, it can use the configured **Book** as a fallback. This rule also applies to fleet items in a *Customer* fleet type if you sold them from a fleet type tracked as a fixed asset. The book must already exist on the fleet item's fixed asset and have a status of *Open* or *Closed*.

Create assignments for the processes that need them. The ability to select any fleet type doesn't mean that every fleet type requires an assignment. Creating an assignment doesn't change the fleet type's **Value tracking method** or, by itself, create a fixed asset.

#### Set up fleet type posting assignments

Before you complete this procedure, create the fleet types described earlier in this section. Also create the item groups, fixed asset groups, and books that your assignments need, as described in [Configure prerequisites for rental management](set-up-rental-prerequisites.md).

To create an assignment for a fleet type and the processes that use it, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Fleet items** > **Posting configuration for fleet types**.
1. Select **New** to add a row.
1. Set the following fields:
    - **Fleet type** – Select the fleet type that the assignment applies to. You can select a fleet type with any value tracking method. Transfers use the target fleet type's assignment; the sales invoice book fallback uses the fleet item's current fleet type.
    - **Item code** – Select *All* to use the assignment for all item groups, unless a group-specific row overrides it. Select *Group* to use it only for one item group.
    - **Item group** – Select the released product's item group when **Item code** is *Group*. This field is required for *Group*. When **Item code** is *All*, the system clears this field and makes it unavailable.
    - **Fixed asset group** – Select the existing fixed asset group to assign when a transfer creates or updates the fleet item's fixed asset. The group supplies defaults for the asset, including numbering and depreciation settings. Learn more in [Configure fixed asset groups](set-up-rental-prerequisites.md#configure-fixed-asset-groups).
    - **Book** – Select the existing fixed asset book to use for the fleet item in this fleet type. Transfers use this book when they create or update the fleet item's asset book. Sales invoicing can also use it to identify an existing asset book, as described earlier in this section.

1. Save the row.
1. Repeat for each fleet type and item group combination that needs different assignments.

For a given fleet type, the system uses a row for the fleet item's item group before it uses the *All* row. A group-specific row replaces the *All* row as a whole; it doesn't inherit missing values from that row. For example, you can create an *All* row for your usual asset group and book, then add a *Group* row for attachments that need different depreciation settings.

Each combination of **Fleet type**, **Item code**, and **Item group** must be unique. You can't change **Fleet type** or **Item code** after you save a row. To change either value, delete the row and create a replacement.

The fields that a process requires aren't necessarily required to save the row. Before you run a transfer into a fleet type tracked as a fixed asset, ensure that a matching row specifies both **Fixed asset group** and **Book**. The page allows you to save an incomplete assignment, but the transfer fails if either value is missing.

Fleet transfers also use the following two inventory journal names from the **General** tab of the **Rental parameters** page:

- **Transfer request inventory asset journal** – An inventory journal of type *Fixed assets*, used for a transfer into a *Fixed asset* fleet type.
- **Transfer request movement journal** – An inventory movement journal, used for a transfer back into an *Inventory* fleet type.

## Configure warehouses and rental locations

A warehouse is a physical facility within a site where inventory is stored. Rental management uses standard Supply Chain Management warehouses, and each branch or site that holds rental fleet inventory requires its own warehouse. The warehouse address appears on fleet item movement documents and is the default delivery address for fleet items that you ship from that branch.

### Warehouse setup for rental operations

Rental management uses standard Supply Chain Management warehouses. Each branch or site that holds rental fleet inventory requires its own warehouse record.

To set up warehouses for rental, go to **Inventory management** > **Setup** > **Inventory breakdown** > **Warehouses**.

> [!IMPORTANT]
> Don't enable **Use warehouse management processes** on warehouses that hold fleet item inventory. The system tracks fleet items at the warehouse level and manages their precise physical location through the fleet location hierarchy described later in this article.

<!--
The Dynamics 365 Supply Chain Management mobile app runs on the Warehouse Management mobile app framework, but it doesn't use warehouse management processes for fleet items. Its workers still need a default warehouse that has **Use warehouse management processes** turned on. Learn more in [Set up the Dynamics 365 Supply Chain Management mobile app](set-up-rental-mobile-app.md).
-->

For each rental warehouse, configure the following settings:

- **Name and address** – The physical address of the branch or site. The system uses this address on fleet item movement documents and as the default delivery address for fleet items that you ship from this warehouse.
- **Site** – Assign the warehouse to the appropriate site.

<a name="understand-rental-locations"></a>

### Understand fleet locations

Rental management tracks a fleet item's physical location in two complementary ways, depending on which fleet the fleet item is in:

- **Inventory warehouses** track the location of fleet items that are in *inventory fleets* (for example, fleet items held as stock, such as *New* or *Used*).
- **Fleet locations** (also called rental locations) track fleet items that are in the *other fleets*, such as the *rental* and *lease* fleets, throughout their lifecycle.

On the **Fleet locations** page, you map the fleet location hierarchy to your inventory warehouses:

- A *Hub* is mapped to a warehouse through its **Linked warehouse** field. Each warehouse belongs to one hub and the hub locations under it, so give every branch its own warehouse.
- A *Hub location* is mapped to a warehouse location through its **Linked warehouse location** field.

Fleet locations are organized into a hierarchy with five location types:

| Location type | Description |
|---|---|
| *Hub* | A main site or branch location. Has its own address and is linked to a warehouse. Can have child *Hub locations*, and one *Transit* location that's required before you can move fleet items internally out of the hub. |
| *Hub location* | A sub-location within a *Hub* (for example, a specific area of the site such as *Ready row*, *Shop*, *Wash bay*, or *Staging area*). Inherits the hub's address and linked warehouse, and can be linked to a warehouse location in that warehouse. |
| *Transit* | Used when a fleet item is in transit between two locations. You can assign a *Transit* location only to a *Hub*. Can't have a parent location. |
| *Job site* | Represents a customer's job site address. The system creates job site fleet locations automatically when a job site record is created. You can't create them manually on the **Fleet locations** page. |
| *Default* | The system fallback location used when no other location is resolved. For example, when a customer picks up a fleet item, its physical location is effectively unknown, so the system uses the default location. Only one *Default* location can exist in the system. |

> [!IMPORTANT]
> **Location type** is mandatory, and you can't change it after you save a location. To correct a wrong type, delete the location and create it again, which you can do while no child locations, transit assignments, or fleet item movements reference it. Decide the type before you save.

The rental location hierarchy looks like this:

- **Default** (system fallback)
- **Hub** (main site or branch)
    - Hub location (Ready row)
    - Hub location (Shop)
    - Hub location (Wash bay)
    - Hub location (Staging area)

- **Transit** (in-transit state for fleet items moving through a hub)
- **Job site** (auto-created per customer job site)

<a name="set-up-rental-locations"></a>

### Set up fleet locations

To set up fleet locations, go to **Rental management (Preview)** > **Setup** > **Fleet locations**. Create the *Transit* location for a branch first, then the *Hub* that uses it. Optionally, create *Hub locations* under that *Hub*.

#### Create a transit location

To create a transit location, follow these steps:

1. Select **New** and enter a **Fleet location** ID and a **Description**.
1. Set **Location type** to *Transit*.
1. Don't set a parent location. Transit locations can't have parents.
1. On the **Address** FastTab, add a postal address to the transit location. You can also enter its **Latitude** and **Longitude**, and the **Sales tax group**.
1. Set the **Linked warehouse** to the inventory warehouse this transit location represents.
1. After you save the record, set the **Transit location** field on the hub that uses it, either while you create the hub or by editing an existing hub.

#### Create a hub

To create a hub, follow these steps:

1. Select **New** and enter a **Fleet location** ID and a **Description**.
1. Set **Location type** to *Hub*.
1. On the **Address** FastTab, add a postal address to the hub. You can also enter its **Latitude** and **Longitude**, and the **Sales tax group**. The system uses the address on delivery documents, and child hub locations inherit it. Child hub locations can't have addresses of their own. A rental quotation or contract whose **Ship to** is the pickup location takes its sales tax group from that address.
1. Set the **Linked warehouse** to the inventory warehouse this hub represents.
1. Assign a **Transit location**, which is an existing *Transit* location that represents the in-transit state for fleet items moving through this hub. This setting is required before you can move any fleet item internally out of this hub. Movements between job sites don't need it.

<a name="create-a-hub-location-sub-location"></a>

#### Create a hub location (optional)

Hub locations are optional sub-locations within a hub. To create a hub location, follow these steps:

1. Select **New** and enter a **Fleet location** ID and a **Description**.
1. Set **Location type** to *Hub location*.
1. Set **Parent location** to the hub this location belongs to. A hub location must have a hub as its parent.
1. Optionally, set the **Linked warehouse location** to a location in the hub's linked warehouse. A hub location takes its **Linked warehouse** from its hub, and you can't change it on the hub location.

If you change a fleet location's **Linked warehouse**, the system clears its **Linked warehouse location**. A change on a hub also moves every hub location under it to the new warehouse, so set their warehouse locations again.

> [!TIP]
> Use hub locations to represent the different physical areas of your site where fleet items are staged, so that rental coordinators and operations staff see where each fleet item is within the site.

#### Work with the location hierarchy

Here are a few tips for working with the location hierarchy:

- You can add sub-locations directly from the hub record. Create and save the hub first, and then add its sub-locations on its **Child locations** tab, where each row becomes a hub location under that hub and in its warehouse.
- When you filter the fleet item availability summary by a hub, the list also includes the fleet items at that hub's child hub locations.
- You can place a manually created fleet item only at a hub or a hub location. The lookup doesn't offer transit, job site, or default locations.
- Job site and transit locations aren't offered on fleet item movements, rental quotations and contracts, sales orders and quotations, or fleet transfers. You maintain job site locations through their job site records.

### How fleet items move between rental locations

The system updates a fleet item's current rental location automatically as the fleet item moves through the rental lifecycle:

- **On outbound shipment** – You change the fleet item location from the hub (or hub sub-location) to the job site.
- **On inbound return** – You change the fleet item location from the job site back to the hub.
- **On internal transfer** – You change the fleet item location between two hub locations or warehouses.

To update a fleet item's inventory location (for example, when you move it between hub locations), follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet items** and open the fleet item.
1. On the Action Pane, open the **Setup** tab, and then select **Update location**.
1. In the drop-down dialog, select the **New location** for the fleet item and then select **Update**.
1. The system posts an inventory transfer journal that uses the journal name in the **Location update** field on the **Rental parameters** page.

## Configure transfer rules

Transfer rules define which fleet-to-fleet transfers the system allows. This setup prevents accidental transfers between incompatible fleet types and controls which fleet transitions are part of the rental purchase option (RPO) process.

To configure transfer rules, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Transfers** > **Transfer rules**.
1. Use the buttons on the Action Pane to create, edit, or delete rows for each allowed transfer.
1. Make the following settings for each row:
    - **Fleet from** – Select the source fleet type (for example, *New*).
    - **Fleet to** – Select the target fleet type (for example, *Rental*).
    - **Rental purchase option transfer** – Select this check box if you use this fleet transition as part of a rental purchase option (RPO) buyout (for example, *Rental* to *Used*, before the fleet item is sold). The RPO process requires a rule that has this flag set. The flag doesn't reserve the transition—a rule that has it set still allows an ordinary manual fleet transfer between the same two fleet types.

> [!IMPORTANT]
> A fleet transfer needs a transfer rule for its **Fleet from** and **Fleet to** fleet types. Create rules for every valid transition in your fleet lifecycle before you process any fleet transfers. A rule doesn't make an unsupported combination of value tracking methods possible. Learn more in [Supported fleet transfers](#supported-fleet-transfers).

Typical rules for a standard rental operation include:

| Fleet from | Fleet to | Purpose |
|---|---|---|
| *New* | *Rental* | Allows a newly purchased asset to be moved to the active rental fleet |
| *New* | *Lease* | Allows a newly purchased asset to be moved to the active lease fleet |
| *Rental* | *Used* | Allows a returned fleet item to be moved to the used fleet for resale |
| *Used* | *Rental* | Allows a refurbished fleet item to be returned to the active rental fleet |
| *Lease* | *Used* | Allows an off-lease fleet item to be moved to the used fleet for resale |

To load rules in bulk, use the *Rental transfer rules* data entity in data management.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Set up rental reference data](set-up-rental-reference-data.md)
- [Configure rental parameters](configure-rental-parameters.md)
- [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md)
- [Understand rental management financial integration](understand-rental-financial-integration.md)
- [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md)
