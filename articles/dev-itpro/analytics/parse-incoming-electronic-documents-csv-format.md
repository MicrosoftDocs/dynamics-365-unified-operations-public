---
# required metadata

title: Parse incoming documents in CSV format
description: This topic provides information about how to set up Electronic reporting (ER) formats to parse incoming CSV formatted documents. 
author: nickselin
manager: AnnBe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 7.3.0, UnifiedOperations, Core
# ms.tgt_pltfrm: 
ms.custom: 27621
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2017-11-10
ms.dyn365.ops.version: AX 7.3.0

---
# Parse incoming documents in CSV format
[!include[banner](../includes/banner.md)]

You can set up Electronic reporting (ER) formats that can parse incoming electronic .csv documents and then use the content for application data updates.

When you configure a new ER format to parse incoming .csv files, you can use the new format to:

- Add a new sequence element that specifies each line in the file must be considered as a separated record.
  
- Add sequence elements as nested items that split the incoming file by lines to specify that each line in the file must be considered as a set of fields.
  - In the **Custom delimiter** field, specify the character that will be recognized as the field separator in the parsing line. You can define multiple field separators for different sequence elements in order to parse specific lines. Note that you can leave the **Custom delimiter** field blank for a certain sequence element. This would mean that any line that is parsed using this sequence will be parsed like a .txt file line. 

- Add sequence elements as nested items that parse each line of the incoming file. To these nested items, add the required elements of TEXT ER data type (String, DateTime, Numeric) to describe the structure of the parsing line as the set of individual fields of different data types

To become more familiar with the details of this feature, play the task guide,  ER Create a format configuration to import data from an external csv file task guide (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process) which shows how the incoming file in .csv format can be parsed by using ER format to update application data.
Download the following files that are required to complete the task guide.

| Title                                  | File name          |
|----------------------------------------|--------------------|
| ER format configuration                | [1099formatcsv.xml](https://go.microsoft.com/fwlink/?linkid=862266)  |
| Sample of incoming file in .csv format | [1099entriescsv.csv](https://go.microsoft.com/fwlink/?linkid=862266) |

If you have not yet completed the task guide, ER Create required configurations to import data from an external file for electronic reporting, download the following file to complete that task guide first.

| Title                                  | File name          |
|----------------------------------------|--------------------|
| ER model configuration               | [1099model.xml](https://go.microsoft.com/fwlink/?linkid=862266)  |
