---
# required metadata

title: Configure shipment consolidation policies
description: How to set up default and custom shipment consolidation policies.
author: GarmMSFT
manager: tfehr
ms.date: 05/01/2020
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
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: 10.0.3
---

# Configure shipment consolidation policies

[!include [banner](../includes/banner.md)]

The shipment consolidation process using shipment consolidation policies allows for automated shipment consolidation during automated and manual release to warehouse. After you enable this feature, you must configure your initial policies. If you don't have any policies configured, then each sales line will generate a separate shipment with a single load line.

The scenarios provided in this topic illustrate how to set up default and custom shipment consolidation policies.

## Enable the shipment consolidation policies feature

> [!IMPORTANT]
> The [first scenario](#scenario-1) provided in this topic includes steps where you first set up a warehouse to use the legacy shipment consolidation feature and *then* enable the shipment consolidation policies. This will let you experience how the upgrade scenario works. If you are planning to use a demo-data environment to work through the first scenario, then don't enable the feature before you do the scenario.

Before you can use this feature, it must be enabled on on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Consolidate shipment*

## Enable demo data

Each of the scenarios in this topic reference values and records included in the standard demo data provided for Supply Chain Management. If you'd like to run the exercises using the values provided here, be sure to work on an environment with the demo data installed, and set the legal entity to **USMF** before you begin.

<a name="scenario-1"></a>

## Scenario 1: Configure default shipment consolidation policies

There are two situations where you must configure the minimum number of default policies after enabling the *Shipment consolidation policies* feature:

- When upgrading and environment that already contains data
- When setting up a completely new environment

### Upgrade an environment with warehouses already configured for cross-order consolidation

In this procedure, we will start with the *Shipment consolidation policies* feature disabled to simulate an environment where the basic cross-order consolidation feature was already in use. Then you'll enable the *Shipment consolidation policies* feature using feature management so you can see how to set up shipment consolidation policies after the upgrade.

To set up default shipment consolidation policies on an environment where warehouses have already been configured for cross-order consolidation:

1. Go to **Warehouse management \> Setup \> Warehouse \> Warehouses**.

1. In the list, find and open the desired warehouse record (for example, warehouse 24 in the **USMF** demo data).

1. Select **Edit** on the action pane.

1. On the **Warehouse** FastTab, set the **Consolidate shipment at release to warehouse** option to **Yes**.

1. Repeat steps 2 through 4 for all warehouses where consolidation is needed.

1. Close the page.

1. Use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable the *Shipment consolidation policies* feature. In feature management, its **Feature name** is *Consolidate shipment*.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**. (You may need to refresh your browser to see this new menu item right after enabling the feature.)

1. Select **Create default setup** on the action pane to create the following:
    - A **CrossOrder** policy for the **Policy type** *Sales orders* (provided you have at least one warehouse enabled to use the legacy consolidation feature).
    - A **Default** policy for the **Policy type** *Sales orders*.
    - A **Default** policy for the **Policy type** *Transfer issue*.
    - A **CrossOrder** policy for the **Policy type** *Transfer issue* (provided you have at least one warehouse enabled to use the legacy consolidation feature).

    > [!NOTE]
    > - The **CrossOrder** policy takes the same fields into consideration as the legacy logic did, excluding the order number (to consolidate lines into shipments based on warehouse, transportation mode of delivery, address, and so on).
    > - Both **Default** policies take the same set of fields into consideration as legacy logic did, including order number (to consolidate lines into shipments based on order number, warehouse, transportation mode of delivery, address, and so on).

1. Select **CrossOrder** policy and select **Edit query** on the action pane.

1. The query opens. Note that warehouses that had **Consolidate shipment at release to warehouse** set to *Yes* are listed here and are therefore included in the query.

### Create default policies for a new environment

To set up default shipment consolidation policies on a brand new environment, use the following procedure.

1. If you haven't already done so, use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable the *Shipment consolidation policies* feature. In feature management, its **Feature name** is *Consolidate shipment*.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.

1. Select **Create default setup** on the action pane to create the following:

    - A **Default** policy for the **Policy type** *Sales orders*.
    - A **Default** policy for the **Policy type** *Transfer issue*.

    > [!NOTE]
    > Both default policies take the same set of fields into consideration as the legacy logic did, including order number (to consolidate lines into shipments based on order number, warehouse, transportation mode of delivery, address, and so on).

## Scenario 2: Configure custom shipment consolidation policies

This scenario shows show to set up custom shipment consolidation policies, which can support complex business requirements where shipment consolidation depends on several conditions. Each of these examples includes a short description of the business case and should be set up in a sequence that ensures a "pyramid-like" evaluation of the queries (such that the policies with the most conditions are evaluated with highest priority).

### Enable the feature and prepare master data for this scenario

Before you can work through the exercises in this scenario, you must enable the feature and prepare the master data needed to do the filtering, as described in this section. (This is also a precondition for the scenarios provided in [Consolidate shipments using shipment consolidation policies](consolidate-shipments.md).)

#### Enable the feature and create the default policies

If you haven't already done so, enable the feature in feature management and create the default consolidation polices as described previously in [Scenario 1: Configure default shipment consolidation policies](#scenario-1).

#### Create two new product filter codes

1. Go to **Warehouse management \> Setup \> Product filters \> Product filters** and add the following two filters:

    - Product filter 1:
        - **Filter code** - *Flammable*
        - **Filter title** - *Code 4*
    - Product filter 2:
        - **Filter code** - *Explosive*
        - **Filter title** - *Code 4*

1. Go to **Product information management \> Products \> Released products**.
1. Open the product with **Item number** *M9200*. (You must select a product that is enabled for advanced warehouse (WMS) processes, and this one is pre-enabled in the **USMF** demo data)
1. On the **Warehouse** FastTab, set **Code 4** to *Flammable*.
1. Close the page.
1. Open the product with **Item number** *M9201*. (This product is also pre-enabled for WMS in the in the **USMF** demo data.)
1. On the **Warehouse** FastTab, set **Code 4** to *Explosive*.
1. Close the page.

#### Create a new transportation mode of delivery

1. Go to **Transportation management > Setup > Carriers > Mode**.

1. Create a new transportation mode called *Airways*, which will be used in consolidation queries.

1. Go to **Transportation management > Setup > Carriers > Shipping carries**.

1. Create a new carrier with the following settings:

    - **Shipping carrier** - *Airways*
    - **Name** - *Airways*
    - **Mode** - *Airways*

1. On **Services** FastTab for your new carrier, add a new row with the following settings:

    - **Carrier service** - *Air*
    - **Transportation method** - *Air*
1. Select **Save** on the action pane.

    > [!NOTE]
    > When you save the new carrier, the **Mode of delivery** field for your new row in the **Services** table is automatically set to *Airwa-Air*. When you use the *Airwa-Air* mode of delivery on a sales order, the *Airways* transportation mode will be used on related shipments.

#### Create an order pool

1. Go to **Sales and marketing \> Setup \> Sales orders \> Order pools**.

1. Create a new order pool (for the consolidation query) with the following settings:

    - **Pool** - Enter an integer that isn't already used by any other pool
    - **Name** - *ShipCons*

1. Go to **Sales and marketing \> Customers \> All customers**.

1. Open the customer with **Account** *US-003*.

1. On the **Sales order defaults** FastTab, set the **Sales order pool** to the pool that you just created it.

1. Close the page and then repeat the previous step for the customer with **Account** *US-004*.

### Create example policy 1

In this example, we'll create a *Customer+Mode* policy for use in the following business case:

- The policy will query for a specific customer account (*US-001*) and mode of delivery (*Airwa-Air*).
- Consolidation with open shipments is off.
- Consolidation is per order ID (separate shipments per order, warehouse, and so on).

To create the shipment consolidation policy for this business case:

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.

1. Set the **Policy type** to *Sales orders*.

1. Select **New** on the action bar to create a new policy and make the following settings for it:

    - **Policy name** -  *CustomerMode*
    - **Policy description** - *Customer account and mode of delivery*.

1. Leave **Consolidate with open shipments** set to *No*.

1. Select **Save** on the action pane.

1. Expand the **Consolidation fields** FastTab

1. In the list of **Remaining fields**, select the row with **Field name** *Mode of delivery*.

1. Select the **Add** button ![forward arrow](media/forward-button.png) to move the field to the **Selected fields** column.

1. Select **Edit query** on the action pane.

1. The query pane opens. On the **Range** tab, find the row with a **Field** value of *Customer account* and set its **Criteria** to *US-001*.

1. Select **Add** to add a new row to the **Range** table and make the following settings for it:

    - **Table** - *Order lines*
    - **Derived table** - *Order lines*
    - **Field** - *Mode of delivery*
    - **Criteria** - *Airwa-Air*

1. Select **OK** to close the query pane.

> [!NOTE]
> For this business case, order lines for customer *US-001* using the mode of delivery *Airwa-Air* won't be consolidated across orders. This policy is intended to be used first in a sequence, in cases where we consolidate shipments for all other modes of delivery for this customer.

### Create example policy 2

In this example, we'll create a *Hazardous goods* policy for use in the following business case:

- The policy will query for a specific filter code (*hazardous*) and mode of delivery (*Airwa-Air*).
- Consolidation with open shipments is on.
- Consolidation is across orders (separate shipments per account, warehouse, and so on, but within the item group specified in the query).

To create the shipment consolidation policy for this business case:

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.

1. Set the **Policy type** to *Sales orders*.

1. Select **New** on the action bar to create a new policy and make the following settings for it:

    - **Policy name** -  *Item type*
    - **Policy description** - *Consolidate the same type of item across orders*.

1. Set **Consolidate with open shipments** to *Yes*.

1. Select **Save** on the action pane.

1. Expand the **Consolidation fields** FastTab

1. In the list of **Remaining fields**, select the row with **Field name** *Mode of delivery*.

1. Select the **Add** button ![forward arrow](media/forward-button.png) to move the field to the **Selected fields** column.

1. Select **Edit query** on the action pane. The query pane opens.

1. Open the **Joins** tab.

1. In the tree, expand and select **Tables \> Load details**.

1. Select **Add table join**.

1. A table of relations opens. Find and select the row with a **Relation** value of *Warehouse item number (Item number)* and then select **Select**. 

1. Open the **Range** tab.

1. Select **Add** to add a new row to the **Range** table and make the following settings for it:

    - **Table** - *Warehouse item number*
    - **Derived table** - *Warehouse item number*
    - **Field** - *Code 4*
    - **Criteria** - *Flammable*

1. Select **OK** to close the query pane.

> [!NOTE]
> For this business case, all order lines where items have a specific filter code (where **Code 4** is set to *Flammable*) will be consolidated across orders with other items of the same kind. If there is an open shipment for the same account, warehouse, and group of items, the new lines will be attached to it.

### Create example policy 3

In this example, we'll create a *Customers' requirements* policy for use in the following business case:

- The policy will query for a specific customer account.
- Consolidation with open shipments is on.
- Consolidation is across orders but based on customer requisitions (multiple orders are grouped into shipments based on the same customer requisition number and warehouse).

To create the shipment consolidation policy for this business case:

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.

1. Set the **Policy type** to *Sales orders*.

1. Select **New** on the action bar to create a new policy and make the following settings for it:

    - **Policy name** -  *CustomerOrderNo*
    - **Policy description** - *Consolidate lines based on customer PO*.

1. Set **Consolidate with open shipments** to *Yes*.

1. Select **Save** on the action pane.

1. Expand the **Consolidation fields** FastTab

1. In the list of **Remaining fields**, select the row with a **Field name** of *Customer requisition*.

1. Select the **Add** button ![forward arrow](media/forward-button.png) to move the field to the **Selected fields** column.

1. In the list of **Remaining fields**, select the row with a **Field name** of *Mode of delivery*.

1. Select the **Add** button ![forward arrow](media/forward-button.png) to move the field to the **Selected fields** column.

1. Select **Edit query** on the action pane.

1. The query pane opens. On the **Range** tab, find the row with a **Field** value of *Customer account* and set its **Criteria** to *US-001*.

1. Select **OK** to close the query pane.

> [!NOTE]
> For this business case, all order lines where sales orders have the same customer-requisition number (which is used as the customer’s purchase order (PO) number) will be consolidated into one shipment regardless of the sales-order number. If there is an open shipment for the same account, warehouse, and customer requisition, the new lines will be attached to it. This policy can be used if the customer sends additional order lines with the same PO number several times a day and wants them all to be grouped in one shipment (resulting in one bill of lading and packing slip).

### Create example policy 4

In this example, we'll create a *Customers allowing consolidation* policy for use in the following business case:

- The policy will query for a specific order pool to identify customers accepting consolidated shipments.
- Consolidation with open shipments is off.
- Consolidation is across orders with regular fields selected.
- The rule can be overridden on a sales order by selecting another order pool.

To create the shipment consolidation policy for this business case:

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.

1. Set the **Policy type** to *Sales orders*.

1. Select **New** on the action bar to create a new policy and make the following settings for it:

    - **Policy name** -  *Order pool*
    - **Policy description** - *Consolidate across orders based on order pool*.

1. Leave **Consolidate with open shipments** set to *No*.

1. Select **Save** on the action pane.

1. Expand the **Consolidation fields** FastTab

1. In the list of **Remaining fields**, select the row with a **Field name** of *Mode of delivery*.

1. Select the **Add** button ![forward arrow](media/forward-button.png) to move the field to the **Selected fields** column.

1. Select **Edit query** on the action pane.

1. Select **Add** to add a new row to the **Range** table and make the following settings for it:

    - **Table** - *Sales orders*
    - **Derived table** - *Sales orders*
    - **Field** - *Pool*
    - **Criteria** - *ShipCons*

1. Select **OK** to close the query pane.

> [!NOTE]
> For this business case, all order lines where sales orders belong to the same order pool will be consolidated into one shipment across sales orders for the same account, warehouse, and transportation mode of delivery. Instead of the order pool, you could use any other field to set a group of customers apart and default to the sales order header. You can use this if the customer is driving the need for consolidation (rather than the warehouse, as in the legacy logic).

### Create example policy 5

In this example, we'll create a *Warehouses allowing consolidation* policy for use in the following business case:

- The policy will query for a specific order pool to identify warehouses that can consolidate shipments.
- Consolidation with open shipments is off.
- Consolidation is across orders with regular fields selected (to replicate the legacy **Warehouse** checkbox).

This business case can most typically be addressed using the default policies you may have created earlier in [scenario 1](#scenario-1). But you can also create similar policies manually by doing the following:

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.

1. Set the **Policy type** to *Sales orders*.

1. Select **New** on the action bar to create a new policy and make the following settings for it:

    - **Policy name** -  *Cross-order*
    - **Policy description** - *Cross-order consolidation for specific warehouses*.

1. Leave **Consolidate with open shipments** set to *No*.

1. Select **Save** on the action pane.

1. Expand the **Consolidation fields** FastTab

1. In the list of **Remaining fields**, select the row with a **Field name** of *Mode of delivery*.

1. Select the **Add** button ![forward arrow](media/forward-button.png) to move the field to the **Selected fields** column.

1. Select **Edit query** on the action pane.

1. The query pane opens. On the **Range** tab, find the row with a **Field** value of *Warehouse* and set its **Criteria** to *61, 63*.

1. Select **OK** to close the query pane.

### Set the sequence order

Now that you have created all of your policies, you must establish the order in which they will be applied. To apply a pyramid-like approach, in which the policies with the most conditions are evaluated with highest priority, do the following

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.

1. Set the **Policy type** to *Sales orders*.

1. Select each policy listed in the left-hand column and then use the **Move up** and **Move down** buttons on the action bar to arrange them into the following order:
    1. CustomerMode
    1. Item type
    1. CustomerOrderNo
    1. Order pool
    1. Cross-order
    1. Default

## Additional resources
- [About shipment consolidation policies](about-shipment-consolidation-policies.md)
- [Consolidate shipments](consolidate-shipments.md)
