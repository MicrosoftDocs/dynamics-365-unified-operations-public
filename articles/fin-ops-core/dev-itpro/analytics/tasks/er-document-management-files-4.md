---
title: ER Use Document Management files in format outputs (Part 4 - Run format)
description: This article describes how to configure an Electronic reporting format to use Document Management files in ER output. (Part 4)
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
ms.search.form: CustOpenInvoicesListPage, CustInvoiceJournal, SalesTable, ERSolutionTable
---
# ER Use Document Management files in format outputs (Part 4 - Run format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. These steps can be performed in the DEMF company.

To complete these steps, you must first complete the steps in the "ER Use Document Management files in format outputs (Part 3: Create format)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Add necessary attachments for sales order of a single invoice
1. Go to Accounts receivable > Invoices > Open customer invoices.
2. Use the Quick Filter to find records. For example, filter on the Invoice field with a value of 'CIV-000148'.
    * CIV-000148  
3. Click to follow the selected invoice's link.
    * CIV-000148  
4. Click to follow the link in the Sales order field.
    * 000148  
5. In the Lines or header field, select the option of Header.
    * Select Header to indicate that this will be the target for adding attachments.  
6. Click Attach.
    * Add a few files as attachments for this sales order. Use the files of the document types that are supported by the Document Management (with file extensions DOCX, DPF, XML, JPG, etc.). Browse and select files to be attached and further processed with the related invoice in the ER electronic message.  
7. Click New.
8. Click File.
9. Click New.
10. Click File.
11. Close the page.
12. Close the page.
13. Close the page.
14. Close the page.

## Run the designed report for the selected invoice
1. Go to Organization administration > Electronic reporting > Configurations.
2. In the tree, expand 'Customer invoice model'.
3. In the tree, expand 'Customer invoice model\Customer invoice model (custom)'.
4. In the tree, select 'Customer invoice model\Customer invoice model (custom)\Electronic invoice sample message'.
5. Click Run.
6. Expand the Records to include () section.
7. Click Filter.
8. Select the row of the Customer invoice journal and the Sales order field.
9. In the Criteria field, type '000148'.
    * In the criteria "Sales order" field, type the order number 000148.  
10. Click OK.
11. Click OK.
    * Review the generated output. Note that for each attachment a single XML node has been created. The attachment's content is populated to the XML output in MIME (base64) text format.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
