---
title: Order promising
description: This article provides information about order promising. Order promising helps you reliably promise delivery dates to your customers and gives you flexibility so that you can meet those dates.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SalesATP, SalesAvailableDlvDates, SalesCarrier
ms.topic: conceptual
ms.date: 02/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Order promising

[!include [banner](../includes/banner.md)]

This article provides information about order promising. Order promising helps you reliably promise delivery dates to your customers and gives you flexibility so that you can meet those dates.

Order promising calculates the earliest ship and receipt dates, and is based on the delivery date control method and transport days. You can select among the following delivery date control methods:

- **Sales lead time** – Sales lead time is the time between creation of the sales order and shipment of the items. The delivery date calculation is based on a default number of days, and doesn't consider stock availability, known demand, or planned supply.
- **ATP (available-to-promise)** – ATP is the quantity of an item that is available and can be promised to a customer on a specific date. The ATP calculation includes uncommitted inventory, lead times, planned receipts, and issues.
- **ATP + Issue margin** – The shipping date equals the ATP date plus the issue margin for the item. The issue margin is the time that is required to prepare the items for shipment.
- **CTP (capable-to-promise)** – Availability is calculated through explosion. If you're using Planning Optimization, the *CTP* delivery date control method isn't allowed and, if it's selected, will cause an error when the calculation runs. For more information about how to set up and use CTP, see [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md).
- **CTP for Planning Optimization** – Use the CTP calculation that is provided by Planning Optimization. This option has no effect if you're using the built-in master planning engine. For more information about how to set up and use CTP, see [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md).

> [!NOTE]
> When a sales order is updated, the order promising information is only updated if the existing order promising date can't be fulfilled, as illustrated in the following examples:
>
> - **Example 1**: The current order promising date is July 20, but due to increased quantity, you won't be able to deliver until July 25. Because the current date can no longer be met, order promising is triggered.
> - **Example 2**: The current order promising date is July 20, but due to decreased quantity, it's now possible to deliver on July 15. However, because the current date can still be fulfilled, order promising isn't triggered, and July 20 remains the order promising date.

## ATP calculations

The ATP quantity is calculated by using the "cumulative ATP with look-ahead" method. The main advantage of this ATP calculation method is that it can handle cases where the sum of issues among receipts is more than the latest receipt (for example, when a quantity from an earlier receipt must be used to meet a requirement). The "cumulative ATP with look-ahead" calculation method includes all issues until the cumulative quantity to receive exceeds the cumulative quantity to issue. Therefore, this ATP calculation method evaluates whether some of the quantity from an earlier period can be used in a later period.

The ATP quantity is the uncommitted inventory balance in the first period. Typically, it's calculated for each period in which a receipt is scheduled. The program calculates the ATP period in days and calculates the current date as the first date for the ATP quantity. In the first period, ATP includes on-hand inventory minus customer orders that are due and overdue.

ATP is calculated by using the following formula:

ATP = ATP for the previous period + Receipts for the current period – Issues for the current period – Net issue quantity for each future period until the period when the sum of receipts for all future periods, up to and including the future period, exceeds the sum of issues up to and including the future period.

Notice that the ATP calculation doesn't include information around expiry date and beyond the ATP time fence that the system expects when any quantity can be promised.

When there are no more issues or receipts to consider, the ATP quantity for the following dates is the same as the latest calculated ATP quantity.

If not all the dimensions that are used for an item are given when the ATP check is completed, they can still be specified on the issue and receipts. In this case, in the ATP calculation, the receipts and issues must be aggregated to the existing dimensions to reduce the number of receipt and issue lines that are used in the ATP calculation.

The ATP quantity that is shown is always greater than or equal to 0 (zero). If the calculation returns a negative ATP quantity (for example, if the quantity that was previously promised exceeds the available quantity), the quantity is automatically set to 0.

### Example

The **ATP backward demand time fence** field controls how far back in time to look for delayed demand orders or inventory issues. The **ATP backward supply time fence** field controls how far back in time to look for delayed supply orders or inventory receipts. For example, if orders that are delayed by only seven days should be considered in the ATP calculation, both fields should be set to **7**.

The **ATP delayed demand offset time** and **ATP delayed supply offset time** fields control when the delayed demand or supply will be considered in the ATP calculation. For example, if the delayed supply and demand should be considered in the ATP calculation the day after tomorrow, both fields should be set to **2**. A value of **2** means that the quantity of an item on a delayed purchase order that should be considered in the ATP calculation will be seen as available two days after the current date.

For the following example, **7** is entered in the **ATP backward demand time fence** and **ATP backward supply time fence** fields, and **1** is entered in the **ATP delayed demand offset time** and **ATP delayed supply offset time** fields.

A purchase order for 200 pieces of a product that should have been received three days ago hasn't been received yet. Therefore, a sales order line for 75 pieces of the same product that should have been shipped yesterday hasn't been shipped.

A customer calls and wants to order 150 pieces of the same product. When you verify the availability of the product, you find that another purchase order for 100 pieces of the product will be delivered 10 days later.

You create a sales order line for the product and enter **150** as the quantity.

Because the delivery date control method is ATP, the ATP data is calculated to find the earliest possible ship date. Based on the settings, the delayed purchase order and sales order are considered, and the resulting ATP quantity for the current date is 0. Tomorrow, when the delayed purchase order is expected to be received, the ATP quantity is calculated as more than 0 (in this case, it's calculated as 125). However, 10 days from now, when the additional purchase order for 100 pieces is expected to be received, the ATP quantity becomes more than 150.

Therefore, the ship date is set to 10 days from now, based on the ATP calculation. Therefore, you tell the customer that the requested quantity can be delivered 10 days from now.

## CTP calculations

CTP functionality lets you give customers realistic dates for when you can promise specific goods. For each sales line, you can provide a date that takes account of existing on-hand inventory, production capacity, and transportation times.

CTP extends ATP functionality by considering capacity information. Whereas ATP considers only material availability and assumes infinite capacity resources, CTP considers availability of both materials and capacity. Therefore, it provides a more realistic picture of whether demand can be satisfied within a given time frame.

CTP works slightly differently, depending on the master planning engine that you're using (Planning Optimization or the built-in engine). CTP for Planning Optimization currently supports only a subset of the CTP scenarios that are supported by the built-in engine.

For detailed information about how to set up and use CTP for each engine, see [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md).

## Next steps

- [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md)
- [Delivery alternatives](delivery-alternatives.md)
- [Inventory Visibility on-hand change schedules and available to promise](../inventory/inventory-visibility-available-to-promise.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
