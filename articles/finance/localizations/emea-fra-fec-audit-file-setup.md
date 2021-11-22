---
# required metadata

title: Prepare your environment to generate an FEC
description: This topic explains how to prepare your Microsoft Dynamics 365 Finance environment to generate a Fichier des écritures comptables (FEC) audit file.
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

# Prepare your environment to generate an FEC

Before you can generate a Fichier des écritures comptables (FEC) audit file, you must import the latest versions of the following Electronic reporting (ER) configurations.

| ER configuration         | Type          | Description |
|--------------------------|---------------|-------------|
| Data export model        | Model         | The unified data model for data export. |
| French FEC model mapping | Model mapping | The configuration that collects data from different data sources to prepare it for FEC reporting. |
| FEC audit file (FR)      | Format        | The exporting format in the FEC structure. |

> [!NOTE]
> After you import all the ER configurations in the previous table, on the **Configurations** page, set the **Default for model mapping** option to **Yes** for the **French FEC model mapping** configuration.

For more information about how to download ER configurations from the Microsoft global repository, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

Starting in version 10.0.20, to use the **FEC audit file (FR)** format, you must define the ER configuration name in a new General ledger parameter. 

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. On the **Ledger** tab, on the **Electronic reporting** FastTab, in the **Ledger transactions export** section, in the **Ledger transactions export** field, select the **FEC audit file (FR)** format.
3. Save the new setting.
