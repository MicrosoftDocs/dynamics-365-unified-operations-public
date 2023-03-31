---
title: ER Use Document Management files in format outputs (Part 3 - Create format)
description: This article describes how to configure an Electronic reporting format to use Document Management files in ER output. (Part 3)
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
ms.search.form: ERWorkspace, ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERComponentTypeDropDialog
---

# ER Use Document Management files in format outputs (Part 3 - Create format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. These steps can be performed in any company.

To complete these steps, you must first complete the steps in the "ER Use Document Management files in format outputs (Part 2: Extend data model" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Create a format to process invoices
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Reporting configurations.
3. In the tree, expand 'Customer invoice model'.
4. In the tree, select 'Customer invoice model\Customer invoice model (custom)'.
    * You will create a format to generate electronic messages with information about any files that have been attached to a sales order that is related to an electronically processing invoice.  
5. Click Create configuration to open the drop dialog.
6. In the New field, enter 'Format based on data model Customer invoice model (custom)'.
7. In the Name field, type 'Electronic invoice sample message'.
    * Electronic invoice sample message  
8. In the Data model definition field, enter or select a value.
    * InvoiceCustomer  
9. Click Create configuration.

## Design a format to populate attachments into generating a message in MIME format
1. Click Designer.
2. Click Add root to open the drop dialog.
3. In the tree, select 'XML\Element'.
4. In the Name field, type 'Invoice'.
    * Invoice  
5. Click OK.
6. Click Add to open the drop dialog.
7. In the tree, select 'XML\Attribute'.
8. In the Name field, type 'SalesOrder'.
    * SalesOrder  
9. Click OK.
10. Click Add Attribute.
11. In the Name field, type 'InvoiceNumber'.
    * InvoiceNumber  
12. Click OK.
13. Click Add Attribute.
14. In the Name field, type 'InvoiceAmount'.
    * InvoiceAmount  
15. Click OK.
16. Click Add to open the drop dialog.
17. In the tree, select 'XML\Element'.
18. In the Name field, type 'EnclosedDocs'.
    * EnclosedDocs  
19. Click OK.
20. In the tree, select 'Invoice\EnclosedDocs'.
21. Click Add Element.
22. In the Name field, type 'Document'.
    * Document  
23. Click OK.
24. In the tree, select 'Invoice\EnclosedDocs\Document'.
25. Click Add to open the drop dialog.
26. In the tree, select 'XML\Attribute'.
27. In the Name field, type 'FileName'.
    * FileName  
28. Click OK.
29. Click Add to open the drop dialog.
30. In the tree, select 'XML\Element'.
31. In the Name field, type 'FileContent'.
    * FileContent  
32. Click OK.
33. In the tree, select 'Invoice\EnclosedDocs\Document\FileContent'.
34. Click Add to open the drop dialog.
35. In the tree, select 'Text\Base64'.
36. Click OK.

## Map format elements to data model as data source
1. In the tree, select 'Invoice\SalesOrder'.
2. Click the Mapping tab.
3. In the tree, expand 'model'.
4. In the tree, select 'model\Sales order number(SalesId)'.
5. Click Bind.
6. In the tree, select 'Invoice\InvoiceNumber'.
7. In the tree, expand 'model\Base invoice(InvoiceBase)'.
8. In the tree, select 'model\Base invoice(InvoiceBase)\Invoice number(Id)'.
9. Click Bind.
10. In the tree, select 'Invoice\InvoiceAmount'.
11. In the tree, select 'model\Base invoice(InvoiceBase)\Invoice amount(Amount)'.
12. Click Bind.
13. In the tree, expand 'model\Invoice attachments'.
14. In the tree, select 'model\Invoice attachments\File content'.
15. In the tree, select 'Invoice\EnclosedDocs\Document\FileContent\Base64'.
16. Click Bind.
17. In the tree, select 'model\Invoice attachments\File name'.
18. In the tree, select 'Invoice\EnclosedDocs\Document\FileName'.
19. Click Bind.
20. In the tree, select 'model\Invoice attachments'.
21. In the tree, select 'Invoice\EnclosedDocs\Document'.
22. Click Bind.
23. Click Save.
24. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
