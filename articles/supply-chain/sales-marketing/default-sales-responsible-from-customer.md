---
title: Default the sales responsible worker from the customer
description: Learn how to default sales order responsibility from customer records, distinguish worker assignments, and manage exceptions.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: CustTable, SalesCreateOrder, SalesTable, SalesTableListPage
ms.topic: how-to
ms.date: 10/22/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Default the sales responsible worker from the customer

[!include [banner](../includes/banner.md)]

Sales order processors don't always manage the customer relationships for the orders they enter. In Microsoft Dynamics 365 Supply Chain Management, you can assign an **Employee responsible** to each customer. When you create a sales order, this assignment supplies the default **Sales responsible** worker, separately from the **Sales taker** who takes the order.

## Prerequisites

To use the behavior described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.50 or later.
- You must have a customer record and a worker to assign as its **Employee responsible**. The following procedure explains how to make this assignment.

This defaulting behavior is on by default. You don't need to turn on a feature in feature management.

## Sales responsible and sales taker

Use the following assignments to distinguish responsibility for a customer or sale from order entry:

- **Employee responsible** – The worker in your organization who manages the customer relationship. Set this assignment on the customer record to provide a default for new sales orders.
- **Sales responsible** – The worker who's responsible for the sales order. The default comes from the ordering customer's **Employee responsible**, if one is assigned. You can change this value for an individual order without changing the customer record.
- **Sales taker** – The worker who takes the sales order. The default is the worker associated with the user who creates the order. Defaulting **Sales responsible** from the customer doesn't change this assignment.

For example, an account manager might manage a customer while an order processor enters its orders. The account manager defaults as **Sales responsible**, and the order processor defaults as **Sales taker**.

The **Sales taker** default can be blank if the user isn't associated with a worker.

## Assign an employee responsible to a customer

Assign the worker who manages the customer relationship so that order processors don't have to select that worker on each new order.

1. Go to **Sales and marketing** > **Customers** > **All customers**.
1. Open the customer record and, on the Action Pane, select **Edit**.
1. Expand the **Sales demographics** FastTab.
1. In the **Employee responsible** field, select the worker in your organization who should be responsible for the customer's sales orders.
1. On the Action Pane, select **Save**.

> [!NOTE]
> The worker must have an employment record in the current legal entity unless cross-company assignments are allowed. To allow these assignments, set **Assign employee responsible from other legal entities** to *Yes* on the **Accounts receivable parameters** page.

## Create a sales order with the customer default

Create an order directly for the customer to verify the default assignments. The ordering customer supplies **Sales responsible**, even if the order uses a different invoice account.

1. Go to **Sales and marketing** > **Sales orders** > **All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Customer account** field, select the customer that you configured.
1. Complete any other required fields, and select **OK**.
1. Switch to the **Header** view.
1. Expand the **Setup** FastTab and review the following fields:
    - **Sales responsible** – The **Employee responsible** worker from the customer that you selected in **Customer account**.
    - **Sales taker** – The worker associated with the user who created the sales order.
1. If necessary, change **Sales responsible** to the worker who should be responsible for this particular order. The worker lookups for both order fields show only active workers.
1. On the Action Pane, select **Save**.

If you change **Customer account** on an order, the application reapplies the newly selected customer's default. A nonblank **Employee responsible** replaces the order's existing **Sales responsible**, including a value that you selected manually.

> [!NOTE]
> Orders created from sales quotations can copy both **Sales responsible** and **Sales taker** from the quotation. Sales agreements can supply **Sales responsible** from the agreement's header defaults. Review these assignments when you create an order from either document. Learn more in [Create and edit sales quotations](tasks/create-edit-sales-quotations.md) and [Sales agreements overview](sales-agreements.md).

## Behavior when employee responsible is blank

If a customer doesn't have an **Employee responsible**, customer defaulting leaves the order's **Sales responsible** unchanged. On a new order, this normally preserves the current-worker default. On an existing order, it preserves the worker who was already assigned.

This behavior also applies when you change **Customer account** to a customer without an **Employee responsible**. For example, the responsible worker from the previous customer can remain on the order. Review the retained assignment to make sure it's appropriate for the new customer.

## Changes to existing sales orders

The customer assignment is copied when you initialize or reinitialize the order from the customer. It isn't a continuously synchronized link. Changing **Employee responsible** on the customer doesn't automatically update existing sales orders.

For a one-off reassignment, open the existing order, switch to the **Header** view, and expand the **Setup** FastTab. Update **Sales responsible** and save the order. If you're assigning a new account manager for future orders, also update **Employee responsible** on the customer.

## Related information

- [Create sales orders](tasks/create-sales-orders.md)
- [Create and edit sales quotations](tasks/create-edit-sales-quotations.md)
- [Sales agreements overview](sales-agreements.md)
- [Sales and marketing overview](overview-sales-marketing.md)
