---
# required metadata

title: Cross-legal entity fulfillment with Distributed Order Management (DOM)
description: Learn how to configure and use cross-legal entity fulfillment optimization with DOM in Dynamics 365 Commerce.
author: josaw1
ms.date: 05/17/2026
ms.topic: how-to
ms.search.form: DOMParameters, DOMFulfillmentProfiles, DOMIntercompanyVendorMapping, DOMManageRules, RetailStoreLocatorGroup
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2026-04-01

---

# Cross-legal entity fulfillment with Distributed Order Management (DOM)

[!include [banner](includes/banner.md)]

This article describes how to set up and use cross-legal entity fulfillment optimization with Distributed Order Management (DOM) in Microsoft Dynamics 365 Commerce.

## Overview

Cross-legal entity fulfillment extends the DOM optimization engine to consider inventory and fulfillment locations across multiple legal entities within your organization. When DOM evaluates the best fulfillment source for a sales order, it can assign a warehouse or store belonging to a different legal entity than the one where the order originated. DOM then automatically creates the required intercompany purchase orders and sales orders to execute the cross-entity fulfillment.

## Business value

Cross-legal entity fulfillment with DOM provides the following benefits:

- **Improved fulfillment efficiency** – Orders can be fulfilled from the best location based on cost, proximity, and inventory availability, even if that location belongs to a different legal entity.
- **Reduced manual intervention** – Automates cross-legal entity order flows, eliminating the need for manual coordination between entities.
- **Enhanced customer experience** – Enables seamless fulfillment across legal entities, ensuring customers receive what they want faster and more reliably.
- **Alignment with global retail needs** – Addresses strong demand from European and global retailers for cross-entity fulfillment capabilities in omnichannel scenarios.

> [!TIP]
> Cross-legal entity fulfillment builds on the cross-company inventory visibility capabilities available in POS. For information about how store associates can view inventory across legal entities, see [Enable cross-company inventory lookup for POS](enable-cross-company-inventory-lookup-pos.md).

## Prerequisites

Before you configure cross-legal entity fulfillment, the following prerequisites must be in place:

- The DOM configuration key must be enabled.
- Intercompany trading relationships must be established between participating legal entities.
- Products must be released and available in all participating legal entities.
- Warehouses must have valid addresses with latitude and longitude values (or Azure Maps must be configured for address resolution).

## Configuration steps

### Step 1: Enable the DOM configuration key

1. Go to **System administration \> Setup \> License configuration**.
2. On the **Configuration keys** tab, expand the **Retail** node.
3. Select the **Distributed Order Management** checkbox.
4. Select **Save**.

> [!NOTE]
> Enabling or disabling configuration keys requires maintenance mode. Use Lifecycle Services (LCS) to enable maintenance mode on your environment.

### Step 2: Configure Azure Maps

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
2. In the left navigation pane, select **Azure Maps**.
3. Set the **Enable Azure Maps** option to **Yes**.
4. Enter a valid Azure Maps key.
5. Select **Save**.

> [!NOTE]
> Azure Maps is required for DOM to calculate distances between fulfillment locations and delivery addresses. For information on how to obtain a key, see [Manage Azure Maps for your organization](dev-itpro/manage-azure-maps.md).

### Step 3: Configure DOM parameters

1. Go to **Retail and Commerce \> Distributed order management \> Setup \> DOM parameters**.
2. On the **General** tab, configure the following settings:
   - Set **Enable distributed order management** to **Yes**.
   - Set **Confirm Azure Maps usage for DOM** to **Yes**.
   - Set the **Fulfillment data retention period (in days)** value.
   - Set the **DOM logs retention period (in days)** value.
   - Set the **Rejection period (in days)** value.
3. On the **Solver** tab, set the **Solver type** to **Production Solver**.
4. On the **Number sequences** tab, assign number sequences to the required DOM entities.

> [!IMPORTANT]
> The **Production Solver** is required for cross-legal entity fulfillment scenarios. The Simplified Solver doesn't support intercompany order creation.

### Step 4: Set up intercompany trading relationships

For each pair of legal entities that participates in cross-entity fulfillment, you must configure intercompany trading relationships.

#### In the selling (fulfilling) legal entity

