---
title: Differences between classic master planning and Planning Optimization
description: This topic lists features that are not yet supported by Planning Optimization and are not listed in the Planning Optimization fit analysis page.
author: crytt
ms.date: 07/06/2021
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-07-06
ms.dyn365.ops.version: 10.0.21
---

# Differences between classic master planning and Planning Optimization

[!include [banner](../../includes/banner.md)]

Planning Optimization results may differ from built-in master planning. This can be caused by pending features. This topic lists features that are not yet supported by Planning Optimization and are not listed in the Planning Optimization fit analysis page.

| Feature | Current behavior in Planning Optimization |
| --- | --- |
| Catch weight products | Catch weight products are considered as usual products.|
| Extensible dimensions | Extensible dimensions are empty on planned orders even when **Coverage plan by dimension** check box is checked on the **Storage dimension groups** page or **Tracking dimension groups** page. |
|Filtered production runs|For details, see [Production planning - Filters](production-planning.md#filters) |
| Plan copy, Delete plan and Plan version cleanup | **Plan copy**, **Delete plan** and **Plan version cleanup** menu items are disabled. |
| Return orders | Return orders are not considered. |
| Scheduling related features | For details, see [Scheduling with infinite capacity](infinite-capacity-planning#limitations.md) |
| Transport calendars | **Transport calendar** column value on the **Modes of delivery** page is ignored. |

## Additional resources

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[Parameters not used by Planning Optimization](not-used-parameters.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]