---
# required metadata

title: Configure shipment consolidation policies
description: How to set up default and custom shipment consolidation policies.
author: GarmMSFT
manager: tfehr
ms.date: 04/20/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: v-olbara
ms.search.validFrom: 2020-04-20
ms.dyn365.ops.version: 10.0.3
---

# Configure shipment consolidation policies

[!include [banner](../includes/banner.md)]

The shipment consolidation process using shipment consolidation policies allows for automated shipment consolidation during automated and manual release to warehouse. After you enable this feature, you must configure your initial policies. If you don't have any policies configured, then each sales line will generate a separate shipment with a single load line.

The scenarios provided in this topic illustrate how to set up default and custom shipment consolidation policies.

<a name="scenario-1"></a>

## Scenario 1: Configure default shipment consolidation policies

There are two situations where you must configure the minimum number of default policies after enabling the *Shipment consolidation policies* feature:

- When upgrading and environment that already contains data
- When setting up a completely new environment

In this scenario, we will illustrate each of these cases using the demo data provided with the **USMF** legal entity.

### Upgrade an environment with warehouses already configured for cross-order consolidation

In this procedure, we will start with the *Shipment consolidation policies* feature disabled to simulate an environment where the basic cross-order consolidation feature was already in use. Then you'll enable the *Shipment consolidation policies* feature using feature management so you can see how to set up shipment consolidation policies after the upgrade.

To set up default shipment consolidation policies on an environment where warehouses have already been configured for cross-order consolidation:

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. In the list, find and select the desired warehouse record (for example, warehouse 51 in the demo data).
1. Select **Edit** on the action pane.
1. On the **Warehouse** FastTab, set the **Consolidate shipment at release to warehouse** option to **Yes**.
1. Repeat steps 2 through 4 for all warehouses where consolidation is needed.
1. Close the page.
1. Use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable the *Shipment consolidation policies* feature. Here, the feature is listed as:
    - **Module** - *Warehouse management*
    - **Feature name** - *Consolidate shipment*
1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**. (You may need to refresh your browser to see this new menu item right after enabling the feature.)
1. Select **Create default setup** on the action pane to create the following:
    - A **CrossOrder** policy for the **Policy type** *Sales orders*.
    - A **Default** policy for the **Policy type** *Sales orders*.
    - A **Default** policy for the **Policy type** *Transfer issue*.
    <!-- KFM: The type appears to be "Transfer issue" not "transfer order"--am I in the right place? I also see a "CrossOrder" policy for transfer issues/orders here. -->

    > [!NOTE]
    > - The **CrossOrder** policy takes the same fields into consideration as the legacy logic did, excluding the order number (to consolidate lines into shipments based on warehouse, transportation mode of delivery, address, and so on).
    > - Both **Default** policies take the same set of fields into consideration as legacy logic did, including order number (to consolidate lines into shipments based on order number, warehouse, transportation mode of delivery, address, and so on).

1. Select **CrossOrder** policy and select **Edit query** on the action pane.
1. The query opens. Note that warehouses that had **Consolidate shipment at release to warehouse** set to *Yes* are listed here and are therefore included in the query.

### Create default policies for a new environment

To set up default shipment consolidation policies on a brand new environment, use the following procedure.

1. If you haven't already done so, use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable the *Shipment consolidation policies* feature. Here, the feature is listed as:
    - **Module** - *Warehouse management*
    - **Feature name** - *Consolidate shipment*
1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Select **Create default setup** on the action pane to create the following:
    - A **Default** policy for the **Policy type** *Sales orders*.
    - A **Default** policy for the **Policy type** *Transfer issue*.
    > [!NOTE]
    > Both default policies take the same set of fields into consideration as the legacy logic did, including order number (to consolidate lines into shipments based on order number, warehouse, transportation mode of delivery, address, and so on).

## Scenario 2: Configure custom shipment consolidation policies

This scenario shows show to set up custom shipment consolidation policies, which can support complex business requirements where shipment consolidation depends on several conditions. Each of these examples includes a short description of the business case and should be set up in a sequence that ensures a "pyramid-like" evaluation of the queries (such that the policies with the most conditions are evaluated with highest priority).

### Enable the feature and prepare master data for this scenario

Before you can work through the exercises in this scenario, you must enable the feature and prepare the master data needed to do the filtering, as described in this section. (This is also a precondition for the scenarios provided in [Consolidate shipments using shipment consolidation policies](../warehousing/consolidate-shipments.md).)

