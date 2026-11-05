---
title: Delays
description: Learn about delayed dates in master planning, which is a due date that a transaction receives if the earliest fulfillment date is later than the requested date.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ReqTransFuturesListPage
ms.topic: how-to
ms.date: 11/02/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Delays

[!INCLUDE [banner](../includes/banner.md)]

This article provides information about delayed dates in master planning. A delayed date is a realistic due date that a transaction receives if the earliest fulfillment date that master planning calculates is later than the requested date.

Master planning can calculate the earliest fulfillment date for a transaction, based on lead times, material availability, capacity availability, and various planning parameters.

If master planning calculates an order date that precedes the current date, the order can't be fulfilled on time. Therefore, the order is delayed. In this case, master planning forward-plans the order from the current date and includes lead times. These lead times start with any lower-level component items. The order then receives a delayed date. A delayed date is a realistic due date, based on the current data. Master planning also calculates the number of delay days.

If you use the deprecated master planning engine, you might choose not to calculate delays, such as when users know that they can expedite lead times by selecting alternative modes of delivery.

You can configure how delays are calculated for a coverage group. You can then attach the coverage group to an item later. Planning Optimization always calculates delays for the coverage group, using **Coverage time fence (days)**. It ignores the **Calculated delays** setting.

If you use the deprecated master planning engine, you can set the start time for the calculation of delays on the **Master planning parameters** page. If an order is fulfilled after this time, a delay of one day is added to the delay date of the order. Planning Optimization doesn't use this start-time setting. For details, see [Parameters not used by Planning Optimization](planning-optimization/not-used-parameters.md).

> [!NOTE]
> In earlier versions, calculated delays were known as *futures messages*, the delayed date was known as the *futures date*, and a delayed transaction was referred to as *a transaction that was future set*.

## Limited delays in production setup with multiple BOM levels

When you work with delays in a production setup that has multiple bill of material (BOM) levels, only the items directly above the item (in the BOM structure) causing the delay are updated with a delay as part of the master planning run. Other items in the BOM structure don't get the delay applied until the first master planning run, when the planned order for the top level is approved or firmed.

To work around this known limitation, the production orders on the top of the BOM structure with delays can be approved (or firmed) before the next master planning run. This way the delay from the delayed approved planned production order is kept and all underlying components are updated accordingly.

Action messages can also be used to identify planned orders that can be moved to a later date, due to other delays in the BOM structure.

## Desired date

On the **Planned order** page, under the **Delays** tab, you can see the **Desired date** for the planned order. The desired date of a planned order is the base date for delays. It's a computed date that equals the **Requested date** calculated from the **Net Requirement**. If the planned order is a BOM line, production line, or kanban line, the desired date is based on the **Requirement date** and the desired date doesn't appear on the **Planned order** page.

## Update the delay when you reschedule a planned order

If the delay value isn't updated when you reschedule a planned order, open the **Rescheduling** dialog box for the planned order. On the **Explosion** FastTab, ensure that the **Perform explosion after rescheduling** option is set to *Yes*.

## Related information

- [Coverage settings](coverage-settings.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
