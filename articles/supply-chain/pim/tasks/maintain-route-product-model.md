--- 
# required metadata 
 
title: Maintain route for a product model
description: Running this procedure requires that a product configuration model exists. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCProductConfigurationModelDetails, PCRouteOperationDetails, WrkCtrCapabilityLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Maintain route for a product model

[!include [banner](../../includes/banner.md)]

Running this procedure requires that a product configuration model exists. This procedure uses the High end speaker model in the demo company USMF to walk you through the process.

## Add a route operation

1. Go to **Product information management \> Products \> Product configuration models**.
1. In the list, find and select the desired record.
    * Select the High end speaker model for this exercise.  
1. In the list, select the link in the selected row.
1. Expand the **Route operations** section.
1. Select **Add**.
1. In the **Name** field, type a value.
1. In the **Description** field, type a value.
1. Select **Save**.

## Enter route operation details

1. Select **Route operation details**.
1. In the **Operation** field, enter or select a value.
1. In the **Oper. No.** field, enter a number.
    * Operation numbers determine the route sequence.  
    * Each property on a route operation can get a static value or be mapped to an attribute. Mapping to an attribute will result in the value being set as part of the configuration.  
1. In the **Route group** field, enter or select a value.
    * The route group determines essential behavior for costing, consumption, and setup.  
1. Select the **Setup** tab.
1. Select the **Times** tab.
1. In the **Process qty.** field, enter a number.
    * Determine how many will be processed during one operation.  
1. In the **Hours/time** field, enter a number.
    * Enter the time ratio.  
1. Select the **Set** check box.
1. In the **Run time** field, enter a number.
    * Determine the processing time for the quantity that you have specified.  
1. Select the **Resource requirements** tab.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Requirement type** field, select an option.
    * Decide if you want to specify specific resources or capabilities that they must possess.  
1. In the **Requirement** field, enter or select a value.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]