#### Enable the feature and create the default policies

If you haven't already done so, enable the feature in feature management and create the default consolidation polices as described previously in [Scenario 1: Configure default shipment consolidation policies](#scenario-1).

#### Set up product filter codes

1. Go to **Warehouse management \> Setup \> Product filters \> Product filters** and add the following two filter codes:

    - Product filter 1:
        - **Filter code** - *Flammable*
        - **Filter title** - *Code 4*
    - Product filter 2:
        - **Filter code** - *Explosive*
        - **Filter title** - *Code 4*
<!-- KFM: continue here -->
2. Go to **Product information management \> Products \> Released products** and set up two WHS-enabled items&mdash;one item with **Flammable** product filter code (**Code 4** field on the **Warehouse** FastTab) and another one with **Explosive** product filter code.

#### Set up the transportation mode of delivery

1. Go to **Transportation management > Setup > Carriers > Modes** and create a new transportation mode that will be used for consolidation query.
    1. For example, **Airways**.

1. Go to **Transportation management > Setup > Carriers > Shipping carries** and create a new carrier with **Airways** mode.
    1. For example, **Airways**.
1. Then expand **Services** FastTab and add **Air** carrier service with **Air** transportation method.
     > [!NOTE]
     > **Mode of delivery** field is automatically filled in with **Airwa-Air** value. When **Airwa-Air** mode of delivery is used on a sales order, **Airways** transportation mode will be used on related shipment.

#### Set up the order pool

1. Go to **Sales and marketing \> Setup \> Sales orders \> Order pools** and create a new order pool that will be used for consolidation query.
    1. For example, **ShipCons**.

2. Go to **Sales and marketing \> Customers \> All customers** and assign new pool to **US-003** and **US-004** customers on the **Sales order defaults** FastTab.

### Add example policy 1

Example of a business case:

- “Customer+Mode” policy
  - Query: Specific Customer account, specific Mode of delivery “Airwa-Air”
  - Consolidation with open shipments is off
  - Consolidation is per order id (separate shipments per order, warehouse, etc.)

To create a shipment consolidation policy that covers mentioned above business case, follow these steps.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Click **New**.
1. In the **Policy name** field, type a value, for example, **CustomerMode**.
1. In the **Policy description** field, type a value, for example, **Customer account and mode of delivery**.
1. Click **Save**.
1. Expand the **Consolidation fields** FastTab
1. In the list of **Remaining fields**, find and select **Mode of delivery** record (where **Field name** = Mode of delivery).
1. Click ![forward arrow](media/forward-button.png) button to move the record under **Selected fields**.
1. Click **Edit query**.
1. In the list, find and select the **Customer account** record.
1. In the **Criteria** field, enter or select a value, for example, **US-001**.
1. In the list, find or add the **Sales order lines.Mode of delivery** record.
1. In the **Criteria** field, enter or select a value, for example, **Airwa-Air**.
1. Click **OK**.

> [!NOTE]
> All order lines with the specified mode of delivery **Airwa-Air** of customer **US-001** will not be consolidated across orders. This is used as a first sequence in case we consolidate shipments for all other modes of delivery for this customer.

### Add example policy 2

Example of a business case:

- “Hazardous goods” policy
  - Query: Specific “hazardous” filter code, specific “Airways” transportation modes of delivery 
  - Consolidation with open shipments is on
  - Consolidation is across orders (separate shipments per account, warehouse, etc. but within the item group specified in the query)

To create a shipment consolidation policy that covers mentioned above business case, follow these steps.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Click **New**.
1. In the **Policy name** field, type a value, for example, **Item type**.
1. In the **Policy description** field, type a value, for example **Consolidate the same type of item across orders**.
1. Click **Save**.
1. In the list of **Remaining fields**, find and select **Mode of delivery** record.
1. Click ![forward arrow](media/forward-button.png) button.
1. Select **Yes** in the **Consolidate with open shipments** field.
1. Click **Edit query**.
1. Click the **Joins** tab.
1. In the tree, expand and select **Tables\Load details**.
1. Click **Add table join**.
1. In the list, find and select **Warehouse item number (Item number)**.
1. Click **Select**.
1. Click the **Range** tab.
1. Click **Add**.
1. Add a record for a filter code from Warehouse items, for example **Warehouse item number.Code 4**.
    1. Any other grouping value can be used.
