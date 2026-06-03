---
title: Cross-legal entity fulfillment with distributed order management (DOM) (preview)
description: Learn how to configure and use cross-legal entity fulfillment optimization with DOM in Dynamics 365 Commerce.
author: yufei-huang
ms.date: 06/03/2026
ms.topic: how-to
ms.search.form: DOMParameters, DOMFulfillmentProfiles, DOMIntercompanyVendorMapping, DOMManageRules, RetailStoreLocatorGroup
ms.author: yufeihuang
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2026-04-01
---

# Cross-legal entity fulfillment with distributed order management (DOM) (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [banner](../includes/preview-banner.md)]

This article describes how to set up and use cross-legal entity fulfillment optimization with distributed order management (DOM) in Microsoft Dynamics 365 Commerce.

## Overview

Cross-legal entity fulfillment extends the DOM optimization engine to consider inventory and fulfillment locations across multiple legal entities within your organization. When DOM evaluates the best fulfillment source for a sales order, it can assign a warehouse or store belonging to a different legal entity than the one where the order originated. DOM then automatically creates the required intercompany purchase orders and sales orders to execute the cross-entity fulfillment.

## Business value

Cross-legal entity fulfillment with DOM provides the following benefits:

- **Improved fulfillment efficiency**: Orders can be fulfilled from the best location based on cost, proximity, and inventory availability, even if that location belongs to a different legal entity.
- **Reduced manual intervention**: Automates cross-legal entity order flows, eliminating the need for manual coordination between entities.
- **Enhanced customer experience**: Enables seamless fulfillment across legal entities, ensuring customers receive what they want faster and more reliably.
- **Alignment with global retail needs**: Addresses strong demand from European and global retailers for cross-entity fulfillment capabilities in omnichannel scenarios.

> [!TIP]
> Cross-legal entity fulfillment builds on the cross-company inventory visibility capabilities available in POS. For information about how store associates can view inventory across legal entities, see [Enable cross-company inventory lookup for POS](enable-cross-company-inventory-lookup-pos.md).

## Prerequisites

Before you configure cross-legal entity fulfillment, complete the following prerequisites:

- Enable the DOM configuration key.
- Establish intercompany trading relationships between participating legal entities.
- Release products and make them available in all participating legal entities.
- Ensure warehouses have valid addresses with latitude and longitude values, or configure Azure Maps for address resolution.

## Configuration steps

### Step 1: Enable the DOM configuration key

1. Go to **System administration** > **Setup** > **License configuration**.
1. On the **Configuration keys** tab, expand the **Retail** node.
1. Select the **Distributed Order Management** checkbox.
1. Select **Save**.

> [!NOTE]
> To enable or disable configuration keys, you need maintenance mode. Use Lifecycle Services (LCS) to enable maintenance mode on your environment.

### Step 2: Configure Azure Maps

1. Go to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce shared parameters**.
1. In the left navigation pane, select **Azure Maps**.
1. Set **Enable Azure Maps** to **Yes**.
1. Enter a valid Azure Maps key.
1. Select **Save**.

> [!NOTE]
> Azure Maps is required for DOM to calculate distances between fulfillment locations and delivery addresses. For information on how to obtain a key, see [Manage Azure Maps for your organization](dev-itpro/manage-azure-maps.md).

### Step 3: Configure DOM parameters

1. Go to **Retail and Commerce** > **Distributed order management** > **Setup** > **DOM parameters**.
1. On the **General** tab, configure the following settings:
   - Set **Enable distributed order management** to **Yes**.
   - Set **Confirm Azure Maps usage for DOM** to **Yes**.
   - Set the **Fulfillment data retention period (in days)** value.
   - Set the **DOM logs retention period (in days)** value.
   - Set the **Rejection period (in days)** value.
1. On the **Solver** tab, set the **Solver type** to **Production Solver**.
1. On the **Number sequences** tab, assign number sequences to the required DOM entities.

> [!NOTE]
> The **Production Solver** is required for cross-legal entity fulfillment scenarios. The **Simplified Solver** doesn't support intercompany order creation.

### Step 4: Set up intercompany trading relationships

For each pair of legal entities that participates in cross-entity fulfillment, you must configure intercompany trading relationships.

#### Selling (fulfilling) legal entity

1. In the selling (fulfilling) legal entity, go to **Accounts receivable** > **Customers** > **All customers**.
1. Create or select the intercompany customer record that represents the ordering legal entity.
1. On the **General** FastTab, in the **Intercompany** section, set **Intercompany** to **Yes**.
1. Configure the intercompany sales order policy, such as automatic sales order creation and direct delivery settings.

