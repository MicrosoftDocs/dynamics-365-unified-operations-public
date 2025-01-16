---
title: Cost management home page
description: Cost management lets you handle the valuation and accounting of raw materials, semi-finished goods, finished goods, and work in progress assets. 
author: prasungoel
ms.author: prasungoel
ms.reviewer: kamaybac
ms.search.form: CostAdminWorkspace, CostAnalysisWorkspace  
ms.topic: overview
ms.date: 12/02/2024
ms.custom: 
  - bap-template
---

# Cost management home page

[!include [banner](../includes/banner.md)]

[Cost management (video)](https://www.youtube.com/watch?v=vXzlC-mOBcg&feature=youtu.be) lets you work with the valuation and accounting of raw materials, semi-finished goods, finished goods, and work-in-progress assets. It's the process of defining, managing, and reporting [Inventory accounting](cost-object.md) and [Manufacturing accounting](bom-calculations.md).

You can define cost policies in the following areas:

- [Predetermined cost](costing-versions.md)
- [Inventory accounting](cost-object.md)
- [Manufacturing accounting](bom-calculations.md)
- [Indirect cost accounting](costing-sheets.md)
- [Ledger integration](production-order-cost-analysis.md)

For example, you can define which inventory valuation methods, such as [FIFO](fifo-physical-value-marking.md), [Weighted average](weighted-average-physical-value-marking.md), [Standard cost](prerequisites-standard-costs.md), or [Moving average](moving-average.md) that you want to apply to products in the [Item model group](../inventory/reserve-inventory-quantities.md) in Inventory accounting.

You can access Inventory accounting and Manufacturing accounting from the **Cost administration** and **Cost analysis** workspaces. These workspaces provide a comprehensive overview of the current status, key performance indicators (KPIs), and detection of deviation.  

> [!TIP]
> Are you new to inventory costing? Check out the following resources:
>
> - [Glossary of terms in Dynamics 365 business processes](/dynamics365/guidance/business-processes/glossary#costing-methodology)
> - [Define service costing overview and relation to other business processes](/dynamics365/guidance/business-processes/concept-to-market-define-service-costing-overview)
> - [Business process for product costing and how it relates to other processes with Dynamics 365](/dynamics365/guidance/business-processes/design-to-retire-define-product-costing-overview)

Manufacturing accounting lets you handle [Job order costing](production-order-cost-analysis.md) in production orders and batch orders, as well as [Backflush costing](backflush-costing.md) in lean manufacturing.

The [Cost management Power BI content](../../fin-ops-core/dev-itpro/analytics/cost-management-content-pack.md) provides managerial insight into inventory and work-in-progress (WIP) inventory, and how cost flows through them by category over time. The information can also be used as a detailed supplement to the financial statement.

## Related information

### What's new and in development

Go to the [Dynamics 365 Release Planner](https://releaseplans.microsoft.com/?app=Supply+Chain+Management) to see what new features have been released and what new features are in development.

### White paper

[BOM calculation by using a costing sheet](https://www.microsoft.com/download/details.aspx?id=101937) describes how to set up a costing sheet that includes material and manufacturing, and how the setup affects the BOM calculation results. To better explain the articles, it provides concrete scenarios and data that demonstrates the effect of the various settings and configurations.

### Blogs

You can find opinions, news, and other information about Cost management on the [Dynamics AX Manufacturing R&D Team blog](/archive/blogs/axmfg/) and [Supply Chain Management in Dynamics AX R&D Team blog](https://blogs.msdn.microsoft.com/dynamicsaxscm). Although some of these posts were written for the previous version of Cost management, the same concepts still apply, and the procedures are also similar in the current version.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
