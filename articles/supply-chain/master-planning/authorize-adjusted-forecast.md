---
# required metadata

title: Authorize an adjusted forecast
description: Not all forecast data must be authorized immediately. This article explains how you can specify the period that a forecast is authorized for. It also explains how you can authorize the forecast for specific companies and forecast models.
author: t-benebo
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqDemPlanImportForecastDialog
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: cb8fd809-605a-4a8b-a390-636edfec21f9
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Authorize an adjusted forecast

[!include [banner](../includes/banner.md)]

Not all forecast data must be authorized immediately. This article explains how you can specify the period that a forecast is authorized for. It also explains how you can authorize the forecast for specific companies and forecast models.

Not all forecast data must be authorized immediately. You can specify the start and end dates of the period that the forecast is authorized for. This functionality lets you freeze specific buckets. 

The start and end dates that you specify must correspond to the start and end dates of the bucket that the forecast is generated in. The system enforces this restriction and automatically adjusts the dates, if adjustment is required. 

On the **Details** tab of the **Authorization** page, you can view details about the forecast that was most recently generated. 

You can select the companies and the forecast models to authorize the forecast for use. By default, the grid includes all the companies that forecast demand has been created for. For each company, the forecast model that corresponds to the current forecast plan that is set up in the master planning parameters is prefilled. However, you can change this forecast model to any forecast model that belongs to that company. If no forecast demand data has been generated for a selected company, you receive a warning message at import time. 

It's very important that you understand how the **Save the manual adjustments made to the baseline demand forecast** check box works. If you've made manual adjustments to the statistical baseline forecast, the adjusted values are authorized for use, even if this check box is cleared. However, the changes are discarded after the authorization. Therefore, the next time that a forecast is generated, that forecast is only a statistical forecast and doesn't have any manual overrides, even if **Transfer manual adjustments to the demand forecast** is selected. Therefore, you can consider the **Save the manual adjustments made to the baseline demand forecast** check box a mechanism that lets you keep or discard all manual changes.

## Additional resources

- [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)
- [Monitor forecast accuracy](monitor-forecast-accuracy.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]