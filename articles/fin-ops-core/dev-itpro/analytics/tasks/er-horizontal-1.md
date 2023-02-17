---
title: ER Use horizontally expandable ranges to dynamically add columns in Excel reports (Part 1 - Design format)
description: This article describes how to configure an Electronic reporting (ER) format to generate reports as OPENXML worksheets (Excel) files. (Part 1)
author: kfend
ms.date: 04/23/2021
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
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
2. In the tree, select `Financial dimensions sample model`.
3. Click Create configuration to open the drop dialog.
4. In the New field, enter `Format based on data model Financial dimensions sample model`.
    * Use the model created in advance as the data source for your new report.  
5. In the Name field, type `Sample report with horizontally expandable ranges`.
    * Sample report with horizontally expandable ranges  
6. In the Description field, type `To make Excel output with dynamically adding columns`.
    * To make Excel output with dynamically adding columns  
7. In the Data model definition field, select Entry.
8. Click Create configuration.

## Design the report format

1. Click Designer.
2. Turn on the `Show details` toggle button.
3. On the Action Pane, click Import.
4. Click Import from Excel.
5. Click Attachments.
    * Import the report`s template. Use Excel file that you downloaded for that.  
6. Click New.
7. Click File.
8. Close the page.
9. In the Template field, enter or select a value.
    * Select the downloaded template.  
10. Click OK.
    * Add a new range to dynamically create Excel output with as many columns as you selected (in the user dialog form) for financial dimensions. Each cell for every column will represent a single financial dimension`s name.  
11. Click Add to open the drop dialog.
12. In the tree, select `Excel\Range`.
13. In the Excel range field, type `DimNames`.
    * DimNames  
14. In the Replication direction field, select `Horizontal`.
15. Click OK.
16. In the tree, select `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal`.
17. Click Move up.
18. In the tree, select `Excel = "SampleFinDimWsReport"\Cell<DimNames>`.
19. Click Cut.
20. In the tree, select `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal`.
21. Click Paste.
22. In the tree, expand `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal`.
23. In the tree, expand `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical`.
24. In the tree, expand `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical`.
25. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical`.
    * Add a new range to dynamically create Excel output with as many columns as you selected (in the user dialog form) for financial dimensions. Each cell for every column will represent a single financial dimension`s value for each reporting transaction.  
26. Click Add Range.
27. In the Excel range field, type `DimValues`.
    * DimValues  
28. In the Replication direction field, select `Horizontal`.
29. Click OK.
30. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<DimValues>`.
31. Click Cut.
32. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Range<DimValues>: Horizontal`.
33. Click Paste.
34. In the tree, expand `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Range<DimValues>: Horizontal`.

## Map format elements to data sources

1. Click the Mapping tab.
2. In the tree, expand `model: Data model Financial dimensions sample model`.
3. In the tree, expand `model: Data model Financial dimensions sample model\Journal: Record list`.
4. In the tree, expand `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list`.
5. In the tree, expand `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list`.
6. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Range<DimValues>: Horizontal\Cell<DimValues>`.
7. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list\Code: String`.
8. Click Bind.
9. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Range<DimValues>: Horizontal`.
10. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list`.
11. Click Bind.
12. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<Credit>`.
13. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Credit: Real`.
14. Click Bind.
15. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<Debit>`.
16. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Debit: Real`.
17. Click Bind.
18. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<Currency>`.
19. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Currency: String`.
20. Click Bind.
21. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<TransDate>`.
22. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Date: Date`.
23. Click Bind.
24. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<TransVoucher>`.
25. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Voucher: String`.
26. Click Bind.
27. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical\Cell<TransBatch>`.
28. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Batch: String`.
29. Click Bind.
30. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Range<TransactionLine>: Vertical`.
31. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list`.
32. Click Bind.
33. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical\Cell<Batch>`.
34. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list\Batch: String`.
35. Click Bind.
36. In the tree, select `Excel = "SampleFinDimWsReport"\Range<JournalLine>: Vertical`.
37. In the tree, select `model: Data model Financial dimensions sample model\Journal: Record list`.
38. Click Bind.
39. In the tree, expand `model: Data model Financial dimensions sample model\Dimensions setting: Record list`.
40. In the tree, select `model: Data model Financial dimensions sample model\Dimensions setting: Record list\Code: String`.
41. In the tree, select `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal\Cell<DimNames>`.
42. Click Bind.
43. In the tree, select `model: Data model Financial dimensions sample model\Dimensions setting: Record list`.
44. In the tree, select `Excel = "SampleFinDimWsReport"\Range<DimNames>: Horizontal`.
45. Click Bind.
46. In the tree, select `Excel = "SampleFinDimWsReport"\Cell<CompanyName>`.
47. In the tree, select `model: Data model Financial dimensions sample model\Company: String`.
48. Click Bind.
49. Click Save.
50. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
