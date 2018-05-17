---
# required metadata

title: Configure data import from SharePoint 
description: This topic explains how to import data from Microsoft SharePoint.
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

To import data by using the Electronic reporting (ER) framework, you must configure an ER format that supports the import and then run a model mapping destination that uses that format as a data source. To import data from Microsoft SharePoint, you must manually locate the file that you want to import. You can use ER configurations to set up data import from files that are stored in SharePoint folders. This topic explains how to complete the import from SharePoint to the application. The examples use vendor transactions as business data.

## Prerequisites
To complete the examples in this topic, you must have the following access:

- Access to Microsoft Dynamics 365 for Finance and Operations for one of the following roles:

    - Electronic reporting developer
    - Electronic reporting functional consultant
    - System administrator

- Access to the instance of Microsoft SharePoint Server that is configured for use with Finance and Operations

## Create an ER configuration
Play the **ER Use formats to import data from an external Excel file** task guides, which are part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process. These task guides walk you through the process of designing and using ER configurations to interactively import vendor transactions from external files in Microsoft Excel format. For more information, see [Parse incoming documents in Microsoft Excel](parse-incoming-documents-excel.md).

When you've finished playing the task guides, you will have the prerequisites for this topic. Those prerequisites include the ER model and format configurations that use the 1099 Payments model and format. These prerequisites are used to import vendor transactions from an Excel file.

> [!NOTE]
> The format for importing vendor transactions is the model mapping default. Therefore, if you run a model mapping of the 1099 Payments model, and that model mapping is of the **To destination** type, the model mapping runs this format to import data from external files. It then uses that data to update application tables.

## Configure Document management parameters
1. On the **Document management parameters** page, configure access to the SharePoint Server instance that will be used by the company that you're currently signed in to. In this example, the company is USMF.
2. Test the connection to the SharePoint Server instance to make sure that you've been granted access.
3. Open the configured SharePoint site, and create the following folders where the incoming files can be stored:

    - Files import source (main)
    - Files import source (alternative)

4. In Finance and Operations, on the **Document type** page, create the following document types that will be used to access the SharePoint folders that you just created:

    - SP Main
    - SP Alternative

5. In the **Group** field, enter **File**. In the **Location** field, enter **SharePoint**. Then enter the address of the SharePoint folder:

    - **For the SP Main document type:** Files import source (main)
    - **For the SP Alternative document type:** Files import source (alternative)

## Configure ER sources for the ER format
1. On the **Electronic reporting source** page, configure the source files for data import by using the configured ER format.
2. Define a file name mask, so that only files that have the .xlsx extension are imported. The file name mask is optional and is used only when it has been defined. You can define only one mask for each ER format.
3. Select both SharePoint folders that you created earlier.

The ER *source* is defined for each application company individually. By contrast, ER *configurations* can be shared across companies. By default, when you delete an ER source setting for an ER format, all connected file states are also deleted.

## Review the files states for the ER format
1. On the **Electronic reporting source** page, select **File states for the sources** to review the content of the configured file sources for the current ER format.
2. In the **Files** section, review the list of file sources that are applicable, based on the file name mask (if a file name mask is defined), and that are ready for data import. For these files, the **Sources log for the import format** section is blank.

    In the **Sources log for the import format** section, you can review the history of files that have already been imported.

You can also open the **File states for the sources** page by selecting **Organization administration** \> **Electronic reporting** \> **File states for the sources**. In this case, the page provides information about file sources for all ER formats that file sources have been configured for in the company that you're currently signed in to.

## Import data from Excel files that are in a SharePoint folder
1. In SharePoint, upload the Excel file that contains vendor transactions to the **Files import source (main)** SharePoint folder that you created earlier.
2. In Finance and Operations, on the **File states for the sources** page, select **Refresh** to refresh the page.

## Import data from SharePoint files
1. Open the ER configurations tree, and expand the list of components of the ER model that your ER format uses for data import.
2. Select the link for the name of the model mapping.
3. Select **Run** to run the selected model mapping. Because you configured file sources for the ER format, you can change the setting of the **File source** option as you require. If you keep the setting of this option, the .xslx files are imported from the configured sources (the SharePoint folders, in this example).

    In this example, you're importing only one file. However, if there are multiple files, they are imported in the order in which they were added to the SharePoint folder.

4. The model mapping can run unattended in batch mode. In this case, every time that a batch runs this ER format, a single file is imported from the configured file sources. Use the following code to implement this batch run.

    ```
    ERObjectsFactory::createMappingDestinationRunByImportFormatMappingId().run()
    ```

    When a file is successfully imported from the SharePoint folder, it's deleted from that folder.

5. Enter the voucher ID, such as **V-00001**, and then select **OK**.
6. On the **File states for the sources** page, select **Refresh** to refresh the page.
7. In the **Files** section, review the list of files. The **Sources log for the import format** section provides the history of the Excel file import. Because this file was successfully imported, it's marked as **Deleted** in the SharePoint folder.
8. Review the **Files import source (main)** SharePoint folder. The Excel files that were successfully imported have been deleted from this folder.
9. In Finance and Operations, select **Accounts payable** \> **Periodic tasks** \> **Tax 1099** \> **Vendor settlement for 1099s**.
10. In the **From date** and **To date** fields, enter appropriate values. Then select **Manual 1099 transactions**.

The vendor transactions for voucher **V-00001** are imported from the SharePoint Excel file to the application.

## Prepare an Excel file for import
1. Open the Excel file that you previously used. In row 3, add information for a vendor that doesn't exist in the application.
2. Upload the updated Excel file that contains vendors transactions to the **Files import source (main)** SharePoint folder.
3. In Finance and Operations, open the ER configurations tree, and expand the list of components of the ER model that your ER format uses for data import.
4. Select **Model mapping name** to update the model mapping so that the incorrect vendor code is considered an error during the data import process.
5. Select **Designer**.
6. On the **Validations** tab, you must change the post-validation action for the validation rule that was configured to evaluate whether the vendor account that is imported exists in the application. Update the value of the **Post-validation action** field to **Stop execution**, save your changes, and close the page.
7. Save your changes, and close the ER model mapping designer.
8. Select **Run** to run the modified ER model mapping.
9. Enter the voucher ID, such as **V-00002**, and then select **OK**.
10. On the **File states for the sources** page, select **Refresh**, and then, in the **Files** section, review the list of files.

    The **Sources log for the import format** section indicates that the import process failed and that the file is still in the SharePoint folder. If you fix this file on SharePoint and then change the status of the file from **Failed** to **Ready** in the **Sources log for the import format** section, you can import the file again.

11. Review the **Files import source (main)** SharePoint folder. Notice that the Excel file that wasn't imported is still in this folder.
12. In Finance and Operations, select **Accounts payable** \> **Periodic tasks** \> **Tax 1099** \> **Vendor settlement for 1099s**, enter appropriate values in the **From date** and **To date** fields, and then select **Manual 1099 transactions**.

Only transactions for voucher V-00001 are available. No transactions for voucher V-00002 are available even the error for the last imported transaction has been found in the Excel file.
