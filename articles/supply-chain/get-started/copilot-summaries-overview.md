---
title: AI summaries with Copilot
description: This article provides an overview of the various types of Microsoft Copilot-generated summaries that are available in Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 05/30/2024
audience: Application User
ms.custom: 
  - bap-template
---

# AI summaries with Copilot

AI summaries with Microsoft Copilot are available on many of the most-used pages in Dynamics 365 Supply Chain Management. These summaries provide a quick overview of the most important information that's related to the page, personalized for the current user. Summaries can include information such as the number of lines on a purchase order, the number of items in a warehouse, or the number of overdue invoices for a vendor.

The information that Copilot provides depends on the current page and user context. For example, the information can vary based on the other pages that the user works with the most, and it's limited based on the user's security roles and permissions.

## Prerequisites

Before you can use AI summaries with Copilot, your system must meet the following requirements:

- You must be running one of the following versions of Supply Chain Management:

    - Version 10.0.38 with proactive quality update 5 (PQU-5) or later
    - Version 10.0.39 with PQU-3 or later
    - Any build of version 10.0.40 or later

- [Power Platform integration](../power-platform/enable-power-platform-integration.md) must be enabled for your environment. Usually all required Copilot components are deployed automatically when Power Platform integration is enabled, but if they aren't working as expected, see [Enable Copilot capabilities in finance and operations apps](../../fin-ops-core/dev-itpro/copilot/enable-copilot.md) for more detailed requirements.

- Depending on the summaries that you want to use, the following features must be enabled in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). These features are turned on by default in Supply Chain Management version 10.0.40 and later.

    - Warehouse Management mobile app insights – *Context-aware worker summary screen in WMA*
    - Product hover summaries – *Product summary when hovering on item*
    - Released product details summary – *Product details summary*
    - Purchase order summary – *Purchase order summary*
    - Sales order summary – *Sales order summary*
    <!-- KFM: Nothing for Vendor summary? -->

- To use Warehouse Management mobile app insights, you must be running Warehouse Management mobile app version 2.3.2.0 or later.

## Warehouse Management mobile app insights

Warehouse Management mobile app insights are provided on the home page of the mobile app. The information that's shown can include the following details:

- The number of pick and receive work lines.
- The number of other warehouse workers who are online in the warehouse where the worker is signed in.
- Insights into the kind of work that's being done. For example, the page might show a worker that most of the current work is related to picking sales orders. It can also show the zone and location where most items must be picked.
- The average number of items per order, plus the average weight and volume of the items.

## Product hover summaries

On most pages that show an item number, users can hover over the item number to view a Copilot-generated summary of the item.

## Released product details summary

The **Released product details** page includes a **Summary by Copilot** FastTab that shows a product summary based on the current user's most-used pages and context.

## Vendor summary

The **All vendors** details page includes a **Summary by Copilot** FastTab that shows status information and insights for the selected vendor. The information that's provided can include the vendor currency, accounting currency, vendor hold status, number of purchase orders, posted vendor invoices, payment status, and more. It can also include the number of overdue vendor invoices, purchasing agreements, and active rebates agreements.

## Purchase order summary

The **All purchase orders** details page includes a **Summary by Copilot** FastTab that shows an overview of the selected purchase order's status. For example, it shows the number of partially or fully confirmed, received, and invoiced lines. The FastTab also shows other selected insights, such as a summary of lines that are overdue or nearly overdue.

## Sales order summary

The **Sales order details** page includes a **Summary by Copilot** FastTab that shows an overview of the selected sales order's status. For example, it shows the number of partially or fully confirmed, received, and invoiced lines. The FastTab also shows other selected insights, such as a summary of lines that are overdue or nearly overdue.

## See also

- [Responsible AI FAQ for AI summaries with Copilot](../faq-summaries.md)
