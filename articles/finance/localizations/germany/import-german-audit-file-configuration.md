--- 
title: Prepare your environment to generate a GDPdU audit file.
description: Learn how to prepare your environment to generate a GDPdU audit file in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 12/03/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Germany
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERSolutionRepositoryTable, ERSolutionImport
---

# Prepare your environment to generate a GDPdU audit file

[!include [banner](../../includes/banner.md)]

This article explains how to prepare your environment to generate a GDPdU audit file in Microsoft Dynamics 365 Finance.

Before you can generate a GDPdU audit file, you must import the latest versions of the following Electronic reporting (ER) configurations.

| ER configuration         | Type          | Description |
|--------------------------|---------------|-------------|
| Data export model        | Model         | The unified data model for data export. This model also contains the **German audit file - default groups** model mapping component necessary to collect data for German audit file. |
| German audit file output | Format        | The exporting format in the GDPdU audit file structure. |

> [!NOTE]
> After you import all the ER configurations in the previous table, on the **Configurations** page, set the **Default for model mapping** option to **Yes** for the **Data export model** configuration.

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
