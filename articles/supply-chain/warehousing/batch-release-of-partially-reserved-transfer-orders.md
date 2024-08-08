---
title: Batch release of partially reserved transfer orders
description: Learn how to set up and apply batch release of partially reserved transfer orders from a mobile device with an outline on where batch releases apply.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 05/26/2017
ms.reviewer: kamaybac
ms.search.form: WHSLoadPlanningWorkbench, WHSFulfillmentPolicy
---

# Batch release of partially reserved transfer orders

[!include [banner](../includes/banner.md)]

The functionality for batch release of partially reserved transfer orders lets
you partially release transfer orders to a warehouse by using a batch job.
Because you have the option to release a partial quantity, you don’t have to
wait for the whole order quantity to be available in the warehouse before you
release an order.

The release of orders to a warehouse is a warehouse management processes (WMS)
process. This process involves activities, such as picking, packing, and
shipping, that a warehouse worker can perform by using a mobile device.

## Where it applies

For this functionality, transfer orders are released to a warehouse by using a
batch job. This functionality is useful when you don’t have enough inventory in
the warehouse, but you still want to transfer items from one warehouse to
another.

## How it is set up

### Specify fulfillment criteria for transfer orders and sales orders

Before an order can be partially released to a warehouse in a batch, the
fulfillment criteria must be met. These fulfillment criteria are determined by
the fulfillment policy.

Fulfillment policies for transfer orders and sales orders are specified at the
company level. Depending on the setup of the fulfillment policy, the release of
orders in a batch will be accepted or rejected. The orders will then be
processed accordingly.

- To create fulfillment policies for transfer orders and sales orders, go to **Warehouse management \> Setup \> Release to warehouse \> Fulfillment policies**, and create a fulfillment policy by entering a name and a description.
- To specify a fulfillment rate, a value type, and the message that is shown if the fulfillment policy is violated, go to **Warehouse management \> Setup \> Release to warehouse \> Fulfillment policies**, and set the **Fulfillment rate**, **Value type**, and **Fulfillment violation message** fields.

### Set the fulfillment policies for transfer orders and sales orders

- To set the fulfillment policies for transfer orders, go to **Inventory management \> Setup \> Inventory and warehouse management parameters**, and then, on the **Transfer orders** tab, in the **Warehouse management** section, select a transfer order fulfillment policy.
- To set the fulfillment policies for sales orders, go to **Accounts receivable \> Setup \> Accounts receivable parameters**, and then, on the **Warehouse management** tab, select a sales order fulfillment policy.

## Allow release in a batch and specify the quantity that should be released in a batch

A batch job is used to release orders to a warehouse in a batch. The parameters that distinguish the orders that should be run in a batch job are set on the batch job itself.

The **Quantity** parameter specifies whether the whole quantity or the physically reserved quantity should be released in the batch. The **Allow release of partially released orders** parameter determines whether orders in the batch should be accepted or rejected if they were partially released earlier.

- To set the **Quantity** and **Allow release of partially released orders** parameters for transfer orders, go to **Warehouse management \> Release to warehouse \> Automatic release of transfer orders**.
- To set the **Quantity** and **Allow release of partially released orders** parameters for sales orders, go to **Warehouse management \> Release to warehouse \> Automatic release of sales orders**.
- To set the **Quantity** and **Allow release of partially released orders** parameters for outbound shipment orders, go to **Warehouse management \> Release to warehouse \> Automatic release of outbound shipment orders**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
