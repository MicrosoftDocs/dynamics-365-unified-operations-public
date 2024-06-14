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

- Depending on the summaries that you want to use, the following features must be enabled in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). These features are turned on by default in Supply Chain Management version 10.0.40 and later.

    - Warehouse Management mobile app insights – *Context-aware worker summary screen in WMA*
    - Product hover summaries – *Product summary when hovering on item*
    - Released product details summary – *Product details summary*
    - Purchase order summary – *Purchase order summary*
    - Sales order summary – *Sales order summary*
    - Vendor summary – *Vendor summary*

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

### Status summary for purchase orders

For purchase orders that aren't cancelled, invoiced, or finalized, a detailed status across lines is provided. The section provides insight on the progression of order lines by listing the lines in the following categories:

- *Not fully received* – Lines where the quantity has not been fully registered or received.
- *Fully received, not fully invoiced* – Lines where the quantity has been fully registered or received.
- *Fully invoiced* – Lines where the quantity has been fully invoiced.

The status section provides filter buttons that let you filter to the lines shown for the purchase order according to their status. Use the filter to quickly find relevant lines so you can take appropriate action. Each filter is only shown when at least one line of the indicated status exists. The following filter buttons are available:

- **Not fully received** – If the number of lines awaiting receipts is only for a subset of all lines in the purchase order, then a filter option is provided to easily filter to those lines and take action.
- **Fully received, not fully invoiced** – If the number of lines fully received but not yet fully invoiced is only for a subset of all lines in the purchase order, then a filter option is provided to easily filter to those lines and take action.

### Insight summary for purchase orders

For purchase orders which are not cancelled, received, invoiced, or finalized, two additional insights across lines are provided: Number of *Nearly overdue or overdue lines* and  Number of *Lines without confirmed receipt dates*. These two insights are complemented with two filter options, by which it is possible to with one click to filter to the PO lines for each of the insights. Note that If this is for a subset of all lines in the purchase order, then filter options are provided to easily filter to those lines and take action.

- *Overdue or Nearly overdue lines* – Number of lines awaiting receipts where current date is equal to or before the expected receipt date (requested or confirmed) are reported.
- *Lines without confirmed receipt dates* – Number of lines without confirmed receipt dates awaiting not fully received.

## Sales order summary

The **Sales order details** page includes a **Summary by Copilot** FastTab that shows an overview of the selected sales order's status. For example, it shows the number of partially or fully confirmed, received, and invoiced lines. The FastTab also shows other selected insights, such as a summary of lines that are overdue or nearly overdue.

### Status summary for sales orders

For Sales orders which are not cancelled or invoiced, a detailed status across lines is provided. The status section provides aggregated information on the progression of order lines in different status buckets. Lines where the quantity has not been fully picked, are reported as *Not fully picked*. Lines where the quantity has not been fully shipped, are reported as *Not fully shipped*. Lines where the quantity has not been fully invoiced, are reported as *Not fully invoiced*.

The information is intended to focus on providing a quick overview of the progression of all SO lines. Compared to purchase order summarization status, sales order summarization status groups lines in buckets which are forward looking. Rather than focusing on what has happened, the lines are grouped in buckets on what is expected to happen from a fulfillment perspective: Not fully picked (representing lines where pick is expected to happen), Not fully shipped (representing lines where Pick is not expected to happen or has already been completed), not fully invoiced (representing lines which have been completely shipped but not fully invoiced yet). Once a line has been fully invoiced, it is no longer reported in the status section, as no additional action is expected fulfillment wise.

The status is complemented by two filter options, by which it is possible to, with one click, to filter to the SO lines for the status buckets *Filter to lines not fully picked* and *Filter to lines not fully shipped*. Note that a filter option is available only if it includes a subset of all lines in the sales order. Using the filter option allows easy and fast access to lines to take action.

- *Filter to lines not fully picked* – If the number of lines awaiting pick represents only a subset of all lines in the sales order, then a filter option is provided to easily filter to those lines and take action.
- *Filter to lines not fully shipped* – If the number of lines fully picked or not requiring picking represents only a subset of all lines in the sales order, then a filter option is provided to easily filter to those lines and take action.

### Insight summary for sales orders

For sales orders which are not cancelled, delivered, or invoiced, two additional insights across lines are provided: Number of *Nearly overdue or overdue lines* and number of *Lines without confirmed ship dates*. These two insights are complemented with two filter options, by which it is possible to with one click to filter to the SO lines for each of the insights. Note that only if a subset of all lines in the sales order qualify for a filter option, then the filter option is provided to easily filter to those lines and take action.

- *Overdue or Nearly overdue lines* – Number of lines awaiting to be shipped (packing slip posted) where current date is equal to or before the expected ship date (requested or confirmed) are reported.
- *Lines without confirmed ship dates* – Number of lines without confirmed ship dates not fully shipped (packing slip posted).

## See also

- [Responsible AI FAQ for AI summaries with Copilot](../faq-summaries.md)
