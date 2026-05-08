---
title: ER Use Document Management files in format outputs (Part 2 - Extend data model)
description: This article describes how to configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. (Part 2)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERDataModelDesigner, ERDataModelContentsItemCreationDialog, ERModelMappingTable, ERModelMappingDesigner, ERExpressionDesignerFormula
---

# ER Use Document Management files in format outputs (Part 2 - Extend data model)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the System Administrator or Electronic Reporting Developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. You can perform these steps in any company.

To complete these steps, you must first complete the steps in the "ER Use Document Management files in format outputs (Part 1: Prepare data model)" task guide.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Extend data model to present the Document Management files in it

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select **Reporting configurations**.
1. In the tree, expand **Customer invoice model**.
1. In the tree, select **Customer invoice model\Customer invoice model (custom)**.
1. Select **Designer**.
1. In the tree, select **Customer invoice(InvoiceCustomer)**.
    * Extend this data model to expose any files that you attached to a sales order that is related to an electronically processing invoice.  
1. Select **New** to open the drop dialog.
1. In the **Name** field, type **Invoice attachments**.
    * Invoice attachments  
1. In the **Item type** field, select **Record list**.
1. Select **Add**.
1. Select **New** to open the drop dialog.
1. In the **Name** field, type **File content**.
    * File content  
1. In the **Item type** field, select **Container**.
1. Select **Add**.
1. Select **New** to open the drop dialog.
1. In the **Name** field, type **File name**.
    * File name  
1. In the **Item type** field, select **String**.
1. Select **Add**.

## Map new data model elements to data sources

1. Select **Map model to datasource**.
1. Use the Quick Filter to filter on the Definition field with a value of `InvoiceCustomer`.
    * InvoiceCustomer  
    * Map new model elements to appropriate data sources.  
1. Select **Designer**.
1. In the tree, select **Invoice attachments**.
1. In the tree, expand **Invoice attachments**.
1. In the tree, select **Invoice attachments\File name**.
1. Select **Edit**.
1. In the Formula field, enter `CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'.'originalFileName()'`.
    * `CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'.'originalFileName()'`  
1. Select **Save**.
1. Close the page.
1. In the tree, select **Invoice attachments\File content**.
1. Select **Edit**.
1. In the Formula field, enter `CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'.'getFileContentAsContainer()'`.
    * `CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'.'getFileContentAsContainer()'`  
1. Select **Save**.
1. Close the page.
1. In the tree, select **Invoice attachments**.
1. Select **Edit**.
1. In the Formula field, enter `CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'`.
    * `CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'`  
1. Select **Save**.
1. Close the page.
1. Select **Save**.
1. Close the page.
1. Close the page.
1. Close the page.
1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
