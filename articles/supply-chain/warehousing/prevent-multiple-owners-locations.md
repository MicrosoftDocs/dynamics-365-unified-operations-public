---
title: Prevent multiple owners in warehouse locations
description: Learn about the Prevent multiple owners feature, which prevents inventory from different owners from being stored in the same warehouse location. This article includes configuration guidance and operational considerations.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSLocationProfile, WHSWorkProcessTemplate, WHSPutAwayTemplate
ms.topic: how-to
ms.date: 07/27/2026
ms.custom:
  - bap-template
---

# Prevent multiple owners in warehouse locations

[!INCLUDE [banner](../includes/banner.md)]

## Overview

The *prevent multiple owners* feature prevents inventory owned by different legal entities or consigned from different parties from being stored in the same warehouse location. It helps you enforce inventory owner segregation in your warehouse by making sure that all the items in a given location have the same owner. This feature is essential for warehouses that manage inventory on behalf of multiple owners, such as third-party logistics (3PL) operations, consignment warehouses, warehouses running in [warehouse management only mode](wms-only-mode-overview.md), or warehouses supporting multiple legal entities with distinct ownership tracking requirements.

### What is inventory owner tracking?

In Dynamics 365 Supply Chain Management, the **Owner** field in the inventory dimensions tracks inventory ownership of each item. This field identifies which legal entity or external party owns a specific inventory lot, enabling proper tracking and settlement in multi-owner scenarios. Location profiles that use the **Prevent multiple owners** constraint enforce rules that make sure that all inventory items in a location share the same **Owner** value.

### When to use this feature

Consider using the *prevent multiple owners* feature in any of the following scenarios:

- **Warehouse management only (WMS-only) mode** – You manage inventory for multiple legal entities or external parties and need to enforce segregation of ownership at the location level.
- **Multi-owner warehouses** – You manage physical inventory owned by multiple legal entities and need to segregate their stock.
- **Third-party logistics (3PL)** – You manage consigned inventory from multiple suppliers or customers and need to prevent cross-mingling.
- **Consignment operations** – You track and manage consigned inventory separately from owned inventory and need location-level guarantees.
- **Regulatory compliance** – Your industry or operational model requires documented segregation of ownership.

### Benefits

The *prevent multiple owners* feature provides the following benefits:

- **Prevents ownership disputes** – Eliminates ambiguity about which owner inventory belongs to when stock is physically co-located.
- **Operational clarity** – Warehouse operators receive clear, immediate feedback when they attempt to violate the constraint.
- **Compliance support** – Simplifies audit trails and regulatory compliance by enforcing segregation rules consistently.
- **Automated constraints** – Reduces the need for manual workarounds or bypass procedures.

## How the feature works

### Core behavior

When you turn on the **Prevent multiple owners** constraint for a location profile, the system enforces the following rules for locations that use that profile:

- Each location can only store inventory for a single owner.
- An empty (undefined) owner value is treated as a distinct owner, so inventory with an empty owner value can only be mixed with other inventory that also has an empty owner value.

### When the system evaluates ownership

The system evaluates the **Prevent multiple owners** constraint at three key stages:

1. **Putaway operations** – When the system selects a location for received or internal-order inventory, it confirms that the location's current inventory (if any) belongs to the same owner.
1. **Manual location changes** – When a warehouse operator manually reassigns inventory to a new location using a mobile device, the system verifies the owner compatibility before it allows the move.
1. **Replenishment operations** – When the system triggers replenishment to refill a picking location, it respects the owner constraint by selecting inventory of the same owner.

### Error handling and operator feedback

If a manual location change violates the constraint, the system rejects the change with a label-driven error before any posting occurs.

If automatic location selection fails due to owner mismatches, the system triggers immediate replenishment to build new capacity for the incoming owner's inventory.

When an operator attempts to putaway inventory to a location that violates the **Prevent multiple owners** constraint, the mobile device displays a dedicated error message. The message informs the operator that the location already contains inventory owned by a different party, and suggests alternative locations.

### Relationship to other mixing constraints

The **Prevent multiple owners** constraint works alongside the other mixing constraints available for location profiles:

- **Allow mixed items** – Controls whether different products can coexist in a location.
- **Allow mixed batches** – Controls whether different batch lots can coexist in a location.
- **Allow mixed status** – Controls whether inventory with different statuses (such as *Available*, *On-order*, or *Damaged*) can coexist in a location.

The system evaluates all constraints together. If any constraint is violated, the location isn't considered as a putaway candidate.

## Prerequisites

To use the *prevent multiple owners* feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.49 or later.
- Your warehouse must be enabled for warehouse management processes (WMS) and use location-directive-driven operations.
- The tracking dimension groups that apply to the relevant items must include the **Owner** dimension.

