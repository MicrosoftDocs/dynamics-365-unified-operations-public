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

- CASE format element can be used as a root element of the ER format configured for parsing incoming electronic documents in xml format. FILE format element is supported as nested element of the CASE element in ER formats that are used for parsing incoming electronic documents in xml format. It allows now to configure a single ER format for parsing incoming electronic documents in xml format that may contain different root xml elements
- New attribute Parsing order of nested elements has been introduced for xml format elements in ER formats that were created for parsing incoming electronic documents. This attribute allows to define for a single xml element that is expected in the incoming file the valid sequence of its nested elements:
  - With option As in format selected, the incoming file will be considered as valid one when the sequence of nested elements in the file is the same as described in ER format
  - With option Any, the incoming file will be considered as valid one when all described in ER format nested elements are presented in the parsing file regardless of their sequence in it

To become familiar with the details of this feature, play the ER improvements in parsing incoming documents to update application data task guide (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process) presenting how the responses from a web service can be parsed by using ER format.

Download the following files that are required to complete certain steps of the mentioned above task guides:
- [ER data model configuration](https://go.microsoft.com/fwlink/?linkid=862266)
- [ER format configuration](https://go.microsoft.com/fwlink/?linkid=862266)
- [Web service response sample 1](https://go.microsoft.com/fwlink/?linkid=862266)
- [Web service response sample 2](https://go.microsoft.com/fwlink/?linkid=862266)
- [Web service response sample 3](https://go.microsoft.com/fwlink/?linkid=862266)
- [Web service response sample 4](https://go.microsoft.com/fwlink/?linkid=862266)

