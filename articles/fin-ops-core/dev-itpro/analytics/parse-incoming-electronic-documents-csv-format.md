---
# required metadata

title: Parse incoming documents in CSV format
description: This topic provides information about how to set up Electronic reporting (ER) formats to parse incoming CSV formatted documents. 
author: nickselin
ms.date: 12/01/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 27621
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2017-11-10
ms.dyn365.ops.version: 7.3

---
# Parse incoming documents in CSV format
[!include [banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to parse incoming electronic documents that represent tabular data in plain text (files in CSV format) and then use the content from these documents to update application data. The following approach can be used:

+ Begin your format's design by adding a new root sequence element to specify that each line in the parsing file is considered a separate record.

    + In the added sequence element, select the appropriate value, for example **New line - Windows (CR LF)**, in the **Special characters** field in the **Sequence element delimiter** field group.

+ Continue your format's design by adding a nested sequence element of the added root sequence element to specify that each line in the parsing file is considered as a set of fields.

    + You can specify the character in the **Custom delimiter** field that will be recognized in the parsing line as a fields separator.

        > [!NOTE]
        > - You can define different field separators for different sequence elements to parse specific file lines in which fields are separated by different characters.
        > - The **Custom delimiter** field can be left blank for certain sequence elements. An empty field means that any file line that is parsed by using this sequence will be parsed like a .txt (fixed length text) file line.

    + In the **Quotation application** field, select the value when you expect that some fields of any line that is parsed by this sequence element will be enclosed by certain characters. The following options are available:

        + **All** – Include quotation characters in the parsing line for any field of any data type. If you select this, define the desired characters in the **Quotation mark** field that will be used for fields quotation. For example, the double quotes character.
        + **Text only** – Include quotation characters in the parsing line for any field of the **String** data type. If you select this, define the desired characters in the **Quotation mark** field that will be used for fields quotation.
        + **Derive from parent only** – Use the same **Quotation application** field settings that are defined for the parent sequence element. Note that the **Quotation mark** field setting will be taken from the settings of the parent sequence element as well.
        + **None** – Exclude quotation characters in the parsing line for any field of any data type.

+ Complete your format's design by adding nested elements for the added sequence element that represents the set of fields of the parsing line. Add the required elements of the **Text** group, such as **String**, **DateTime**, and **Numeric**, to describe the structure of the parsing line as a set of individual fields of different data types.

    + For each format element that represents an individual field of the parsing line, by default, nothing is selected in the **Multiplicity** field. This means that the value of the field in the parsing line is considered required. In the **Multiplicity** field, select **Zero one** to consider the value of this field in the parsing line as optional.

        > [!NOTE]
        > The data source item **isMatch** is available when you map this format to ER data model for each **String**, **DateTime**, or **Numeric** format element with the option **Zero one** selected in the **Multiplicity** field. When this field contains a value, **isMatch** will return **True**. If there is no value in the field, it will return **False**.

To learn more about this feature, play the task guide, **ER Create a format configuration to import data from an external CSV file** (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process), which walks through how the incoming CSV file can be parsed by using the ER format to update application data.

Download the following files to complete the task guide mentioned above.

| Title                                  | File name                                                            |
|----------------------------------------|----------------------------------------------------------------------|
| ER format configuration                | [1099formatcsv.xml](https://go.microsoft.com/fwlink/?linkid=862266)  |
| Sample of incoming file in .csv format | [1099entriescsv.csv](https://go.microsoft.com/fwlink/?linkid=862266) |

Download the following file that is required to complete the task guide mentioned above if you have not played the task guide, **ER Create required configurations to import data from an external file for electronic reporting** in the current Finance and Operations application.

| Title                  | File name                                                       |
|------------------------|-----------------------------------------------------------------|
| ER model configuration | [1099model.xml](https://go.microsoft.com/fwlink/?linkid=862266) |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]