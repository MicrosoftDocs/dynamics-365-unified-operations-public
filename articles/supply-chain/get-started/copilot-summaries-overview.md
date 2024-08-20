---
title: AI summaries with Copilot
description: This article provides an overview of the various types of Microsoft Copilot-generated summaries that are available in Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 06/17/2024
ms.custom: 
  - bap-template
ms.collection:
  - bap-ai-copilot
---

# AI summaries with Copilot

AI summaries with Microsoft Copilot are available on many of the most-used pages in Dynamics 365 Supply Chain Management. These summaries provide a quick overview of the most important information that's related to the page, personalized for the current user. Summaries can include information such as the number of lines on a purchase order, the number of items in a warehouse, or the number of overdue invoices for a vendor.

The information that Copilot provides depends on the current page and user context. For example, the information can vary based on the other pages that the user works with the most, and it's limited based on the user's security roles and permissions.

## Prerequisites

Before you can use AI summaries with Copilot, your system must meet the following requirements:

- You must be running one of the following versions of Supply Chain Management:

    - Version 10.0.39 with proactive quality update 3 (PQU-3) or later
    - Version 10.0.40 with PQU-1 or later
    - Any build of version 10.0.41 or later

- [Power Platform Integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md) must be enabled for your environment. Usually, all the components that are required to use Copilot summaries are automatically deployed when Power Platform Integration is enabled. However, if they don't work as expected, see [Enable Copilot capabilities in finance and operations apps](../../fin-ops-core/dev-itpro/copilot/enable-copilot.md) for more detailed requirements.

- Depending on the summaries that you want to use, the following features must be enabled in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). All of these features are turned on by default.
    - Warehouse Management mobile app insights – *Context-aware worker summary screen in WMA*
    - Product hover summaries – *Product summary when hovering on item*
    - Released product details summary – *Product details summary*
    - Purchase order summary – *Purchase order summary*
    - Sales order summary – *Sales order summary*
    - Vendor summary – *Vendor summary*

- To use Warehouse Management mobile app insights, you must be running Warehouse Management mobile app version 2.3.2.0 or later.

## Warehouse Management mobile app insights

Warehouse Management mobile app insights are provided to warehouse workers when they sign in (depending on configuration) and are available on demand by going to the **Summary** page. The information that's shown can include the following details:

- The number of pick and receive work headers or lines.
- The number of Warehouse Management mobile app sessions that are active in the warehouse.
- Insights into the types of work waiting to be completed. This information lets warehouse workers get an overview of the workload so they can better plan their shifts.
- Overall workload, displayed as headers or lines.
- Details of available work by work type.
- AI-generated insights that provide more information about available work.

## Product hover summaries

On most pages that show an item number, users can hover over the item number to view a Copilot-generated summary of the item.

## Released product details summary

The **Released product details** page includes a **Summary by Copilot** FastTab that shows a product summary based on the current user's most-used pages and context.

## Vendor summary

The **All vendors** details page includes a **Summary by Copilot** FastTab that shows status information and insights for the selected vendor. The information that's provided can include the vendor currency, accounting currency, vendor hold status, number of purchase orders, posted vendor invoices, payment status, and more. It can also include the number of overdue vendor invoices, purchasing agreements, and active rebates agreements.

## Purchase order summary

The **All purchase orders** details page includes a **Summary by Copilot** FastTab that shows an overview of the selected purchase order's status. For example, it shows the number of partially or fully confirmed, received, and invoiced lines. The FastTab also shows other selected insights, such as a summary of order lines that are overdue or nearly overdue.

### Status summary for purchase orders

For purchase orders that aren't canceled, invoiced, or finalized, the **Status** section of the **Summary by Copilot** FastTab for purchase orders provides status details that apply across all order lines. The section provides insights into the progression of order lines in each of the following categories:

- **Not fully received** – Lines where the quantity hasn't been fully registered or received.
- **Fully received, not fully invoiced** – Lines where the quantity has been fully registered or received, but not yet fully invoiced.
- **Fully invoiced** – Lines where the quantity has been received and fully invoiced.

