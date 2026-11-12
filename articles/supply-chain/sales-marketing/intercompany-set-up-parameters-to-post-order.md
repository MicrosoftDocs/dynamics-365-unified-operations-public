---
title: Post intercompany orders
description: Learn how to set up the system to post intercompany orders, including a step-by-step process.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: how-to
ms.date: 11/10/2026
ai-usage: ai-assisted
ms.reviewer: kamaybac
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines
---

# Post intercompany orders

[!INCLUDE [banner](../../includes/banner.md)]

The system can automatically post both the intercompany purchase order and the original customer invoice when you post an intercompany customer invoice.

> [!NOTE]
> Before you perform this procedure, set up the print management in your organization to point to the correct invoice printer. This setup ensures that the invoice for the original sales order prints on the correct printer.

## Set up intercompany posting

Follow these steps to set the system to post both the intercompany purchase order and the original customer invoice when you post an intercompany customer invoice:

1. Go to **Sales and marketing** > **Sales orders** > **All sales orders**.
1. Open the sales order that you want to work with.
1. On the Action Pane, select **Edit**.
1. Open the **Header** view.
1. On the **Intercompany settings** FastTab, set **Direct delivery** to *Yes* to enable direct delivery throughout the intercompany chain (all orders).
1. On the Action Pane, select **Save** to save the sales order with the new setting.
1. Go to **Procurement and sourcing** > **Vendors** > **All vendors**.
1. Open the vendor that you want to work with.
1. On the Action Pane, open the **General** tab and select **Intercompany**.
1. On the **Intercompany** page, open the **Purchase order policies** tab.
1. In the **Intercompany purchase order (direct delivery)** field group, clear the **Post invoice automatically** checkbox.
1. In the **Original sales order (direct delivery)** field group, select the **Post invoice automatically** and **Print invoice automatically** checkboxes.

## Can't invoice the original sales order or direct delivery purchase order

After you turn on **Post invoice automatically** on the vendor's **Intercompany** page for a direct delivery scenario, you can't invoice the original customer-facing sales order or the original direct delivery purchase order independently. The parameters described in this article control and enforce synchronization of the intercompany and direct delivery invoices.

To continue, invoice the intercompany sales order in the intercompany vendor's legal entity first. The original sales order and purchase order are then synchronized. For the invoicing steps, see [Invoice an intercompany sales order](intercompany-sales-order-for-external-customer.md#invoice-an-intercompany-sales-order).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
