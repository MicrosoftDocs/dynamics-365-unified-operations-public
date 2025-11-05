---
title: Configure shipment consolidation policies
description: Learn how to set up default and custom shipment consolidation policies with an outline on turning on the Shipment consolidation policies feature.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 09/07/2022
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench, WHSFilterGroupTable, TMSMode, WHSShipmentConsolidation, WHSFilterGenerallyAvail, WHSOutboundLoadPlanningWorkbench
---

# Configure shipment consolidation policies

[!include [banner](../includes/banner.md)]

The shipment consolidation process that uses shipment consolidation policies allows for automated shipment consolidation during automated and manual release to the warehouse. After you turn on this feature, you must configure your initial policies. If no policies are configured, each sales line will generate a separate shipment that has a single load line.

The scenarios that are presented in this article show how to set up default and custom shipment consolidation policies.

## Scenario: Configure custom shipment consolidation policies

This scenario provides an example that shows how to set up custom shipment consolidation policies and then test them by using demo data. Custom policies can support complex business requirements where shipment consolidation depends on several conditions. For each example policy later in this scenario, a short description of the business case is included. These example policies should be set up in a sequence that ensures a pyramid-like evaluation of the queries. (In other words, the policies that have the most conditions should be evaluated as having the highest priority.)

### Make demo data available

This scenario references values and records that are included in the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) that is provided for Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to *USMF* before you begin.

### Prepare master data for this scenario

