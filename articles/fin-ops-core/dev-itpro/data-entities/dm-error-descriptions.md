---
# required metadata

title: Data management error descriptions
description: This topic describes the error messages that you might encounter in data management.
author: Sunil-Garg
manager: AnnBe
ms.date: 01/08/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 25341
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2018-09-15
ms.dyn365.ops.version: Platform update 20

---

# Data management error descriptions
This topic documents the scenarios when a specific error will be seen. This is not a complete list of errors and scenarios, however this list will be continuously updated so keep checking back for updates. Any feedback on this page with regards to specific errors that should be covered are welcome. We will strive to prioritize your feedback requests so that this topic stays up to date.

[!include [banner](../includes/banner.md)]

This topic describes the error messages that you might encounter in data management.

## Import to target failed due to an update conflict as more than one process is trying to update the same record at the same time
When you use recurring imports (enqueue API), if the files are sent to the end point at high frequency and the sequential processing of messages isn't enabled, data management will try to process the files in parallel. 
When files are processed in parallel, and multiple files have the same record, multiple threads will try to update the same record at the same time. 
If this is a data issue, you must update the data so that the same records don’t repeat across files. 
If this is not a data issue and the entity is expected to handle such cases, this might be a bug. For bugs, to mitigate the issue, you can choose to sequentially process the files. If this is not a data issue and the entity is not expected to process in parallel, then this entity must not be subjected to parallel processing. You should enable sequential processing of messages in the recurring job. 

## There are field(s) which are not mapped to Entity &lt;EntityName&gt;
It is a common practice to use the export functionality to generate the entity template file which can be later used for imports. However, while exporting the template, in fixed width format with 'First row header' set to 'No' (in source data formats set up), the exported template will not have the column names. When this file is imported, it will result in this error. 

## Data package download - Error downloading data package for job ''. Record for ID - {GUID} not found
One of the scenarios where this can happen is when the environment, such as the dev environment, points to the database in another environment, such as UAT, and the export job is run from the source environment. which is dev in this example. The exported file gets uploaded to the blob storage that is associated with the source environment (dev, in this example). However, this job will also show up in the target environment (UAT) since the database is shared. If a you try to download the exported file using the **Download file** option, this error will display because the file does not exist in the blob storage of the target environment (UAT) from where you are trying to download.

## XML is not in correct format-Exception from HRESULT: 0xC0010009
This is a generic message that covers all XML formatting issues in the file. For example, the data project has mappings for columns that do not exist in the file that is being used for the operation. This can happen if certain columns were removed from the file and this file is now used. Either fix the mapping in the data project or fix the file to have all the columns as expected.

## Error while uploading a file during export
When running an export on a development environment, an error could occur relating to not being able to upload the export file. This could occur if Azure storage emulator is not available or an older version of the emulator is installed. To resolve this issue, install the latest emulator, re-start the virtual machine (VM), and re-run the export job. The storage emulator can be installed from [Azure storage emulator](https://docs.microsoft.com/azure/storage/common/storage-use-emulator).

