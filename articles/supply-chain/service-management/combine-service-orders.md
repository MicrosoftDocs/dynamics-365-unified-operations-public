---
title: Combine service orders  
description: Learn about combining service orders, including examples and a table defining and providing transaction types for various agreement line numbers.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 05/01/2018
ms.custom: 
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable
---

# Combine service orders

[!include [banner](../includes/banner.md)]

When you create service order lines automatically on the **Service agreements** page, you can choose one of the following options to specify how you want to group them:

- **By service agreement**
- **By service task**
- **By employee**
- **By service object**

## Example

You create a service agreement that has a start date on 03-31-2007. In the **Combine service orders** field, you specify **By service object**. You then create the following service agreement lines:

| Agreement line number | Transaction type | Description | Interval | Service object | Start date |
|-----------------------|------------------|-------------|----------|----------------|------------|
| 1                     | **Hour**         | SAL1        | Weekly   | X-1            | 04-01-2007 |
| 2                     | **Hour**         | SAL2        | Biweekly | X-2            | 04-01-2007 |
| 3                     | **Hour**         | SAL3        | Weekly   | X-2            | 04-01-2007 |

You don't specify time windows for any of the service agreement lines. Therefore, the service order lines won't move from the calculated day on which they fall.

Next, you generate service order lines from the **Create service orders** page from 04-01-2007 until 04-30-2007.

In total, 10 service orders are created. Because the combined setting that you selected was **By service object**, all service orders that are created have only service order lines with one specific service object. Service order lines that are generated from the service agreement and have the same service date and object are combined on the same service order.

> [!NOTE]
> In this example, the calendar that is specified on the **Service management parameters** page has no closed days.

Additional grouping of service order lines into service orders occurs according to any time window that you specify on the service agreement lines.

## Related information

- [Create service orders automatically](create-service-orders-automatically.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
