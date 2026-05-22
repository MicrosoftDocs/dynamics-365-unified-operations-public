---
title: ER Use horizontally expandable ranges to dynamically add columns in Excel reports (Part 1 - Design format)
description: This article describes how to configure an Electronic reporting (ER) format to generate reports as OPENXML worksheets (Excel) files. (Part 1)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERComponentTypeDropDialog
---

# ER Use horizontally expandable ranges to dynamically add columns in Excel reports (Part 1 - Design format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to generate reports as OPENXML worksheets (Excel) files in which the required columns can be created dynamically as horizontally expandable ranges. These steps can be performed in any company.

To complete these steps, you must first complete these three task guides:

"ER Create a configuration provider and mark it as active"

"ER Use financial dimensions as a data source (Part 1: Design data model)"

"ER Use financial dimensions as a data source (Part 2: Model mapping)"

You must also download and save a local copy of the template with a sample report found here, [Sample Financial Dimensions Web Service Report](https://download.microsoft.com/download/3/1/3/313e2090-bc0a-421f-bf96-c58da9bc0dea/SampleFinDimWsReport.xlsx).

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Create a new report configuration

1. Go to Organization administration > Electronic reporting > Configurations.
1. In the tree, select `Financial dimensions sample model`.
1. Click Create configuration to open the drop dialog.
1. In the New field, enter `Format based on data model Financial dimensions sample model`.
    * Use the model created in advance as the data source for your new report.  
1. In the Name field, type `Sample report with horizontally expandable ranges`.
    * Sample report with horizontally expandable ranges  
1. In the Description field, type `To make Excel output with dynamically adding columns`.
    * To make Excel output with dynamically adding columns  
1. In the Data model definition field, select Entry.
1. Click Create configuration.

## Design the report format

1. Click Designer.
1. Turn on the `Show details` toggle button.
1. On the Action Pane, click Import.
1. Click Import from Excel.
1. Click Attachments.
    * Import the report`s template. Use Excel file that you downloaded for that.  
1. Click New.
1. Click File.
1. Close the page.
1. In the Template field, enter or select a value.
    * Select the downloaded template.  
1. Click OK.
    * Add a new range to dynamically create Excel output with as many columns as you selected (in the user dialog form) for financial dimensions. Each cell for every column will represent a single financial dimension`s name.  
1. Click Add to open the drop dialog.
1. In the tree, select `Excel\Range`.
1. In the Excel range field, type `DimNames`.
    * DimNames  
1. In the Replication direction field, select `Horizontal`.
1. Click OK.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal`.
1. Click Move up.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Cell<DimNames>`.
1. Click Cut.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal`.
1. Click Paste.
1. In the tree, expand `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal`.
1. In the tree, expand `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical`.
1. In the tree, expand `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical`.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical`.
    * Add a new range to dynamically create Excel output with as many columns as you selected (in the user dialog form) for financial dimensions. Each cell for every column will represent a single financial dimension`s value for each reporting transaction.  
1. Click Add Range.
1. In the Excel range field, type `DimValues`.
    * DimValues  
1. In the Replication direction field, select `Horizontal`.
1. Click OK.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<DimValues>`.
1. Click Cut.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Range<DimValues>: Horizontal`.
1. Click Paste.
1. In the tree, expand `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Range<DimValues>: Horizontal`.

## Map format elements to data sources

1. Click the Mapping tab.
1. In the tree, expand `model: Data model Financial dimensions sample model`.
1. In the tree, expand `model: Data model Financial dimensions sample model\Journal: Record list`.
1. In the tree, expand `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list`.
1. In the tree, expand `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list`.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Range<DimValues>: Horizontal\Cell<DimValues>`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list\Code: String`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Range<DimValues>: Horizontal`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<Credit>`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Credit: Real`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<Debit>`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Debit: Real`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<Currency>`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Currency: String`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<TransDate>`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Date: Date`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<TransVoucher>`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Voucher: String`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<TransBatch>`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Batch: String`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Cell<Batch>`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Batch: String`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical`.
1. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list`.
1. Click Bind.
1. In the tree, expand `model: Data model Financial dimensions sample model\Dimensions setting: Record list`.
1. In the tree, select `model: Data model Financial dimensions sample model\Dimensions setting: Record list\Code: String`.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal\Cell<DimNames>`.
1. Click Bind.
1. In the tree, select `model: Data model Financial dimensions sample model\Dimensions setting: Record list`.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal`.
1. Click Bind.
1. In the tree, select `Excel = "SampleFinDimWsReport"\Cell<CompanyName>`.
1. In the tree, select `model: Data model Financial dimensions sample model\Company: String`.
1. Click Bind.
1. Click Save.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
