---
# required metadata

title: Data management error descriptions
description: This topic describes the error messages that you might encounter in data management.
author: Sunil-Garg
manager: AnnBe
ms.date: 09/20/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
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
If this is not a data issue and the entity is expected to handle such cases, you can chose to sequentially process the files or reduce the frequency of which the files are sent to the end point. However, if you reduce the frequency, you might continue to receive this error, depending on the timing.

## There are field(s) which are not mapped to entity name
It is a common practice to use the export functionality to generate the entity template file which can be later used for imports. However, while exporting the template, in fixed width format with 'First row header' set to 'No' (in source data formats set up), the exported template will not have the column names. When this file is imported, it will result in this error. 

  
