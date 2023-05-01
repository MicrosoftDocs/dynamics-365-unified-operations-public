---
title: ER Use Document Management files in format outputs (Part 5 - Modify and run format)
description: This article describes how to configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. (Part 5)
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
ms.search.form: ERSolutionTable, EROperationDesigner, ERComponentTypeDropDialog, ERExpressionDesignerFormula, SysQueryForm
---
# ER Use Document Management files in format outputs (Part 5 - Modify and run format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. These steps can be performed in the DEMF company.

To complete these steps, you must first complete the steps in the "ER Use Document Management files in format outputs (Part 4: Run format)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Modify the format to populate attachments into generating messages in binary format
1. Go to Organization administration > Electronic reporting > Configurations.
2. In the tree, expand 'Customer invoice model'.
3. In the tree, expand 'Customer invoice model\Customer invoice model (custom)'.
4. In the tree, select 'Customer invoice model\Customer invoice model (custom)\Electronic invoice sample message'.
5. Click Designer.
    * You will populate the invoice message in the generating output as an XML file using UNICODE encoding.  
6. Click Add root to open the drop dialog.
7. In the tree, select 'Common\File'.
8. In the Name field, type 'Xml message'.
    * Xml message  
9. In the Encoding field, type 'UTF-8'.
    * UTF-8  
10. Click OK.
    * Configure the generating output as a zipped file.  
11. Click Add root to open the drop dialog.
12. In the tree, select 'Common\Folder'.
13. In the Name field, type 'Zip output'.
    * Zip output  
14. Click OK.
15. In the tree, select 'Zip output'.
    * Add attachments to the generating zipped file as files with original names and extensions.  
16. Click Add to open the drop dialog.
17. In the tree, select 'Common\File'.
18. In the Name field, type 'Attached file'.
    * Attached file  
19. Click OK.
20. In the tree, select 'Zip output\Attached file'.
21. Click Add to open the drop dialog.
22. In the tree, select 'Text\Base64'.
23. Click OK.

## Map new format elements to data model
1. Click the Mapping tab.
2. In the tree, expand 'model'.
3. In the tree, expand 'model\Invoice attachments'.
4. In the tree, select 'Zip output\Attached file\Base64'.
5. In the tree, select 'model\Invoice attachments\File content'.
6. Click Bind.
7. In the tree, select 'Zip output\Attached file'.
8. Click Edit filename.
9. In the tree, expand 'model'.
10. In the tree, expand 'model\Invoice attachments'.
11. In the tree, select 'model\Invoice attachments\File name'.
12. Click Add data source.
13. Click Save.
14. Close the page.
15. In the tree, select 'model\Invoice attachments'.
16. Click Bind.
17. Click Save.
18. Close the page.

## Run the designed report for the selected invoice
1. Click Run.
2. Expand the Records to include () section.
3. Click Filter.
4. Select the row of the Customer invoice journal and the Sales order field.
5. In the Criteria field, In the criteria "Sales order" field, type the order number 000148.
    * 000148  
6. Click OK.
7. Click OK.
    * Review the generated output. Note,that in addition to the invoice message in XML format, a single file has been created for each attachment. The attachment files are populated with the zipped output in binary format.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
