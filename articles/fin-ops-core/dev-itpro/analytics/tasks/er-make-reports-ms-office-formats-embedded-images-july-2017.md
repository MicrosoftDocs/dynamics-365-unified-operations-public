---
title: Design configurations to generate reports in Office format that have embedded images
description: This article describes about how to design configurations that generate electronic documents in Excel and Word formats that contain embedded images.
author: kfend
ms.date: 04/23/2021
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
# Design configurations to generate reports in Office format that have embedded images

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, first complete the procedure, "ER Create a configuration provider and mark it as active." 
This procedure explains how to design Electronic reporting (ER) configurations to generate a Microsoft Excel or Word document that contains embedded images. In this procedure, you will create the required ER configurations for the sample company, Litware, Inc. These steps can be completed using the USMF dataset. 
This procedure is created for users with the assigned role of system administrator or electronic reporting developer. Before you begin, download and save the following files: 

| Description                                          | File name                   |
|------------------------------------------------------|-----------------------------|
| ER data model configuration                          | [Model for cheques.xml](https://download.microsoft.com/download/6/e/a/6ea166fd-1382-4fdb-8dcb-0f13379f9c8e/Modelforcheques.xml)       |
| ER format configuration                              | [Cheques printing format.xml](https://download.microsoft.com/download/1/7/c/17c301e3-c4ee-4886-ae75-440fcc002c8c/Chequesprintingformat.xml) |
| Company logo image                                   | [Company logo.png](https://download.microsoft.com/download/8/2/e/82e6bd81-caac-4e9a-bfce-1392ce7c8616/Companylogo.png)            |
| Signature image                                      | [Signature image.png](https://download.microsoft.com/download/5/0/9/509151b3-06fc-4870-9408-7c9a43b72771/Signatureimage.png)         |
| Alternative signature image                          | [Signature image 2.png](https://download.microsoft.com/download/3/0/0/30045bf1-0ff6-4215-9162-b77c2f5dcc7c/Signatureimage2.png)       |
| Microsoft Word template for printing payment checks  | [Cheque template Word.docx](https://download.microsoft.com/download/4/4/d/44d9d255-9ad1-42fe-87db-23f319fd8e89/ChequetemplateWord.docx)   |

## Verify prerequisites  
 1. Go to Organization administration > Workspaces > Electronic reporting.  
 2. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as Active. If you don't see this configuration provider, complete the steps in the procedure, "Create a configuration provider and mark it as active."   
 3. Click Reporting configurations.  
 
## Add a new ER model configuration  
 1. Instead of creating a new model, you can load the ER model configuration file (Model for cheques.xml) that you saved earlier. This file contains the sample data model for payment cheques and the mapping of the data model to the data components of the Dynamics 365 for Operations application.   
 2. On the Versions FastTab, click Exchange.   
 3. Click Load from XML file.  
 4. Click Browse, and then select Model for cheques.xml.   
 5. Click OK.  
 6. The loaded model will be used as a data source of information to generate documents that contain images in Excel and Word.  

## Add a new ER format configuration  
 1. Instead of creating a new format, you can load the ER format configuration file (Cheques printing format.xml) that you saved earlier. This file contains the sample layout of the format to print cheques using the pre-printed form and the mapping of this format to the 'Model for cheques' data model.   
 2. Click Exchange.  
 3. Click Load from XML file.  
 4. Click Browse and select the Cheques printing format.xml file.   
 5. Click OK.  
 6. In the tree, expand 'Model for cheques'.  
 7. In the tree, select 'Model for cheques\Cheques printing format'.  
 8. The loaded format will be used to generate documents that contain images in Excel and Word.   

## Configure ER user parameters  
 1. On the Action Pane, click Configurations.  
 2. Click User parameters.  
 3. Select Yes in the Run settings field.  
  Turn on the 'Run draft' flag to start the draft version of the selected format instead of the completed one.  
 4. Click OK.  

## Configure Cash & bank management parameters  
 1. Go to Cash and bank management > Bank accounts > Bank accounts.  
 2. Use the Quick Filter to filter on the Bank account field with a value of 'USMF OPER'.  
 3. On the Action Pane, click Set up.  
 4. Click Check.  
 5. Expand the Setup section.  
 6. Click Edit.  
 7. Select Yes in the Company logo field.  
 8. Click Company logo.  
 9. Click Change.  
 10. Click Browse and select the file that you downloaded earlier, Company logo.png.   
 11. Click Save.  
 12. Close the page.  
 13. Expand the Signature section.  
 14. Select Yes in the Print first signature field.  
 15. Click Change.  
 16. Click Browse and select the file that you downloaded earlier, Signature image.png.   
 17. Expand the Copies section.  
 18. In the Watermark field, select an option.  
 19. Select Yes in the Generic electronic Export format field.  
 20. Select 'Cheques printing form' configuration.  
 21. Now the selected ER format will be used for printing cheques.  
 22. Click Attach.  
 23. Click New.  
 24. Click File.  
 25. Click Browse and select the file that you downloaded earlier, Signature image 2.png.   
 26. Close the page.  
 27. Close the page.  
 28. Close the page.  
 29. Go to Cash and bank management > Setup > Cash and bank management parameters.  
 30. Select Yes in the Allow prenote creation on inactive bank accounts: field.  
 31. Click Save.  
 32. Close the page.  


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
