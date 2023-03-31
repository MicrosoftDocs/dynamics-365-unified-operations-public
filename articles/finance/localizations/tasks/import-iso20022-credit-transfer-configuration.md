--- 
# required metadata 
 
title: Import ISO20022 credit transfer configuration
description: This procedure shows how to import a vendor payment electronic reporting configuration. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionImport   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Import ISO20022 credit transfer configuration

[!include [banner](../../includes/banner.md)]

This procedure shows how to import a vendor payment electronic reporting configuration. The German ISO 20022 credit transfer format is used as an example. This procedure can be used for other available electronic reporting format. 

This task was created using the demo data company DEMF but you can use any demo data company to complete this task.

This is the first of five tasks, that together illustrate the vendor payment process using electronic reporting configurations. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

1. Go to Organization administration > Workspaces > Electronic reporting.
2. In the list of available configuration providers, select Microsoft.
3. Click Set active.
4. Click Repositories.
5. Click Open.
6. Click Show filters.
7. Apply the following filters: Enter a filter value of "ISO20022 Credit transfer (DE)" on the "Configuration name" field using the "begins with" filter operator
    * Alternatively, you can find the configuration in the list, select it, and then move it to the Import task.  
8. Click Import.
    * If the Import button is not available, it means that the configuration has  already been imported.  
9. Click Yes.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]