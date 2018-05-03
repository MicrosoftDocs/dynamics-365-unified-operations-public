---
# required metadata

title: Configure data import from SharePoint 
description: 
author: NickSelin
manager: AnnBe
ms.date: 04/24/2018
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

When you need to import data using the Electronic reporting (ER) framework, you must configure an ER format that supports the import and then run the model mapping destination that uses the format as a data source. When you want to import data from Microsoft SharePoint, you must manually browse the local folders of SharePoint to locate the file for import.
You can use your ER configurations to set up data import from files that are stored in SharePoint folders. This topic explains how to complete the import by using vendor transactions as business data that must be imported to the application.

## Prerequisites
To complete the example in this topic, you must have the following access:

- Access to Finance and Operations for one of the following roles:
  - Electronic reporting developer
  - Electronic reporting functional consultant
  - System administrator
- Access to the SharePoint Server that is configured for use with Finance and Operations

## Create necessary ER configurations
1.	Play the set of ER Use formats to import data from an external Excel file task guides (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process), which walk you through the details of design and usage of ER configurations to interactively import vendors transactions to the application from the external files in Excel workbook format (find more details on this page). 
2.	When you finished playing these guides, you will have in your application all prerequisites that are necessary for this example:

    - ER model and format configurations including 1099 Payments model and format  for importing vendor transactions from Excel.
      > [!NOTE]
      > Note that the format for importing vendors’ transactions is marked as a default for model mapping. It means that if you would run a model mapping of the 1099 Payments model of the To destination type, it will run this format to import data from external files and use this data to update application tables.
  
    - Microsoft Excel file with vendors transactions to be imported to the application:


## Configure Document management parameters
1.	On the Document management parameters page, configure access to the SharePoint Server that will be used in the company that you're signed in to (the USMF company in this example).
2.	Test the connection to the SharePoint Server to make sure that you've been granted access.
3.	Open the configured SharePoint site. Create new folders where the incoming files can be stored:

    - Files import source (main);
    - Files import source (alternative).
4.	In Finance and Operations, on the Document types page, create new document types that will be used to access the SharePoint folders that you just created. Enter File in the Group field and SharePoint in the Location field, and then enter the address of the SharePoint folder:

    - Files import source (main) for the SP Main document type;
    - Files import source (alternative) for the SP Alternative document type.

## Configure ER sources for your ER format
1.	On the Electronic reporting source page, configure the sources of files for data import by using the configured ER format:
a.	Define the file name’s mask to filter for data import the only files with the extension XLSX;
b.	Select both SharePoint folders that have been previously created.

Note that the file name’s mask is optional and in use only when defined. Currently, you can define the only one mask for a single ER format.

Note that multiple SharePoint folders can be selected for a single ER format as sources of files for data import.

Note that the ER source is defined for each application company individually. Unlike ER configurations, ER format sources are company dependent.

Note that when you delete an ER source setting for an ER format, all connected file states (described in the article below) will be also deleted (by default).

## Review files states for your ER format
1.	Click the File states for the sources button to review the content of configured file sources for the current ER format.
2.	In the Files section, review the list of files:
a.	Either located in the file sources (applicable based on the file name mask if defined) and ready for data import:
i.	The Sources log for the import format section is blank for such files.
b.	Or already imported files:
i.	In the Sources log for the import format section, review the history of this file import.

Note that you can also use the Organization administration > Electronic reporting > File states for the sources path to access this page. In this case the page will present information about file sources for all ER formats to which file sources have been configured in the currently logged company.

## Import data from SharePoint folder located Excel files
### Prepare Excel file for data import
1.	On the SharePoint, upload the Excel file with vendors transactions to the previously created SharePoint folder Files import source (main).
2.	On the File states for the sources button form, click Refresh to update the content of the page.
Note that previously uploaded to the SharePoint Excel file appeared in this form with the status Ready.
a.	Status Ready is assigned automatically for each new file in the SharePoint folder. It means that this file is ready for import.
b.	Status Importing is applied automatically by the ER report when this file will be locked by import process to prevent its usage by other processes (if many of them are running simultaneously).
c.	Status Imported is assigned automatically by the ER report when the import of this file successfully completed. It means that the imported file has been deleted from the configured source.
d.	Status Failed is assigned automatically by the ER report when the import of this file completed with errors / exceptions.
e.	Status On hold can be assigned manually by user on this form. It means that this file will not be imported for now. It can be used to postpone the import of some files.

