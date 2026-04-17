---
title: ER Use Document Management files in format outputs (Part 3 - Create format)
description: This article describes how to configure an Electronic reporting format to use Document Management files in ER output. (Part 3)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERComponentTypeDropDialog
---

# ER use Document Management files in format outputs (Part 3 - Create format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. You can perform these steps in any company.

To complete these steps, you must first complete the steps in the "ER Use Document Management files in format outputs (Part 2: Extend data model" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Create a format to process invoices

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select **Reporting configurations**.
1. In the tree, expand **Customer invoice model**.
1. In the tree, select **Customer invoice model\Customer invoice model (custom)**.
    * You create a format to generate electronic messages with information about any files that you attach to a sales order that relates to an electronically processing invoice.  
1. Select **Create configuration** to open the drop dialog.
1. In the **New** field, enter *Format based on data model Customer invoice model (custom)*.
1. In the **Name** field, type *Electronic invoice sample message*.
    * Electronic invoice sample message  
1. In the **Data model definition** field, enter or select a value.
    * InvoiceCustomer  
1. Select **Create configuration**.

## Design a format to populate attachments into generating a message in MIME format

1. Click **Designer**.
1. Click **Add root** to open the drop dialog.
1. In the tree, select **XML\Element**.
1. In the **Name** field, type **Invoice**.
    * Invoice  
1. Click **OK**.
1. Click **Add** to open the drop dialog.
1. In the tree, select **XML\Attribute**.
1. In the **Name** field, type **SalesOrder**.
    * SalesOrder  
1. Click **OK**.
1. Click **Add Attribute**.
1. In the **Name** field, type **InvoiceNumber**.
    * InvoiceNumber  
1. Click **OK**.
1. Click **Add Attribute**.
1. In the **Name** field, type **InvoiceAmount**.
    * InvoiceAmount  
1. Click **OK**.
1. Click **Add** to open the drop dialog.
1. In the tree, select **XML\Element**.
1. In the **Name** field, type **EnclosedDocs**.
    * EnclosedDocs  
1. Click **OK**.
1. In the tree, select **Invoice\EnclosedDocs**.
1. Click **Add Element**.
1. In the **Name** field, type **Document**.
    * Document  
1. Click **OK**.
1. In the tree, select **Invoice\EnclosedDocs\Document**.
1. Click **Add** to open the drop dialog.
1. In the tree, select **XML\Attribute**.
1. In the **Name** field, type **FileName**.
    * FileName  
1. Click **OK**.
1. Click **Add** to open the drop dialog.
1. In the tree, select **XML\Element**.
1. In the **Name** field, type **FileContent**.
    * FileContent  
1. Click **OK**.
1. In the tree, select **Invoice\EnclosedDocs\Document\FileContent**.
1. Click **Add** to open the drop dialog.
1. In the tree, select **Text\Base64**.
1. Click **OK**.

## Map format elements to data model as data source

1. In the tree, select `Invoice\SalesOrder`.
1. Select the **Mapping** tab.
1. In the tree, expand `model`.
1. In the tree, select `model\Sales order number(SalesId)`.
1. Select **Bind**.
1. In the tree, select `Invoice\InvoiceNumber`.
1. In the tree, expand `model\Base invoice(InvoiceBase)`.
1. In the tree, select `model\Base invoice(InvoiceBase)\Invoice number(Id)`.
1. Select **Bind**.
1. In the tree, select `Invoice\InvoiceAmount`.
1. In the tree, select `model\Base invoice(InvoiceBase)\Invoice amount(Amount)`.
1. Select **Bind**.
1. In the tree, expand `model\Invoice attachments`.
1. In the tree, select `model\Invoice attachments\File content`.
1. In the tree, select `Invoice\EnclosedDocs\Document\FileContent\Base64`.
1. Select **Bind**.
1. In the tree, select `model\Invoice attachments\File name`.
1. In the tree, select `Invoice\EnclosedDocs\Document\FileName`.
1. Select **Bind**.
1. In the tree, select `model\Invoice attachments`.
1. In the tree, select **Invoice\EnclosedDocs\Document**.
1. Select **Bind**.
1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
