---
title: Generate reports in Office format that have embedded images
description: This article describes how to design Electronic reporting (ER) configurations to generate electronic documents in Excel and Word containing embedded images.
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

# Generate reports in Office format that have embedded images

[!include [banner](../../includes/banner.md)]

The following steps explain how a user playing either 'System administrator' or 'Electronic reporting developer' role can design Electronic reporting (ER) configurations to generate electronic documents in MS office formats (Excel and Word) containing embedded images.

In this example, you use the created ER configurations for sample company, 'Litware, Inc.'. To complete these steps, you must first complete the steps in the "ER Make reports in MS Office formats with embedded images (Part 2: Review configurations)" task guide. You can perform these steps in 'USMF' company.


## Run format with initial model mapping

1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.
1. Use the Quick Filter to filter on the Bank account field with a value of **USMF OPER**.
1. On the Action Pane, select **Set up**.
1. Select **Check**.
1. Select **Print test**.
    * Run the format for testing purposes.  
1. Select **Yes** in the Negotiable check format field.
1. Select **OK**.
    * Review the created output. The company logo is presented in the report as well as the authorized person's signature. The signature image is taken from the field of the 'Container' data type of the cheque layout record that is associated with the selected bank account.  
1. Expand the Copies section.
1. Select **Edit**.
1. In the Watermark field, enter **Print watermark as Void**.
    * Change the watermark layout setting to show the watermark text in generating document in an Excel shape element.  
1. Select **Print test**.
1. Select **OK**.
    * Review the created output. The watermark is shown in the created report in accordance to the selection option.  
1. Close the page.
1. On the Action Pane, select **Manage payments**.
1. Select **Checks**.
1. Select **Show filters**.
1. Apply the following filters: Enter a filter value of "381","385","389" on the "Check number" field using the "is one of" filter operator.
1. In the list, mark all rows.
1. Select **Print check copy**.
    * Run the format to reprint the selected cheques.  
    * Review the created output. The selected cheques are reprinted. The company logo and labels don't print out since they appear on the pre-printed form.  

## Modify the mapping of the imported data model

1. Close the page.
1. Close the page.
1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, select *Model for cheques*.
1. Select **Designer**.
1. Select **Map model to datasource**.
1. Select **Designer**.
        * Change the binding of the data model's signature item to get the signature image from the file that's attached to the cheque layout record associated with the selected bank account.    
1. Turn off **Show details**.
1. In the tree, expand *layout*.
1. In the tree, expand *layout\signature*.
1. In the tree, select *layout\signature\image = chequesaccount.'<Relations'.BankChequeLayout.Signature1Bmp'*.
1. In the tree, expand *chequesaccount*.
1. In the tree, expand *chequesaccount.'<Relations'*.
1. In the tree, expand *chequesaccount.'<Relations'.BankChequeLayout'*.
1. In the tree, expand *chequesaccount.'<Relations'.BankChequeLayout.'<Relations'*.
1. In the tree, expand *chequesaccount.'<Relations'.BankChequeLayout.'<Relations'.<Documents'*.
1. In the tree, select *chequesaccount.'<Relations'.BankChequeLayout.'<Relations'.<Documents.getFileContentAsContainer()*.
1. Select **Bind**.
1. Select **Save**.
1. Close the page.
1. Close the page.
1. Close the page.
1. Close the page.

## Run format using the adjusted model mapping

1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.
1. Use the Quick Filter to find records. For example, filter on the **Bank account** field with a value of `USMF OPER`.
1. On the Action Pane, select **Set up**.
1. Select **Check**.
1. Select **Print test**.
1. Select **OK**.
    * Review the created output. The image from the Document Management attachment is presented as the signature of an authorized person.  

## Use MS Word document as a template in the imported format

1. Close the page.
1. Close the page.
1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand *Model for cheques*.
1. In the tree, select *Model for cheques\Cheques printing format*.
1. Select **Designer**.
1. Select **Attachments**.
1. Select **Delete**.
1. Select **Yes**.
1. Select **New**.
1. Select **File**.
    * Select **Browse** and select the downloaded in advance *Cheque template Word.docx* file.  
1. Close the page.
1. In the **Template** field, enter or select a value.
1. Select **Save**.
1. Close the page.
1. Select **Edit**.
1. Select **Yes** in the **Run Draft** field.
1. Close the page.
1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.
1. Use the **Quick Filter** to filter on the **Bank account** field with a value of *USMF OPER*.
1. Select **Check**.
1. Select **Print test**.
1. Select **OK**.
    * Review the created output. The output is generated as a Word document with embedded images presenting the company logo, the signature of an authorized person, and the selected text of the watermark.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
