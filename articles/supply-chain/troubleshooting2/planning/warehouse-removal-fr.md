---
# required metadata

title: Warehouse removal from Demand forecast Dimension not working
description: Warehouse removal from Demand forecast Dimension not working
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ForecastSales
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: crytt@microsoft.com

---

# Warehouse removal from Demand forecast Dimension not working

KB Number: 4614408

When Customer does not select the warehouse in the demand forecast parameters and when he selects the demand forecast lines, he is still able to see the warehouse column even though it was not selected in the parameters.

## Resolution
The dimension settings under Demand forecasting parameters are not related to the shown dimenstions on "Manual forecast entry -> Demand forecast lines".

The dimension settings under Demand forecasting parameters control the baseline forecast generated and displayed in Adjusted demand forecast, it is not controlling the required dimensions for "real" demand forecast. The records in Adjusted demand forecast can be Authorized and become "real" forecast entry for a forecast model that can be used for master planning.

On Manual forecast entry -> Demand forecast lines: The dimenstions for the "real" forecast shown in the demand forecast lines are part of the inventory dimensions, similar to sales order lines. If warehouse is not setup as a mandatory inventory dimension the column can be hidden.



