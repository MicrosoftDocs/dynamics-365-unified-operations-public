---
title: Delivery schedules
description: Delivery schedules allow you to track order line quantity when you're using multiple deliveries for a single sales order, sales quotation, or purchase order.
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

In Supply Chain Management, delivery schedules are used to manage and track the delivery of order quantities in multiple shipments. This is particularly useful when a single sales order, sales quotation, or purchase order needs to be delivered in several parts over time.

Here's a breakdown of how it works:

1. **Create delivery schedules** – When you create a delivery schedule, the total quantity of an order line is divided into multiple delivery lines specific to its delivery schedule, quantity, mode of delivery, and storage dimensions. Each delivery line represents a separate shipment.
1. **Manage delivery lines** – Delivery lines can have different delivery dates, quantities, modes of delivery, and storage dimensions (like site and warehouse). The original order line is converted into a commercial line, which acts as a header for the delivery lines. Changes to delivery line quantities automatically update the commercial line to reflect the total quantity.
1. **Process orders** – Orders with delivery schedules are processed against the delivery lines. This includes posting packing slips, product receipts, and invoicing. When documents like confirmations or invoices are printed, only the delivery lines are shown, not the original commercial lines.

When you create a delivery schedule, the type of the original order line is automatically changed to *Order line with multiple deliveries*. A line of this type is referred to as a commercial line and is marked by an icon. The delivery line is marked by a different icon. If you change a quantity on a delivery line, the commercial line is updated to the total quantity of the delivery schedule. If a trade agreement has a total discount for the order defined, the delivery schedule ensures that your order is eligible for the total order discount, even when the order is split into separate deliveries.

Orders that have a delivery schedule are processed against the delivery lines. Processing includes the posting of packing slips, product receipts, and invoicing.

Document printouts of orders and quotations that have a delivery schedule show only the delivery lines. They don't show the original lines (commercial lines).

> [!NOTE]
> Only the delivery lines are shown when you perform the following actions:
>
> - Post
> - Copy pages
> - Browse list pages and reports

When you confirm sales quotations, the resulting sales orders show the whole delivery schedule, even the order lines that have multiple deliveries. In addition, the whole delivery schedule is shown on all the major pages, such as sales orders, sales quotations, and purchase orders.

## Example of a delivery schedule

In this scenario, a customer requests delivery of 600 chairs in batches of 100 chairs over a period of six months. To keep track of the delivery requirements, you create a delivery schedule. On the delivery schedule page, you create six separate delivery lines. Each delivery line contains 100 chairs and indicates the delivery date for those 100 chairs. In this case, each line is offset on the first of the month for six consecutive months.

| Item                              | Value                                    |
|-----------------------------------|------------------------------------------|
| Total order (original order line) | 600 chairs                               |
| Requested delivery schedule       | 100 chairs per month                     |
| Requested time frame for delivery | 6 months, on the first day of each month |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
