---
title: "Guide: Modify a demand forecast manually"
description: This article describes how to modify the forecast for an item
author: t-benebo
ms.date: 08/12/2019
ms.topic: how-to
ms.search.form: EcoResProductDetailsExtended, ForecastSales   
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Guide: Modify a demand forecast manually

[!include [banner](../../includes/banner.md)]

This procedure shows how to modify the forecast for an item. This procedure is intended for the production planner.

## Modify the forecast for a selected item

To modify the forecast for a selected item:

1. Go to **Product information management \> Products \> Released products**.
1. In the list, find and select the desired record. Select the item for which you want to modify the forecast.
1. On the Action Pane, open the **Plan** tab and select **Demand forecast**.
1. In the list, select a row. If there are no forecast lines, create a new line by selecting **New** on the Action Pane.  
1. In the **Sales quantity** field, enter a positive number. This number represents the forecasted quantity for the item. An error will be shown if you enter a negative number.
1. Fill out the other fields as needed.
1. Select **Save** on the Action Pane.

## Modify the forecast for one or more items with Microsoft Excel

To modify the forecast for one or more items with Microsoft Excel:

1. Do one of the following:
    - Open the **Demand forecast** page for any item (it doesn't matter which one) as described in the previous section.
    - Go to **Master planning \> Forecasting \> Manual forecast entry \> Demand forecast lines**.
1. On the Action Pane, select **Open in Microsoft Office \> Demand forecast entries**.
1. Select a download location, save, and then open the downloaded file in Excel.
1. If you see a warning, choose to **Enable editing**.
1. In Excel, sign in to Supply Chain Management using the Microsoft Dynamics task pane. You must sign in with the **Keep me signed in** option enabled and you must trust the data connection app.
1. The Excel spreadsheet now shows all the current demand forecast lines for your company.  Add, delete, and edit demand forecast lines as needed.
1. Select **Publish** on the Microsoft Dynamics task pane to upload your changes back to Supply Chain Management.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
