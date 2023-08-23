---
title: Make-to-order supply automation
description: This article describes how to set up and use the various enhancements that are added by the Make-to-order supply automation feature.
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

The *Make-to-order supply automation* feature adds several enhancements to Microsoft Dynamics 365 Supply Chain Management. These enhancements enable you to perform the following tasks:

- View the resource capacity load for a user-defined period, and therefore enable long-term evaluation of the capacity load.
- Improve flexibility by controlling the delay tolerance (negative days) for each master plan.
- Keep products available for last-minute orders and optimize the use of existing supply by pegging the latest possible supply to a demand instead of using the first possible supply.
- Keep component assignment flexible for production orders after firming, so that the system can optimize for last-minute demand changes. In other words, limit marking to one level.
- Control the fulfillment policy for each sales order. Default settings are taken from the customer setup.
- Enhance intercompany information flow. Purchase orders are updated so that they include fields for the mode of delivery, delivery terms, and external item number. This change ensures that detailed demand information can flow to the supplying company.

This article describes how to set up and use each enhancement.

## Turn the Make-to-order supply automation feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *Make-to-order supply automation* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Set the number of days to show on Capacity load page

The **Capacity load** page lets you review a resource's available capacity. The *Make-to-order supply automation* feature enhances the **Capacity load** page by adding a **Number of days** field. You can use this field to limit the number of days that the **Overview** grid shows. The value that you set is saved in memory. Therefore, if you leave the page and then return later, the **Overview** grid will still show the number of days that you last specified.

To open the **Capacity load** page so that you can review the available capacity for an individual resource, follow these steps.

1. Go to **Organization administration \> Resources \> Resources**.
1. Select a resource to inspect.
1. On the Action Pane, on the **Resource** tab, in the **View** group, select **Capacity load**.
1. Use the **Number of days** filter to limit the number of days that the **Overview** grid shows.

To open the **Capacity load** page so that you can review the available capacity for a resource group, follow these steps.

1. Go to **Organization administration \> Resources \> Resource groups**.
1. Select a resource group to inspect.
1. On the Action Pane, on the **Resource group** tab, in the **View** group, select **Capacity load**.
1. Use the **Number of days** filter to limit the number of days that the **Overview** grid shows.

## Apply a single level of marking when you firm planned orders

*Marking* is used to link supply and demand. It resembles *pegging*, which indicates how master planning expects to cover demand. However, marking is more permanent than pegging. The *Make-to-order supply automation* feature adds the ability to limit inventory marking to a single level when planned orders are firmed. It adds the following new options to the **Update marking** field in the **Firming** dialog box when you're firming a planned order:

- *Single level standard* – Single-level marking is used. Single-level marking marks only the main item, not its bill of materials (BOM) components. Therefore, you can keep component assignment for production orders flexible after firming. Single-level marking enables the system to optimize for last-minute demand changes. In *standard* single-level marking, requirement orders are marked against their fulfillment orders, but fulfillment orders aren't marked if they have remaining quantity.
- *Single level extended* – Single-level marking is used. In *extended* single-level marking, requirement orders are marked against their fulfillment orders, and fulfillment orders are always marked, regardless of whether any quantity remains.

These options are also available in the **Update marking** field on the **Standard update** tab of the **Master planning parameters** page, where you define the default selection for the **Firming** dialog box.

For more information, see [Inventory marking](planning-optimization/marking.md).

## Set delay tolerance (negative days) at the master plan level

The *Make-to-order supply automation* feature adds the ability to configure delay tolerance (negative days) at the master plan level. The setting is also available at the item coverage and coverage group levels. If negative days are assigned at more than one level, the system applies the following hierarchy to decide which setting to use:

- If negative days are configured on the **Master plans** page, that setting overrides all other negative days settings when the plan runs.
- If negative days are configured on the **Item coverage** page, that setting overrides the coverage group setting.
- Negative days that are configured on the **Coverage groups** page apply only if negative days haven't been configured for a relevant item or master plan.

To set negative days for a master plan, follow these steps.

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select a master plan in the list pane, or create a new one.
1. On the **Time fences in days** FastTab, set the **Negative days** option to *Yes*.
1. In the nearby field, enter the number of negative days to allow.

For more information about how to use negative days, see [Delay tolerance (negative days)](planning-optimization/delay-tolerance.md).

## Control the pegging sequence used during master planning

