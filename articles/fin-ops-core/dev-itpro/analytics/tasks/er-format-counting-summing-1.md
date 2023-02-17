---
title: ER Configure format to do counting and summing (Part 1 - Create format)
description: This article describes how to configure an Electronic reporting format to do counting and summing based on data of the already generated text output. (Part 1)
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionRepositoryCreateDropDialog, ERSolutionImport
  - ERSolutionTable
---
# ER Configure format to do counting and summing (Part 1 - Create format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to do counting and summing based on data of the already generated text output. These steps can be performed in any company.

To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Get access to the list of configurations provided by Microsoft
1. Go to Organization administration > Workspaces > Electronic reporting.
    * Make sure that the "Litware, Inc." provider is available and marked as active.  
2. Select the "Litware, Inc." provider.
3. Click Repositories.
    * If a repository of the "Operations resources" type already exists, skip the remaining steps of the current sub-task.  
4. Click Add to open the drop dialog.
5. In the Configuration repository type field, enter 'Operations resources'.
6. Click Create repository.
7. Click OK.

## Get the Intrastat configurations provided by Microsoft
1. Click Open.
2. In the tree, select 'Intrastat model\Intrastat (DE)'.
3. Click Import.
    * Click Import for version 1.1 of the selected configuration.  
4. Click Yes.
5. Close the page.
6. Close the page.
7. Click Reporting configurations.
8. In the tree, expand 'Intrastat model'.
9. In the tree, select 'Intrastat model\Intrastat (DE)'.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
