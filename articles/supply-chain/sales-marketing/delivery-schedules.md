---
title: Delivery schedules
description: Learn about delivery schedules, which you can use to track order line quantities when you use multiple deliveries for a single sales order, sales quotation, or purchase order.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: PurchDeliverySchedule, SalesDeliverySchedule, SalesQuotationDeliverySchedule, SalesQuotationDeliverySchedule
ms.topic: conceptual
ms.date: 01/27/2025
ms.custom: 
  - bap-template
---

# Delivery schedules

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Supply Chain Management, delivery schedules are used to manage and track the delivery of order quantities in multiple shipments. They are particularly useful when a single sales order, sales quotation, or purchase order must be delivered in several parts over time.

Here's a breakdown of how delivery schedules work:

1. **Create delivery schedules.** When you create a delivery schedule, the total quantity of an order line is divided into multiple delivery lines, based on the delivery schedule, quantity, mode of delivery, and storage dimensions (such as site and warehouse). Each delivery line represents a separate shipment.
1. **Manage delivery lines.** Delivery lines can have different delivery dates, quantities, modes of delivery, and storage dimensions. The original order line is converted to a *commercial line*, which acts as a header for the delivery lines. If delivery line quantities are changed, the commercial line is automatically updated so that it reflects the total quantity.
1. **Process orders.** Orders that have a delivery schedule are processed against the delivery lines. This processing includes the posting of packing slips, product receipts, and invoicing. When documents such as confirmations or invoices are printed, only the delivery lines are shown, not the original commercial lines.

When you create a delivery schedule, the type of the original order line is automatically changed to *Order line with multiple deliveries*. A line of this type is referred to as a commercial line and is marked by a symbol. The delivery line is marked by a different symbol. If you change a quantity on a delivery line, the commercial line is updated to the total quantity of the delivery schedule. If a trade agreement defines a total discount for the order, the delivery schedule ensures that your order is eligible for the total order discount, even when the order is split into separate deliveries.

Orders that have a delivery schedule are processed against the delivery lines. This processing includes the posting of packing slips, product receipts, and invoicing.

Document printouts of orders and quotations that have a delivery schedule show only the delivery lines. They don't show the original lines (commercial lines).

> [!NOTE]
> Only the delivery lines are shown when you perform the following actions:
>
> - Post
> - Copy pages
> - Browse list pages and reports

When you confirm sales quotations, the resulting sales orders show the whole delivery schedule, even the order lines that have multiple deliveries. In addition, the whole delivery schedule is shown on all the major pages, such as sales orders, sales quotations, and purchase orders.

## Example of a delivery schedule

In this example, a customer requests delivery of 600 chairs in batches of 100 chairs over a period of six months. To keep track of the delivery requirements, you create a delivery schedule. On the delivery schedule page, you create six separate delivery lines. Each delivery line contains 100 chairs and indicates the delivery date for those 100 chairs. In this case, each line is offset on the first of the month for six consecutive months.

| Item                              | Value                                    |
|-----------------------------------|------------------------------------------|
| Total order (original order line) | 600 chairs                               |
| Requested delivery schedule       | 100 chairs per month                     |
| Requested time frame for delivery | 6 months, on the first day of each month |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
