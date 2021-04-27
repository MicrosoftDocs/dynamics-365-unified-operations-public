---
# required metadata

title: Parse incoming documents to update application data
description: This topic provides information about how to set up Electronic reporting (ER) formats that can be used to parse incoming documents.
author: nickselin
ms.date: 11/01/2017
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
ms.assetid: e3f7960d-2e01-46a7-9ac8-c355ac933cd6
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2017-11-10
ms.dyn365.ops.version: 7.3

---
# Parse incoming documents to update application data
[!include [banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats and run them in the application, to parse incoming electronic documents and then use their content to update application data.

The following new ER functionality that has been introduced improves the parsing of incoming electronic documents in XML format:

- The **CASE** format element can be used as a root element of the ER format that is configured to parse incoming electronic documents in XML format. The **FILE** format element is supported as a nested element of the **CASE** element. Therefore, you can configure a single ER format to parse incoming electronic documents that might contain different root XML elements.
- A **Parsing order of nested elements** attribute has been introduced for XML format elements in ER formats. You can use this attribute to define a single XML element that is expected in the incoming file. There are two valid sequences of the nested elements:

    - **As in format** – The incoming file is valid when the sequence of nested elements in the file is the same as the order that is described in the ER format.
    - **Any** – The incoming file is valid when all nested elements in the ER format are present in the parsing file, regardless of their sequence in that file.

To become more familiar with the details of this feature, play the task guide, ER - Parse incoming documents to update application data (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process). This task guide shows how the responses from a web service can be parsed by using an ER format.

To complete some steps of the task guide, you must download the following files:

| Content description           | File                                                              |
|-------------------------------|-------------------------------------------------------------------|
| ER data model configuration   | [EFSTAmodel.xml](https://go.microsoft.com/fwlink/?linkid=862266)  |
| ER format configuration       | [EFSTAformat.xml](https://go.microsoft.com/fwlink/?linkid=862266) |
| Web service response sample 1 | [Response1.xml](https://go.microsoft.com/fwlink/?linkid=862266)   |
| Web service response sample 2 | [Response2.xml](https://go.microsoft.com/fwlink/?linkid=862266)   |
| Web service response sample 3 | [Response3.xml](https://go.microsoft.com/fwlink/?linkid=862266)   |
| Web service response sample 4 | [Response4.xml](https://go.microsoft.com/fwlink/?linkid=862266)   |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]