Master planning uses a *pegging sequence* to determine which supply will cover which demand. The *Make-to-order supply automation* feature adds a new **Use latest possible supply** option that gives you more control over the pegging sequence. The new option lets you keep products available for last-minute orders and optimize the use of existing supply by pegging the latest possible supply to a demand instead of using the first possible supply.

You can set the pegging sequence at the master plan, item coverage, or coverage group level. If a pegging sequence is set up at more than one level, the system applies the following hierarchy to decide which setting to use:

- If a pegging sequence is set up on the **Master plans** page, that setting overrides all other pegging sequence settings when the plan runs.
- If a pegging sequence is set up on the **Item coverage** page, that setting overrides the coverage group setting.
- The pegging sequence that is set up on the **Coverage groups** page applies only if pegging sequence settings haven't been configured for a relevant item or master plan.

To set up pegging at the coverage group level, follow these steps.

1. Go to **Master planning \> Setup \> Coverage \> Coverage groups**.
1. Select a group in the list pane, or create a new one.
1. On the **General** FastTab, in the **Pegging sequence** section, use the **Consume on-hand inventory** and **Use latest supply** fields to configure your pegging sequence. The table later in this section shows how these settings are combined to define your pegging sequence.

To set up pegging at the item coverage level, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select a product in the grid, or create a new one.
1. On the Action Pane, on the **Plan** tab, select **Item coverage**.
1. The **Item coverage** page provides rows that let you define coverage rules that apply to the item at each warehouse. Select an existing row in the grid, or create a new one.
1. On the **General** tab, select the **Override pegging sequence** checkbox.
1. Use the **Consume on-hand inventory** and **Use latest supply** fields to configure your pegging sequence. The table later in this section shows how these settings are combined to define your pegging sequence.

To set up pegging at the master plan level, follow these steps.

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select a master plan in the list pane, or create a new one.
1. On the **General** FastTab, set the **Override pegging sequence** option to *Yes*.
1. Use the **Consume on-hand inventory** and **Use latest supply** fields to configure your pegging sequence. The table later in this section shows how these settings are combined to define your pegging sequence.

The following table shows how the **Consume on-hand inventory** and **Use latest supply** settings are combined to establish your pegging sequence.

| | Use latest supply = Yes | Use latest supply = No |
|---|---|---|
| **Consume on-hand inventory** = *Before all supply* | <ol><li>On-hand</li><li>Existing supply that can meet the demand date</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>Create new supply (planned order)</li></ol> | <ol><li>On-hand</li><li>Existing supply that can meet the demand date</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>Create new supply (planned order)</li></ol> |
| **Consume on-hand inventory** = *After all supply* | <ol><li>Existing supply that can meet the demand date</li><li>On-hand</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>Create new supply (planned order)</li></ol> | <ol><li>Existing supply that can meet the demand date</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>On-hand</li><li>Create new supply (planned order)</li></ol> |

## Review and set the fulfillment policy that applies to each sales order

Fulfillment policies control the percentage of the total order price or quantity that must be physically reserved before you can release a sales order to the warehouse. You can set a global default fulfillment policy and then override it for specific customers as you require. The *Make-to-order supply automation* feature adds the ability to view what default policy actually applies to any order and apply an order-specific override as required.

- To set the global fulfillment policy default for sales orders, go to **Accounts receivable \> Setup \> Accounts receivable parameters**. Then, on the **Warehouse management** tab, set the **Sales order fulfillment policy** field to the name of the policy that you want to use. 
- To set a customer-specific fulfillment policy for sales orders, go to **Accounts receivable \> Customers \> All customers**. Then, on the **Warehouse** tab, set the **Fulfillment policy** field to the name of the policy that you want to use.

To view the default policy that applies to any order and apply an order-specific override, follow these steps.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Open the sales order that you want to inspect or edit.
1. Select the **Header** view.
1. On the **Warehouse** FastTab, review and edit the following fields as required:

    - **Order fulfillment policy** – Select the fulfillment policy to use for the selected order. The default policy will be overridden. To use the default fulfillment policy that is shown in the **Default fulfillment policy** field, leave this field blank.
    - **Default fulfillment policy** – This field shows the default fulfillment policy that applies if the **Order fulfillment policy** field is blank. This field is read-only. If it's blank, no customer-specific or global default fulfillment policy is defined.

    If both the **Order fulfillment policy** field and the **Default fulfillment policy** field are blank, no fulfillment policy applies. However, other restrictions might be in place, and might require that reservations or other conditions be met before the sales order can be released.

