---
# required metadata

title: Master planning home page
description: Master planning allows companies to determine and balance the future need for raw materials and capacity to meet company goals. 
author: t-benebo
ms.date: 12/03/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Master planning home page

[!include [banner](../includes/banner.md)]

At its core, Master planning allows companies to determine and balance the future need for raw materials and capacity to meet company goals. Master planning assesses the following:

- What raw materials and capacities are currently available?
- What raw materials and capacities are required to complete production? For example, what must be manufactured, purchased, transferred, or set aside as safety stock before you can complete production.

Master planning uses the information to calculate the requirements and generate planned orders.

The three main planning processes are:

- **Master planning** - The Master plan calculates net requirements. It is based on actual current orders and enables companies to control inventory replenishment on a short-term, day-to-day basis. Another term to describe it is the *Net requirements plan*. For more information, see [Master plans overview](master-plans.md).

- **Forecast planning** - The Forecast schedule calculates gross requirements. It is based on future projections (or forecasts), and enables companies to conduct long-term planning of materials and capacity. For more information, see [Demand forecasting overview](introduction-demand-forecasting.md).

- **Intercompany master planning** - The Intercompany master plan calculates net requirements across legal entities. It connects demand and supply between companies not only for short term, firm demand and supply but also for long-term, planned (that is not yet firmed) demand and supply. For more information, see [Intercompany planning](planning-optimization/Intercompany-planning.md).

Companies can change the output of the plan. They can run regenerative, net change, or both. Regenerative plans update all requirements, whereas, net change plans only update the plan on items with new requirements that have come in since the last scheduling run.

Master scheduling plans typically involve the short term, which can be anywhere from one week to six months. The Master planning module determines the supply (materials) and capacity (resources) needs that will meet current demand (the net requirements). In most companies this is extended to include the longest cumulative lead time among the products to be received.

## Learning map

The following learning map shows the major concepts and tasks that make up the framework of the Master planning module. Click the links in the [Quick links](#quick-links) section to learn how to use the module.

[![Learning map for master planning.](./media/master-planning-learning-map.png)](./media/master-planning-learning-map.png)

## Quick links

- [Master plans overview](master-plans.md)  
- [Generate a constrained plan](./tasks/constrained-plan.md)
- [Create a material plan for co-products](./tasks/create-material-plan-co-products.md)
- [Master planning and multisite functionality overview](master-plan-multisite-functionality.md)
- [Create an intercompany plan](./tasks/create-intercompany-plan.md)
- [Demand forecasting overview](introduction-demand-forecasting.md)
- [Forecast reduction keys](reduction-keys.md)

## Additional resources

### Roadmaps

Go to the [Microsoft Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to see what new features have been released and what new features are in development.

### Blogs

You can find opinions, news, and other information about Master planning and other solutions on the
[Dynamics AX Manufacturing R&D Team blog](/archive/blogs/axmfg/) and [Supply Chain Management in Dynamics AX R&D Team blog](https://blogs.msdn.microsoft.com/dynamicsaxscm).

### Task guides

Additional help is available as task guides. To access task guides, click the **Help** button on any page.

### Webinars

[Use Azure machine learning for demand forecasting](https://www.youtube.com/watch?v=4nQsccdFFDA&feature=youtu.be)

### Tech conference recordings

- [Extend the demand forecasting functionality](https://www.youtube.com/watch?v=4OIKIXLiNjI&feature=youtu.be)
- [Master planning - tips and tricks for troubleshooting performance](https://youtu.be/7v8BPmEs9Dg)
- [MRP performance tuning](https://youtu.be/RLXybx20B5o)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]