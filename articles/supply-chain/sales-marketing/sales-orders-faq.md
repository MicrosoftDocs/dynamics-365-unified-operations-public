---
title: Frequently asked questions about sales orders 
description: Access answers to frequently asked questions that come up when working with sales orders in Dynamics 365 Supply Chain Management.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: SalesTable, SalesTableListPage, SalesTableListPage_SalesCancelOrder
ms.topic: faq
ms.date: 08/26/2024
ms.custom: 
  - bap-template
--- 
 
# Sales order FAQs

[!include [banner](../includes/banner.md)]

This page addresses frequently asked questions that come up when working with sales orders in Dynamics 365 Supply Chain Management.

## Can I link a purchase order to a sales order to fulfill demand?

You can create a purchase order from a sales order. Learn more in [Create a purchase order from a sales order](/dynamics365/supply-chain/sales-marketing/tasks/create-purchase-order-sales-order).

## Can I cancel or delete a sales order or return order?

You can cancel only sales orders and return orders that are in a *Created* state. Learn more in [Cancel a return order](/dynamics365/supply-chain/service-management/cancel-return-order).

## Can I restore an invoiced sales order that was deleted?

If an invoiced sales order was deleted by mistake, you can restore it or view its details.

Go to **Customer account \> Transactions \> Original document \> View details**. Find the invoice that you're looking for and select it to view its details. These details include the sales order reference. You should also be able to access the sales order details from that page.

## How do I delete orphaned sales order records?

To clean up orphaned sales order records, run the *Sales order deletion* periodic job by going to either of the following places:

- Sales and marketing \> Periodic tasks \> Clean up \> Delete sales orders
- Retail and commerce \> Retail and commerce IT \> Clean up \> Delete sales orders

## Is there a way to calculate commissions on invoices that have already been posted?

Supply Chain Management doesn't currently support the calculation of commissions for posted invoices.
