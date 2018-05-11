---
# required metadata

title: Split generated files based on file size and content quantity
description: 
author: NickSelin
manager: AnnBe
ms.date: 05/03/2018
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

# Split generated files based on file size and content quantity

[!include[banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats to generate outgoing documents in xml format. Sometimes, these documents can be accepted only when they meet specific criteria such file size or limited numbers of certain xml nodes. You can design ER formats to generate electronic documents that can satisfy the requirements specified by the recipients of the documents. 

  -	File size limit can be defined for the FILE format element as an ER expression. When an ER report is generated and the limit is exceeded, ER will finish creating the current file and then continue making the next one.
  -	A limit to the quantity of elements can be defined for any XML ELEMENT format as an ER expression. When the number of xml nodes in the generated file exceeds the defined limit during an ER report execution, ER will finish creating the current file and then continue making the next one.
  -	A limit on the quantity of elements can be defined for any XML SEQUENCE format element as an ER expression. When the number of nested xml nodes of this format element in the generated file exceeds the defined limit during an ER report execution, ER will finish creating the current file and the continue making the next one.
  -	Any XML ELEMENT format element can be marked as non-breakable to keep the nested items of xml nodes generated under the format element in a single generated file.

In addition to the XML ELEMENT and XML SEQUENCE format element, you can add xml nodes to the generated file by using the RAW XML format element. When you do this, the nodes will not be considered when the number of nodes is calculated to evaluate the xml items quantity limits. 

If you configured some GER files destinations for a FILE format element that has been configured to split the generated output whenever some limits are exceeded, each piece of generated output will be sent as an individual file to the configured files destinations. To uniquely name the files that have been created by splitting the output, the ER expression for the ER format FILE component must be configured. The ER data source of the NUMBER SEQUENCE type can be included and the number sequence will be incremented for each piece of the splitting output.

To learn more about this feature, play the task guide, **ER Xml file splitting based on limits of file size and items quantity** (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process), which walks through how an ER format can be configured to split generated files based on limits of file size and content item quantity.
Download the following files to complete the task guide mentioned above.

- [ER model configuration -	XmlFilesSplittingModel.xml](https://go.microsoft.com/fwlink/?linkid=874111) 
- [ER format configuration -	XmlFilesSplittingFormat.xml](https://go.microsoft.com/fwlink/?linkid=874111) 


