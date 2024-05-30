---
title: AI summaries with Copilot
description: This article provides an overview of the various types of Copilot-generated summaries that are available in Microsoft Dynamics 365 Supply Chain Management. 
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

AI summaries with Copilot are available on many of the most-used pages in Microsoft Dynamics 365 Supply Chain Management. These summaries provide a quick overview of the most important information related to the page, personalized for the current user. Summaries can include information such as the number of lines on a purchase order, the number of items in a warehouse, or the number of overdue invoices for a vendor.

The information provided by Copilot varies to match the current page and user context. For example, the information can vary based on which other pages the user works with the most and is restricted based on each user's security roles and permissions.

## Prerequisites

To use AI summaries with Copilot, your system must meet the following requirements:

- You must be running one of the following versions of Microsoft Dynamics 365 Supply Chain Management:
    - Version 10.0.38 with PQU-5 or later.
    - Version 10.0.39 with PQU-3 or later.
    - Any build of 10.0.40 or later.

- Depending on which summaries you want to use, the following features must be enabled in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). These features are turned on by default in Supply Chain Management version 10.0.40 and newer.
    - Warehouse Management mobile app insights – *Context-aware worker summary screen in WMA*
    - Product hover summaries – *Product summary when hovering on item*
    - Released product details summary – *Product details summary*
    - Purchase order summary – *Purchase order summary*
    - Sales order summary – *Sales order summary*
    <!-- KFM: Nothing for Vendor summary? -->

- To use Warehouse Management mobile app insights, you must be running Warehouse Management mobile app version 2.3.2.0 or higher.

## Warehouse Management mobile app insights

Warehouse Management mobile app insights are provided on the home page of the mobile app. Information that can be shown includes the following:

- The number of pick and receive work lines.
- How many other warehouse workers are online in the warehouse where the worker is signed in.
- Insights into the kind of work being done. For example, it might tell a worker that most of the current work is about picking sales orders and can also show the zone and location where most items are to be picked.
- The average number of items per order, plus the average weight and volume of the items.

## Product hover summaries

On nearly any page that shows an item number, users can hover over the item number to see a Copilot-generated summary of that item.

## Released product details summary

The **Released product details** page provides a **Summary by Copilot** FastTab that provides a product summary according to the current user's most-used pages and context.

## Vendor summary

The **All vendors** details page provides a **Summary by Copilot** FastTab that displays status information and insights for the selected vendor. The information provided can include vendor currency, accounting currency, vendor hold status, number of purchase orders, posted vendor invoices, payment status, and more. It can also include the number of overdue vendor invoices, purchasing agreements, and active rebates agreements.

## Purchase order summary

The **All purchase orders** details page provides a **Summary by Copilot** FastTab that shows an overview of the selected purchase order's status (such as the number of partially or fully confirmed, received, and invoiced lines) and other selected insights (such as a summary of lines that are overdue or nearly overdue).

## Sales order summary

The **Sales order details** page provides a **Summary by Copilot** FastTab that shows an overview of a selected sales order's status (such as the number of partially or fully confirmed, received, and invoiced lines) and other selected insights (such as a summary of lines that are overdue or nearly overdue).
