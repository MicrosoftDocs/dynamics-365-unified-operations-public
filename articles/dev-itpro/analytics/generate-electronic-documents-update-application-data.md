---
# required metadata

title: Generate electronic documents and update application data using the Electronic reporting tool
description: You can design Electronic reporting (ER) formats that can be used in the Finance and Operations application to generate outgoing electronic documents. You can also design ER formats that parse incoming electronic documents and use the content in those documents to update application data.
author: NickSelin
manager: AnnBe
ms.date: 11/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace
# ROBOTS: 
audience: Developer, IT Pro, Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 27621
ms.assetid: 018a11ae-854c-4f36-9358-8c39baca882d
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Generate electronic documents and update application data using the Electronic reporting tool

You can design Electronic reporting (ER) formats that can be used in the Finance and Operations application to generate outgoing electronic documents. You can also design ER formats that parse incoming electronic documents and use the content in those documents to update application data. 

With this functionality, a single ER format can be used to generate outgoing electronic documents and then update the application data. This feature can be used in the following scenarios:

- To prevent repeated usage of application data in subsequent processes you can mark an application’s data immediately after it is used to generate electronic documents. For example, you can mark payment transactions as already processed immediately after they have been included in a generated payment message.
- To store the processing details of electronic documents that have been generated using ER logic. For example, a unique payment message identification that is generated using the ER expression. The expression is based on information entered in the ER dialog box when the ER format is run to generate documents.

To learn more about this feature, play the set of ER Generate documents with application data update Task guides (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process), which walk you through the details of Intrastat reporting and archiving. The following files are required to complete certain steps in these Task guides. Download and save these files to your local machine.

- [ER data model configuration: Intrastat (model)](https://go.microsoft.com/fwlink/?linkid=849038)
- [ER model mapping configuration: Intrastat (mapping)](https://go.microsoft.com/fwlink/?linkid=849038)
- [ER format configuration: Intrastat (format)](https://go.microsoft.com/fwlink/?linkid=849038)
