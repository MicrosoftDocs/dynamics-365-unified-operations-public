---
title: Sales and purchase cycles for Spain
description: Learn how to set up sales order or purchase order cycles for a vendor or customer for legal entities in Spain in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2025
ms.reviewer: johnmichalak
ms.search.region: Spain
ms.search.validFrom: 2016-11-30
---

# Sales and purchase cycles for Spain

[!include [banner](../../includes/banner.md)]

This article explains how to set up sales order or purchase order cycles for a vendor or customer for legal entities in Spain in Microsoft Dynamics 365 Finance.

Depending on the requirements of their customers and vendors, some Spanish companies don't update all documents that are included in the sales or purchase cycle. Here are some examples of sales or purchase documents that aren't updated:

- Quotes
- Confirmations
- Packing slips
- Invoices

For legal entities that have their primary address in Spain, you can specify which documents should be available on sales orders or purchase orders. You can also specify which documents should be available for customers or vendors.

## Prerequisites

Before you can set up default documents for the sales and purchase cycles, you must set up the following parameters:

- **Sales cycle**: Select this option on the **Accounts receivable parameters** page to set up a default sales document cycle for customers. You can also select the document types that will be available on sales orders.
- **Purchase cycle**: Select this option on the **Procurement and sourcing parameters** page to set up a default purchase document cycle for vendors. You can also select the document types that will be available on purchase orders.

## Set up a document cycle for each customer or vendor

You can specify which documents are active for a specific customer or vendor.

To set up a specific sales document cycle for a customer, follow these steps.

1. In Dynamics 365 Finance, go to the **All customers** page.
1. Select a customer.
1. Select **Sell** \> **Set up** \> **Sales cycle** \> **Edit**.

To set up a specific purchase document cycle for a vendor, follow these steps.

1. In Dynamics 365 Finance, go to the **All vendors** page.
1. Select a vendor.
1. Select **Procurement** \> **Set up** \> **Purchase cycle** \> **Edit**.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
