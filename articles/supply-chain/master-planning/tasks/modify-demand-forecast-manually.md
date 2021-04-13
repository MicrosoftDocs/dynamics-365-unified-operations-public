---
title: Modify a demand forecast manually
description: This topic describes how to modify the forecast for an item
author: ChristianRytt
ms.date: 08/12/2019
ms.topic: business-process
ms.search.form: EcoResProductDetailsExtended, ForecastSales   
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Modify a demand forecast manually

[!include [banner](../../includes/banner.md)]

This procedure shows how to modify the forecast for an item. The demo data company used to create this procedure is USMF. This procedure is intended for the production planner. 


## Modify the forecast for an item

1. Go to **Modules \> Product information management \> Products \> Released products**.
1. In the list, find and select the desired record. Select the item for which you want to modify the forecast. For example, you can select item *D0001*.  
1. On the Action Pane, open the **Plan** tab and select **Demand forecast**.
1. In the list, select a row. If there are no forecast lines, create a new line by selecting **New** on the Action Pane.  
1. In the **Sales quantity** field, enter a positive number. This number represents the forecasted quantity for the item. An error will be shown if you enter a negative number.
1. Select **Save** on the Action Pane.


## Modify the forecast in Microsoft Excel

1. With the **Demand forecast** page still open, on the Action Pane, select **Open in Microsoft Office \> Edit Demand forecast**.
1. In Excel, add, delete, and edit demand forecast lines as needed. If you are not able to see the data in Excel, you must sign in with the **Keep me signed in** option enabled and you must trust the data connection app.  


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
