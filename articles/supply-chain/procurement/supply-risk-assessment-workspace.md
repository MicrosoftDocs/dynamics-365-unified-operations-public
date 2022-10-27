---
title: Actionable workspace to discover and handle supplier risks
description: The Supply Risk Assessment workspace gives you a direct view on top key insights related to supplier performance and related risks. It also provides embedded reports for detailed performance and risk analysis.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/27/2022 
ms.custom: bap-template
---

# Actionable workspace to discover and handle supplier risks

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.31 GA -->

The **Supply risk assessment** workspace gives you a direct view into the top key insights related to supplier performance and related risks. It also provides [embedded reports](supply-risk-assessment-reports.md) for detailed performance and risk analysis.

## Open the Supply risk assessment workspace

To open the workspace, go to **Procurement and sourcing \> Workspaces \> Supply risk assessment**.

The workspace provides three tabs for direct actionable navigation and embedded analytic reporting using Power BI.

- **Overview**
- **Performance**
- **Risk**

Each tab is described in detail later in this article.

> [!NOTE]
> If the workspace is empty or isn't showing the latest data you expect to see, you may need to initialize or refresh the data. For instructions, see [Configure supply risk assessment](supply-risk-assessment-configuration.md).

## The Overview tab

The **Overview** tab shows metrics and actionable content that let you navigate to relevant views and records in Supply Chain Management, such as planned orders, products, vendors, and more. The data shown in the **Overview** tab are filtered by the currently selected legal entity.

[<img src="media/sra-workspace-page.png" alt="Supply risk assessment workspace, screenshot." title="Supply risk assessment workspace, screenshot" width="720" />](media/sra-workspace-page.png)

### Key insights

The **Key insights** FastTab of the **Overview** tab shows the following tiles, each of which reports a metric calculated for the scope of the workspace:

- **Late confirmed** – The number of purchase order lines where vendors returned a confirmed delivery date (CDD) that was later than your requested delivery date (RDD).
- **Not on time** – The number of purchase order lines that weren't delivered on time (OT).
- **Not in full** – The number of purchase order lines that weren't delivered in full (IF).
- **Single sourced** – The number of planned order items that have only one vendor assigned, which potentially indicates increased risk

Each of these tiles summarizes a view, which you can open by selecting the relevant tile. The following screenshot shows the details view available from the **Single sourced** tile. It shows on-time in-full (OTIF) ratings and highlights whether your [configured threshold](supply-risk-assessment-configuration.md) was met for each item.

![Single sourced items view, screenshot.](media/sra-single-source-planned-items.png "Single sourced items view, screenshot")

### Details and impact

The **Details and impact** FastTab of the **Overview** tab shows a tile for each product and vendor that didn't meet the OTIF rate expectations based on past purchase orders. There's one tab each for **Products not OTIF** and **Vendors not OTIF**.

Each tile shows the number of items ordered and the number of items delivered in the relevant unit of measure. The header of each tile shows the number of relevant order lines for this calculation. The following screenshot shows an example of tiles on the **Vendors not OTIF** tab.

![Details and Impact view screenshot.](media/sra-details-impact.png "Details and Impact view screenshot")

Select a tile to see the list of order lines counted by that tile.

### Links

The **Links** FastTab provides convenient links to the **Supply risk assessment parameters** page (see [Configure supply risk assessment](supply-risk-assessment-configuration.md)) and to the integrated supply risk assessment report (see [Power BI reports for risks analysis and performance ranking](supply-risk-assessment-reports.md)).

## The Performance and Risk tabs

The **Performance** and **Risk** tabs provide in-depth analytics reports of your vendor and supply performance and the calculated risks for your planned supply orders. For more information about how to work with these reports, see [Power BI reports for risks analysis and performance ranking](supply-risk-assessment-reports.md).

## Next steps

Explore how the purchase order fulfillment history from the perspective of products or vendors can be used to calculate future risk for your supply. See [Power BI reports for risks analysis and performance ranking](supply-risk-assessment-reports.md).
