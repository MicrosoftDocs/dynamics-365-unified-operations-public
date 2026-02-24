---
title: Design configurations to generate documents that have application data
description: This article describes how to design Electronic reporting (ER) configurations to generate an electronic document. (Part 1 - Import configurations).
author: kfend
ms.date: 02/24/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Design configurations to generate documents that have application data

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, [Import configurations to generate documents that have application data](er-generate-documents-application-data-update-part-1-import-configurations.md).

The steps in this procedure explain how to design Electronic reporting (ER) configurations to generate an electronic document. In this procedure, you run the ER imported format configuration that you created for the sample company, Litware, Inc. to generate electronic documents.

This procedure is created for users with the assigned role of system administrator or electronic reporting developer. You can complete these steps by using the DEMF dataset.

Before you begin, change the country/region context for the DEMF company from DEU (Germany) to BEL (Belgium). Select **Organization administration** > **Organizations** > **Legal entities** to update the country/region code in the primary address of the legal entity DEMF. Restart your application.


## Run imported ER format

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Intrastat (model)**.
1. In the tree, select **Intrastat (model)\Intrastat (format)**.
1. Select **Run**.
    * Run the draft version of the ER format configuration to generate the Intrastat report.  
1. In the **Enter file name** field, type `intrastat.xml`.
    * Specify the name of the file.  
1. Select **OK**.
    * Review the generated XML file.  
1. Close the page.
1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.
    * Open this form to view the Intrastat transactions that are included in the generated electronic document.  
1. Select **Intrastat archive**.
    * Because the executed ER format doesn't contain any settings for application data update, the details of the completed Intrastat report aren't archived.  
1. Close the page.
1. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
