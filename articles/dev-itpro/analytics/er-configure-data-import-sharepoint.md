---
# required metadata

title: Configure data import from SharePoint 
description: This topic explains how to import data from SharePoint.
author: NickSelin
manager: AnnBe
ms.date: 05/11/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 220314
ms.assetid: 2685df16-5ec8-4fd7-9495-c0f653e82567
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2018-04-01
ms.dyn365.ops.version: Release 8.0

---
# Configure data import from SharePoint

[!include[banner](../includes/banner.md)]

When you import data using the Electronic reporting (ER) framework, you must configure an ER format that supports the import and then run a model mapping destination that uses the format as a data source. When you want to import data from Microsoft SharePoint, you must manually locate the file for import. You can use ER configurations to set up data import from files that are stored in SharePoint folders. Using vendor transactions as business data, this topic explains how to complete the import from SharePoint to the application.

## Prerequisites
To complete the examples in this topic, you must have the following:

- Access to Microsoft Dynamics 365 for Finance and Operations for one of the following roles:
  - Electronic reporting developer
  - Electronic reporting functional consultant
  - System administrator
- Access to the SharePoint Server that is configured for use with Dynamics 365 for Finance and Operations

## Create an ER configuration
Play the task guides, **ER Use formats to import data from an external Excel file** (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process), which walk you through how to design and use ER configurations to interactively import vendor transactions from the external files in Microsoft Excel. For more information see [Parse incoming documents in Microsoft Excel](parse-incoming-documents-excel.md). 
When you have finished playing the guides, you will have the prerequisites required for this example. The prerequisists include the ER model and format configurations with 1099 Payments model and format. These are used to import vendor transactions from Excel.

> [!NOTE]
> The format for importing vendor transactions is the model mapping default. This means that if you run a model mapping of the 1099 Payments model wtih the**To destination** type, it will run this format to import data from external files and then use the data to update application tables.

## Configure Document management parameters
1.	On the **Document management parameters** page, configure access to the SharePoint Server that will be used by the company that you're signed into. In this example, USMF.
2.	Test the connection to the SharePoint Server to make sure that you've been granted access.
3.	Open the configured SharePoint site and create the following new folders where the incoming files can be stored.

  - Files import source (main)
  - Files import source (alternative)
  
4.	In Finance and Operations, on the **Document type** page, create the following new document types that will be used to access the SharePoint folders that you just created. 

  - SP Main document type
  - SP Alternative document type

5. In the **Group** field, enter **File**, and in the **Location** field, enter **SharePoint**. Next, enter the address of the SharePoint folder. 

  - Files import source (main) for the SP Main document type
  - Files import source (alternative) for the SP Alternative document type

## Configure ER sources for your ER format
1.	On the **Electronic reporting source** page, configure the source files for data import by using the configured ER format.
2. Define the file name’s mask to filter data import to only files with the extension, XLSX. The file name's mask is option and is used only when it has been defined. You can only define one mask for one ER format.
3. Select both SharePoint folders that you created.

The ER *source* is defined for each application company individually. Unlike ER *configurations* which can be shared across companies. When you delete an ER source setting for an ER format, all connected file states will be also deleted by default.

## Review files states for your ER format
1.	Click **File states for the sources** to review the content of the configured file sources for the current ER format.
2.	In the **Files** section, review the list of files:

  - File sources that are applicable based on the file name mask if it is defined and ready for data import. The Sources log for the import format section is blank for these files.
  - In the **Sources** log, in the **Import** section, you can review the history of already imported files.

You can also go to **Organization administration** > **Electronic reporting** > **File states for the sources** to access the page. In this case the page will provide information about file sources for all ER formats for which file sources have been configured in the currently logged company.

## Import data from SharePoint folder located Excel files
1.	In SharePoint, upload the Excel file with vendor transactions to the SharePoint folder, **Files import source (main)** that you created earlier in this topic.
2.	On the **File states for the sources** form, click **Refresh** to update the page. 

## Import data from SharePoint files
1.	Open the ER configurations tree and expand the list of components of the ER model that is used by your ER format for data import. 2. Click on the model mapping name link.
3.	Click **Run** to execute the selected model mapping. Because you configured file sources for the ER format, you can change the **File source option** if needed. If you keep this option, the .xslx files will be imported from the configured sources, which in this example are the SharePoint folders.
In this example, we're only importing one file. However, when there are multiple files, they will be imported in the order in which they were added to the SharePoint folder.

Model mapping can be executed unattended in batch mode. In this case, any time a batch runs this ER format, a single file will be imported from the configured file sources.
4. Use the following code to implement this batch run:

        ERObjectsFactory::createMappingDestinationRunByImportFormatMappingId().run()

When a file is successfully imported from the SharePoint folder, it will be deleted from this folder.
5.	Enter the Voucher ID, for example V-00001, and then click **OK**.
6.	Open the **File states for the sources** form and click **Refresh** to update the page.
7.	In the **Files** section, review the list of files. The **Sources log** for the import format section provides the history of the Excel file import. As this file was successfully imported, it is marked as **Deleted** in the SharePoint folder.
8.	Review the SharePoint folder, **Files import source (main)**. The successfully imported Excel files has been deleted from this folder.
9.	Click **Accounts payable** > **Periodic tasks** > **Tax 1099** > **Vendor settlement for 1099s** and in the **From date** and **To date** fields, enter the appropriate values. Then click **Manual 1099 transactions**.
The vendors’ transactions of the voucher **V-00001** have been imported from the SharePoint Excel file to the application.

## Prepare Excel file for import
1. Using the Excel file that you previously used, in row three, add information for a vendor that doesn't exist in your application.
2. Upload the updated Excel file with the vendors transactions to the SharePoint folder, **Files import source (main)**.
3. In Dynamics 365 for Finance and Operations, open the ER configurations tree and expand the list of components of the ER model that is used by your ER format for data import. 
4. Click **Model mapping name** to update the model mapping to consider the incorrect vendor code an error in the data import process.
5. Click Designer, select the Validations tab, and change the post-validation action for the validation rule that was configured to evaluate whether the importing vendor account exists in the application.
6. Update the value to **Stop execution**, save your changes, and close the form.
7. Save changes and close the ER model mapping designer.
8.	Click **Run** to execute the modified ER model mapping.
9.	Enter the voucher ID, for example V-00002, and click **OK**.
10.	Open the **File states for the sources** form, click Refresh and in the **Files** section, review the list of files.
The **Sources log** for the **Import format** section tells you that the import process failed and the file is still in the SharePoint folder. If you fix this file on SharePoint and change the status of this file on the **Sources log** for the **Import format** form from **Failed** to **Ready**, this file can be imported again.
11.	Review the SharePoint folder, **Files import source (main)**. Notice that the Excel file that was not imported is still in this folder.
12. Click **Accounts payable** > **Periodic tasks** > **Tax 1099** > **Vendor settlement for 1099s**, enter the appropriate values in the **From date** and **To date** fields, and then click **Manual 1099 transactions**.
9.	Define appropriate values in From date and To date fields, and click Manual 1099 transactions.
Only transactions for voucher **V-00001** are available. There are no transactions of the voucher **V-00002** available even the error has been discovered for the last imported transaction in the Excel file.