1. Go to **Accounts receivable \> Customers \> All customers**.
2. Create or select the intercompany customer record that represents the ordering legal entity.
3. On the **General** FastTab, in the **Intercompany** section, set **Intercompany** to **Yes**.
4. Configure the intercompany sales order policy (for example, automatic sales order creation and direct delivery settings).

#### In the ordering (source) legal entity

1. Go to **Accounts payable \> Vendors \> All vendors**.
2. Create or select the intercompany vendor record that represents the fulfilling legal entity.
3. On the **General** FastTab, in the **Intercompany** section, set **Intercompany** to **Yes**.
4. Configure the intercompany purchase order policy (for example, automatic purchase order creation).

> [!NOTE]
> Both the intercompany customer and the intercompany vendor must be configured and linked for the same pair of legal entities. Ensure that the trading policies allow automatic intercompany order creation.

### Step 5: Configure DOM intercompany vendor mapping

The intercompany vendor mapping tells DOM which vendor to use when creating purchase orders for cross-entity fulfillment.

1. Go to **Retail and Commerce \> Distributed order management \> Setup \> DOM Intercompany vendor mapping**.
2. Select **New**.
3. In the **Source legal entity** field, select the legal entity where the original sales order exists.
4. In the **Target legal entity** field, select the legal entity that fulfills the order.
5. In the **Intercompany vendor** field, select the vendor account (in the source legal entity) that represents the fulfilling legal entity.
6. Repeat for each legal entity pair.
7. Select **Save**.

### Step 6: Configure fulfillment groups

Fulfillment groups define the locations (warehouses and stores) that DOM can consider for fulfillment. For cross-legal entity scenarios, include locations from all participating legal entities.

1. Go to **Retail and Commerce \> Channel setup \> Fulfillment groups**.
2. Select **New** and enter a name and description.
3. Select **Add line** or **Add lines** to add locations from multiple legal entities.
4. For each location, specify whether it can be used for **Shipping**, **Pickup**, or both.
5. Select **Save**.

