---
title: Review configurations to generate reports in Office format that have embedded images
description: This article describes how to design reporting configurations to generate electronic documents that contain embedded images. (Part 1 - Set up parameters).
author: kfend
ms.date: 02/24/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Review configurations to generate reports in Office format that have embedded images

[!include [banner](../../includes/banner.md)]

To complete these steps, you must first complete the steps in the "ER Make reports in MS Office formats with embedded images (Part 1: Set up parameters)" task guide.

This procedure shows how to design Electronic reporting (ER) configurations to generate electronic documents that contain embedded images in Microsoft Excel and Microsoft Word. In this example, you review ER configurations for the sample company Litware, Inc. 

This procedure is intended for users who have the System administrator or Electronic reporting developer role assigned to them. You can complete the steps by using the USMF data set.


## Review the imported data model

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, select **Model for cheques**.
1. Select **Designer**.
        * This model represents payment cheques from the business standpoint and the mapping of this model to the application's data sources. Review this model by the ER Operations designer. The attributes of the model elements include structure, name, description, data type, and more.      
1. In the tree, expand **root**.
1. In the tree, select **root\cheques**.
1. In the tree, expand **root\cheques**.
1. In the tree, expand **root\cheques\attributes**.
1. In the tree, expand **root\payer**.
1. In the tree, select **root\istestrun**.
1. In the tree, select **root\layout**.
    * The layout element of this model represents the details of the printing cheque form layout for the selected bank account. It also includes two nodes of the Container data type to store images.   
1. In the tree, expand **root\layout**.
1. In the tree, select **root\layout\company logo**.
1. In the tree, expand **root\layout\company logo**.
1. In the tree, select **root\layout\company logo\image**.
1. In the tree, select **root\layout\company logo\isprinted**.
1. In the tree, select **root\layout\signature**.
1. In the tree, expand **root\layout\signature**.
1. In the tree, select **root\layout\signature\image**.
1. In the tree, select **root\layout\signature\isprinted**.
        * Two image data model elements are bound to the fields of the tables that contain images of the company logo and the authorized person's signature in binary format.  
1. In the tree, expand **root\layout\watermark**.
1. Select **Map model to datasource**.
1. Select **Designer**.
1. In the tree, expand **chequesselected**.
1. In the tree, expand **layout**.
1. In the tree, expand **layout\company logo**.
1. In the tree, expand **layout\signature**.
1. In the tree, expand **layout\watermark**.
1. Toggle **Show details** on.
        * The cheques data model element is bound to the TmpChequePrintout table that, at runtime, contains records for cheques that the user selects for printing.      
1. Close the page.
1. Close the page.
1. Close the page.

## Review the imported format

1. In the tree, expand **Model for cheques**.
1. In the tree, select **Model for cheques\Cheques printing format**.
1. Select **Designer**.
1. Select **Attachments**.
1. Select **Open**.
    * Open the attached report's template in Excel.  
        * Review the attached report's Excel template that you use to print cheques. The template contains two cheques per page and is designed to print cheques to the preprinted form. Two blank images are embedded. These blank images are for the company logo and the signature of the person who is authorizing a payment. Verify that the images are named **CompLogo** and **SignatureImage**, respectively, in Excel.      
1. Close the page.
1. In the tree, expand **Report**.
1. In the tree, expand **Report\ChequeLines**.
1. In the tree, select **Report\ChequeLines\CompLogo**.
1. Toggle **Show details** on.
    * The **CompLogo** format's cell element represents the Excel item that populates the company logo image in the report. This format element is bound to the image data model element that, at runtime, contains a company logo image in binary format.   
1. Select the **Mapping** tab.
1. Select **Edit enabled**.
        * You can make the **CompLogo** format's cell element so that it's no longer enabled. In this case, the associated Excel image element hides a company logo in the generated report. If the enabled expression returns **TRUE** and the defined binding brings no image, the associated Excel image element shows an image saved in the Excel template.      
1. Close the page.
1. In the tree, expand **labels: Container**.
        * Some labels presented in the preprinted cheque form are included in the report when you create it for testing purposes. However, the preprinted form already includes these labels, so the labels don't print during real printing.    
1. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