1. In the **Criteria** field, enter or select a value, for example **Flammable**.
1. Click **OK**.

> [!NOTE]
> All order lines where items have the same Filter code 4, for example “Flammable”, will be consolidated across orders with other items of the same kind. If there is an open shipment for the same account, warehouse, and group of items, the new lines will be attached to it.

### Add example policy 3

Example of a business case.

- Customer's' requirements policy
  - Query: Specific Customer account
  - Consolidation with open shipments is on
  - Consolidation is across orders but based on Customer requisition (multiple orders are grouped into shipments based on the same Customer requisition number and warehouse)

To create a shipment consolidation policy that covers mentioned above business case, follow these steps.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Click **New**.
1. In the **Policy name** field, type a value, for example **CustomerOrderNo**.
1. In the **Policy description** field, type a value, for example **Consolidate lines based on customer PO**.
1. Select **Yes** in the **Consolidate with open shipments** field.
1. Click **Save**.
1. In the list of **Remaining fields**, find and select the **Customer requisition** record.
1. Click ![forward arrow](media/forward-button.png) button.
1. In the list of **Remaining fields**, find and select the **Mode of delivery** record.
1. Click ![forward arrow](media/forward-button.png) button.
1. Click **Edit query**.
1. In the list, find and select the **Customer account** record.
1. In the **Criteria** field, enter or select a value, for example, **US-001**.
1. Click **OK**.

> [!NOTE]
> All order lines where sales orders have the same Customer requisition number (which is used as the customer’s PO number) will be consolidated into one shipment regardless of Sales order number. If there is an open shipment for the same account, warehouse, and customer requisition, the new lines will be attached to it. It can be used if the customer sends additional order lines with the same PO number several times a day and wants them all to be grouped in one shipment (resulting in one bill of lading and packing slip).

### Add example policy 4

Example of a business case.

- Customers allowing consolidation policy
  - Query: Specific Order pool to identify customers accepting consolidated shipments
  - Consolidation with open shipments is off
  - Consolidation is across orders with regular fields selected
  - Rule can be overridden on a sales order by selecting another order pool

To create a shipment consolidation policy that covers mentioned above business case, follow these steps.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Click **New**.
1. In the **Policy name** field, type **Order pool**.
1. In the **Policy description** field, type a value, for example **Consolidate across orders based on order pool**.
1. Click  **Save**.
1. In the list of **Remaining fields**, find and select the **Mode of delivery** records.
1. Click ![forward arrow](media/forward-button.png) button.
1. Click **Edit query**.
1. In the list, find and add the **Sales orders.Pool** record.
1. In the **Criteria** field, enter or select a value, for example, **ShipCons**.
1. Click **OK**.

> [!NOTE]
> All order lines where sales orders belong to the same Order pool will be consolidated into one shipment across sales orders for the same account, warehouse, and transportation mode of delivery. Order pool can be replaced with any other field setting a group of customers apart and defaulting to the sales order header. This can be used if the customer and not the warehouse (like in the legacy logic) is driving the need for consolidation.

### Add example policy 5

Example of a business case.

- Warehouses allowing consolidation policy
  - Query: Specific Order pool to identify warehouses that can consolidate shipments
  - Consolidation with open shipments is off
  - Consolidation is across orders with regular fields selected (replication of the current “Warehouse” checkbox)

To create a shipment consolidation policy that covers mentioned above business case, if it wasn't created automatically as part of Scenario 1, follow these steps.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Click **New**.
1. In the **Policy name** field, type a value, for example **CrossOrder**.
1. In the **Policy description** field, type a value, for example **Cross-order consolidation for specific warehouses**.
1. Click **Save**
1. In the list, find and select the **Mode of delivery**.
1. Click ![forward arrow](media/forward-button.png) button.
1. Click **Edit query**.
1. In the list of **Remaining fields**, find and select the **Warehouse** record.
1. In the **Criteria field**, type **61, 63**.
1. Click **OK**.
    - It is manual replication of the legacy logic where the consolidation decision was driven by specific warehouses.
1. In the list, find and select the desired policies and by using **Move up/Move down** buttons arrange them in the order of applicability (pyramid-like approach) as follows:
    1. CustomerMode
    1. Item type
    1. CustomerOrderNo
    1. Order pool
    1. CrossOrder
    1. Default

## Related articles and demo scripts

- [About shipment consolidation policies](../warehousing/about-shipment-consolidation-policies.md)  
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
