---
title: Delays
description: Learn about delayed dates in master planning, which is a due date that a transaction receives if the earliest fulfillment date is later than the requested date.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 03/31/2020
ms.reviewer: kamaybac
ms.search.form: ReqTransFuturesListPage
ms.assetid: 5ffb1486-2e08-4cdc-bd34-b47ae795ef0f
---

# Delays

[!include [banner](../includes/banner.md)]

This article provides information about delayed dates in master planning. A delayed date is a realistic due date that a transaction receives if the earliest fulfillment date that master planning calculates is later than the requested date.

Master planning can calculate the earliest fulfillment date for a transaction, based on lead times, material availability, capacity availability, and various planning parameters. 

If master planning calculates an order date that precedes the current date, the order can't be fulfilled on time. Therefore, the order is delayed. In this case, master planning forward-plans the order from the current date and includes lead times. These lead times start with any lower-level component items. The order then receives a delayed date. A delayed date is a realistic due date, based on the current data. Master planning also calculates the number of delay days. 

In some situations, you might choose not to calculate delays, such as when users know that they can expedite lead times by selecting alternative modes of delivery. 

You can configure how delays are calculated for a coverage group. You can then attach the coverage group to an item later. 

On the **Master planning parameters** page, you can set the start time for the calculation of delays. If an order is fulfilled after this time, a delay of one day is added to the delay date of the order. 

> [!NOTE]
> In earlier versions, calculated delays were known as *futures messages*, the delayed date was known as the *futures date*, and a delayed transaction was referred to as *a transaction that was future set*.

## Limited delays in production setup with multiple BOM levels
When you work with delays in a production setup that has multiple BOM levels, it is important to note that only the items directly above the item (in the BOM structure) causing the delay, will be updated with a delay as part of the master planning run. Other items in the BOM structure will not get the delay applied until the first master planning run, when the planned order for the top level is approved or firmed. 

To work around this known limitation, the production orders on the top of the BOM structure with delays can be approved (or firmed) prior to the next master planning run. This way the delay from the delayed approved planned production order will be kept and all underlying components will be updated accordingly.
Action messages can also be used to identify planned orders that can be moved to a later date, due to other delays in the BOM structure.

## Desired date

On the **Planned order** page, under the **Delays** tab is the **Desired date** for the planned order. The desired date of a planned order is the base date for delays, which is a computed date that equals the **Requested date** calculated from the **Net Requirement**. If the planned order is a BOM line, production line or kanban line, the desired date is based on the **Requirement date** and the desired date will not be shown on the **Planned order** page.

## Related information

- [Coverage settings](coverage-settings.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]