#### Ordering (source) legal entity

1. In the ordering (source) legal entity, go to **Accounts payable** > **Vendors** > **All vendors**.
1. Create or select the intercompany vendor record that represents the fulfilling legal entity.
1. On the **General** FastTab, in the **Intercompany** section, set **Intercompany** to **Yes**.
1. Configure the intercompany purchase order policy, such as automatic purchase order creation.

> [!NOTE]
> You must configure and link both the intercompany customer and the intercompany vendor for the same pair of legal entities. Ensure that the trading policies allow automatic intercompany order creation.

### Step 5: Configure DOM intercompany vendor mapping

The intercompany vendor mapping tells DOM which vendor to use when creating purchase orders for cross-entity fulfillment.

1. Go to **Retail and Commerce** > **Distributed order management** > **Setup** > **DOM Intercompany vendor mapping**.
1. Select **New**.
1. In the **Source legal entity** field, select the legal entity where the original sales order exists.
1. In the **Target legal entity** field, select the legal entity that fulfills the order.
1. In the **Intercompany vendor** field, select the vendor account (in the source legal entity) that represents the fulfilling legal entity.
1. Repeat for each legal entity pair.
1. Select **Save**.

### Step 6: Configure fulfillment groups

Fulfillment groups define the locations (warehouses and stores) that DOM can consider for fulfillment. For cross-legal entity scenarios, include locations from all participating legal entities.

1. Go to **Retail and Commerce** > **Channel setup** > **Fulfillment groups**.
1. Select **New** and enter a name and description.
1. Select **Add line** or **Add lines** to add locations from multiple legal entities.
1. For each location, specify whether it can be used for **Shipping**, **Pickup**, or both.
1. Select **Save**.

