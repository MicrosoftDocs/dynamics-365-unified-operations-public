---
title: Backflush costing
description: Learn about the concept of backflush costing that is used for Lean manufacturing, including an outline on configuring backflush costing.
author: prasungoel
ms.author: prasungoel
ms.reviewer: kamaybac
ms.search.form: LeanCosting, LeanCostingTimeBucket
ms.topic: how-to
ms.date: 01/31/2025
ms.custom: 
  - bap-template
---

# Backflush costing

[!include [banner](../includes/banner.md)]

This article introduces the concept of backflush costing that is used for Lean manufacturing.

Costing for Lean manufacturing enables the production flow to use the cost accumulation method that is known as backflush costing. In the backflush costing method, the direct materials that are consumed are accumulated in the production flow's work in progress (WIP) cost account. The standard cost inventory model group is used. The products that are received from the production flow are deducted from WIP at their standard cost. The main difference between backflush costing and standard cost is that, for backflush costing, variances aren't calculated per kanban or finished product. Instead, variances are calculated per production flow over a period. This method introduces a truly lean concept for reporting material consumption. Dedicated picked quantities of material aren't reported to a kanban or production order. Instead, full batches or handling units are staged to the production flow. After the batches or handling units are registered as empty, they're declared consumed. Advanced consumption might be used, depending on the [configuration of the production flow](../production-control/lean-manufacturing-modeling-lean-organization.md). Before advanced consumption can be used, organizations must allow themselves to make material vanish in the WIP of the production flow. The periodic backflush costing determines the effective value of WIP to the end of the period. This determination is based on the kanban handling units and the kanban job status. Deviations between the effective values and the actual WIP values per cost group and item are accounted and shown as variances.

## Configuring backflush costing

To enable costing, you must complete the following setup:

- **Set up WIP accounts for the production group and production flow.** The WIP accounts for the production flow are specified in the production group. The backflush costing production flow calculates variances as the difference in the WIP value before and after backflush costing is run for each production flow. Therefore, we recommend that you create a WIP account for every production flow.
- **Assign a cost category to the resource group.** You must assign a cost category to the run-time category of the work cell. To determine variances by activity, you should create a cost category for every work cell. The cost categories for setup and quantity aren't considered in costing for lean manufacturing. The WIP accounts per resource group are ignored in backflush costing. For subcontracted activities, no cost category is required. The cost group that is assigned to the active service is used instead.
- **Assign cost groups.** To enable segmentation of the cost contribution in a production flow, you must assign cost groups by cost group type:
    - *Direct material cost group* – Direct material requires a cost group that identifies the material category for costing. This cost group enables an aggregated view of cost, WIP, and variances by direct material.
    - *Direct manufacturing cost group* – The direct manufacturing cost group captures the direct cost contribution of operational resources to the production flow. This cost group enables an aggregated view of cost, WIP, and variances by direct manufacturing cost.
    - *Indirect cost group* – The indirect cost group is required in order to calculate the indirect cost contribution to the production flow. This cost group enables an aggregated view of cost, WIP, and variances by indirect cost.
    - *Direct outsourcing cost group* – The cost group for the services enables an aggregated view of assigned cost and WIP, and determines the cost variances of the subcontracted services.
    - *Cost group for a finished product* – Finished products require a cost group that identifies the product category for costing. This cost group enables an aggregated view of cost, WIP, and variances by product category. The standard cost for products is calculated by using the cost calculation that is based on the bill of materials (BOM), and either the production flow and kanban rules or the route.

### Costing sheet

The costing sheet models the cost structure for the company and is built by the cost groups to classify the cost. The costing sheet has various forms. It shows cost information according to the structure that is designed in it. In the costing sheet, you also define the formula that is used to calculate the indirect cost. The calculation formula can be based on quantities, weight, volume, or value.

- **Define a costing version.** In the costing version, the company defines how the cost should be maintained. A costing version can contain a set of standard cost records or a set of planned cost records, depending on the costing type that is assigned to the costing version. The costing version that is used for costing for Lean manufacturing must be based on standard cost.
- **Assign an inventory model group for released products.** All products that are related to the production flow must be assigned to an inventory model group that uses the *Standard cost* inventory model group. Standard cost is maintained per site and activation date. For product masters, the inventory model group can be selected if the cost is maintained per variant or product master.
- **By definition, subcontracted services are non-inventoried services.** Subcontracted activities have no inventory model group. To cost a subcontracted activity correctly, you must make sure that the service activity belongs to an inventory model group where the inventory policy is set to *Stocked product = False*.

For output products, cost calculation that is based on the production flow requires that a standard cost be maintained for the services that are related to subcontracted activities. The cost group that is assigned to the services is used to determine the cost variances of the subcontracted activity.

## Cost calculation for Lean manufacturing

For products that are supplied out of a production flow, the BOM calculation must be based on either a route version or a production flow. The BOM calculation calculates the cost of a product and the related breakdown to the resources and material that are required in order to build the product. The deduction from the WIP account for the production flow is done by using the breakdown of a product by item and cost group.

### Calculation that is based on the production flow

Lean manufacturing for Dynamics 365 Supply Chain Management is independent of routes. The cost calculation for products that are supplied from a production flow can be based on the production flow itself. Before the calculation can be done, a kanban rule must be created that supplies the product out of the production flow. If a product can be supplied from multiple production flows at the same site on the calculation date, you can select the production flow for the BOM calculation. On the **Default production flow** page, you can configure a default production flow for each item. If multiple kanban rules exist for the same product in the same production flow that is active on the calculation date, the calculation selects the first kanban rule that is active for the calculation.

