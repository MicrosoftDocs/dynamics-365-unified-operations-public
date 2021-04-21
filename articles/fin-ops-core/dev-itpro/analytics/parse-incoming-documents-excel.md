---
# required metadata

title: Parse incoming documents in Excel format
description:  This topic provides information about designing Electronic reporting (ER) formats to parse content contained in incoming Microsoft Excel files. 
author: NickSelin
ms.date: 05/25/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 220314
ms.assetid: 2685df16-5ec8-4fd7-9495-c0f653e82567
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2018-04-01
ms.dyn365.ops.version: Release 8.0

---

# Parse incoming documents in Excel format

[!include[banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to parse incoming Microsoft Excel files that represent data in Microsoft Excel workbooks (files in XLSX format). You can then use the content from these files to update application data. This is useful if you:

- Design a new model and format and want to test them at run-time. In this case, Excel will simulate the actual application data.
- Manage data beyond your application in Excel and want to import this data to submit a specific report.

To learn more about this feature, play the task guides **ER Import data from a Microsoft Excel file (Part 1: Design format)** and **ER Import data from a Microsoft Excel file (Part 2: Import data)** (parts of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process). These task guides walk through how the incoming Excel file can be parsed by using the ER format to import information from incoming documents and update application data. You can download the task guide files from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=874684).

Download the following files to complete the task guides mentioned above.

| Content description                         | File                                                                       |
|---------------------------------------------|----------------------------------------------------------------------------|
| Incoming file in .XLSX format - template    | [1099import-template.xlsx](https://go.microsoft.com/fwlink/?linkid=862266) |
| Incoming file in .XLSX format - sample data | [1099import-data.xlsx](https://go.microsoft.com/fwlink/?linkid=862266)     |

If you have not yet played the following task guide, [ER Create required configurations to import data from an external file](./tasks/er-required-configurations-import-data.md) in the current Finance and Operations application, download the following file.

| Content description    | File                                                            |
|------------------------|-----------------------------------------------------------------|
| ER model configuration | [1099model.xml](https://go.microsoft.com/fwlink/?linkid=862266) |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]