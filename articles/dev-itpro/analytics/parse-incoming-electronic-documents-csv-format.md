---
# required metadata

title: Parse incoming documents in CSV format
description: This topic provides information about how to set up Electronic reporting (ER) formats to parse incoming CSV formatted documents. 
author: nickselin
manager: AnnBe
ms.date: 12/01/2017
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

You can design Electronic reporting (ER) formats that can be used to parse incoming electronic csv files and then use the content from the csv files to update application data.
There are multiple ways to configure a new ER format for parsing incoming csv files:

- Add a new sequence element which specifies that each line in the file is considered a separated record
- Add a nested item in a sequence element that splits the incoming file by line
- Add a nested item in a sequence element that parses each line of the incoming file

### Add a new sequence element which specifies that each line in the file is considered a separated record
In the sequence element, select the appropriate value, for example **New line - Windows (CR LF)**, in the Special characters field of the fields’ group Sequence element delimiter.

### Add a nested item in a sequence element that splits the incoming file by lineAdd a nested item in a sequence element that parses each line of the incoming file. Add required elements of **TEXT** ER data type (**String**, **DateTime**, **Numeric**) to describe the structure of the parsing line as the set of individual fields of different data types.
You can specify the character in the **Custom delimiter** field that will be recognized in the parsing line as a fields separator.

> [!NOTE]
   > It is possible to define different field separators for different sequence elements to parse specific file lines in which fields are separated by different characters. It is also possible to keep the Custom delimiter field blank for certain sequence element. This setting means that any file line which is parsed by using this sequence will be parsed like a txt file line.

In the Quotation application field, select the value for when you expect that some fields of any line that is parsed by this sequence component will be enclosed by certain characters. The following options are available:

- **All** - Include quotation characters in the parsing line for any field of any data type.
  - If you select this, define the desired character(s) in the Quotation mark field that will be used for fields quotation, for example the double quotes character.
- **Text only** - Include quotation characters in the parsing line for any field of the String data type.
  - If you select this, define the desired characters in the Quotation mark field that will be used for fields quotation.
- **Derive from parent only** - Use the same sequence element as the Quotation application field’s settings that are defined for the parent sequence element.
Note that the Quotation mark field setting will be taken from the settings of the parent sequence element as well.
- **None** - Exclude quotation characters in the parsing line for any field of any data type.

### Add a nested item in a sequence element that parses each line of the incoming file
Add a nested item in a sequence element that parses each line of the incoming file. Add required elements of the **TEXT** ER data type, such as **String**, **DateTime**, and **Numeric**, to describe the structure of the parsing line as a set of individual fields of different data types.

For each added format element that represents an individual field of the parsing line, by default, nothing is selected in the **Multiplicity** field. This means that the value of the field in the parsing line is considered as mandatory in the parsing file.
In the Multiplicity field, select **Zero one** to allow for empty lines in the parsing file. This will mean that a field’s value in the parsing file is considered optional.

> [!NOTE]
   > Each **String**, **DateTime**, or **Numeric** format element with the option **Zero one** selected in the **Multiplicity** field, the data source item **isMatch** will be available in the mapping of this format to ER data model. This item **isMatch** will return **True** when the parsing line contains value for such field. It will return **False** otherwise.

To become more familiar with the details of this feature, play task guide, **ER Create a format configuration to import data from an external csv file** (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process) which walks through how the incoming csv file can be parsed by using the ER format to update application data.
Download the following files to complete the task guide mentioned above.


| Title                                  | File name          |
|----------------------------------------|--------------------|
| ER format configuration                | [1099formatcsv.xml](https://go.microsoft.com/fwlink/?linkid=862266)  |
| Sample of incoming file in .csv format | [1099entriescsv.csv](https://go.microsoft.com/fwlink/?linkid=862266) |

Download the following file that is required to complete the task guide mentioned above if you have not played the task guide, **ER Create required configurations to import data from an external file for electronic reporting** in the current Dynamics 365 for Finance and Operation application.

| Title                                  | File name          |
|----------------------------------------|--------------------|
| ER model configuration               | [1099model.xml](https://go.microsoft.com/fwlink/?linkid=862266)  |
