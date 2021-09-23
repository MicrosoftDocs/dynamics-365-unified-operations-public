---
# required metadata

title: Modify Electronic reporting formats by reapplying Excel templates
description: This topic describes how to modify the Electronic reporting (ER) format that is used to generate business documents by reapplying a modified Excel template. 
author: NickSelin
ms.date: 06/01/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace
# ROBOTS: 
audience: Developer, IT Pro, Application user
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 27621
ms.assetid: e3f7960d-2e01-46a7-9ac8-c355ac933cd6
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---
# Modify Electronic reporting formats by reapplying Excel templates

[!include [banner](../includes/banner.md)]

The Electronic reporting (ER) tool is used to generate business documents in an electronic format. To generate a business document, you must create an ER format, and then use the ER designer to define the layout of the business document and specify the data that should be included in it. You can then run the ER format to generate the business document.

The ER tool can be used to generate business documents as Microsoft Excel files. You can use an Excel document as a template for these documents. To define the document layout in the ER designer, you can import the contents of the Excel document that you want to use as a template into the defined ER format. For more details, and to practice this scenario, play the task guide **ER Design a configuration for generating reports in OPENXML format** (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process).

If you edit the Excel document that is used as a template for a business document, new ER functionality lets you reapply the updated template to the ER format. The ER format is then updated so that it adheres to the updated template. For more details about this functionality, play the task guide **ER Modify a format by reapplying an Excel template** (part of the 7.5.5.3 Acquire/Develop IT service/solution components (10683) business process). In the task guide step where you import an updated template, use the modified template of the Payment Report Excel file, SampleVendPaymWsReport2, as a template.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]