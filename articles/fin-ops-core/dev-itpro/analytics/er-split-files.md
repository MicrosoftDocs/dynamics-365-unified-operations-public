---
# required metadata

title: Split generated XML files based on file size and content quantity
description: This topic provides information about how to split generated files based on the file size and content item quantity.
author: NickSelin
ms.date: 04/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: EROperationDesigner, ERFormatDestinationTable
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

# Split generated XML files based on file size and content quantity

[!include[banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to generate outgoing documents in XML format. Sometimes, those documents can be accepted only when they meet specific criteria, such a maximum file size or a maximum number of some XML nodes. You can design ER formats to generate electronic documents that satisfy the requirements that the recipients of those documents specify.

- For the FILE format element, you can define a limit on the file size as an ER expression. If the defined limit is exceeded when an ER report is generated, ER finishes creating the current file and then moves on to create the next file.
- For any XML ELEMENT format, you can define a limit on the number of elements as an ER expression. If the number of XML nodes in the file that is generated exceeds the defined limit when an ER report is run, ER finishes creating the current file and then moves on to create the next file.
- For any XML SEQUENCE format element, you can define a limit on the number of child elements as an ER expression. If the number of nested XML nodes of the format element in the generated file exceeds the defined limit when an ER report is run, ER finishes creating the current file and then moves on to create the next file.
- You can mark any XML ELEMENT format element as non-breakable. In this way, you can keep the nested items of XML nodes that are generated under the format element in a single generated file.

In addition to using the XML ELEMENT and XML SEQUENCE format elements to add XML nodes to the generated file, you can use the RAW XML format element. However, nodes that you add by using the RAW XML format element aren't considered when the number of nodes is calculated to evaluate the limits on the number of elements.

If you configured file destinations for a FILE format element that has been configured to split the generated output whenever specific limits are exceeded, each piece of generated output is sent to the configured file destination as an individual file. To uniquely name the files that are created by splitting the output, you must configure an ER expression for the FILE format element. If you include an ER data source of the NUMBER SEQUENCE type, the number sequence will be incremented for each piece of the split output.

To learn more about this feature, play the **ER Split XML files based on the file size or content item quantity** task guide, which is part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process and can be downloaded from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=874684). This task guide walks you through the process of configuring an ER format to split generated files based on limits on the file size and content item quantity. To complete the task guide, you must download the following files:

- [ER model configuration -	XmlFilesSplittingModel.xml](https://download.microsoft.com/download/e/a/f/eaffe96a-22ec-4a32-898a-f4328c91c387/XmlFilesSplittingModel.xml)
- [ER format configuration - XmlFilesSplittingFormat.xml](https://download.microsoft.com/download/e/9/c/e9c5849b-8254-4cdf-bb00-4c2ebc72ddec/XmlFilesSplittingFormat.xml)

## Additional resources
[Electronic reporting (ER) destinations](electronic-reporting-destinations.md)

[Formula designer in Electronic reporting (ER)](general-electronic-reporting-formula-designer.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
