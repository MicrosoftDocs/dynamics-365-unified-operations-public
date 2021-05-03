---
# required metadata

title: Prepare your environment to generate the FEC
description: This topic explains how to prepare your Dynamics 365 Finance environment to generate the FEC.
author: liza-golub
ms.date: 05/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.author: elgolu
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: France

---

# Prepare your environment to generate the FEC

Before you can generate an FEC audit file, you must import the latest versions of the Electronic reporting (ER) configurations listed in the following table.

| **ER configuration**     | **Type**      | **Description**                                                                               |
|--------------------------|---------------|-----------------------------------------------------------------------------------------------|
| Data export model        | Model         | Unified data model for data exporting.                                                        |
| French FEC model mapping | Model mapping | Configuration that collects data from different data sources to prepare it for FEC reporting. |
| FEC audit file (FR)      | Format        | Exporting format in the structure of FEC.                                                     |

> [!NOTE]
> After you import all of the ER configurations in the table, on the **Configurations** page, set the **Default for model mapping** option to **Yes** for the **French FEC model
mapping** configuration.

For more information about how to download ER configurations from the Microsoft global repository, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

To use the **FEC audit file (FR)** format, define the ER configuration name in a new General ledger parameter. 

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. Expand the **Electronic reporting** FastTab, and then select the **Ledger** tab.
3. In the **Ledger transactions export** group, in the **Ledger transactions export** field, select the format **FEC audit file (FR)**.
4. Save the new setting.
