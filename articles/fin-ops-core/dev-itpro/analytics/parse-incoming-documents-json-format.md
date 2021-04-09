---
# required metadata

title: Parse incoming documents in JSON format
description: This topic explains how to set up Electronic reporting (ER) formats to parse incoming documents in JavaScript Object Notation (JSON) format.
author: kfend
ms.date: 05/20/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: EROperationDesigner, ERParameters
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
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.1

---

# Parse incoming documents in JSON format

[!include[banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to parse incoming electronic documents that represent data in a text format that is based on JavaScript (in other words, files in JavaScript Object Notation \[JSON\] format).

To learn more about this feature, download the files in the following table, and then play the ER Create a format configuration to import data from an external JSON file task guide. This task guide shows how an ER format can be used to parse an incoming JSON file to update application data.

| Title                                  | File name |
|----------------------------------------|-----------|
| ER format configuration                | [Format for importing vendors' trans_JSON.xml](https://go.microsoft.com/fwlink/?linkid=874111) |
| Sample of incoming file in .csv format | [1099entries_JSON.txt](https://go.microsoft.com/fwlink/?linkid=874111) |

## Requirements

Before you complete the ER Create a format configuration to import data from an external JSON file task guide, the following requirement must be met:

- Parent elements in the JSON file can be only object elements.
- Nested elements for an object should be property elements, so that a valid JSON structure is created.
- JSON arrays can be only nested elements of the property elements of an object.
- JSON arrays can contain only JSON objects. They can't contain direct string/numeric values and nested arrays. Elements in these arrays will be parsed in order, as they are specified in the format. Multiplicity settings on each JSON object will be considered.

Additionally, you must complete the [ER Create required configurations to import data from an external file](tasks/er-required-configurations-import-data.md) task guide if you haven't already completed it. Download the following file to complete the task guide.

| Title                  | File name |
|------------------------|-----------|
| ER model configuration | [1099model.xml](https://go.microsoft.com/fwlink/?linkid=874111) |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]