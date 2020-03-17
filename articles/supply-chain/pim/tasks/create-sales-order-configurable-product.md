--- 
# required metadata 
 
title: Create a sales order for a configurable product
description: This procedure shows how to apply a configuration template to a product on a sales order. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, SalesOrderProcessingWorkspace, SalesCreateOrder, SalesTable, PCRuntimeConfigurator, PCTemplateConfigurationSelection   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a sales order for a configurable product

[!include [banner](../../includes/banner.md)]

This procedure shows how to apply a configuration template to a product on a sales order. This example uses the D0006 speaker model in the USMF demo data company. Typically, a sales order processor uses this procedure.


## Create a sales order
1. Click Sales order processing and inquiry.
2. Click New.
3. Click Sales order.
4. In the Customer account field, select US-001. 
5. Click OK.
6. In the Item number field, select D0006.
    * For this task, you must select a configurable product.  
7. Click Product and supply.
8. Click Configure line.
    * Note that the price has changed, based on the configuration that was selected, and that the Include cable field is now set to True.  
    * Note the default price and the settings that are selected for the cable.  
9. Click Load template.
    * This example shows how you can apply a template to select a predefined configuration. If you're using this procedure as a task guide and want to see the other attribute values that are available, you must click the Unlock button.  
10. Click OK.
11. Click OK.
12. Expand the Line details section.
13. Click the Product tab.
    * The configuration of the item is now listed under the product dimensions.  
14. Close the page.

## Select the product configuration

