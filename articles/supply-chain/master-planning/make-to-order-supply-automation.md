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
- Keep products available for last-minute orders and optimize usage of existing supply. This is achieved by using the latest possible supply to a demand, instead of using the first possible supply.
- Keep component assignment flexible for production orders after firming, which enables the system to optimize for last-minute demand changes. In other words, limit marking to one level.
- Control the fulfillment policy for each sales order, with default settings taken from the customer setup.
- Enhance intercompany information flow. Purchase orders are updated to include fields for mode of delivery, delivery terms, and external item number. This ensures that detailed demand information can flow to the supplying company.

This article describes how to set up and use each of these enhancements.

## Turn on the Make-to-order supply automation feature

Before you can use the features described in this topic, you must turn them on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace, where the feature is listed in the following way:

- **Module:** *Master Planning*
- **Feature name:** *Make-to-order supply automation*

## Choose the number of days to show on Capacity load page

The *Make-to-order supply automation* feature enhances the **Capacity load** page by adding a **Number of days** field, which lets you limit the number of days shown in the **Overview** grid. If you return to the page later, it will remember the value you last entered here.

<!-- KFM: Confirm the following two procedures. -->

To open the **Capacity load** page so you can review the available capacity on a resource, follow these steps:

1. Go to **Organization administration \> Resources \> Resources**.
1. Select a resource to inspect.
1. On the Action Pane, on the **Resource** tab, in the **View** group, select **Capacity load**.

To open the **Capacity load** page so you can review the available capacity on a resource group, follow these steps:

1. Go to **Organization administration \> Resources \> Resource groups**.
1. Select a resource group to inspect.
1. On the Action Pane, on the **Resource group** tab, in the **View** group, select **Capacity load**.

## Apply a single level of marking when firming planned orders

The *Make-to-order supply automation* feature adds the ability to limit inventory marking to a single level when firming planned orders. It adds the following new options to the **Update marking** drop-down list provided on the **Firming** dialog box when you are firming a planned order. It also adds these options to the **Standard update** tab of the **Master planning parameters** page, where you establish the default selection for the **Firming** dialog box. <!-- KFM: Confirm this. -->

- *Single level standard* – Uses single-level marking, which lets you keep component assignment flexible for production orders after firming. Single-level marking enables the system to optimize for last-minute demand changes. With standard single-level marking, requirement orders are marked against their fulfillment orders, but fulfillment orders are not marked if they have remaining quantity.
- *Single level extended* – Uses single-level marking, but with extended single-level marking, requirement orders are marked against their fulfillment orders and fulfillment orders are marked regardless of whether any quantity remains or not.

For more information about how to use marking and where to find these settings, see [Inventory marking with Planning Optimization](planning-optimization/marking.md) <!-- KFM: Confirm the new texts added to the target of this link. -->

## Override negative days (delay tolerance) on Master Plan

Negative days (delay tolerance) parameter can be controlled under Master Plan form to improve flexibility for each master plan.

Whenever you enable **Negative days** on Master plan, the entered value in Negative days will be used for all products during planning regardless of any specific value has been defined in **Coverage Groups** or **Item Coverage**

## Use latest possible supply during pegging

By enabling the **Use latest possible supply** option, you can keep the products available for last-minute orders and optimize the usage of the existing supply.

Setting can be set under **Pegging sequence** group on **Master plans**, **Coverage groups** and **Item coverage** forms. Before this change, the group is called On-hand inventory.

The pegging sequence will be as per selection:

|  | **Use latest supply = Yes** | **Use latest supply = No** |
|-------------------------|-------------------------|-------------------------|
| **On-hand before all supply** | <ol><li>On-hand</li><li>Existing supply that can meet the demand date</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>Create new supply (planned order)</li></ol> | <ol><li>On-hand</li><li>Existing supply that can meet the demand date</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>Create new supply (planned order)</li></ol> |
| **On-hand after all supply** | <ol><li>Existing supply that can meet the demand date</li><li>On-hand</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>Create new supply (planned order)</li></ol> | <ol><li>Existing supply that can meet the demand date</li><li>Existing supply that can't meet the demand date, but still within negative days</li><li>On-hand</li><li>Create new supply (planned order)</li></ol> |


## Fulfillment policy on Sales Header

Fulfillment policy for releasing to warehouse can be controlled for each sales order. To override the default value of fulfillment policy, the user can enter the new value on **Order fulfillment policy** field for each sales order on header section.

Default fulfillment policy shows the value if any policy is set on customer setup, otherwise the value from the account receivable warehouse parameters. Default fulfillment policy field is only informational and read-only and this cannot be changed in sales order form.

## Delivery information on purchase order line

You can define **Delivery terms** and **Mode of delivery** parameters per purchase order line under the delivery tab of line details. If these fields are empty, the value will be used from purchase order header.

The update of the value for delivery information on purchase header can be configured to update for lines by setting the options under Procurement and sourcing parameters.

The value of delivery information in the purchase line will be synchronized through intercompany orders.

## Synchronization of External item and description through intercompany

You can enable the synchronization of **External** item reference and **Text** description of item through intercompany orders no matter if the order is direct delivery or not.

If **Customer account** is set on purchase header, purchase order lines will take **External** item and **Text** descriptions from this **Customer account** rather than from the vendor specified on the purchase order.

For synchronization, you need to enable **External item ID and item name** policy on **Purchase order policies** under customer's **Intercompany** parameters.
