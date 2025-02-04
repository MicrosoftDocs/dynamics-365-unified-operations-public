---
title: Time windows 
description: Learn how you can use time windows to optimize the scheduling of service order lines with a table that defines various methods.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMATimeAgreement
ms.topic: conceptual
ms.date: 01/30/2025
ms.custom: 
  - bap-template
---

# Time windows  

[!include [banner](../includes/banner.md)]

You can use time windows to optimize the scheduling of service order lines. You can set up the system so that it automatically creates service orders. Based on the criteria specified by a time window, you can connect as many service order lines as possible to as few service orders as possible.

Time windows specify how far a service order line can move from its calculated date. The calculated date is the date when the service order line was scheduled to occur. The date is based on its interval setting and the service period that you defined on the **Create service orders** page. You define a time window by using the values in the following table.

| Method | Description |
|--|--|
| Week | The date that the service order line can be moved to any open day in the same week as the initial calculated date. |
| Month | The date that the service order line can be moved to any open day in the same month as the initial calculated date. For example, the calculated date for a service order line is February 15, 2017. The service order line can be scheduled for any weekday between February 1 and February 28, 2017. |
| Manual | You define the maximum number of days before or after the initial calculated date that the service order line can be moved. |

If you don't specify a time window for a service agreement line, the service order line that is derived from the service agreement must be on the exact date for which it was originally scheduled.

## Related information

- [Create time windows](create-time-windows.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
