---
title: Remove outliers from historical transaction data when calculating a demand forecast
description: Learn how to exclude outliers from the historical data that is used to calculate a demand forecast. By excluding outliers, you can improve forecast accuracy.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
ms.search.form: ReqDemPlanForecastParameters, ReqDemPlanOutlierQuerySetup, ReqDemPlanOutlierQueryPreview
ms.assetid: 88a964af-14eb-4c5c-945b-388e5908362c
---

# Remove outliers from historical transaction data when calculating a demand forecast

[!include [banner](../includes/banner.md)]
[!INCLUDE [demand-planning-banner](../includes/demand-planning-banner.md)]

This article describes how to exclude outliers from the historical data that is used to calculate a demand forecast. By excluding outliers, you can improve forecast accuracy.

You can exclude outliers to improve forecast accuracy. This is an optional task. Here is an overview of the process:

1. Go to **Master planning** &gt; **Setup** &gt; **Demand forecasting** &gt; **Outlier removal** to open the **Outlier removal** page, where you can use a query to select the transactions to exclude.
1. Select the company that the query applies to, and then enter a name and description. The **Query date** field is automatically set to the current date.
1. Select the **Active** checkbox to exclude the transactions that the query finds from the historical data. This setting will take effect when you create a baseline forecast.
1. On the **Outlier removal query** page, you can add, remove, and select the criteria that define which transactions will be excluded when the baseline forecast is calculated. For example, select a specific item or order transaction to exclude.
1. Select **Display transactions**. The **Outlier transactions** page lists the transactions that meet the criteria that you defined in the query, and that will be excluded from the historical data when the demand forecast is calculated.

> [!NOTE]
> You can also create a query that is based on an existing query. Select the query to copy, and then select **Duplicate**. The **Query date** field identifies the version. You can use the query as it is, or you can select **Edit query** to modify the criteria. You can optionally modify the name and description of the new query.

## Related information

- [Demand forecasting overview](introduction-demand-forecasting.md)
- [Monitor forecast accuracy](monitor-forecast-accuracy.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
