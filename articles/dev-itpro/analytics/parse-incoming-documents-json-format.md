---
# required metadata

title: Parse incoming documents in JSON format
description: This topic provides information about how to set up Electronic reporting (ER) formats to parse incoming JSON formatted documents.
author: kfend
manager: AnnBe
ms.date: 05/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: EROperationDesigner, ERParameters
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
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.1

---

# Parse incoming documents in JSON format
[!include[banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to parse incoming electronic documents that represent data in text format based on JavaScript (files in JSON format).

To learn more about this feature, download the files in the following table, and then play the task guide, ER Create a format configuration to import data from an external JSON file. This task guide walks through how the incoming JSON file can be parsed by using the ER format to update application data.

| Title                                  | File name                                    |
|----------------------------------------|----------------------------------------------|
| ER format configuration                | [Format for importing vendors' trans_JSON.xml](https://go.microsoft.com/fwlink/?linkid=874111) |
| Sample of incoming file in .csv format | [1099entries_JSON.txt](https://go.microsoft.com/fwlink/?linkid=874111)                         |
## Requirements
Before you complete the task guide, ER Create aformat configuration to import data from an external JSON file, the following is required:

- Parent elements in JSON file can only be object elements.
- A nested element for object should be a property element to create a valid JSON structure.
- JSON array can only be only nested element of property element of object.
- Json array can only contain Json objects. It can't contain direct string/numeric values and nested arrays). Elements in the array will be parsed in order as they specified in the format with consideration regarding multiplicity settings on each json object.

Additionally, if you have not already, you must complete the task guide, [ER Create required configurations to import data from an external file for electronic reporting](tasks/er-required-configurations-import-data.md). Download the following file to complete the task guide if necessary.

| Title                  | File name     |
|------------------------|---------------|
| ER model configuration | [1099model.xml](https://go.microsoft.com/fwlink/?linkid=874111) |
