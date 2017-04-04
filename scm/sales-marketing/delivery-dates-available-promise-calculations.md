---
# required metadata

title: Order promising
description: This article provides information about order promising. Order promising helps you reliably promise delivery dates to your customers and gives you flexibility so that you can meet those dates.
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: SalesATP, SalesAvailableDlvDates
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 193933
ms.assetid: 676fc53a-fa25-4688-9f26-1005316763b8
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Order promising

This article provides information about order promising. Order promising helps you reliably promise delivery dates to your customers and gives you flexibility so that you can meet those dates.

Order promising calculates the earliest ship and receipt dates, and is based on the delivery date control method and transport days. You can select among four delivery date control methods:

-   **Sales lead time** – Sales lead time is the time between creation of the sales order and shipment of the items. The delivery date calculation is based on a default number of days, and does not consider stock availability, known demand, or planned supply.
-   **ATP (available-to-promise)** – ATP is the quantity of an item that is available and can be promised to a customer on a specific date. The ATP calculation includes uncommitted inventory, lead times, planned receipts, and issues.
-   **ATP + Issue margin** – The shipping date is equal to the ATP date plus the issue margin for the item. The issue margin is the time that is required to prepare the items for shipment.
-   **CTP (capable-to-promise)** – Availability is calculated through explosion.

## ATP calculations
The ATP quantity is calculated by using the “cumulative ATP with look-ahead” method. The main advantage of this ATP calculation method is that it can handle cases where the sum of issues among receipts is more than the latest receipt (for example, when a quantity from an earlier receipt must be used to meet a requirement). The “cumulative ATP with look-ahead” calculation method includes all issues until the cumulative quantity to receive exceeds the cumulative quantity to issue. Therefore, this ATP calculation method evaluates whether some of the quantity from an earlier period can be used in a later period.  

The ATP quantity is the uncommitted inventory balance in the first period. Typically, it's calculated for each period in which a receipt is scheduled. The program calculates the ATP period in days and calculates the current date as the first date for the ATP quantity. In the first period, ATP includes on-hand inventory minus customer orders that are due and overdue.  

ATP is calculated by using the following formula:  

ATP = ATP for the previous period + Receipts for the current period – Issues for the current period – Net issue quantity for each future period until the period when the sum of receipts for all future periods, up to and including the future period, exceeds the sum of issues up to and including the future period.  

When there are no more issues or receipts to consider, the ATP quantity for the following dates is the same as the latest calculated ATP quantity.  

If not all the dimensions that are used for an item are given when the ATP check is completed, they can still be specified on the issue and receipts. In this case, in the ATP calculation, the receipts and issues must be aggregated to the existing dimensions to reduce the number of receipt and issue lines that are used in the ATP calculation.  

The ATP quantity that is shown is always greater than or equal to 0 (zero). If the calculation returns a negative ATP quantity (for example, if the quantity that was previously promised exceeds the available quantity), the program automatically sets the quantity to **0**.

### Example

The **ATP backward demand time fence** field controls how far back in time to look for delayed demand orders or inventory issues. The **ATP backward supply time fence** field controls how far back in time to look for delayed supply orders or inventory receipts. For example, if orders that are delayed by only seven days should be considered in the ATP calculation, both fields should be set to **7**.  

The **ATP delayed demand offset time** and **ATP delayed supply offset time** fields control when the delayed demand or supply will be considered in the ATP calculation. For example, if the delayed supply and demand should be considered in the ATP calculation the day after tomorrow, both fields should be set to **2**. A value of **2** means that the quantity of an item on a delayed purchase order that should be considered in the ATP calculation will be seen as available two days after the current date.  

For the following example, **7** is entered in the **ATP backward demand time fence** and **ATP backward supply time fence** fields, and **1** is entered in the **ATP delayed demand offset time** and **ATP delayed supply offset time** fields.  

A purchase order for 200 pieces of a product that should have been received three days ago hasn't been received yet. Therefore, a sales order line for 75 pieces of the same product that should have been shipped yesterday hasn't been shipped.  

A customer calls and wants to order 150 pieces of the same product. When you verify the availability of the product, you find that another purchase order for 100 pieces of the product will be delivered 10 days later.  

You create a sales order line for the product and enter **150** as the quantity.  

Because the delivery date control is method is ATP, the ATP data is calculated to find the earliest possible ship date. Based on the settings, the delayed purchase order and sales order are considered, and the resulting ATP quantity for the current date is 0. Tomorrow, when the delayed purchase order is expected to be received, the ATP quantity is calculated as more than 0 (in this case, it's calculated as 125). However, 10 days from now, when the additional purchase order for 100 pieces is expected to be received, the ATP quantity becomes more than 150.  

Therefore, the ship date is set to 10 days from now, based on the ATP calculation. Therefore, you tell the customer that the requested quantity can be delivered 10 days from now.

