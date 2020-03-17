--- 
# required metadata 
 
title: Design ER configurations to generate reports in Word format
description: The following steps explain how a user in either the System administrator or Electronic reporting developer role can configure an Electronic reporting formats to generate reports as Microsoft Word files. 
author: NickSelin
manager: AnnBe 
ms.date: 08/12/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: ERWorkspace, ERSolutionTable, EROperationDesigner,  LedgerJournalTable, LedgerJournalTransVendPaym   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Design ER configurations to generate reports in Word format

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in either the System administrator or Electronic reporting developer role can configure an Electronic reporting (ER) formats to generate reports as Microsoft Word files. These steps can be performed in the GBSI company.

To complete these steps, you must first complete the steps in the "Create an ER configuration for generating reports in OPENXML format" task guide. In advance, you must also download and save the following templates locally for the sample report:

- [Template of Payment Report](https://go.microsoft.com/fwlink/?linkid=862266)
- [Bounded Template of Payment Report](https://go.microsoft.com/fwlink/?linkid=862266)


This procedure is for a feature that was added in Microsoft Dynamics 365 for Operations version 1611.


## Select the existing ER report configuration
1. In the **Navigation pane, go to Modules > Organization administration > Workspaces > Electronic reporting**. Make sure that the configuration provider 'Litware, Inc.' is selected as active.  
2. Click **Reporting configurations**. We will re-use the existing ER configuration that has been originally designed to generate the report output in OPENXML format.  
3. In the tree, expand 'Payment model'.
4. In the tree, select 'Payment model\Sample worksheet report'.
5. Click Designer.

## Replace the Excel template with the Word template

Currently, the Excel document is used as a template to generate the output in OPENXML format. We will import the report's template in Word format.

1. Click **Attachments**. Replace the existing Excel template with the Word template that you downloaded earlier, SampleVendPaymDocReport.docx. Note, this template only contains the layout of the document we want to generate as ER output.  
2. Click **Delete**.
3. Click **Yes**.
4. Click **New**.
5. Click **File**.
6. Click **Browse**. Navigate to and select SampleVendPaymDocReport.docx that you previously downloaded. Click **OK**. Select the template that you downloaded in the previous step.  
7. In the **Template** field, enter or select a value.

## Extend the Word template by adding a custom XML part
1. Click **Save**. In addition to storing configuration changes, the Save action also updates the attached Word template. The structure of the designed format is ported to the attached Word document as a new custom XML part with the name 'Report'. Note that the attached Word template contains not only the layout of the document we want to generate as ER output, it also contains the structure of data that ER will populate into this template at runtime.  
2. Click **Attachments**.
    + Now you need to bind the elements of the custom XML part 'Report' to the Word document parts.  
    + If you're familiar with Word documents that can be designed as forms containing content controls that are bounded with elements of custom XML parts – play all steps of the next sub-task to create such a document. For more details, see [Create forms that users complete or print in Words](https://support.office.com/article/Create-forms-that-users-complete-or-print-in-Word-040c5cc1-e309-445b-94ac-542f732c8c8b?ui=en-US&rs=en-US&ad=US). Otherwise, skip all the steps in the next sub-task.  

## Get Word with custom XML part to do data bindings

Open this document in Word and do the following:  
1. Open the Word Developer tab (customize the ribbon if it is not enabled yet).
2. Select XML mapping pane.
3. Select the 'Report' custom XML part in the lookup.
4. Do mapping of the elements of the selected custom XML part and content controls of the Word document.  5. Save the updated Word document on a local drive.  

## Upload the Word template with custom XML part bounded to content controls
1. Click **Delete**.
2. Click **Yes**. Add a new template. If you competed the steps in the previous subtask, select the Word document that you prepared and saved locally. Otherwise, select the SampleVendPaymDocReportBounded.docx MS Word template that you downloaded earlier.  
3. Click **New**.
4. Click **File**.
5. Click **Browse**. Navigate to and select SampleVendPaymDocReportBounded.docx that you previously downloaded. Click **OK**.
6. In the **Template** field, select the document that you downloaded in the previous step.
7. Click **Save**.
8. Close the page.

## Execute the format to create Word output
1. On the **Action Pane**, click **Configurations**.
2. Click **User parameters**.
3. Select Yes in the **Run settings** field.
4. Click **OK**.
5. Click **Edit**.
6. Select Yes in the **Run Draft** field.
7. Click **Save**.
8. Close the page.
9. Close the page.
10. In the **Navigation pane**, go to **Modules > Accounts payable > Payments > Payment journal**.
11. Click **Lines**.
12. In the list, mark or unmark all rows.
13. Click **Payment status**.
14. Click **None**.
15. Click **Generate payments**.
16. Click **OK**.
17. Click **OK**. Analyze the generated output. Note that the created output is presented in Word format and contains the details of the processed payments.  