> [!TIP]
> Create a comprehensive fulfillment group that includes all shipping-capable warehouses across your legal entities, then associate it with your DOM fulfillment profile. This is the same fulfillment group concept used for [cross-company inventory lookup in POS](enable-cross-company-inventory-lookup-pos.md#configure-fulfillment-groups-with-cross-entity-warehouses).

### Step 7: Configure DOM rules

1. Go to **Retail and Commerce \> Distributed order management \> Setup \> Manage rules**.
2. Configure rules based on your business requirements. Common rules for cross-entity scenarios include:
   - **Fulfillment location priority rule** – Define priority across locations in different legal entities.
   - **Maximum distance rule** – Limit fulfillment to locations within a specified distance.
   - **Minimum inventory rule** – Reserve minimum stock at each location.
   - **Partial orders rule** – Allow or restrict order splitting across locations and legal entities.

For more information about DOM rules, see [DOM rules](dom-rules.md).

### Step 8: Set up DOM fulfillment profiles

The fulfillment profile is the central configuration that ties legal entities, rules, modes of delivery, and sales origins together.

1. Go to **Retail and Commerce \> Distributed order management \> Setup \> Fulfillment profiles**.
2. Select **New**.
3. Enter a **Profile** name and **Description**.
4. Set the **Auto apply result** option as needed.
5. On the **Legal entities** FastTab, select **Add** and add all legal entities that participate in cross-entity fulfillment.
6. On the **Rules** FastTab, select **Add** and link the rules you configured in Step 7.
7. Optionally, assign a **Fulfillment group** to restrict which warehouses DOM considers.
8. On the Action Pane, on the **Setup** tab, select **Modes of delivery**:
   - Select **New** for each legal entity and mode of delivery combination.
9. On the Action Pane, on the **Setup** tab, select **Sales order origins**:
   - Select **New** for each legal entity and sales origin combination.
10. Set **Enable profile** to **Yes**.
11. Select **Save**.

> [!IMPORTANT]
> All legal entities that should participate in cross-entity fulfillment must be added to the fulfillment profile. If a legal entity isn't added, DOM doesn't consider its locations during optimization.

### Step 9: Configure DOM cost configuration (optional)

To enable cost-based optimization across legal entities:

1. Go to **Retail and Commerce \> Distributed order management \> Setup \> Cost configuration**.
2. Define cost factors such as shipping costs, handling costs, and intercompany transfer costs.
3. Associate costs with specific locations or groups.

For more information, see [DOM cost configuration](dom-costs.md).

### Step 10: Set up the DOM processor batch job

1. Go to **Retail and Commerce \> Distributed order management \> Batch processing \> DOM processor job setup**.
2. On the **Parameters** FastTab, in the **Fulfillment profile** field, select the profile you configured.
3. On the **Run in the background** FastTab, select a **Batch group**.
4. Enter a **Task description**.
5. Select **Recurrence** and configure the job schedule.
6. Select **OK**.

## How cross-legal entity fulfillment works

After configuration is complete, the cross-legal entity fulfillment process works as follows:

1. A sales order is created in the source legal entity (for example, through POS or e-commerce).
2. DOM runs and evaluates all eligible fulfillment locations across legal entities.
3. DOM identifies the optimal fulfillment location, which may be in a different legal entity.
4. If the selected location is in a different legal entity, DOM:
   - Creates an **intercompany purchase order** in the source legal entity.
   - Creates an **intercompany sales order** in the fulfilling legal entity.
5. The fulfilling legal entity processes the intercompany sales order (pick, pack, ship).
6. Upon shipment, the intercompany purchase order in the source legal entity is updated.
7. The original sales order is marked as fulfilled.

## Fulfillment scenarios

### Full fulfillment

The fulfilling legal entity ships the entire ordered quantity. The intercompany sales order, purchase order, and original sales order are all updated to reflect completed delivery.

### Partial fulfillment

The fulfilling legal entity ships only part of the ordered quantity. The delivery remainder is updated across the intercompany chain (intercompany sales order → purchase order → original sales order). DOM can reassign the remaining quantity in a subsequent run.

### Rejection

The fulfilling location rejects the fulfillment assignment. DOM marks the line as rejected and attempts to reassign it to an alternative location in the next DOM run. Reassignment options include:

- A different warehouse in the same legal entity.
- A warehouse in a different legal entity.
- The same vendor but a different warehouse.

### Cancellation

When the delivery remainder is set to zero on the intercompany sales order, the cancellation cascades through the intercompany chain. The behavior of the original sales order depends on the Accounts receivable parameters configuration.

## Validation checklist

After completing the configuration, verify the setup by confirming the following:

| Step | Validation |
|------|-----------|
| 1 | DOM parameters show **Enabled** status. |
| 2 | Fulfillment profile lists all participating legal entities. |
| 3 | Intercompany vendor mapping has entries for each legal entity pair. |
| 4 | Intercompany customer/vendor records are properly linked. |
| 5 | Fulfillment group includes warehouses from all legal entities. |
| 6 | A test sales order is correctly assigned to a cross-entity location by DOM. |
| 7 | Intercompany PO and SO are automatically created after DOM applies the result. |

## Troubleshooting

| Issue | Resolution |
|-------|-----------|
| DOM doesn't consider locations in other legal entities. | Verify that all legal entities are added to the fulfillment profile and that warehouses are included in the fulfillment group. |
| Intercompany orders aren't created after DOM run. | Check the DOM intercompany vendor mapping and ensure intercompany trading policies allow automatic order creation. |
| DOM run fails with solver errors. | Ensure the **Production Solver** is selected and properly licensed. The Simplified Solver doesn't support cross-entity scenarios. |
| Distance calculation errors. | Verify that Azure Maps is configured and that warehouse addresses have valid geographic information. |
| Rejected lines aren't reassigned. | Check the rejection period in DOM parameters. Lines within the rejection period aren't reassigned to the same location. |

## Related features

Cross-legal entity fulfillment works alongside other cross-company capabilities in Dynamics 365 Commerce:

- [Enable cross-company inventory lookup for POS](enable-cross-company-inventory-lookup-pos.md) – Allows store associates to view inventory across legal entities in POS before orders are placed.
- [Intercompany trade setup](../supply-chain/sales-marketing/intercompany-trade-set-up.md) – Provides the foundational intercompany trading configuration used by DOM.

## Additional resources

[DOM overview](dom.md)

[Set up DOM](dom-set-up.md)

[DOM rules](dom-rules.md)

[DOM cost configuration](dom-costs.md)

[DOM processing](dom-processing.md)

[Results of DOM runs](dom-runs-results.md)

[Clean up DOM fulfillment plans and logs](dom-clean-up.md)

[DOM extensibility](dom-extensibility.md)

[DOM limitations](dom-limitations.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