> [!TIP]
> Create a comprehensive fulfillment group that includes all shipping-capable warehouses across your legal entities and then associate it with your DOM fulfillment profile. This concept is the same fulfillment group concept used for [cross-company inventory lookup in POS](enable-cross-company-inventory-lookup-pos.md#configure-fulfillment-groups-with-cross-entity-warehouses).

### Step 7: Configure DOM rules

1. Go to **Retail and Commerce** > **Distributed order management** > **Setup** > **Manage rules**.
1. Configure rules based on your business requirements. Common rules for cross-entity scenarios include:
   - **Fulfillment location priority rule**: Define priority across locations in different legal entities.
   - **Maximum distance rule**: Limit fulfillment to locations within a specified distance.
   - **Minimum inventory rule**: Reserve minimum stock at each location.
   - **Partial orders rule**: Allow or restrict order splitting across locations and legal entities.

For more information, see [DOM rules](dom-rules.md).

### Step 8: Set up DOM fulfillment profiles

The fulfillment profile is the central configuration that ties legal entities, rules, modes of delivery, and sales origins together.

1. Go to **Retail and Commerce** > **Distributed order management** > **Setup** > **Fulfillment profiles**.
1. Select **New**.
1. Enter a **Profile** name and **Description**.
1. Set the **Auto apply result** option as needed.
1. On the **Legal entities** FastTab, select **Add** and add all legal entities that participate in cross-entity fulfillment.
1. On the **Rules** FastTab, select **Add** and link the DOM rules you configured in [Step 7: Configure DOM rules](#step-7-configure-dom-rules).
1. Optionally, assign a **Fulfillment group** to restrict which warehouses DOM considers.
1. On the action pane, on the **Setup** tab, select **Modes of delivery**:
   - Select **New** for each legal entity and mode of delivery combination.
1. On the action pane, on the **Setup** tab, select **Sales order origins**:
   - Select **New** for each legal entity and sales origin combination.
1. Set **Enable profile** to **Yes**.
1. Select **Save**.

> [!IMPORTANT]
> Add all the legal entities that should participate in a cross-entity fulfillment to the fulfillment profile. If you don't add a legal entity, DOM doesn't consider its locations during optimization.

### Step 9: Configure DOM cost configuration

> [!NOTE]
> This step is optional.

To enable cost-based optimization across legal entities:

1. Go to **Retail and Commerce** > **Distributed order management** > **Setup** > **Cost configuration**.
1. Define cost factors such as shipping costs, handling costs, and intercompany transfer costs.
1. Associate costs with specific locations or groups.

For more information, see [DOM cost configuration](dom-costs.md).

### Step 10: Set up the DOM processor batch job

1. Go to **Retail and Commerce** > **Distributed order management** > **Batch processing** > **DOM processor job setup**.
1. On the **Parameters** FastTab, in the **Fulfillment profile** field, select the profile you configured.
1. On the **Run in the background** FastTab, select a **Batch group**.
1. Enter a **Task description**.
1. Select **Recurrence** and configure the job schedule.
1. Select **OK**.

## How cross-legal entity fulfillment works

After you complete the configuration, the cross-legal entity fulfillment process works as follows:

1. A sales order is created in the source legal entity (for example, through POS or e-commerce).
1. DOM runs and evaluates all eligible fulfillment locations across legal entities.
1. DOM identifies the optimal fulfillment location, which might be in a different legal entity.
1. If the selected location is in a different legal entity, DOM:
   - Creates an **intercompany purchase order** in the source legal entity.
   - Creates an **intercompany sales order** in the fulfilling legal entity.
1. The fulfilling legal entity processes the intercompany sales order (pick, pack, ship).
1. Upon shipment, the intercompany purchase order in the source legal entity is updated.
1. The original sales order is marked as fulfilled.

## Fulfillment scenarios

### Full fulfillment

The fulfilling legal entity ships the entire ordered quantity. The intercompany sales order, purchase order, and original sales order are all updated to reflect completed delivery.

### Partial fulfillment

The fulfilling legal entity ships only a part of the ordered quantity. The delivery remainder is updated across the intercompany chain (intercompany sales order > purchase order > original sales order). DOM can reassign the remaining quantity in a subsequent run.

### Rejection

The fulfilling location rejects the fulfillment assignment. DOM marks the line as rejected and attempts to reassign it to an alternative location in the next DOM run. Reassignment options include:

- A different warehouse in the same legal entity.
- A warehouse in a different legal entity.
- The same vendor but a different warehouse.

### Cancellation

When the delivery remainder is set to zero on the intercompany sales order, the cancellation cascades through the intercompany chain. The behavior of the original sales order depends on the **Accounts receivable** parameters configuration.

## Validation checklist

After completing the configuration, verify the setup by confirming the following validation checks:

| Step | Validation |
| ---- | ---------- |
| 1 | DOM parameters show **Enabled** status. |
| 2 | Fulfillment profile lists all participating legal entities. |
| 3 | Intercompany vendor mapping has entries for each legal entity pair. |
| 4 | Intercompany customer/vendor records are properly linked. |
| 5 | Fulfillment group includes warehouses from all legal entities. |
| 6 | A test sales order is correctly assigned to a cross-entity location by DOM. |
| 7 | Intercompany PO and SO are automatically created after DOM applies the result. |

## Troubleshoot

| Issue | Resolution |
| ----- | ---------- |
| DOM doesn't consider locations in other legal entities. | Verify that you add all legal entities to the fulfillment profile and include warehouses in the fulfillment group. |
| Intercompany orders aren't created after DOM run. | Check the DOM intercompany vendor mapping and ensure intercompany trading policies allow automatic order creation. |
| DOM run fails with solver errors. | Ensure the **Production Solver** is selected and properly licensed. The **Simplified Solver** doesn't support cross-entity scenarios. |
| Distance calculation errors. | Verify that Azure Maps is configured and that warehouse addresses have valid geographic information. |
| Rejected lines aren't reassigned. | Check the rejection period in DOM parameters. Lines within the rejection period aren't reassigned to the same location. |

## Related features

Cross-legal entity fulfillment works alongside other cross-company capabilities in Dynamics 365 Commerce:

- [Enable cross-company inventory lookup for POS](enable-cross-company-inventory-lookup-pos.md): Allows store associates to view inventory across legal entities in POS before orders are placed.
- [Intercompany trade setup](../supply-chain/sales-marketing/intercompany-trade-set-up.md): Provides the foundational intercompany trading configuration used by DOM.

## More resources

- [DOM overview](dom.md)
- [Set up DOM](dom-set-up.md)
- [DOM rules](dom-rules.md)
- [DOM cost configuration](dom-costs.md)
- [DOM processing](dom-processing.md)
- [Results of DOM runs](dom-runs-results.md)
- [Clean up DOM fulfillment plans and logs](dom-clean-up.md)
- [DOM extensibility](dom-extensibility.md)
- [DOM limitations](dom-limitations.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
