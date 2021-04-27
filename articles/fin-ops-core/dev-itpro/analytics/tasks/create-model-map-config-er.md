--- 
# required metadata 
 
title: Create Electronic reporting (ER) model mapping configurations
description: Use this procedure to design a new Electronic reporting (ER) model mapping configuration and use built-in ER functions for efficient aggregate calculations. 
author: NickSelin
ms.date: 12/12/2017
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 

---
# Create Electronic reporting (ER) model mapping configurations

[!include [banner](../../includes/banner.md)]

Use this procedure to design a new Electronic reporting (ER) model mapping configuration and use built-in ER functions for efficient aggregate calculations. In this procedure, you will create a configuration for sample company, Litware, Inc. 

This procedure is created for uses with the assigned role of System administrator or Electronic reporting developer.

These steps can be completed using any dataset. To complete these steps, you must first complete the steps in the procedure, "Create a configuration provider and mark it as active."

1. Go to Organization administration > Workspaces > Electronic reporting.
    * Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as Active. If you don't see this configuration provider, complete the steps in the procedure, "Create a configuration provider and mark it as active".  
2. Click Reporting configurations.
3. Click Show filters.
4. In the "Name" field, enter the filter value, "Intrastat" and use the filter operator "begins with".
    * Apply this filter to find the 'Intrastat' data model configuration. This model may already exist in the configurations tree. If it does, skip the next sub-task.   

## Get the Intrastat model configuration provided by Microsoft
1. Close the page.
2. Close the page.
3. Go to Organization administration > Workspaces > Electronic reporting.
4. In the list, find and select the desired record.
    * Select the Microsoft provider tile.  
5. Click Repositories.
    * Click Repositories in the Microsoft provider tile.  
6. Click Show filters.
7. In the "Type name" field, enter the filter value, "resources" and use the filter operator "contains". 
8. Click Open.
9. In the tree, select 'Intrastat model'.
10. Click Import.
11. Click Yes.
    * You imported the ER model configuration that contains the data model that you will use to explore how the new ER functionality can be used.  
12. Close the page.
13. Close the page.
14. Click Reporting configurations.

## Add a new model mapping configuration
1. In the tree, select 'Intrastat model'.
2. Click Create configuration to open the drop dialog.
3. In the New field, enter 'Model Mapping based on data model Intrastat'.
4. In the Name field, type 'Intrastat sample mapping'.
    * Intrastat sample mapping  
5. Click Create configuration.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]