## Import data from SharePoint files
1.	Open the ER configurations tree and expand the list of components of the ER model that is used by your ER format for data import. Click on the model mapping name link:
2.	Click Run to execute the selected model mapping.
Note that since you configured files sources for the ER format, the File source option is offered for you to be changed if required. If you keep this offer, the XLSX files will be imported from the configured sources – SharePoint folders in our case.

Be aware that the files will be imported in the predefined order – as earlier a file has been placed to the SharePoint folder, as earlier it will be imported.

Note that now we will run this model mapping to import the only one file. Same model mapping can be executed unattended in batch mode – in this case any time a batch will run this ER format, a single file will be imported from the configured file sources. Use the following code to implement this batch run:

ERObjectsFactory::createMappingDestinationRunByImportFormatMappingId().run()

Be aware that when a file has been successfully imported from the SharePoint folder, it will be deleted from this folder.

3.	Enter the desire voucher id, for example V-00001, and click OK.
Note that the Infolog contains the user’s notification that a residing in the SharePoint folder file has been successfully imported.

4.	Open the File states for the sources button form, click Refresh to update the content of the page.
5.	In the Files section, review the list of files.

Note that the Sources log for the import format section presents the history of the Excel file import. As this file was successfully imported, it is marked as deleted in the SharePoint folder.

6.	Review the SharePoint folder Files import source (main).

Note that the successfully imported Excel files has been deleted from this folder.

7.	Open the Vendor settlement for 1099s form by using the Accounts payable > Periodic tasks > Tax 1099 > Vendor settlement for 1099s path.
8.	Define appropriate values in From date and To date fields, and click Manual 1099 transactions:
Note that vendors’ transactions of the voucher V-00001 have been imported from the SharePoint located Excel file to your application.

## Prepare another Excel file for data import
1.	Update the previously used for data import Excel file – put to the third row the code of a vendor that does not exist in your application:
2.	On the SharePoint, upload the updated Excel file with vendors transactions to the previously created SharePoint folder Files import source (main).

## Import data from SharePoint files
1.	Open the ER configurations tree and expand the list of components of the ER model that is used by your ER format for data import. Click on the model mapping name link.
2.	Update the model mapping to consider the incorrect vendor code as an error in data import process:
a.	Click Designer.
b.	Select Validations tab.
c.	Change the post-validation action for a validation rule that was configured to evaluate whether the importing vendor account exists in the application from Continue execution (write a remark) value to Stop execution (raise an error) value:
d.	Save changes and close the ER model mapping designer.

3.	Click Run to execute the modified ER model mapping.
4.	Enter the desire voucher id, for example V-00002, and click OK.
Note that the Infolog contains the user’s notification that residing in SharePoint folder file contains incorrect vendor account and can’t be imported.

5.	Open the File states for the sources button form, click Refresh to update the content of the page.
6.	In the Files section, review the list of files.
Note that the Sources log for the import format section tells user that the import process for this file failed and this file is still in the SharePoint folder (Is deleted checkbox is unchecked). If you fix this file on the SharePoint (put the correct vendor’s account instead of the incorrect one) and change the status of this file on the Sources log for the import format form from Failed to Ready, this file can be imported again.

7.	Review the SharePoint folder Files import source (main).

Note that the non-imported Excel files is still in this SharePoint folder.

8.	Open the Vendor settlement for 1099s form by using the Accounts payable > Periodic tasks > Tax 1099 > Vendor settlement for 1099s path.
9.	Define appropriate values in From date and To date fields, and click Manual 1099 transactions:

Note that the only voucher V-00001 vendors’ transactions are available. There are no transactions of the voucher V-00002 available even the error has been discovered for the last imported transaction in the Excel file.






