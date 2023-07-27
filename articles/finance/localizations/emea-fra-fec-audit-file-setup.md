---
title: Prepare your environment to generate an FEC
description: This article explains how to prepare your Microsoft Dynamics 365 Finance environment to generate a Fichier des écritures comptables (FEC) audit file.
author: liza-golub
ms.date: 07/27/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: France
ms.author: egolub
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

> [!NOTE]
> If you introduce a customization to the FEC ER configurations, and you don't use the **Ledger transactions export** field on the **General ledger parameters** page to predefine the format that must be used to generate FEC, we recommend that you use the *derive* function to create a customized ER format from the **FEC audit file (FR)** format in the **Electronic reporting** workspace. In this way, the new custom format will be a child configuration of **FEC audit file (FR)**. For more information about how to create a custom format, see [Create a custom format](../../fin-ops-core/dev-itpro/analytics/er-quick-start2-customize-report.md).

## Prepare your environment to generate a Missing numbers justification annex of FEC

As of Finance version 10.0.33, you can set up specific number sequences to generate the [Missing numbers justification annex](emea-fra-fec-audit-file-structure.md#missing-numbers-justification) of FEC. 

1. In the **Feature management** workspace, on the **All** tab, find and select the feature **(France) Number sequences setup for FEC Missing numbers justification**, and then select **Enable now**.

This feature allows you to specify number sequences on the **Number sequences setup for FEC Missing numbers justification** FastTab of the **Ledger** tab on the **General ledger parameters** page. The number sequences are analyzed when the **FEC Missing numbers justification** report is generated. Prefix segment information of different number sequences must not intersect. When this feature isn't enabled, the **FEC Missing numbers justification** report analyzes all the possible number sequences used for vouchers numbering with the assumption that the prefix segment information of the number sequences is composed of alphabetic characters and doesn't include numbers. Use this feature to generate the **FEC Missing numbers justification** report for specific number sequences or if there are numerical symbols in prefix segments information of the number sequences used for vouchers numbering.

2. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
3. On the **Number sequences setup for FEC Missing numbers justification** FastTab of the **Ledger** tab, specify the number sequences to be analyzed when the **FEC Missing numbers justification** report is generated.

> [!NOTE]
> We recommend using number sequences that have different formats with alphanumeric segments that contain incrementing numbers without incrementing letters and with a total value of alphanumeric segments less than 9,223,372,036,854,775,808 (int64). Setting up identical formats for different number sequences or not fulfilling the mentioned recommendation to Alphanumeric segment might prevent you from being able to generate the [Missing numbers justification annex](emea-fra-fec-audit-file-structure.md#missing-numbers-justification) of FEC.  
