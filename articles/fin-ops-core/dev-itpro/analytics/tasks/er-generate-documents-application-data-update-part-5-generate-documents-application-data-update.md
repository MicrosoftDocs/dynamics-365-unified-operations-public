---
title: Generate documents that have application data
description: Learn how to generate electronic documents with application data updates using Electronic Reporting (ER) configurations.
author: kfend
ms.date: 02/25/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Generate documents that have application data

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, [Modify formats to generate documents that have application data](er-generate-documents-application-data-update-part-4-modify-format.md).

The steps in this procedure explain how to design Electronic reporting (ER) configurations to generate an electronic document and update application data. In this procedure, you execute the ER format configuration to generate the Intrastat report and update application data for archiving details of the reporting process.

This procedure is created for users with the assigned role of system administrator or electronic reporting developer. You can complete these steps by using the DEMF dataset. Before you begin, make sure that the country/region context for the DEMF company is BEL (Belgium).


## Set up foreign trade parameters

1. Go to **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.
1. Select the **Number sequences** tab.

    To archive details of the Intrastat reporting process, you need to identify records of each archive. You must configure a special number sequence for this process.  

1. Select the **Intrastat archive ID** reference.
1. In the **Number sequence code** field, type a value.

    In the **Number sequence code** field, enter or select the value **Fore_2**.  

1. Resolve changes to the Number sequence code.
1. Select **Save**.
1. Close the page.

## Run modified ER format

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Intrastat (model)**.
1. In the tree, select **Intrastat (model)\Intrastat (format)**.
1. Select **Run**.
1. In the **Enter file name** field, type **intrastat2.xml**.
1. Select **OK**.

## Review ER format execution results

Review the generated XML file.  

1. Close the page.
1. Go to **Tax** > **Declarations** > **Foreign trade** > **Intrastat**.

    Open this form containing the Intrastat transactions included in the generated electronic document.    

1. Select **Intrastat archive**.

    Since the executed ER format now contains settings for application data update, the details of the completed Intrastat reporting are archived. In this form, you can see the header record of the created archive.  

1. Select **Details**.

    In this form, you can see the details for the created archive.  

1. Close the page.
1. Close the page.
1. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
