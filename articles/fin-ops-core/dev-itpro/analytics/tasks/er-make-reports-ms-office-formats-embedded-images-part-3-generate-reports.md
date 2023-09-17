---
title: Generate reports in Office format that have embedded images
description: This article describes how to design Electronic reporting (ER) configurations to generate electronic documents in Excel and Word containing embedded images.
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
# Generate reports in Office format that have embedded images

[!include [banner](../../includes/banner.md)]

The following steps explain how a user playing either 'System administrator' or 'Electronic reporting developer' role can design Electronic reporting (ER) configurations to generate electronic documents in MS office formats (Excel and Word) containing embedded images.

In this example, you will use created ER configurations for sample company, 'Litware, Inc.'.  To complete these steps, you must first complete the steps in the "ER Make reports in MS Office formats with embedded images (Part 2: Review configurations)" task guide. These steps can be performed in 'USMF' company.


## Run format with initial model mapping
1. Go to Cash and bank management > Bank accounts > Bank accounts.
2. Use the Quick Filter to filter on the Bank account field with a value of 'USMF OPER'.
3. On the Action Pane, click Set up.
4. Click Check.
5. Click Print test.
    * Run the format for testing purposes.  
6. Select Yes in the Negotiable check format field.
7. Click OK.
    * Review the created output. The company logo is presented in the report as well as the authorized person's signature. The signature image is taken from the field of the 'Container' data type of the cheque layout record that is associated with the selected bank account.  
8. Expand the Copies section.
9. Click Edit.
10. In the Watermark field, enter 'Print watermark as Void'.
    * Change the watermark layout setting to show the watermark text in generating document in an Excel shape element.  
11. Click Print test.
12. Click OK.
    * Review the created output. The watermark is shown in the created report in accordance to the selection option.  
13. Close the page.
14. On the Action Pane, click Manage payments.
15. Click Checks.
16. Click Show filters.
17. Apply the following filters: Enter a filter value of "381","385","389" on the "Check number" field using the "is one of" filter operator.
18. In the list, mark all rows.
19. Click Print check copy.
    * Run the format to reprint the selected cheques.  
    * Review the created output. The selected cheques have been reprinted. The company logo and labels are not printed out since they are presented on the pre-printed form.  

## Modify the mapping of the imported data model
1. Close the page.
2. Close the page.
3. Go to Organization administration > Electronic reporting > Configurations.
4. In the tree, select 'Model for cheques'.
5. Click Designer.
6. Click Map model to datasource.
7. Click Designer.
    * We will change the binding of the data model's signature item to get the signature image from the file that has been attached to the cheque layout record that is associated with the selected bank account.  
8. Turn off Show details.
9. In the tree, expand 'layout'.
10. In the tree, expand 'layout\signature'.
11. In the tree, select 'layout\signature\image = chequesaccount.'<Relations'.BankChequeLayout.Signature1Bmp'.
12. In the tree, expand 'chequesaccount'.
13. In the tree, expand 'chequesaccount\<Relations'.
14. In the tree, expand 'chequesaccount\<Relations\BankChequeLayout'.
15. In the tree, expand 'chequesaccount\<Relations\BankChequeLayout\<Relations'.
16. In the tree, expand 'chequesaccount\<Relations\BankChequeLayout\<Relations\<Documents'.
17. In the tree, select 'chequesaccount\<Relations\BankChequeLayout\<Relations\<Documents\getFileContentAsContainer()'.
18. Click Bind.
19. Click Save.
20. Close the page.
21. Close the page.
22. Close the page.
23. Close the page.

## Run format using the adjusted model mapping
1. Go to Cash and bank management > Bank accounts > Bank accounts.
2. Use the Quick Filter to find records. For example, filter on the Bank account field with a value of 'USMF OPER'.
3. On the Action Pane, click Set up.
4. Click Check.
5. Click Print test.
6. Click OK.
    * Review the created output. The image from the Document Management attachment is presented as the signature of an authorized person.  

## Use MS Word document as a template in the imported format
1. Close the page.
2. Close the page.
3. Go to Organization administration > Electronic reporting > Configurations.
4. In the tree, expand 'Model for cheques'.
5. In the tree, select 'Model for cheques\Cheques printing format'.
6. Click Designer.
7. Click Attachments.
8. Click Delete.
9. Click Yes.
10. Click New.
11. Click File.
    * Click Browse and select the downloaded in advance 'Cheque template Word.docx' file.  
12. Close the page.
13. In the Template field, enter or select a value.
14. Click Save.
15. Close the page.
16. Click Edit.
17. Select Yes in the Run Draft field.
18. Close the page.
19. Go to Cash and bank management > Bank accounts > Bank accounts.
20. Use the Quick Filter to filter on the Bank account field with a value of 'USMF OPER'.
21. Click Check.
22. Click Print test.
23. Click OK.
    * Review the created output. The output has been generated as a Word document with embedded images presenting the company logo, the signature of an authorized person and the selected text of the watermark.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