As appropriate, the **Status** section provides buttons that let you filter the order lines according to their status. Use the filters to quickly find relevant order lines so that you can take appropriate action. Each filter is shown only when at least one order line has the indicated status. The following filter buttons might be shown:

- **Not fully received** – Show only order lines where the quantity hasn't been fully registered or received.
- **Fully received, not fully invoiced** – Show only order lines where the quantity has been fully registered or received, but not yet fully invoiced.

### Insight summary for purchase orders

For purchase orders that aren't canceled, received, invoiced, or finalized, the **Insights** section of the **Summary by Copilot** FastTab for purchase orders provides two more insights that apply across all order lines:

- **Overdue or nearly overdue lines** – The number of order lines that are awaiting receipt and have an expected receipt date (requested or confirmed) that's after the current date.
- **Lines without confirmed receipt dates** – The number order lines that are awaiting receipt or haven't been fully received, and don't have a confirmed receipt date.

As appropriate, the **Insights** section provides buttons that let you filter the order lines according to their status. Use the filters to quickly find relevant order lines so that you can take appropriate action. Each filter is shown only when at least one order line has the indicated status. The following filter buttons might be shown:

- **Overdue or nearly overdue lines** – Show only order lines that are overdue or nearly overdue.
- **Lines without confirmed receipt dates** – Show only order lines that are awaiting receipt or haven't been fully received, and don't have a confirmed receipt date.

## Sales order summary

The **Sales order details** page includes a **Summary by Copilot** FastTab that shows an overview of the selected sales order's status. For example, it shows the number of partially or fully confirmed, received, and invoiced order lines. The FastTab also shows other selected insights, such as a summary of order lines that are overdue or nearly overdue.

### Status summary for sales orders

For sales orders that aren't canceled or invoiced, the **Status** section of the **Summary by Copilot** FastTab for sales orders provides status details that apply across all order lines. The section provides insights into the progression of order lines in each of the following categories:

- **Not fully picked** – Lines where the quantity hasn't been fully picked.
- **Not fully shipped** – Lines where the quantity has been picked (or doesn't require picking) but not fully shipped.
- **Not fully invoiced** – Lines where the quantity has been completely shipped but not yet fully invoiced.

The **Status** section provides a quick overview of the progression of all sales order lines. Unlike purchase order status summaries, sales order status summaries groups order lines into categories that are forward looking. In other words, instead of focusing on what already happened, the categories focus on what is expected to happen from a fulfillment perspective.

As appropriate, the **Insights** section provides buttons that let you filter the order lines according to their status. Use the filters to quickly find relevant order lines so that you can take appropriate action. Each filter is shown only when at least one order line has the indicated status. The following filter buttons might be shown:

- **Filter to lines not fully picked** – Show only order lines that haven't been fully picked.
- **Filter to lines not fully shipped** – Show only order lines that have been picked (or don't require picking) but not fully shipped.

### Insight summary for sales orders

For sales orders that aren't canceled, delivered, or invoiced, the **Insights** section of the **Summary by Copilot** FastTab for sales orders provides two more insights that apply across all order lines:

- **Overdue or nearly overdue lines** – The number of order lines that waiting to be shipped (packing slip posted) and have an expected ship date (requested or confirmed) that's after the current date.
- **Lines without confirmed ship dates** – The number of order lines that aren't fully shipped (packing slip posted) and don't have a confirmed ship date.

As appropriate, the **Insights** section provides buttons that let you filter the order lines according to their status. Use the filters to quickly find relevant order lines so that you can take appropriate action. Each filter is shown only when at least one order line has the indicated status. The following filter buttons might be shown:

- **Overdue or nearly overdue lines** – Show only order lines that are overdue or nearly overdue.
- **Lines without confirmed ship dates** – Show only order lines that aren't fully shipped (packing slip posted) and don't have a confirmed ship date.

## Related information

- [Responsible AI FAQ for AI summaries with Copilot](../faq-summaries.md)