Before you can go through the exercises in this scenario, you must prepare the master data that is required to do the filtering, as described in the following subsections. (These prerequisites also apply to the scenarios that are listed in the [Example scenarios of how to use shipment consolidation policies](#example-scenarios) section.)

#### Create two new product filter codes

1. Go to **Warehouse management \> Setup \> Product filters \> Product filters**, and add two product filters:

    - Product filter 1:

        - **Filter code:** *Flammable*
        - **Filter title:** *Code 4*

    - Product filter 2:

        - **Filter code:** *Explosive*
        - **Filter title:** *Code 4*

1. Go to **Product information management \> Products \> Released products**.
1. Open the product that has item number *M9200*. (The product that you select must be enabled for advanced warehouse \[WMS\] processes, and this product is pre-enabled for WMS processes in the **USMF** demo data.)
1. On the **Warehouse** FastTab, set the **Code 4** field to *Flammable*.
1. Close the page.
1. Open the product that has item number *M9201*. (This product is also pre-enabled for WMS processes in the in the **USMF** demo data.)
1. On the **Warehouse** FastTab, set the **Code 4** field to *Explosive*.
1. Close the page.

#### Create a new transportation mode of delivery

1. Go to **Transportation management \> Setup \> Carriers \> Mode**.
1. Create a transportation mode that will be used in consolidation queries, and name it *Airways*.
1. Go to **Transportation management \> Setup \> Carriers \> Shipping carriers**.
1. Create a carrier that has the following settings:

    - **Shipping carrier:** *Airways*
    - **Name:** *Airways*
    - **Mode:** *Airways*

1. On the **Services** FastTab for the new carrier, add a row that has the following settings:

    - **Carrier service:** *Air*
    - **Transportation method:** *Air*

1. On the Action Pane, select **Save**.

    > [!NOTE]
    > When you save the new carrier, the **Mode of delivery** field for the new row in the **Services** grid is automatically set to *Airwa-Air*. When you use the *Airwa-Air* mode of delivery for a sales order, the *Airways* transportation mode will be used for related shipments.

#### Create an order pool

1. Go to **Sales and marketing \> Setup \> Sales orders \> Order pools**.
1. Create an order pool that will be used for the consolidation query. This order pool should have the following settings:

    - **Pool:** Enter an integer that isn't already used by any other pool.
    - **Name:** *ShipCons*

1. Go to **Sales and marketing \> Customers \> All customers**.
1. Open the customer that has account number *US-003*.
1. On the **Sales order defaults** FastTab, set the **Sales order pool** field to the order pool that you just created.
1. Close the page, and then repeat steps 4 and 5 for the customer that has account number *US-004*.

### Create example policy 1

In this example, you will create a *Customer+Mode* policy that can be used for the following business case:

- The policy will query for a specific customer account (*US-001*) and a specific mode of delivery (*Airwa-Air*).
- Consolidation with open shipments is turned off.
- Consolidation is done per order ID. (In other words, there will be separate shipments per order, warehouse, and so on.)

Follow these steps to create the shipment consolidation policy for this business case.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Set the **Policy type** field to *Sales orders*.
1. On the Action Pane, select **New** to create a policy that has the following settings:

    - **Policy name:** *CustomerMode*
    - **Policy description:** *Customer account and mode of delivery*

1. Leave the **Consolidate with open shipments** option set to *No*.
1. On the Action Pane, select **Save**.
1. On the **Consolidation fields** FastTab, in the **Remaining fields** list, select the row where the **Field name** field is set to *Mode of delivery*.
1. Select the **Add** button ![Right arrow.](media/forward-button.png) to move the field to the **Selected fields** list.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, in the grid, find the row where the **Field** field is set to *Customer account*, and set the **Criteria** field for that row to *US-001*.
1. Select **Add** to add a row that has the following settings to the grid:

    - **Table:** *Order lines*
    - **Derived table:** *Order lines*
    - **Field:** *Mode of delivery*
    - **Criteria:** *Airwa-Air*

1. Select **OK** to close the dialog box.

> [!NOTE]
> For this business case, order lines for customer *US-001* that use the *Airwa-Air* mode of delivery won't be consolidated across orders. This policy is intended to be used first in a sequence, in cases where shipments for all other modes of delivery are consolidated for this customer.

### Create example policy 2

In this example, you will create a *Hazardous goods* policy that can be used for the following business case:

- The policy will query for a specific filter code (*hazardous*) and a specific mode of delivery (*Airwa-Air*).
- Consolidation with open shipments is turned on.
- Consolidation is done across orders. (In other words, there will be separate shipments per account, warehouse, and so on, but only within the item group that is specified in the query.)

Follow these steps to create the shipment consolidation policy for this business case.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Set the **Policy type** field to *Sales orders*.
1. On the Action Pane, select **New** to create a policy that has the following settings:

    - **Policy name:** *Item type*
    - **Policy description:** *Consolidate the same type of item across orders*

1. Set the **Consolidate with open shipments** option to *Yes*.
1. On the Action Pane, select **Save**.
1. On the **Consolidation fields** FastTab, in the **Remaining fields** list, select the row where the **Field name** field is set to *Mode of delivery*.
1. Select the **Add** button ![Right arrow.](media/forward-button.png) to move the field to the **Selected fields** list.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Joins** tab, expand and select **Tables \> Load details** in the tree.
1. Select **Add table join**.
1. In the grid of relations that appears, find and select the row where the **Relation** field is set to *Warehouse item number (Item number)*, and then select **Select**.
1. On the **Range** tab, select **Add** to add a row that has the following settings to the grid:

    - **Table:** *Warehouse item number*
    - **Derived table:** *Warehouse item number*
    - **Field:** *Code 4*
    - **Criteria:** *Flammable*

1. Select **OK** to close the dialog box.

> [!NOTE]
> For this business case, all order lines where items have a specific filter code (that is, the filter code where the **Code 4** field is set to *Flammable*) will be consolidated with other items of the same type across orders. If there is an open shipment for the same account, warehouse, and group of items, the new lines will be attached to it.

### Create example policy 3

In this example, you will create a *Customers' requirements* policy that can be used for the following business case:

- The policy will query for a specific customer account.
- Consolidation with open shipments is turned on.
- Consolidation is done across orders but is based on customer requisitions. (In other words, multiple orders will be grouped into shipments, based on the same customer requisition number and warehouse.)

Follow these steps to create the shipment consolidation policy for this business case.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Set the **Policy type** field to *Sales orders*.
1. On the Action Pane, select **New** to create a policy that has the following settings:

    - **Policy name:** *CustomerOrderNo*
    - **Policy description:** *Consolidate lines based on customer PO*

1. Set the **Consolidate with open shipments** option to *Yes*.
1. On the Action Pane, select **Save**.
1. On the **Consolidation fields** FastTab, in the **Remaining fields** list, select the row where the **Field name** field is set to *Customer requisition*.
1. Select the **Add** button ![Right arrow.](media/forward-button.png) to move the field to the **Selected fields** list.
1. In the **Remaining fields** list, select the row where the **Field name** field is set to *Mode of delivery*.
1. Select the **Add** button ![Right arrow.](media/forward-button.png) to move the field to the **Selected fields** list.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, find the row where the **Field** field is set to *Customer account*, and set the **Criteria** field for that row to *US-001*.
1. Select **OK** to close the dialog box.

> [!NOTE]
> For this business case, all order lines where sales orders have the same customer requisition number will be consolidated into one shipment, regardless of the sales order number. (The customer requisition number is used as the customer's purchase order \[PO\] number.) If there is an open shipment for the same account, warehouse, and customer requisition, the new lines will be attached to it. This policy can be used if the customer sends additional order lines that have the same PO number several times during a day and wants all the lines to be grouped into one shipment. (In other words, there will be one bill of lading and one packing slip.)

### Create example policy 4

In this example, you will create a *Customers allowing consolidation* policy that can be used for the following business case:

- The policy will query for a specific order pool to identify customers who accept consolidated shipments.
- Consolidation with open shipments is turned off.

- You can override the rule on a sales order by selecting a different order pool.

Follow these steps to create the shipment consolidation policy for this business case.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Set the **Policy type** field to *Sales orders*.
1. On the Action Pane, select **New** to create a policy that has the following settings:

    - **Policy name:** *Order pool*
    - **Policy description:** *Consolidate across orders based on order pool*

1. Leave the **Consolidate with open shipments** option set to *No*.
1. On the Action Pane, select **Save**.
1. On the **Consolidation fields** FastTab, in the **Remaining fields** list, select the row where the **Field name** field is set to *Mode of delivery*.
1. Select the **Add** button ![Right arrow.](media/forward-button.png) to move the field to the **Selected fields** list.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, select **Add** to add a row that has the following settings to the grid:

    - **Table:** *Sales orders*
    - **Derived table:** *Sales orders*
    - **Field:** *Pool*
    - **Criteria:** *ShipCons*

1. Select **OK** to close the dialog box.

> [!NOTE]
> For this business case, all order lines where sales orders belong to the same order pool will be consolidated into one shipment across sales orders for the same account, warehouse, and transportation mode of delivery. Instead of the order pool, you can use any other field to distinguish a group of customers and use the sales order header by default. You can use this approach if the customer, not the warehouse, is driving the need for consolidation. (In the earlier consolidation logic, the warehouse drove the need for consolidation.)

### Create example policy 5

In this example, you will create a *Warehouses allowing consolidation* policy that can be used for the following business case:

- The policy will query for a specific order pool to identify warehouses that can consolidate shipments.
- Consolidation with open shipments is turned off.

Typically, this business case can be addressed by using the default policies. However, you can also manually create similar policies by following these steps.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Set the **Policy type** field to *Sales orders*.
1. On the Action Pane, select **New** to create a policy that has the following settings:

    - **Policy name:** *Cross-order*
    - **Policy description:** *Cross-order consolidation for specific warehouses*

1. Leave the **Consolidate with open shipments** option set to *No*.
1. On the Action Pane, select **Save**.
1. On the **Consolidation fields** FastTab, in the **Remaining fields** field, select the row where the **Field name** field is set to *Mode of delivery*.
1. Select the **Add** button ![Right arrow.](media/forward-button.png) to move the field to the **Selected fields** list.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, find the row where the **Field** field is set to *Warehouse*, and set the **Criteria** field for that row to *61, 63*.
1. Select **OK** to close the dialog box.

### Set the order

Now that you've created all your policies, you must establish the order that they will be applied in. To use a pyramid-like approach, where the policies that have the most conditions are evaluated as having the highest priority, follow these steps.

1. Go to **Warehouse management \> Setup \> Release to warehouse \> Shipment consolidation policies**.
1. Set the **Policy type** field to *Sales orders*.
1. Select each policy that is listed in the left column, and then use the **Move up** and **Move down** buttons on the Action Pane to arrange the policies in the following order:

    1. CustomerMode
    1. Item type
    1. CustomerOrderNo
    1. Order pool
    1. Cross-order
    1. Default

## <a name="example-scenarios"></a> Example scenarios of how to use shipment consolidation policies

The following scenarios illustrate how you could use the shipment consolidation policies that you created while reading this article. Each scenario walks you through a shipment consolidation process that uses shipment consolidation policies during automated or manual release to the warehouse:

- Scenario 1: [Consolidate shipments when they are released to the warehouse by using Automatic release of sales orders](../warehousing/consolidate-shipments-automatic.md)
- Scenario 2: [Consolidate shipments when the shipment consolidation policy is overridden from the Release to warehouse page](../warehousing/consolidate-shipments-release-to-warehouse-override.md)
- Scenario 3: [Consolidate shipments by releasing to warehouse from the outbound load planning workbench](../warehousing/consolidate-shipments-load-planning-workbench.md)
- Scenario 4: [Consolidate shipments by using the shipment consolidation workbench](../warehousing/consolidate-shipments-manual-workbench.md)
- Scenario 5: [Consolidate shipments manually by using the Consolidate shipments page](../warehousing/consolidate-shipments-manual-form.md)

## Related information

- [Shipment consolidation policies overview](about-shipment-consolidation-policies.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