## Configure a location profile to prevent multiple owners

Enable the owner-segregation constraint as needed for each relevant location profile. After you complete this procedure, any location that uses the updated profile is subject to the owner-mixing checks described in the [How the feature works](#how-the-feature-works) section, both during putaway and during manual location changes. Repeat this procedure for each location profile that should enforce single-owner storage.

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Location profiles**.
1. In the list of location profiles, select the profile you want to configure. If it doesn't exist, select **New** to create one.
1. On the **Action Pane**, select **Edit**.
1. On the **General** FastTab, set **Prevent multiple owners** to *Yes* to enforce single-owner segregation for locations that use this profile.

    > [!NOTE]
    > The **Prevent multiple owners** option is independent of the other mixing constraints (**Allow mixed items**, **Allow mixed batches**, **Allow mixed status**). You can freely combine these constraints as needed.

    > [!IMPORTANT]
    > When you change **Prevent multiple owners** from *No* to *Yes* for a location profile that already contains inventory, the system checks to make sure that no existing inventory violates the new constraint. If it detects violations, you see an error dialog that lists locations and their current inventory owners. Perform one or more of the following actions based on the content of the error message. Then try to enable the option again.
    >
    > - **Relocate inventory** – Move inventory with different owners to separate locations manually or according to a transfer order.
    > - **Reserve capacity** – Create new locations dedicated to specific owners.
    > - **Schedule the change** – Enable the constraint during a maintenance window when relevant locations are empty.

1. Select **Save**.

## Set up the Inventory owner dimension on a tracking dimension group

Inventory ownership is tracked through the **Owner** dimension on the tracking dimension group that is assigned to your items. If this dimension isn't active, the **Owner** field stays blank on inventory transactions, and the *prevent multiple owners* checks described in the [How the feature works](#how-the-feature-works) section have nothing to compare against. Use this procedure to enable the **Owner** dimension on each tracking dimension group that applies to items that you want to segregate by owner.

> [!IMPORTANT]
> Activating the **Owner** dimension changes the inventory tracking model for any item that uses the group. Plan the change carefully for items that already have on-hand inventory or open transactions, and follow your organization's standard process for modifying tracking dimension groups.

1. Go to **Product information management** > **Setup** > **Dimension and variant groups** > **Tracking dimension groups**.
1. Follow one of these steps:
    - On the Action Pane, select **New** to create a tracking dimension group. Enter a name and description, and then select **Save** on the Action Pane.
    - In the list pane, select the existing tracking dimension group that you want to update.

1. On the **Tracking dimension** FastTab, in the **Owner** row, select the checkboxes in the **Active** and **Physical inventory** columns.
1. Select **Save**.
1. Assign the tracking dimension group to each released product that you want to track by owner. To do this, go to **Product information management** > **Products** > **Released products**, where you can assign a **Tracking dimension group** to each new or existing released products.
    - For new products, assign a **Tracking dimension group** in the dialog when you create the released product.
    - For existing products, go to the Action Pane, open the **Product** tab and, from the **Set up** group, select **Dimension groups**. In the drop-down dialog, set the **Tracking dimension group** field.

## Assign an inventory owner to inventory

After you activate the **Owner** dimension on a tracking dimension group, you must also assign an actual owner value to the inventory that flows through your warehouse. The *prevent multiple owners* feature compares these owner values when it evaluates location candidates, so any inventory that doesn't have an owner assigned is treated as belonging to a separate, *empty owner* group, as described in the [How the feature works](#how-the-feature-works) section.

Assigning an owner to inventory has two parts: registering each party that can own inventory, and then making sure that owner is set on inbound and internal transactions.

### Register inventory owners

Register inventory owners before referencing them on transactions. Inventory owners are typically either vendors that consign stock to your warehouse or other legal entities for which you manage inventory.

- If you're using warehouse management only (WMS-only) mode, each source system setup must have a *Warehouse inventory owner* configuration that contains a mapping for every **Owner** value that the source system might send in an order line. The mapping ensures that the system can recognize the owner and assign it to inventory transactions. To make the configuration, open the relevant source system record and select **Warehouse inventory owner** on the Action Pane. Learn more in [Configure your source systems](wms-only-mode-setup.md#source-systems).

- If you're not using WMS-only mode, register inventory owners on the **Inventory owners** page. Go to **Inventory management** > **Setup** > **Dimensions** > **Inventory owners** and, for each owner, make the following settings:
    - **Vendor account** – Select the vendor that owns the inventory. The **Name** and **Owner** fields are populated automatically.
    - **Owner** – Optionally, enter an owner value that's easier for external parties (such as the vendor) to recognize. You can edit this field only until you save the record.

### Set the owner on inventory transactions

After you register owners, the **Owner** value flows onto inventory through the transaction that brings the stock on hand or changes who owns it. Use the appropriate method for your scenario:

- **Consignment replenishment orders** – When you create a consignment replenishment order for a vendor that's registered as an inventory owner, the vendor is set as the owner on each order line automatically. The product receipt update then registers physical on-hand inventory under that owner. For details, see [Set up consignment](../inventory/consignment.md).
- **Inventory ownership change journal** – Use a journal of type *Ownership change* to transfer existing on-hand inventory from one owner to another (for example, from a vendor to your own legal entity when you consume consignment stock). Create the journal from **Inventory management** > **Journal entries** > **Items** > **Inventory ownership change**.
- **Other inbound transactions** – For purchase orders, transfer orders, and inbound shipment orders, open the order, select a line, and on the **Line details** FastTab, open the **Product** tab and assign the **Owner**.

> [!NOTE]
> If you post an inventory transaction without an owner value, the resulting on-hand inventory is tracked under an empty owner. Locations that use a profile where **Prevent multiple owners** is set to *Yes* then treat that inventory as incompatible with any inventory that has a non-empty owner, and the reverse.

## Example configuration

The following end-to-end example shows how the *prevent multiple owners* feature works. It illustrates one of the [scenarios](#when-to-use-this-feature) where the feature is most useful—a third-party logistics (3PL) warehouse—and demonstrates how location profiles, zones, and location directives work in combination with the **Prevent multiple owners** constraint to keep each owner's inventory segregated.

In this example, your 3PL warehouse stores consigned inventory from two customer partners (Partner A and Partner B). You want to prevent their stock from commingling. Therefore, you might configure your warehouse as follows:

1. Create two location profiles:
   - Name the first profile *3PL-PARTNER-A* and set **Prevent multiple owners** to *Yes*.
   - Name the second profile *3PL-PARTNER-B* and set **Prevent multiple owners** to *Yes*.

1. Assign locations in zone A to use the *3PL-PARTNER-A* profile and locations in zone B to use the *3PL-PARTNER-B* profile.

1. Configure location directives and putaway templates to route Partner A inventory to zone A and Partner B inventory to zone B.

1. When receiving Partner A inventory:
   - The system automatically assigns it to a zone A location using the *3PL-PARTNER-A* profile.
   - If a location is full, the system finds alternate locations within zone A with the same owner already present.
   - If no available capacity exists for Partner A's owner, the system either suggests a new empty location or initiates replenishment to free capacity.

## Day-to-day warehouse operations

After you configure location profiles to prevent multiple owners, day-to-day warehouse operations must align with the new constraint so that putaway, replenishment, and manual moves continue to flow smoothly. The following sections describe what warehouse managers should plan for, how operators should respond on the mobile device, and how to recover when the system can't find a compatible location.

### For warehouse managers

As a warehouse manager, your role is to make sure the location-profile configuration translates into a workable physical layout and that operators have enough capacity per owner to keep putaway flowing. The following planning and monitoring activities help you avoid *owner mismatch* errors and capacity issues:

- **Monitor owner segregation** – Use the warehouse location master data to confirm that locations assigned to constrained profiles contain expected inventory owners.
- **Plan location allocation** – Allocate sufficient location capacity to each owner based on forecasted volumes.
- **Coordinate with 3PL partners** – If you manage multiple partners' inventory, agree on owner-assignment conventions to avoid empty-owner ambiguity.

### For warehouse operators

Warehouse operators typically use a mobile device or terminal and barcode scanner to manage putaway, picking, and manual relocation tasks. The system handles owner segregation automatically in most cases, but operators need to know how to respond when a location is rejected so they don't bypass the **Prevent multiple owners** constraint or accidentally commingle stock.

During putaway:

1. Scan the item and owner code as directed by your receiving process.
1. The system automatically selects a location respecting the owner constraint.
1. If you see an error message that the location already has inventory from a different owner, *do not manually override it*. The constraint exists to prevent commingling. Instead, take these steps:
    - Confirm with your supervisor that the inventory owner is correct.
    - Wait for the system to suggest an alternate location (usually automatic).
    - If prompted, manually select an alternate location suggested by the system.

When manually relocating inventory:

1. Always verify the inventory owner before reassigning to a new location.
1. If the system rejects your location change due to owner mismatch, it means that the location is incompatible. Choose a location that already contains inventory of the same owner, or an empty location if available.

### When putaway fails

If the system can't find an available location due to owner constraints, it performs one of the following actions:

- **Recover automatically** – The system might trigger immediate replenishment to consolidate and free capacity for the new owner.
- **Provide operator guidance** – The mobile device or work queue displays a message that explains the constraint and suggests next steps.
- **Wait for manual intervention** – In rare cases, a supervisor might need to manually relocate existing low-priority inventory to free capacity.

## Interaction with location directives

Location directives control where inventory is placed during putaway and picking. When the **Prevent multiple owners** constraint is active, the system implements the following behaviors to ensure that directives respect owner segregation:

- **Strategy refinement** – The system augments location-directive logic to include owner as a grouping dimension alongside item, batch, and status.
- **Multi-step filtering** – Location selection first applies traditional directive criteria (zone, aisle, and so on), then filters by compatible owners.
- **Replenishment triggers** – If the directive is set to enable immediate replenishment, a failed putaway due to owner mismatch triggers replenishment, which is similar to item or batch mismatches.

For example, suppose you have a directive that routes all purchase order receipts to a bulk location. The system evaluates the directive as follows depending on whether the **Prevent multiple owners** constraint is enabled:

- **Without owner constraint** – Each item is placed in any bulk location that has available capacity.
- **With owner constraint** – Items are only placed in bulk locations that exclusively contain items for the same owner. If no suitable bulk location exists, the directive might select a different location class or trigger replenishment.

## Troubleshooting

### Inventory owner information isn't available

#### Symptom

The system doesn't show inventory owner information on location or work displays.

#### Resolution

Confirm that the tracking dimension group for your items includes the **Owner** field. If it's missing, add it to the tracking dimension group for the items, and then perform a new receipt to generate inventory with owner tracking.

### Changing **Prevent multiple owners** from *No* to *Yes* fails

#### Symptom

When you try to enable **Prevent multiple owners** on a location profile, the system displays an error dialog that lists conflicting inventory.

#### Resolution

To resolve the conflict, do one of the following actions:

- Relocate the conflicting inventory to other locations that don't use this profile.
- Create separate location profiles for each owner and adjust your location assignments.

When the location is empty or contains only single-owner inventory, try again to enable the constraint.

### Operators frequently receive "owner mismatch" errors

#### Symptom

Warehouse operators report frequent constraint-violation errors during putaway.

#### Possible causes

This problem can occur for any of the following reasons:

- **Insufficient segregated capacity** – You allocated too few locations to each owner. Expand the location pool or reduce expected volumes.
- **Incorrect owner assignment** – Incoming inventory is being tagged with the wrong owner code. Review the receiving process and incoming document data.
- **Directive misconfiguration** – Location directives might not be routing inventory to the correct owner-dedicated locations. Review directive sequencing and query criteria.

#### Resolution

To resolve the issue, consider these steps:

- Work with your warehouse planner to rebalance capacity allocation per owner.
- Audit incoming data quality and owner-assignment rules.
- Review location directives to ensure they route inventory by owner correctly.

## Frequently asked questions

### Does the "Prevent multiple owners" constraint apply during cycle counting?

No. Cycle counting is a physical inventory verification process and doesn't enforce putaway constraints. However, if cycle counting reveals that a location contains inventory with multiple owners (from inventory that was placed before the constraint was enabled), you should relocate one owner's stock to another location to comply with the constraint going forward.

### What happens if an owner code is empty or null?

The system treats empty owner values as a distinct owner and only mixes them with other inventory that also has an empty owner. This approach prevents accidentally commingling unowned inventory with owner-specific inventory.

### Can I enable both "Prevent multiple owners" and "Allow mixed items" on the same location profile?

Yes. Both constraints work independently. The location allows multiple items but only from the same owner.

### Does this feature support multi-owner inventory transfers?

The constraint prevents storing multi-owner inventory in the same location. To transfer inventory between owners, you must use a separate transfer order and ensure inventory passes through a quarantine or staging location configured to allow multiple owners (that is, with the constraint disabled).

### If I disable "Prevent multiple owners", what happens to existing inventory?

Disabling the constraint doesn't automatically move inventory. Existing multi-owner inventory (if any) remains in place. Disabling simply stops enforcing the constraint for future putaway operations.

## Related information

- **Location profiles** – For general information on setting up location profiles and constraints, see [Create location profiles](tasks/create-location-profile.md).
- **Location product dimension mixing** – To learn about mixing constraints for product dimensions, see [Location product dimension mixing](location-product-dimension-mixing.md).
- **Location directives** – For guidance on setting up location directives, see [Create location directives](create-location-directive.md) and [Control work by using work templates and location directives](control-warehouse-location-directives.md).
- **Warehouse management overview** – For a broader introduction to warehouse management concepts, see [Warehouse management overview](warehouse-management-overview.md).
