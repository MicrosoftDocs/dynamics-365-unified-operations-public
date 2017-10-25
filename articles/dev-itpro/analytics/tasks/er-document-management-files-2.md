--- 
# required metadata 
 
title: Extend data model to use Document Management files in format outputs for electronic reporting (ER)
description: The following steps explain how a user assigned to the System Administrator or Electronic Reporting Developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. 
author: NickSelin
manager: AnnBe 
ms.date: 10/28/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Extend data model to use Document Management files in format outputs for electronic reporting (ER)

[!include[task guide banner](../../includes/task-guide-banner.md)]

The following steps explain how a user assigned to the System Administrator or Electronic Reporting Developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. These steps can be performed in any company.

To complete these steps, you must first complete the steps in the “ER Use Document Management files in format outputs (Part 1: Prepare data model)” task guide.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Extend data model to present the Document Management files in it
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Reporting configurations.
3. In the tree, expand 'Customer invoice model'.
4. In the tree, select 'Customer invoice model\Customer invoice model (custom)'.
5. Click Designer.
6. In the tree, select 'Customer invoice(InvoiceCustomer)'.
    * We will extend this data model to expose in it any files that have been attached to a sales order that is related to an electronically processing invoice.  
7. Click New to open the drop dialog.
8. In the Name field, type 'Invoice attachments'.
    * Invoice attachments  
9. In the Item type field, select 'Record list'.
10. Click Add.
11. Click New to open the drop dialog.
12. In the Name field, type 'File content'.
    * File content  
13. In the Item type field, select 'Container'.
14. Click Add.
15. Click New to open the drop dialog.
16. In the Name field, type 'File name'.
    * File name  
17. In the Item type field, select 'String'.
18. Click Add.

## Map new data model elements to Dynamics 365 for Finance and Operations, Enterprise edition data sources
1. Click Map model to datasource.
2. Use the Quick Filter to filter on the Definition field with a value of 'InvoiceCustomer'.
    * InvoiceCustomer  
    * We will map new model elements to appropriate data sources.  
3. Click Designer.
4. In the tree, select 'Invoice attachments'.
5. In the tree, expand 'Invoice attachments'.
6. In the tree, select 'Invoice attachments\File name'.
7. Click Edit.
8. In the Formula field, enter 'CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'.'originalFileName()''.
    * CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'.'originalFileName()'  
9. Click Save.
10. Close the page.
11. In the tree, select 'Invoice attachments\File content'.
12. Click Edit.
13. In the Formula field, enter 'CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'.'getFileContentAsContainer()''.
    * CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'.'getFileContentAsContainer()'  
14. Click Save.
15. Close the page.
16. In the tree, select 'Invoice attachments'.
17. Click Edit.
18. In the Formula field, enter 'CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents''.
    * CustInvoiceJour.'>Relations'.SalesTable.'<Relations'.'<Documents'  
19. Click Save.
20. Close the page.
21. Click Save.
22. Close the page.
23. Close the page.
24. Close the page.
25. Click Change status.
26. Click Complete.
27. Click OK.