### Calculation that is based on the route

Calculation that is based on a route is as valid as calculation that is based on a production flow. However, calculation that is based on a route doesn't use the costing for Lean manufacturing functionality. The route should use resource requirements for resource groups. To avoid systematic variances, it should also use the same work cells, or at least the same cost categories. Again, you should avoid cost categories for setup and quantity. They don't help calculate the cost in a more granular breakdown than Lean manufacturing cost backflushing. To determine which option (production flow or route) you should use to calculate the cost, consider the results of the cost breakdown. The version that comes closer to reality and produces fewer variances overall is the better option. In a Lean manufacturing environment where a product is supplied by a single production flow and a single kanban rule, the calculation that is based on the production flow is probably more accurate. For a product that can be supplied by Lean manufacturing and production orders on the same site, or that can have multiple production flows or multiple kanban rules in the same flow, a calculation might be more accurate if it's based on a route version that is built specifically for the cost calculation, not for the production. The production flow calculation must be used to calculate products that involve subcontracting. The cost models for subcontracting via production orders and subcontracting in Lean manufacturing are using two different approaches. Lean manufacturing introduces a new cost group type, *Direct outsourcing*, to calculate subcontracted services.

## Material consumption

When material is consumed from inventory to WIP, the cost of material is added to WIP at its actual standard cost for a cost group. This operation occurs under the following conditions:

- Kanban issues are posted for kanban picking lines that update inventory.
- Transfer jobs are completed that update inventory on pick but not receipt (Transfer of material from inventory to WIP).

## Receiving products from the production flow

Products are received from the production flow under the following conditions:

- Process jobs are completed that have **Update inventory on receipt** set to *Yes*.
- Transfer jobs are completed that update inventory on receipt, but that have **Update inventory on pick set** to *No* (Transfer from WIP to inventory). This option lets you receive any products out of a production flow independently of the BOM and route configuration. The process just follows the physical flows. This option is especially suitable for receiving by-products, co-products, or scrap out of a production flow, and for correcting the cost balance of the production flow WIP accordingly.

Products that are received from the production flow are deducted from WIP.

## Products in WIP

The WIP model of Lean manufacturing lets you use the kanban handling unit status to manage the material, semi-finished products, and finished products that are part of WIP.

- **Assigned** - The kanban can have consumed material that is accounted in WIP.
- **Received** - If the kanban refers to a last activity where **Update inventory on receipt** is set to *No*, it represents a full handling unit of a product or a semi-finished product that isn't registered to inventory.

Material in WIP isn't visible in inventory on-hand overviews. However, it's visible in the kanban quantity overviews.

## Consuming products in WIP

Products in WIP are consumed when the corresponding kanban handling units are emptied. A kanban empty signal doesn't produce an active costing transaction but will take effect when the next backflush costing is run. Emptied kanban handling units are no longer accounted as on-hand and therefore calculated as consumed within the period.

### Automatic empty registration

Scheduled or event kanbans can be set to automatic empty registration in the kanban rule:

- **When handling units are received** - By default, for scheduled kanbans, the material is declared as consumed when the last job of the kanban is completed. For fixed quantity kanbans, this option is recommended only for single-bin kanbans, because it returns the card to the source of demand whenever a kanban is received at the final destination.
- **When source requirement is registered** - This option is available only for event kanbans and is the default option for them. In connection to WIP, this option is useful for keeping WIP clean, because kanbans for components in WIP are automatically emptied, and therefore consumed from WIP, when the parent kanban is prepared.

In conclusion, kanban handling units can be assigned (= in process), received (=full), or emptied. There's no partial emptying. Therefore, to enable accurate registration of consumption, it's important that you limit the product quantities of a kanban so that they're less than the consumption per period. Products that are moved to the shop floor in large batches that cover days or weeks of demand shouldn't be consumed to WIP. Instead, these products should be kept in inventory.

## Backflush costing steps

You should run backflush costing to periodically value the WIP and produce an end-of-period status that calculates the variances of material, labor, and indirect costs. The calculated variances are posted to the variance accounts. In the backflush costing process, all production flows of the legal entity are used in the same batch run. When backflush costing is run in a batch, the processing might be multi-threaded by production flow. The backflush period is defined by an end date. You can't post new transactions to a date when a backflush costing calculation has been run. You should never run backflush costing for the current date before the day is actually over. Backflush costing performs the following steps.

1. Determine the unused quantities in the production flow as of the period's end date. After the backflush costing is run, you can view the unused quantities on the date of the costing run in the **Unused quantities** dialog box.
2. Calculate the production flow's net realized usage over the period.
3. Clear the WIP from the realized resource consumption and products.
4. Calculate production variances to standard cost for the period.

    **For consumed components for the period:**
    - Financially update the net realized quantities of material that the production flow consumed over the period. The system processes in first in, first out (FIFO) order on the individual inventory transactions as to financially update the physically updated transactions for the production flow, until the net realized quantities for the period are reached.
    - Transactions are financially split to map the exact consumed quantities.
    - Unused quantities in the production flow WIP remain in physically updated status.

    **For production completed quantities of the period:**
    - Financially update the inventory transactions for the completed quantities for the period.

    **For the conversion cost:**
    - The applied conversion cost transactions (route transactions) that were recorded for the period are financially updated.
    - All direct manufacturing cost is financially updated. All kanban process jobs that are completed during the period are accumulated.
    - All indirect cost calculated for the consumed material within the period is calculated and deducted from WIP. The remaining indirect cost is posted as a variance.

5. Calculate the production variances to standard cost. The variance is calculated per cost group.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
