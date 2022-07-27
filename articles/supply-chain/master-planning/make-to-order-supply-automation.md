---
title: Make-to-order supply automation
description: XXXX
author: XXXX
ms.date: MM/DD/YYYY
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: XXXX
ms.search.validFrom: YYYY-MM-DD
ms.dyn365.ops.version: 10.0.XX
---

# Make-to-order supply automation

[!include [banner](../includes/banner.md)]

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

## Number of days filter on Capacity load page

The *Make-to-order supply automation* feature adds a **Number of days** field to the **Capacity load** page. Use the **Number of days** field to limit the number of days shown in the grid. If you return to the page later, it will remember the value you most recently entered here.

To open the **Capacity load** page, go to 

## Single level of inventory marking policy

There are options called *Single level standard* and*Single level extended* for inventory marking to keep component assignment flexible for production orders after firming, which enables the system to optimize for last-minute demand changes. In other words, limiting marking to only one level.

The difference between standard and extended is on the remaining quantity on fulfillment orders. Requirement orders are marked against their fulfillment orders, but fulfillment orders are not marked if they have remaining quantity when standard is selected. When extended is selected, fulfillment orders are marked regardless of whether any quantity remains or not.

Please review <https://docs.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/marking> for more information regarding to marking policy.

These new options are available while firming of planned orders, or **Firming/Update Marking** settings under **Master Planning Parameters**.

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
