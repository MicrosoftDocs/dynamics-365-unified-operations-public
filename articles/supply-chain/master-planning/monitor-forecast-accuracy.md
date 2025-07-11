---
title: Monitor forecast accuracy
description: Learn about the types of forecast accuracy that Dynamics 365 Supply Chain Management calculates, and explains how you can view the accuracy values.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 01/07/2020
ms.reviewer: kamaybac
ms.search.form: ReqDemPlanForecastDetails
ms.assetid: 810a0d63-f4c6-4167-b2b3-a178b74ead89
---

# Monitor forecast accuracy

[!include [banner](../includes/banner.md)]
[!INCLUDE [demand-planning-banner](../includes/demand-planning-banner.md)]

This article describes the types of forecast accuracy that Microsoft Dynamics 365 Supply Chain Management calculates, and explains how you can view the accuracy values.

Supply Chain Management calculates the following types of forecast accuracy:

- Historical forecast accuracy, by comparing the historical forecast that Master Planning uses with the historical demand. To view the values (both absolute values and percentage values) for historical forecast accuracy, select **Show accuracy** on the **Demand forecast details** page.
- The estimated accuracy of the forecasting model that is used to generate the predictions. You can view the accuracy percentage under **Model details - MAPE** on the **Demand forecast details** page.

> [!NOTE]
> If you use the Demand forecasting Microsoft Azure Machine Learning, the calculation of internal model accuracy is based on the test data set. To specify the size of the test data set, set the **TEST\_SET\_SIZE\_PERCENT** parameter on the **Demand forecasting parameters** page. For example, if you set the value to **20**, the last 20 percent of the historical data will be used to calculate the internal model accuracy.

## Related information

- [Authorize an adjusted forecast](authorize-adjusted-forecast.md)
- [Remove outliers from historical transaction data when calculating a demand forecast](remove-historical-outliers-calculating-demand-forecast.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
