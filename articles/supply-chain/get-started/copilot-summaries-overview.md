---
title: AI summaries with Copilot
description: This article provides an overview of the various types of Microsoft Copilot-generated summaries that are available in Dynamics 365 Supply Chain Management.
author: prasungoel
ms.author: prasungoel
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 09/11/2025
ms.update-cycle: 180-days
ms.custom: 
  - bap-template
ms.collection:
  - bap-ai-copilot
---

# AI summaries with Copilot

AI summaries with Microsoft Copilot are available on many of the most-used pages in Dynamics 365 Supply Chain Management. These summaries provide a quick overview of the most important information that's related to the page, personalized for the current user. Summaries can include information such as the number of lines on a purchase order, the number of items in a warehouse, or the number of overdue invoices for a vendor.

The information that Copilot provides depends on the current page and user context. For example, the information can vary based on the other pages that the user works with the most, and it's limited based on the user's security roles and permissions.

> [!TIP]
> Users can provide feedback to Copilot by selecting the thumbs-up or thumbs-down buttons shown under the summaries. You can add support for written feedback by turning on [enhanced user feedback for Copilot](../../fin-ops-core/dev-itpro/copilot/enable-copilot-feedback.md). This feedback helps improve the quality of the summaries that Copilot generates.

## TechTalk video

For a video overview of all of the features described in this topic, watch [Copilot Capabilities in Dynamics 365 Finance and SCM | Dynamics 365 TechTalk](https://www.youtube.com/watch?v=QQN7tZYr1jc).

## Prerequisites

Before you can use AI summaries with Copilot, your system must meet the following requirements:

- You must be running one of the following versions of Supply Chain Management:

    - Version 10.0.39 with proactive quality update 3 (PQU-3) or later
    - Version 10.0.40 with PQU-1 or later
    - Any build of version 10.0.41 or later

- [Power Platform Integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md) must be enabled for your environment. Usually, all the components that are required to use Copilot summaries are automatically deployed when Power Platform Integration is enabled. However, if they don't work as expected, see [Enable Copilot capabilities in finance and operations apps](../../fin-ops-core/dev-itpro/copilot/enable-copilot.md) for more detailed requirements.

- To use Workload insights with Copilot in the Warehouse Management mobile app, you must be running Warehouse Management mobile app version 2.3.2.0 or later.

## Turn AI summaries with Copilot on or off

Admins can control which AI summaries are shown in your system by searching for the following features in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

- Workload insights with Copilot in the Warehouse Management mobile app – *Context-aware worker summary screen in WMA*
- Product hover summaries – *Product summary when hovering on item*
- Released product details summary – *Product details summary*
- Purchase order summary – *Purchase order summary*
- Sales order summary – *Sales order summary*
- Vendor summary – *Vendor summary*

All of these features are turned on by default, but you can turn any or all of them off if you don't want to see them.

## Workload insights with Copilot in the Warehouse Management mobile app

The Warehouse Management mobile app provides a *workload* page that shows work summaries and AI-generated insights to help warehouse workers better plan their shift. The information can include the following details:

- The number of pick and receive work headers or work lines.
- The number of active warehouse mobile app sessions in the warehouse.
- Insights into the available work types.
- The current workload. This information can be shown either as work headers or work lines.
- Details of the available work per work type.
- More information about the available work. Microsoft Copilot generates this information in natural language.

The following illustration shows an example of the workload page in the Warehouse Management mobile app. When workers first open the page, it shows an overview of unstarted tasks that are scheduled for the current warehouse, together with a natural-language summary that Copilot generates (left). Workers can then tap any tile to view detailed information about open work by type (right). This information helps them quickly grasp their objectives for the day.

:::image type="content" source="../warehousing/media/wma-insights-worklines.png" alt-text="Screenshots of the initial and detailed views of unstarted work lines scheduled for the current warehouse." lightbox="../warehousing/media/wma-insights-worklines.png":::

Learn more in [Workload insights with Copilot in the Warehouse Management mobile app](../warehousing/warehouse-management-mobile-app-insights.md).

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

## Traceability summaries

The [Traceability Add-in for Dynamics 365 Supply Chain Management](../traceability/traceability-overview.md) lets you collect business and industry-specific data across the product value chain, which can be used for regulation audits and compliance process. The Traceability app in Power Apps provides two types of Copilot-generated summaries: activity summaries and where-used summaries.

### Traceability activity summaries

Traceability collects activity events across the supply chain and product lifecycle, but it isn't always easy for users to get a quick picture of a tracked object's history. Copilot analyzes the many activity events associated with a selected tracked object and then provides a natural-language summary that helps you quickly understand the object's history. This summary is shown at the top of the full list of activity events.

### Traceability where-used summaries

Traceability provides a comprehensive where-used insight report, which lets you track the usage of items across various processes. Copilot offers detailed where-used summaries at both the item-number and quantity levels, allowing for precise analysis.

## Related information

- [Workload insights with Copilot in the Warehouse Management mobile app](../warehousing/warehouse-management-mobile-app-insights.md)
- [Responsible AI FAQ for AI summaries with Copilot](../faq-summaries.md)
- [Responsible AI FAQ for Workload insights with Copilot](../faq-wma-copilot.md)