## Set the delivery mode and terms on individual purchase order lines

All purchase orders include **Delivery terms** and **Mode of delivery** settings on the order header. The *Make-to-order supply automation* feature adds these settings to each order line. Therefore, you can define overrides of the **Delivery terms** and/or **Mode of delivery** value for any or all order lines as required. For lines where no override is defined, the value from the header is used. You can specify whether a change to the value of one or both of these fields on the order header should also update all lines.

To specify what should happen to line settings if a user changes the **Delivery terms** and/or **Mode of delivery** value on an order header, follow these steps.

1. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**.
1. On the **General** tab, on the **Default values and parameters** FastTab, select the **Update order lines** link.
1. In the **Update order lines** dialog box, in the **Updating Delivery terms** and **Update Mode of delivery** fields, select one of the following values:

    - *Never* – Never update the order lines after the settings are changed on the order header.
    - *Always* – Always update all order lines after the settings are changed on the order header.
    - *Prompt* – If a user changes one or both settings on the order header, open a dialog bot that asks whether the user wants to update all lines so that they match the change to one or both settings.

To set delivery information on a purchase order header, follow these steps.

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Open the purchase order that you want to edit.
1. Select the **Header** view.
1. On the **Delivery** FastTab, set the **Mode of delivery** and **Delivery terms** fields as required.
1. Depending on the settings on the **Procurement and sourcing parameters** page, you might be asked whether you want to apply your changes to all order lines.

To set delivery information overrides for a purchase order line, follow these steps.

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Open the purchase order that you want to edit.
1. Select the **Lines** view.
1. On the **Purchase order lines** FastTab, select the line to edit.
1. On the **Line details** FastTab, on the **Delivery** tab, set the **Mode of delivery** and **Delivery terms** fields as required. Clear one or both fields to use the matching settings on the header.

For intercompany orders, values for the **Mode of delivery** and **Delivery terms** fields on each purchase order line will be synced between the purchase order and its related sales order.

## Sync external item IDs and descriptions for intercompany orders

For intercompany orders, the *Make-to-order supply automation* feature enables external item IDs and text descriptions on purchase order lines to be synced with the related intercompany sales order lines, regardless of whether the purchase order is for direct delivery. The feature also adds the ability to specify the final external customer account on an intercompany purchase order. The system will then automatically take external item IDs and text descriptions from the external customer record instead of the (internal) intercompany vendor record.

To set up an intercompany vendor to sync external item IDs and item names between intercompany purchase orders and their related intercompany sales orders, follow these steps.

1. Go to **Procurement and sourcing \> Vendors \> All vendors**.
1. Select the intercompany vendor that you want to set up.
1. On the Action Pane, on the **General** tab, in the **Set up** group, select **Intercompany**.
1. On the **Intercompany** page, on the **Purchase order polices** tab, in the **Intercompany purchase order -\> Intercompany sales order** section, select the **External item ID and item name** checkbox.

To specify the final external customer account for an intercompany purchase order, follow these steps. The **Customer account** field applies only to intercompany purchase orders. Use it to specify the account number of the customer who will eventually receive the goods. When this field is set, purchase order lines will take external item descriptions and numbers from the specified customer account instead of the intercompany vendor that is specified on the purchase order. If you change the customer account later, external item descriptions and IDs will be updated so that they match the values for the new account. External item descriptions and IDs for each line will also be synced to the matching intercompany sales order.

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Open the purchase order that you want to set up, or create a new one.
1. Select the **Header** view.
1. In the **Reference** section, set the **Customer account** field to the relevant external customer account.

To specify external item IDs and text descriptions for a purchase order line for an intercompany order, follow these steps. The values that you set will be synced with the related intercompany sales order lines, regardless of whether the purchase order is for direct delivery.

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Open the purchase order that you want to set up, or create a new one.
1. Select the **Lines** view.
1. On the **Purchase order lines** FastTab, select the line to edit.
1. On the **Line details** FastTab, on the **General** tab, in the **Order line** section, in the **Text** field, provide an external description of the item that is specified on the selected order line. This value will be synced with the related intercompany sales order line.
1. In the **Reference** section, in the **External** field, provide an external item ID for the item that is specified on the selected order line. This value will be synced with the related intercompany sales order line.

For more information, see [Create and invoice an intercompany sales order for an external customer](../sales-marketing/intercompany-sales-order-for-external-customer.md).
