---
title: Make-to-order supply automation
description: This article describes how to set up and use the various enhancements added by the Make-to-order supply automation feature
author: t-benebo
ms.date: 07/27/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-07-27
ms.dyn365.ops.version: 10.0.29
---

# Make-to-order supply automation

[!include [banner](../includes/banner.md)]

<!-- KFM: Does any part of this feature rely on Planning Optimization? I.e., where should this go in the TOC? -->

The *Make-to-order supply automation* feature adds several enhancement to Dynamics 365 Supply Chain Management. It enables you to do the following:

- View the resource capacity load for a user-defined period, thereby enabling long-term evaluation of the capacity load.
- Improve flexibility by controlling the delay tolerance (negative days) for each master plan.
- Keep products available for last-minute orders and optimize usage of existing supply. This is achieved by pegging the latest possible supply to a demand, instead of using the first possible supply.
- Keep component assignment flexible for production orders after firming, which enables the system to optimize for last-minute demand changes. In other words, limit marking to one level.
- Control the fulfillment policy for each sales order, with default settings taken from the customer setup.
- Enhance intercompany information flow. Purchase orders are updated to include fields for mode of delivery, delivery terms, and external item number. This ensures that detailed demand information can flow to the supplying company.

This article describes how to set up and use each of these enhancements.

## Turn on the Make-to-order supply automation feature

