---
title: Master planning home page
description: Master planning allows you to determine and balance the future need for raw materials and capacity to meet your goals.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ReqCreatePlanWorkspace
ms.topic: overview
ms.date: 03/26/2026
ms.custom: 
  - bap-template
---

# Master planning home page

[!include [banner](../includes/banner.md)]

At its core, master planning helps you determine and balance the future need for raw materials and capacity to meet your goals. Master planning assesses the following questions:

- What raw materials and capacities are currently available?
- What raw materials and capacities are required to complete production? For example, what must be manufactured, purchased, transferred, or set aside as safety stock before you can complete production.

Master planning uses this information to calculate the requirements and generate planned orders.

The three main planning processes are:

- **Master planning** - The master plan calculates net requirements. It's based on actual current orders and enables you to control inventory replenishment on a short-term, day-to-day basis. Another term to describe it is the *Net requirements plan*. Learn more in [Master plans overview](master-plans.md).

- **Forecast planning** - The forecast schedule calculates gross requirements. It's based on future projections (or forecasts), and enables you to conduct long-term planning of materials and capacity. Learn more in [Demand forecasting overview](introduction-demand-forecasting.md).

- **Intercompany master planning** - The intercompany master plan calculates net requirements across legal entities. It connects demand and supply between companies not only for short term, but also for long-term, planned (not yet firmed) demand and supply. Learn more in [Intercompany planning](planning-optimization/Intercompany-planning.md).

You can change the output of the plan.

Master scheduling plans typically involve the short term, which can be anywhere from one week to six months. The Master planning module determines the supply (materials) and capacity (resources) needs that will meet current demand (the net requirements). In most companies, this planning process extends to include the longest cumulative lead time among the products to be received.

> [!NOTE]
> With Planning Optimization, all plans are regenerative, whereas the deprecated master planning engine had a concept of net change and regenerative planning run. Regenerative plans update all requirements, whereas net change plans only update the plan for items with new requirements that were added since the last scheduling run.

## Learning map

The following learning map shows the major concepts and tasks that make up the framework of the Master planning module.

[:::image type="content" source="./media/master-planning-learning-map.png" alt-text="Learning map for master planning." lightbox="./media/master-planning-learning-map.png":::](./media/master-planning-learning-map.png)

## Related information

### Roadmaps

Go to the [Dynamics 365 and Microsoft Power Platform release planner](https://releaseplans.microsoft.com/?app=Supply+Chain+Management) to see what new features are released and what new features are in development.

### Blogs

Find opinions, news, and other information about Master planning and other solutions on the
[Dynamics AX Manufacturing R&D Team blog](/archive/blogs/axmfg/) and [Microsoft Dynamics 365 Blog](https://www.microsoft.com/en-us/dynamics-365/blog/).

### Webinars

[Use Azure Machine Learning for demand forecasting](https://www.youtube.com/watch?v=4nQsccdFFDA&feature=youtu.be)

### Tech conference recordings

- [Planning Optimization service](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/dynamics-365-supply-chain-management---planning-optimization-service-february-21-2020)
- [Get started with Planning Optimization](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/get-started-with-planning-optimization-for-dynamics-365-supply-chain-management-march-1-2021)
- [Demand forecasting series](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/demand-forecasting-with-azure-machine-learning-series)
- [Extend the demand forecasting functionality](https://www.youtube.com/watch?v=4OIKIXLiNjI&feature=youtu.be)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
