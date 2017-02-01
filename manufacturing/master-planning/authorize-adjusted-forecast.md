---
# required metadata

title: Authorize an adjusted forecast | Microsoft Docs
description: Not all forecast data must be authorized immediately. This article explains how you can specify the period that a forecast is authorized for. It also explains how you can authorize the forecast for specific companies and forecast models.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-03-30 12:35:48
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: ReqDemPlanImportForecastDialog
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 2094
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 72734
ms.assetid: 98bae996-7c21-4643-be11-fd72b05d9b01
ms.region: global
ms.industry: Manufacturing
ms.author: roxanad

---

# Authorize an adjusted forecast

Not all forecast data must be authorized immediately. This article explains how you can specify the period that a forecast is authorized for. It also explains how you can authorize the forecast for specific companies and forecast models.

Not all forecast data must be authorized immediately. You can specify the start and end dates of the period that the forecast is authorized for. This functionality lets you freeze specific buckets. The start and end dates that you specify must correspond to the start and end dates of the bucket that the forecast is generated in. The system enforces this restriction and automatically adjusts the dates, if adjustment is required. On the **Details** tab of the **Authorization** page, you can view details about the forecast that was most recently generated. You can select the companies and the forecast models to authorize the forecast for use. By default, the grid includes all the companies that forecast demand has been created for. For each company, the forecast model that corresponds to the current forecast plan that is set up in the master planning parameters is prefilled. However, you can change this forecast model to any forecast model that belongs to that company. If no forecast demand data has been generated for a selected company, you receive a warning message at import time. It's very important that you understand how the **Save the manual adjustments made to the baseline demand forecast** check box works. If you've made manual adjustments to the statistical baseline forecast, the adjusted values are authorized for use, even if this check box is cleared. However, the changes are discarded after the authorization. Therefore, the next time that a forecast is generated, that forecast is only a statistical forecast and doesn't have any manual overrides, even if **Transfer manual adjustments to the demand forecast** is selected. Therefore, you can consider the **Save the manual adjustments made to the baseline demand forecast** check box a mechanism that lets you keep or discard all manual changes.

See also
--------

[Making manual adjustments to the baseline forecast](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/making-manual-adjustments-to-the-baseline-forecast)

[Monitoring forecast accuracy](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/monitoring-forecast-accuracy)

