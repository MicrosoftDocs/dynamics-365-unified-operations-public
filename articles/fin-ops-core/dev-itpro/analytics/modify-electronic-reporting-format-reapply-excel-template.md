---
title: Modify Electronic reporting formats by reapplying Excel templates
description: This article describes how to modify the Electronic reporting (ER) format that is used to generate business documents by reapplying a modified Excel template.
author: kfend
ms.date: 05/18/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro, Application user
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: e3f7960d-2e01-46a7-9ac8-c355ac933cd6
ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace
---
# Modify Electronic reporting formats by reapplying Excel templates

[!include [banner](../includes/banner.md)]

The Electronic reporting (ER) tool is used to generate business documents in an electronic format. To generate a business document, you must create an ER format, and then use the ER designer to define the layout of the business document and specify the data that should be included in it. You can then run the ER format to generate the business document.

The ER tool can be used to generate business documents as Microsoft Excel files. You can use an Excel document as a template for these documents. To define the document layout in the ER designer, you can import the contents of the Excel document that you want to use as a template into the defined ER format. For more details, and to practice this scenario, play the task guide **ER Design a configuration for generating reports in OPENXML format** (part of the 7.5.4.3 Acquire/Develop IT service/solution components (10677) business process). In the task guide step where you import an Excel template, use the initial template of the Payment Report Excel file, [SampleVendPaymWsReport](https://download.microsoft.com/download/e/6/b/e6bb79f0-cc08-44af-96fa-49c7929d4fb8/SampleVendPaymWsReport.xlsx).

If you edit the Excel document that is used as a template for a business document, new ER functionality lets you reapply the updated template to the ER format. The ER format is then updated so that it adheres to the updated template. For more details about this functionality, play the task guide **ER Modify a format by reapplying an Excel template** (part of the 7.5.5.3 Acquire/Develop IT service/solution components (10683) business process). In the task guide step where you import an updated template, use the modified template of the Payment Report Excel file, [SampleVendPaymWsReport2](https://download.microsoft.com/download/3/1/0/3104d397-c9c5-4227-b68e-f98625313801/SampleVendPaymWsReport2.xlsx).

## Additional resources

[Update a template](er-fillable-excel.md#update-a-template)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
