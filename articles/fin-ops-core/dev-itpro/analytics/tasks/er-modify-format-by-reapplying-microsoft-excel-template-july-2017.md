--- 
# required metadata 
 
title: Modify formats by reapplying Excel templates
description: To complete the steps in this procedure, you must first complete the procedure, ER - Design a configuration for generating reports in OPENXML format. 
author: NickSelin
ms.date: 06/19/2017
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
ms.dyn365.ops.version: AX 7.0.0 
---
# Modify formats by reapplying Excel templates

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, ER - Design a configuration for generating reports in OPENXML format.

This procedure explains how to modify an Electronic reporting (ER) format configuration by reapplying a Microsoft Excel template that has been modified. In this procedure, you will import a modified Excel template into ER format configurations that have been created for the sample company, Litware, Inc., and then generate electronic documents. This procedure is intended for users who have the system administrator or electronic reporting developer role. These steps can be completed by using the GBSI dataset. Before you begin, download and save the file, SampleVendPaymWsReport2.xlsx, which is listed in the Help topic, Modify Electronic reporting format by reapplying an Excel template (modify-electronic-reporting-format-reapply-excel-template/).

1. Go to Organization administration > Workspaces > Electronic reporting.
    * Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as Active. If you don't see this configuration provider, complete the steps in the procedure, Create a configuration provider and mark it as active.  

## Select the ER format
1. Click Reporting configurations.
2. In the tree, expand 'Payment model'.
3. In the tree, select 'Payment model\Sample worksheet report'.
4. Click Attachments.
    * Note that the SampleVendPaymWsReport.xlsx Excel file is currently used as a template for payment journal processing.   
5. Click Open.
    * Click Open to explore the layout of the Excel template.  
    * Review the template. Note that it currently includes the following details for each payment line: vendor account number, vendor name, bank, routing number, account number, debit, credit, and currency. For this example, we want to extend this list by adding details about the payment date.   
6. Close the page.

## Reapply a new Excel template to ER format
1. Click Designer.
    * Open the draft version of the selected ER format for editing.  
2. On the Action Pane, click Import.
3. Click Update from Excel.
    * Click 'Update template', and then select the file, SampleVendPaymWsReport2.xlsx.  
    * Click Update template and browse to get the downloaded earlier SampleVendPaymWsReport2.xlsx file.  
4. Click OK.
    * The SampleVendPaymWsReport2.xlsx template is applied. The structure of the ER format is synchronized with the content of the template, whose elements are added to the ER format. Any existing elements in the ER format that aren't included in the template are removed from the format definition.  
5. In the tree, select 'Excel'.
    * Note that the Template field now contains a reference to the new template.   
6. Click Attachments.
7. Click Open.
    * Click Open to explore the layout of the modified Excel template.  
    * Review the template. Note that it now contains a line for the payment date.   
8. Close the page.
9. In the tree, expand 'Excel'.
10. In the tree, expand 'Excel\PaymLines'.
11. In the tree, select 'Excel\PaymLines\PaymDate'.
    * Note that the ER format now contains one more item. A cell, PaymDate, has been added to the Excel template.  
12. Click the Mapping tab.
13. In the tree, expand 'model'.
14. In the tree, expand 'model\Payments'.
15. In the tree, select 'model\Payments\Transaction date(TransactionDate)'.
16. Click Bind.
    * Specify what data is added to the new cell at runtime.  
17. Click Save.
18. Close the page.

## Enable the modified draft version of the ER format for use in payment journal processing
1. On the Action Pane, click Configurations.
2. Click User parameters.
3. Select Yes in the Run settings field.
4. Click OK.
5. Click Edit.
6. Select Yes in the Run Draft field.

## Use the modified draft version of the ER format for payment journal processing

Review the created worksheet, including new detail of payment lines – payment date.  


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]