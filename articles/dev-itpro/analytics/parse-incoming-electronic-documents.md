---
# required metadata

title: Parse incoming documents to update application data
description: This topic provides information about how to set up Electronic reporting (ER) formats that can be used to parse incoming documents and then apply selected content to update application data. 
author: nselin
manager: AnnBe
ms.date: 11/01/2017
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
ms.search.scope: AX 7.3.0, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 27621
ms.assetid: e3f7960d-2e01-46a7-9ac8-c355ac933cd6
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2017-11-10
ms.dyn365.ops.version: AX 7.3.0

---
# Parse incoming documents to update application data
[!include[banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats that can be executed in the Dynamics 365 for Operations application to parse incoming electronic documents to use their content for application data update.
With new ER functionality introduced, the parsing incoming electronic documents in xml format has been improved:

- The **CASE** format element can be used as a root element of the ER format that is configured to parse incoming electronic documents in xml format. The **FILE** format element is supported as nested element of the **CASE** element. This format allows you to configure a single ER format for parsing incoming electronic documents that may contain different root xml elements.
- The new attribute **Parsing order of nested elements** has been introduced for xml format elements in ER formats. You can use this attribute to define a single xml element that is expected in the incoming file. There are two valid sequences of the nested elements:
  - **As in format** - The incoming file is valid when the sequence of nested elements in the file is the same as described in ER format.
  - **Any** - The incoming file is valid when all ER format nested elements are presented in the parsing file regardless of their sequence in the file.

To become more familiar with the details of this feature, play the task guide, ER - Parse incoming documents to update application data (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process) which shows how the responses from a web service can be parsed by using an ER format.

Download the following files that are required to complete certain steps of the task guide:
- [ER data model configuration](https://go.microsoft.com/fwlink/?linkid=862266)
- [ER format configuration](https://go.microsoft.com/fwlink/?linkid=862266)
- [Web service response sample 1](https://go.microsoft.com/fwlink/?linkid=862266)
- [Web service response sample 2](https://go.microsoft.com/fwlink/?linkid=862266)
- [Web service response sample 3](https://go.microsoft.com/fwlink/?linkid=862266)
- [Web service response sample 4](https://go.microsoft.com/fwlink/?linkid=862266)

