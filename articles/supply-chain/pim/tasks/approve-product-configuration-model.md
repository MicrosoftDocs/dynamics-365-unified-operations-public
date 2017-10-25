--- 
# required metadata 
 
title: Approve a product configuration model
description: Running this procedure requires that at least one product configuration model is available. 
author: YuyuScheller
manager: AnnBe 
ms.date: 03/02/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: yuyus
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Approve a product configuration model

[!include[task guide banner](../../includes/task-guide-banner.md)]

Running this procedure requires that at least one product configuration model is available. This procedure uses the High end speaker model in the demo data company USMF. Note that this model has already been approved, but the procedure walks you through the entire process.

1. Click Product variant model definition.
2. Click Product configuration models.
3. In the list, find and select the desired record.
    * Select the High end speaker model for this procedure.  
4. Click Versions.
5. Click New.
6. In the Product number field, enter or select a value.
    * The reference to a product represents a version of a product configuration model. Only product masters which have the constraint-based configuration technology will appear in this list.  
7. In the From date field, enter a date.
    * Select when the product model version will be available.  
8. In the To date field, enter a date.
    * Select an end date when this product model version will expire, or select Never.  
9. Click Approve to open the drop dialog.
10. In the Approved by field, enter or select a value.
    * Select the person who is responsible for approving product models for use in operations.  
11. Click OK.
12. In the Pricing method field, select an option.
    * Activate the product model version. It is only possible to have one product active for one product model at a time.  
13. Close the page.

