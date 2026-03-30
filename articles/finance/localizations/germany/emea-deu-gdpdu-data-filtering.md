---
title: Add filters to an audit file configuration
description: Learn how to add a data filter in the German audit file, including a step-by-step process for adding the possibility of filtering data in reports.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.search.region: Austria, Germany
ms.search.form: ERWorkspace
---

# Add filters to an audit file configuration

[!include [banner](../../includes/banner.md)]

This article explains how to add a filter for data in the German audit file. For example, you can add a filter for the **Posting layer** field in the **General journal entry** table.

As explained in [German audit file (GDPdU/GoBD) overview](emea-deu-gdpdu-audit-data-export.md#sachkontobuchungen- -general-ledger-accounts-), the **SPEZIALBUCHUNG** (Posting layer) field of **Sachkontobuchungen** data set comes from the **$GeneralJournalEntry/PostingLayer** electronic reporting data source path. To add the possibility of filtering data in the report by the **SPEZIALBUCHUNG** (Posting layer) field, complete the following steps:

1. Go to **Workspaces** > **Electronic reporting**, and then select **Reporting configurations**.
2. In the configuration tree, select the **Data export model** configuration, and derive it by creating a format that your company uses.
3. Select the derived configuration, and on the Action Pane, select **Designer**. 
4. On the **Data model** page, on the Action Pane, select **Map model to datasource**.
5. On the **Model to datasource mapping** page, select the **Group** definition. On the Action Pane, select **Designer**, and then search for the **$GeneralJournalEntry** data source in the **Data sources** section on the **Model mapping design** page.

  The **$GeneralJournalEntry** data source is a calculated record list that sources data from the **GeneralJournalEntry** table (you can see this data source from the formula for **$GeneralJournalEntry**).
  
1. In the **Data sources** section on the **Model mapping design** page, search for **GeneralJournalEntry** and select this table.
1. In the **Data sources** section, select **Edit** and then select the **Ask for query** check box for the **GeneralJournalEntry** table. Select **OK**.

:::image type="content" source="../media/ask-for-query-gl-entries.png" alt-text="Screenshot of the Ask for query check box selected for the General ledger entries table.":::

1. Save, close, and complete the configuration.
1. Unmark the **Default for model mapping** parameter for the parent configuration, **Data export model**, if it's marked. Select your derived configuration as **Default for model mapping**.  

When you make this change and run **Data export** periodic tasks, you see **Records to include** on the FastTab in the dialog box for the report for the **General journal entry** table. Select **Filter** to specify conditions for general ledger entries filtering.

:::image type="content" source="../media/filter-setup.png" alt-text="Screenshot of filtering conditions setup on Data export periodic tasks.":::

To filter by the **Posting layer** field in the **General journal entry** table, select **Posting layer** in the **Field** column, and then select the necessary posting layer in the **Criteria** column.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]