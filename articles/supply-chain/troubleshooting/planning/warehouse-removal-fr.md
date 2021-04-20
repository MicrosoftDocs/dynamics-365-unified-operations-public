---
title: Can't remove the warehouse demand forecast dimension from forecast lines
description: Can't remove the warehouse demand forecast dimension from forecast lines
author: ChristianRytt
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ForecastSales
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Can't remove the warehouse demand forecast dimension from forecast lines

KB Number: 4614408

## Symptoms

This issue occurs when the **Warehouse** dimension is not assigned on the **Forecast dimensions** tab of the **Demand forecasting parameter** page. Even with this setting, you are still able to see the **Warehouse** column on the **Demand forecast** page (**Master planning \> Forecasting \> Manual forecast entity \> Demand forecast lines**).

## Resolution

The **Forecast dimensions** settings on the **Demand forecasting parameter** page don't affect the **Demand forecast** page. They control the baseline forecast generated and displayed in the adjusted demand forecast, but don't control the required dimensions for the "real" demand forecast. You can authorize the records shown on the **Adjusted demand forecast** page to convert them to "real" forecast entries for a forecast model, which can then be used for master planning.

On the **Demand forecast** page, the dimensions for the "real" forecast shown in the demand forecast lines are part of the inventory dimensions, similar to sales order lines. If your system isn't set to use **Warehouse** as a mandatory inventory dimension, then you can customize the page to hide the column.
