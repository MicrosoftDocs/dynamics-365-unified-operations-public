---
title: Delivery schedules
description: Delivery schedules allow you to track order line quantity when you are using multiple deliveries for a single sales order, sales quotation, or purchase order.
author: kamaybac
ms.author: adpattanaik
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
ms.search.form: PurchDeliverySchedule, SalesDeliverySchedule, SalesQuotationDeliverySchedule, SalesQuotationDeliverySchedule
ms.assetid: 44cac104-c36c-4371-a992-9178b3fd65e9
---

# Delivery schedules

[!include [banner](../includes/banner.md)]

Delivery schedules allow you to track order line quantity when you are using multiple deliveries for a single sales order, sales quotation, or purchase order.

Use a delivery schedule when the total quantity on an order or quotation line must be delivered in multiple shipments. Individual shipments are represented by delivery lines. Two or more delivery lines make up one delivery schedule. The delivery lines can have different delivery dates, quantities, modes of delivery, and storage dimensions, such as site and warehouse.  

**Example of a delivery schedule**

| Item                              | Value                                    |
|-----------------------------------|------------------------------------------|
| Total order (original order line) | 600 chairs                               |
| Requested delivery schedule       | 100 chairs per month                     |
| Requested time frame for delivery | 6 months, on the first day of each month |

In this scenario, the customer requests delivery of 600 chairs in batches of 100 chairs over a period of six months. To keep track of the delivery requirements, you create a delivery schedule. On the delivery schedule page, you create six separate delivery lines. Each delivery line contains 100 chairs and indicates the delivery date for those 100 chairs. In this case, each line is offset on the first of the month for six consecutive months.  

When you create a delivery schedule, the type of the original order line is automatically changed to **Order line with multiple deliveries**. A line of this type is referred to as a commercial line and is marked by an icon. The delivery line is marked by a different icon. If you change a quantity on a delivery line, the commercial line is updated to the total quantity of the delivery schedule. If a trade agreement has defined a total discount for the order, the delivery schedule ensures that your order is eligible for the total order discount, even when the order is split into separate deliveries.  

Orders that have a delivery schedule are processed against the delivery lines. Processing includes the posting of packing slips, product receipts, and invoicing.  

Document printouts of orders and quotations that have a delivery schedule show only the delivery lines. They don't show the original lines (commercial lines). **Note:** In addition, only the delivery lines are shown when you perform these actions:

-   Post
-   Copy pages
-   Browse list pages and reports

When you confirm sales quotations, the resulting sales orders show the whole delivery schedule, even the order lines that have multiple deliveries. In addition, the whole delivery schedule is shown on all the major pages, such as sales orders, sales quotations, and purchase orders.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]