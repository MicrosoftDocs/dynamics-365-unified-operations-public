---
title: ER Use Document Management files in format outputs (Part 1 - Prepare data model)
description: This article describes how to configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. (Part 1)
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
  - ERSolutionTable, ERSolutionCreateDropDialog
---
# ER Use Document Management files in format outputs (Part 1 - Prepare data model)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. These steps can be performed in any company.

To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Get access to the list of configurations provided by Microsoft
1. Go to Organization administration > Workspaces > Electronic reporting.

    Make sure that the 'Litware, Inc.' provider is available and marked as active.  

2. Select the 'Litware, Inc.' provider.
3. Click Repositories.

    If a repository of the 'Operations resources' type already exists, skip the remaining steps of the current sub-task.  

4. Click Add to open the drop dialog.
5. In the Configuration repository type field, enter 'Operations resources'.
6. Click Create repository.
7. Click OK.

## Get the Customer invoice model configurations provided by Microsoft
1. Click Show filters.
2. Apply the following filters: Enter a filter value of "Operations resources" on the "Name" field using the "begins with" filter operator; Enter a filter value of "" on the "Description" field using the "begins with" filter operator
3. Click Show filters.
4. Click Open.
5. In the tree, select 'Customer invoice model'.

    Select the model configuration 'Customer invoice model' to import it.  

6. Click Import.

    Click Import for version 1 of the selected configuration.  

7. Click Yes.
8. Close the page.
9. Close the page.
10. Click Reporting configurations.
11. In the tree, select 'Customer invoice model'.

## Create the derived model to support access to the Document Management files.
You will create our own configuration of the Customer invoice model deriving it from the configuration provided by Microsoft. You will use this configuration to implement access to the Document Management files and make them available for electronic documents that you will create based on this model.  
1. Click Create configuration to open the drop dialog.
2. In the New field, enter 'Derive from Name: Customer invoice model, Microsoft'.
3. In the Name field, type 'Customer invoice model (custom)'.
4. Click Create configuration.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
