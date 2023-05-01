---
title: Review configurations to generate reports in Office format that have embedded images
description: This article describes how to design reporting configurations to generate electronic documents that contain embedded images. (Part 1 - Set up parameters).
author: kfend
ms.date: 06/13/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Review configurations to generate reports in Office format that have embedded images

[!include [banner](../../includes/banner.md)]

To complete these steps, you must first complete the steps in the "ER Make reports in MS Office formats with embedded images (Part 1: Set up parameters)" task guide.

This procedure shows how to design Electronic reporting (ER) configurations to generate electronic documents that contain embedded images in Microsoft Excel and Microsoft Word. In this example, you will review ER configurations for the sample company Litware, Inc. 

This procedure is intended for users who have the System administrator or Electronic reporting developer role assigned to them. The steps can be completed by using the USMF data set.


## Review the imported data model
1. Go to Organization administration > Electronic reporting > Configurations.
2. In the tree, select 'Model for cheques'.
3. Click Designer.
    * This model is designed to represent payment cheques from the business standpoint and the mapping of this model to the application's data sources. Review this model by the ER Operations designer. Note the attributes of the model elements that are presented: structure, name, description, data type, and so on.   
4. In the tree, expand 'root'.
5. In the tree, select 'root\cheques'.
6. In the tree, expand 'root\cheques'.
7. In the tree, expand 'root\cheques\attributes'.
8. In the tree, expand 'root\payer'.
9. In the tree, select 'root\istestrun'.
10. In the tree, select 'root\layout'.
    * The layout element of this model represents the details of the printing cheque form layout for the selected bank account. It also includes two nodes of the Container data type to store images.   
11. In the tree, expand 'root\layout'.
12. In the tree, select 'root\layout\company logo'.
13. In the tree, expand 'root\layout\company logo'.
14. In the tree, select 'root\layout\company logo\image'.
15. In the tree, select 'root\layout\company logo\isprinted'.
16. In the tree, select 'root\layout\signature'.
17. In the tree, expand 'root\layout\signature'.
18. In the tree, select 'root\layout\signature\image'.
19. In the tree, select 'root\layout\signature\isprinted'.
    * Note that two image data model elements are bound to the fields of the tables that contain images of the company logo and the authorized person's signature in binary format.  
20. In the tree, expand 'root\layout\watermark'.
21. Click Map model to datasource.
22. Click Designer.
23. In the tree, expand 'chequesselected'.
24. In the tree, expand 'layout'.
25. In the tree, expand 'layout\company logo'.
26. In the tree, expand 'layout\signature'.
27. In the tree, expand 'layout\watermark'.
28. Toggle 'Show details' on.
    * Note that the cheques data model element is bound to the TmpChequePrintout table that, at runtime, will contain records for cheques that the user has selected for printing.   
29. Close the page.
30. Close the page.
31. Close the page.

## Review the imported format
1. In the tree, expand 'Model for cheques'.
2. In the tree, select 'Model for cheques\Cheques printing format'.
3. Click Designer.
4. Click Attachments.
5. Click Open.
    * Open the attached report's template in Excel.  
    * Review the attached report's Excel template that will be used to print cheques. The template contains two cheques per page and is designed to print cheques to the preprinted form. Note that two blank images are embedded. These blank images are for the company logo and the signature of the person who is authorizing a payment. Verify that the images are named CompLogo and SignatureImage, respectively, in Excel.   
6. Close the page.
7. In the tree, expand 'Report'.
8. In the tree, expand 'Report\ChequeLines'.
9. In the tree, select 'Report\ChequeLines\CompLogo'.
10. Toggle 'Show details' on.
    * Note that the 'CompLogo' format's cell element represents the Excel item that is used to populate the company logo image in the report. This format element is bound to the image data model element that, at runtime, contains a company logo image in binary format.   
11. Click the Mapping tab.
12. Click Edit enabled.
    * Note that you can make the 'CompLogo' format's cell element so that it's no longer enabled. In this case, the associated Excel image element will hide a company logo in the generated report. If the enabled expression returns TRUE and the defined binding brings no image, the associated Excel image element will show an image that has been saved in the Excel template.   
13. Close the page.
14. In the tree, expand 'labels: Container'.
    * Some labels that are presented in the preprinted cheque form will be included in the report when it's created for testing purposes. However, those labels won't be printed during real printing, because the preprinted form already includes them.  
15. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
