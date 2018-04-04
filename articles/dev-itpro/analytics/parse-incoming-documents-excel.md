---
# required metadata

title: Parse incoming documents in Microsoft Excel
description:  This topic provides information about designing Electronic reporting (ER) formats to parse and then use the content contained in incoming Microsoft Excel files. 
author: NickSelin
manager: AnnBe
ms.date: 04/04/2018
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

# Parse incoming documents in Microsoft Excel

[!include[banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to parse incoming Microsoft Excel files that represent data in Microsoft Excel workbooks (files in XLSX format) and then use the content from these files to update application data. This approach can be used:

-	If you designed a new model and format and want to test them at run-time. In this case, Excel will simulate the actual application data.
-	If you manage data beyond your application in Excel and want to import this data to submit a specific report.

To learn more about this feature, play the task guides **Design formats to import data from an external Excel file** and **Import data from an external Excel file** (parts of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process), which walk through how the incoming Excel file can be parsed by using the ER format to import information from incoming documents and update application data.
Download the following files to complete the task guides mentioned above.

- [Incoming file in .XLSX format - template](https://go.microsoft.com/fwlink/?linkid=862266)
- [Incoming file in .XLSX format - sample data](https://go.microsoft.com/fwlink/?linkid=862266)

If you have not played yet the task guide, [Create required configurations to import data from an external file](./tasks/er-required-configurations-import-data.md) in the current Dynamics 365 for Finance and Operation application, download the following file.

- [ER model configuration](https://go.microsoft.com/fwlink/?linkid=862266)


