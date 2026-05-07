---
title: Design configurations to generate reports in Office format that have embedded images
description: This article describes about how to design configurations that generate electronic documents in Excel and Word formats that contain embedded images.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Design configurations to generate reports in Office format that have embedded images

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, first complete the procedure, "ER Create a configuration provider and mark it as active."
This procedure explains how to design Electronic reporting (ER) configurations to generate a Microsoft Excel or Word document that contains embedded images. In this procedure, you create the required ER configurations for the sample company, Litware, Inc. You can complete these steps by using the USMF dataset.
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

 1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.  
 1. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure, "Create a configuration provider and mark it as active."
 1. Select **Reporting configurations**.    

## Add a new ER model configuration  

 1. Instead of creating a new model, load the ER model configuration file (`Model for cheques.xml`) that you saved earlier. This file contains the sample data model for payment cheques and the mapping of the data model to the data components of the Dynamics 365 for Operations application.
 1. On the **Versions** FastTab, click **Exchange**.
 1. Click **Load from XML file**.  
 1. Click **Browse**, and then select `Model for cheques.xml`.
 1. Click **OK**.  
 1. Use the loaded model as a data source of information to generate documents that contain images in Excel and Word.    

## Add a new ER format configuration  

 1. Instead of creating a new format, load the ER format configuration file (`Cheques printing format.xml`) that you saved earlier. This file contains the sample layout of the format to print cheques using the pre-printed form and the mapping of this format to the **Model for cheques** data model.
 1. Click **Exchange**.  
 1. Click **Load from XML file**.  
 1. Click **Browse** and select the `Cheques printing format.xml` file.
 1. Click **OK**.  
 1. In the tree, expand **Model for cheques**.  
 1. In the tree, select **Model for cheques\Cheques printing format**.  
 1. Use the loaded format to generate documents that contain images in Excel and Word.

## Configure ER user parameters  

 1. On the Action Pane, click **Configurations**.  
 1. Click **User parameters**.  
 1. Select **Yes** in the **Run settings** field.  
  Turn on the **Run draft** flag to start the draft version of the selected format instead of the completed one.  
 1. Click **OK**.    

## Configure Cash and bank management parameters  

 1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.  
 1. Use the Quick Filter to filter on the **Bank account** field with a value of `USMF OPER`.  
 1. On the Action Pane, select **Set up**.  
 1. Select **Check**.  
 1. Expand the **Setup** section.  
 1. Select **Edit**.  
 1. Select **Yes** in the **Company logo** field.  
 1. Select **Company logo**.  
 1. Select **Change**.  
 1. Select **Browse** and select the file that you downloaded earlier, **Company logo.png**.
 1. Select **Save**.  
 1. Close the page.  
 1. Expand the **Signature** section.  
 1. Select **Yes** in the **Print first signature** field.  
 1. Select **Change**.  
 1. Select **Browse** and select the file that you downloaded earlier, **Signature image.png**.
 1. Expand the **Copies** section.  
 1. In the **Watermark** field, select an option.  
 1. Select **Yes** in the **Generic electronic Export format** field.  
 1. Select **Cheques printing form** configuration.  
 1. Now the selected ER format is used for printing cheques.  
 1. Select **Attach**.  
 1. Select **New**.  
 1. Select **File**.  
 1. Select **Browse** and select the file that you downloaded earlier, **Signature image 2.png**.
 1. Close the page.  
 1. Close the page.  
 1. Close the page.  
 1. Go to **Cash and bank management** > **Setup** > **Cash and bank management parameters**.  
 1. Select **Yes** in the **Allow prenote creation on inactive bank accounts:** field.  
 1. Select **Save**.  
 1. Close the page.    

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
