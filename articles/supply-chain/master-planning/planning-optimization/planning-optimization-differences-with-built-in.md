---
title: Differences between built-in master planning and Planning Optimization
description: This topic lists features that Planning Optimization doesn't yet support and that aren't listed on the Planning Optimization fit analysis page.
author: crytt
ms.date: 07/30/2021
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-07-30
ms.dyn365.ops.version: 10.0.21
---

# Differences between built-in master planning and Planning Optimization

[!include [banner](../../includes/banner.md)]

Planning Optimization results might differ from results from the built-in master planning engine. The differences can be caused by pending features. This topic lists features that Planning Optimization doesn't yet support and that aren't listed on the **[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)** page].

| Feature | Current behavior in Planning Optimization |
|---|---|
| Catch weight products | Catch-weight products are considered usual products.|
| Extensible dimensions | Extensible dimensions are empty on planned orders, even when the **Coverage plan by dimension** checkbox is selected on the **Storage dimension groups** or **Tracking dimension groups** page. |
| Filtered production runs | For details, see [Production planning - Filters](production-planning.md#filters). |
| Forecast planning | Forecast planning isn't supported. We recommend that you use master planning where a forecast model is assigned to the master plan. |
| Number sequences for planned orders | Number sequences for planned orders aren't supported. Planned order numbers are generated on the service side. |
| Plan copy, delete plan, and plan version cleanup | <p>The following items are disabled under **Master planning \> Master planning \> Maintain plans** in the navigation pane:</p><ul><li>Plan copy</li><li>Delete plan</li><li>Plan version cleanup</li></ul> |
| Return orders | Return orders aren't considered. |
| Scheduling related features | For details, see [Scheduling with infinite capacity](infinite-capacity-planning.md#limitations). |
| Transport calendars | The value in the **Transport calendar** column on the **Modes of delivery** page is ignored. |

## Additional resources

- [Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
- [Parameters not used by Planning Optimization](not-used-parameters.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
