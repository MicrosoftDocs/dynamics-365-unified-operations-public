--- 
title: Import ISO20022 direct debit configuration
description: Learn how to import a customer payment electronic reporting configuration, including a step-by-step process using the DEMF demo data company. 
author: mrolecki
ms.author: mrolecki
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: johnmichalak  
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionImport
ms.dyn365.ops.version: Version 7.0.0 
---

# Import ISO20022 direct debit configuration

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to import a customer payment electronic reporting configuration. This procedure uses the ISO 20022 direct debit format as an example. 



This procedure was created using the demo data company DEMF but you can use any demo data company for this purpose.



This is the first of five procedures that demonstrate the customer payment process using electronic reporting configurations.

1. Go to Organization administration > Workspaces > Electronic reporting.
2. In the list of available configuration providers, select Microsoft.
3. Click Set active.
4. Click Repositories.
5. Click Open.
6. Click Show filters.
7. Apply the following filters: Enter a filter value of "ISO20022 Direct debit (DE)" on the "Configuration name" field using the "begins with" filter operator
    * Optionally, you can find the configuration in the list, select it, and skip this step.  
8. Click Import.
    * If the Import button is not available, it means that the configuration has been imported already.  
9. Click Yes.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]