Before you can use the features described in this topic, you must turn them on for your system. Admins can use the [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace, where the feature is listed in the following way:

- **Module:** *Master Planning*
- **Feature name:** *Make-to-order supply automation*

## Choose the number of days to show on Capacity load page

The **Capacity load** page lets you review a resources's available capacity. The *Make-to-order supply automation* feature enhances the **Capacity load** page by adding a **Number of days** field, which lets you limit the number of days shown in the **Overview** grid. If you return to the page later, it will remember the value you last entered here.

<!-- KFM: Confirm the following two procedures. -->

To open the **Capacity load** page so you can review the available capacity for an individual resource, follow these steps:

1. Go to **Organization administration \> Resources \> Resources**.
1. Select a resource to inspect.
1. On the Action Pane, on the **Resource** tab, in the **View** group, select **Capacity load**.
1. Use the **Number of days** filter to limit the number of days shown in the **Overview** grid.

To open the **Capacity load** page so you can review the available capacity for a resource group, follow these steps:

1. Go to **Organization administration \> Resources \> Resource groups**.
1. Select a resource group to inspect.
1. On the Action Pane, on the **Resource group** tab, in the **View** group, select **Capacity load**.
1. Use the **Number of days** filter to limit the number of days shown in the **Overview** grid.

## Apply a single level of marking when firming planned orders

*Marking* is used to link supply and demand. It resembles *pegging*, which indicates how master planning expects to cover demand, but marking is more permanent than pegging. The *Make-to-order supply automation* feature adds the ability to limit inventory marking to a single level when firming planned orders. It adds the following new options to the **Update marking** drop-down list provided on the **Firming** dialog box when you are firming a planned order:

- *Single level standard* – Uses single-level marking, which lets you keep component assignment flexible for production orders after firming. <!-- KFM: We should descirbe more clearly just what we mean by "single level". --> Single-level marking enables the system to optimize for last-minute demand changes. With standard single-level marking, requirement orders are marked against their fulfillment orders, but fulfillment orders are not marked if they have remaining quantity.
- *Single level extended* – Uses single-level marking, but with extended single-level marking, requirement orders are marked against their fulfillment orders and fulfillment orders are marked regardless of whether any quantity remains or not.

These options are also available in the **Update marking** drop-down list on the **Standard update** tab of the **Master planning parameters** page, where you establish the default selection for the **Firming** dialog box. <!-- KFM: Confirm this. -->

For more information, see [Inventory marking with Planning Optimization](marking.md) <!-- KFM: Confirm the new texts added to the target of this link. -->

## Set delay tolerance (negative days) at the master plan level

The *Make-to-order supply automation* feature adds the ability to configure delay tolerance (negative days) at the mater plan level. The setting is also available at the item coverage and coverage group level. If negative days are assigned at more than one level, the system applies the following hierarchy to decide which setting to use:

- If negative days are configured on the **Master plans** page, then that setting overrides all other negative days settings when that plan runs.
- If negative days are configured on the **Item coverage** page, then that setting overrides the coverage group setting.
- Negative days configured on the **Coverage groups** page only apply when negative days have not been configured for a relevant item or master plan.

To set negative days for a master plan, follow these steps:

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select a master plan from the list pane, or create a new one.
1. Expand the **Time fences in days** FastTab.
1. Set **Negative days** to *Yes*.
1. Enter the number of negative days to allow in the nearby field.

For more information about how to use negative days, see [Delay tolerance (negative days)](delay-tolerance.md) <!-- KFM: Confirm the new texts added to the target of this link. -->

## Control the pegging sequence used during master planning

Master planning uses a *pegging sequence* to resolve which supply will cover which demand. The *Make-to-order supply automation* feature adds a new option (**Use latest possible supply**), which gives you additional control over the pegging sequence. The new option lets you keep products available for last-minute orders and optimize usage of existing supply. This is achieved by pegging the latest possible supply to a demand, instead of using the first possible supply.

You can set the pegging sequence at the master plan, item coverage, or coverage group level. If a pegging sequence is set up at more than one level, the system applies the following hierarchy to decide which setting to use:

- If a pegging sequence is set up on the **Master plans** page, then that setting overrides all other pegging sequence settings when that plan runs.
- If a pegging sequence is set up on the **Item coverage** page, then that setting overrides the coverage group setting.
- The pegging sequence set up on the **Coverage groups** page only applies when pegging sequence settings have not been configured for a relevant item or master plan.

Use the following procedure to set up pegging at the coverage group level:

1. Go to **Master planning \> Setup \> Coverage \> Coverage groups**.
1. Select a group from the list pane or create a new one.
1. Expand the **General** FastTab.
1. In the **Pegging sequence** field group, use the **Consume on-hand inventory** and **Use latest supply** settings to configure your pegging sequence. The table later in the section shows how these settings combine to establish your pegging sequence.

Use the following procedure to set up pegging at the item coverage level:

1. Go to **Product information management \> Products \> Released products**.
1. Select a product in the grid or create a new one.
1. On the Action Pane, open the **Plan** tab and select **Item coverage**.
1. The **Item coverage** page opens. This page provides rows that let you establish coverage rules that apply to this item at each warehouse. Either select an existing row from the grid or create a new one.
1. Open the **General** tab.
1. Mark the **Override pegging sequence** check box.
1. Use the **Consume on-hand inventory** and **Use latest supply** settings to configure your pegging sequence. The table later in the section shows how these settings combine to establish your pegging sequence.

Use the following procedure to set up pegging at the master plan level:

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select a master plan from the list pane, or create a new one.
1. Expand the **General** FastTab.
1. Set **Override pegging sequence** to *Yes*.
1. Use the **Consume on-hand inventory** and **Use latest supply** settings to configure your pegging sequence. The table later in the section shows how these settings combine to establish your pegging sequence.

The following table shows how the **Consume on-hand inventory** and **Use latest supply** settings combine to establish your pegging sequence:

|  | **Use latest supply** = *Yes* | **Use latest supply** = *No* |
|-------------------------|-------------------------|-------------------------|
| **Consume on-hand inventory** = *Before all supply* | <ol><li>On-hand</li><li>Existing supply that can meet the demand date</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>Create new supply (planned order)</li></ol> | <ol><li>On-hand</li><li>Existing supply that can meet the demand date</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>Create new supply (planned order)</li></ol> |
| **Consume on-hand inventory** = *After all supply* | <ol><li>Existing supply that can meet the demand date</li><li>On-hand</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>Create new supply (planned order)</li></ol> | <ol><li>Existing supply that can meet the demand date</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>On-hand</li><li>Create new supply (planned order)</li></ol> |

## View and set the fulfillment policy that applies to each sales order

Fulfillment policies control the percentage of the total order price or quantity that must be physically reserved before you can release a sales order to the warehouse. You can set a global default fulfillment policy and override the global default for specific customers if needed. The *Make-to-order supply automation* feature adds the ability to see what default policy actually applies to any order and to apply an order-specific override if needed.

- To set the global fulfillment policy default for sales orders, go to **Accounts receivable \> Setup \> Accounts receivable parameters**. Then open the **Warehouse management** tab and set **Sales order fulfillment policy** to the name of the policy you want to use. 
- To set a customer-specific fulfillment policy for sales orders, go to **Accounts receivable \> Customers \> All customers**. Then expand the **Warehouse** tab and set **Fulfillment policy** to the name of the policy you want to use.

Use the following procedure to view the default policy that applies to any order and to apply an order-specific override if needed:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Open the sales order you want to inspect or edit.
1. Select the **Header** view.
1. Expand the **Warehouse** FastTab.
1. View and edit the following fields as needed:
    - **Order fulfillment policy** – Select the fulfillment policy to use for this specific order (overriding all defaults). Leave this blank to use the **Default fulfillment policy** shown for this order.
    - **Default fulfillment policy** – Shows the default fulfillment policy that applies if the **Order fulfillment policy** field is blank. This value is read-only. If **Default fulfillment policy** is blank, that means that no customer-specific or global default fulfillment policy is defined.

    If both the **Order fulfillment policy** and **Default fulfillment policy** are blank, then no fulfillment policy applies, but other restrictions might be in place that require reservations or other conditions to be met before the sales order can be released.

## Set delivery mode and terms on individual purchase order lines

All purchase orders include settings for **Delivery terms** and **Mode of delivery** on the order header. The *Make-to-order supply automation* feature adds the ability to also define **Delivery terms** and/or **Mode of delivery** overrides for any or all order lines. For lines where no override is defined, the value from the header is used. You can configure whether a change in one or both of these fields on the order header should also update all lines.

Use the following procedure to choose what should happen to the line settings if a user changes the **Delivery terms** and/or **Mode of delivery** on an order header:

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**.
1. Open the **General** tab.
1. Select the **Update order lines** link at the top of the **Default values and parameters** FastTab.
1. The **Update order lines** dialog opens. For the **Updating Delivery terms** and **Update Mode of delivery** fields, select one of the following values:
    - *Never* – Never update the order lines after changing these settings in the order header.
    - *Always* – Always update all order lines after changing these settings in the order header.
    - *Prompt* – If a user changes one or both of these settings in the header, display a dialog that asks whether the user wants to update all lines to match the change in one or both of these fields.

Use the following procedure to set delivery information on a purchase order header:

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Open the purchase order you want to edit.
1. Select the **Header** view.
1. Expand the **Delivery** FastTab.
1. Set value for the **Mode of delivery** and **Delivery terms** fields as needed.
1. Depending on the settings made on the **Procurement and sourcing parameters**, you may be asked whether you want to apply your changes to all order lines.

Use the following procedure to set delivery information overrides for a purchase order line:

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Open the purchase order you want to edit.
1. Select the **Lines** view.
1. On the **Purchase order lines** FastTab, select the line you want to edit.
1. On the **Line details** FastTab, open the **Delivery** tab.
1. Set value for the **Mode of delivery** and **Delivery terms** fields as needed. Clear one or both of these fields to use the matching settings in the header.

For intercompany orders, values for the **Mode of delivery** and **Delivery terms** fields in each purchase order line will be synchronized between the purchase order and its related sales order. <!-- KFM: Please confirm this rephrasing. More info may be needed here, and maybe a link too -->

## Synchronize external item IDs and descriptions for intercompany orders

For intercompany orders, the *Make-to-order supply automation* feature makes it possible for external item IDs and text descriptions on purchase order lines to be synchronized with their related intercompany sales order lines, regardless of whether the purchase order is direct delivery or not. It also adds the ability to specify the final external customer account on an intercompany purchase order, which will cause the system to automatically take external item IDs and text descriptions from the external customer record rather than the (internal) intercompany vendor record.

Use the following procedure to set up an intercompany vendor to synchronize external item IDs and item names between intercompany purchase orders and their related intercompany sales orders:

1. Go to **Procurement and sourcing \> Vendors \> All vendors**.
1. Select the intercompany vendor you want to set up.
1. On the Action Pane, open the **General** tab and, from the **Set up** group, select **Intercompany**.
1. The **Intercompany** page opens. Open the **Purchase order polices** tab.
1. In the **Intercompany purchase order -> Intercompany sales order** field group, mark the **External item ID and item name** check box.

Use the following procedure to specify the final external **Customer account** for an intercompany purchase order. This setting only applies to intercompany purchase orders. Use it to specify the account number of the customer who will eventually receive the goods. When this field is set, purchase order lines will take external item descriptions and numbers from this customer account rather than from the intercompany vendor specified on the purchase order. If you change the customer account later, then external item descriptions and IDs will be updated to match the new account. External item descriptions and IDs for each line will also be synched to the matching intercompany sales order.

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Open the purchase order you want to set up, or create a new one.
1. Select the **Header** view.
1. In the **Reference** field group, set **Customer account** to the relevant external customer account.

Use the following procedure to specify external item IDs and text descriptions for a purchase order line for an intercompany order. These values will be synchronized with their related intercompany sales order lines, regardless of whether the purchase order is direct delivery or not.

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Open the purchase order you want to set up, or create a new one.
1. Select the **Lines** view.
1. On the **Purchase order lines** FastTab, select the line you want to edit.
1. On the **Line details** FastTab, open the **General** tab.
1. In the **Order line** field group, edit the **Text** field to provide an external description of the item specified on the selected order line. This value will be synced with its related intercompany sales order line.
1. In the **Reference** field group, edit the **External** field to provide an external item ID for the item specified on the selected order line. This value will be synced with its related intercompany sales order line.

<!-- KFM: I suppose the intercompany order will eventually result in an external sales order. Are we also synchronizing these values there? Or are we only syncing between the intercompany purchase and sales orders? -->

For more information, see [Create and invoice an intercompany sales order for an external customer](../../sales-marketing/intercompany-sales-order-for-external-customer.md). <!-- KFM: I think this topic describes the scenario we mean here, but I'm not sure. Please confirm. I could be that we should copy/adapt this section for that topic too. -->
