---
title: ER Use Document Management files in format outputs (Part 1 - Prepare data model)
description: This article describes how to configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. (Part 1)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionRepositoryCreateDropDialog, ERSolutionImport
  - ERSolutionTable, ERSolutionCreateDropDialog
---

# ER use Document Management files in format outputs (Part 1 - Prepare data model)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. You can perform these steps in any company.

To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Get access to the list of configurations provided by Microsoft

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.

    Make sure that the **Litware, Inc.** provider is available and marked as active.  

1. Select the **Litware, Inc.** provider.
1. Select **Repositories**.

    If a repository of the **Operations resources** type already exists, skip the remaining steps of the current sub-task.  

1. Select **Add** to open the drop dialog.
1. In the **Configuration repository type** field, enter **Operations resources**.
1. Select **Create repository**.
1. Select **OK**.

## Get the customer invoice model configurations provided by Microsoft

1. Select **Show filters**.
1. Apply the following filters: Enter a filter value of **Operations resources** on the **Name** field by using the **begins with** filter operator. Enter a filter value of "" on the **Description** field by using the **begins with** filter operator.
1. Select **Show filters**.
1. Select **Open**.
1. In the tree, select **Customer invoice model**.

    Select the model configuration **Customer invoice model** to import it.  

1. Select **Import**.

    Select **Import** for version 1 of the selected configuration.  

1. Select **Yes**.
1. Close the page.
1. Close the page.
1. Select **Reporting configurations**.
1. In the tree, select **Customer invoice model**.

## Create the derived model to support access to the Document Management files

Create your own configuration of the Customer invoice model by deriving it from the configuration provided by Microsoft. Use this configuration to implement access to the Document Management files and make them available for electronic documents that you create based on this model.  

1. Select **Create configuration** to open the drop dialog.
1. In the **New** field, enter `Derive from Name: Customer invoice model, Microsoft`.
1. In the **Name** field, type `Customer invoice model (custom)`.
1. Select **Create configuration**.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
