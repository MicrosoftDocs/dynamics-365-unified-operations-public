---
title: Generate electronic documents and update application data by using ER
description: You can design Electronic reporting (ER) formats that can be used in the application to generate outgoing electronic documents.
author: kfend
ms.date: 04/23/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro, Application user
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 018a11ae-854c-4f36-9358-8c39baca882d
ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace
---

# Generate electronic documents and update application data by using ER

[!include [banner](../includes/banner.md)]

You can design Electronic reporting (ER) formats that can be used in the application to generate outgoing electronic documents. You can also design ER formats that parse incoming electronic documents and use the content in those documents to update application data.

With this functionality, a single ER format can be used to generate outgoing electronic documents and then update the application data. This feature can be used in the following scenarios:

- To prevent repeated usage of application data in subsequent processes you can mark an application’s data immediately after it is used to generate electronic documents. For example, you can mark payment transactions as already processed immediately after they have been included in a generated payment message.
- To store the processing details of electronic documents that have been generated using ER logic. For example, a unique payment message identification that is generated using the ER expression. The expression is based on information entered in the ER dialog box when the ER format is run to generate documents.

To learn more about this feature, play the set of ER Generate documents with application data update Task guides (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process), which walk you through the details of Intrastat reporting and archiving. The following files are required to complete certain steps in these Task guides. Download and save these files to your local machine.

- [ER data model configuration: Intrastat (model)](https://download.microsoft.com/download/9/c/e/9ceeacbe-c13e-422e-96f2-594c4a6b45b7/Intrastatmodel.xml)
- [ER model mapping configuration: Intrastat (mapping)](https://download.microsoft.com/download/2/1/d/21ddaaeb-64c5-4408-a35f-1ccb922d40a4/Intrastatmapping.xml)
- [ER format configuration: Intrastat (format)](https://download.microsoft.com/download/8/b/b/8bbb8891-e88d-4739-b92a-2d1d2fffcb79/Intrastatformat.xml)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
