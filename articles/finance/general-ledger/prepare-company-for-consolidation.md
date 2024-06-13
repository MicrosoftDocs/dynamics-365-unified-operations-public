---
title: Prepare a legal entity for the consolidation process
description: During a consolidation, you gather transactions from several sets of legal entity accounts into a single set of legal entity accounts.
author: jinniew
ms.author: jiwo
ms.topic: article
ms.date: 10/30/2020
ms.custom:
ms.reviewer: kfend 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-10-30
ms.search.form: 
ms.dyn365.ops.version: 8.0.1
---

# Prepare a legal entity for the consolidation process

[!include [banner](../includes/banner.md)]

During a consolidation, you gather transactions from several sets of legal entity accounts into a single set of legal entity accounts. This article explains how to prepare a legal entity for a consolidation.

> [!NOTE]
> We recommend that you use Management Reporter for Microsoft Dynamics 365 Finance to combine the financial results for multiple legal entities in a consolidated format. Management Reporter lets you create consolidated financial reports across legal entities, use Excel to import consolidation data from other sources, and translate amounts into any number of reporting currencies without having to run the consolidation process in Dynamics 365 Finance.

You can print reports, such as financial statements, from the consolidated legal entity. However, you can't use the consolidated legal entity for daily transactions.

You can consolidate data from legal entities that use different databases than the consolidated legal entity. This consolidation process is referred to as an *import consolidation*. Alternatively, the legal entities can use the same database as the consolidated legal entity. This consolidation process is referred to as an *online consolidation*.

The consolidated legal entity collects the results and balances of the subsidiaries. To prepare a consolidated legal entity for a consolidation, follow these steps.

1. Go to **Organization administration \> Organizations \> Legal entities**.
2. Select **New** to create the legal entity that will be the consolidated legal entity.
3. Select the **Use for financial consolidation process** check box, and then enter information about the consolidated legal entity. Be sure to enter this information exactly as you want it to appear on financial statements for the consolidated legal entity.
4. Close the page.
5. Select the consolidated legal entity in the field in the upper-right corner of the page, and then select **OK**.
6. Go to **General ledger \> Setup \> Ledger**.
7. Select the chart of accounts, the fiscal calendar, the accounting currency, an optional reporting currency, and the default type of exchange rate for the consolidated legal entity. 
8. Go to **General ledger \> Setup \> Currency \> Currency exchange rates**.
9. Set up currency exchange rates in relevant periods for the currencies of the subsidiary legal entities.
10. Close the page.
11. If the consolidated legal entity has subsidiaries that use foreign currencies, follow these steps:

    1. Go to **General ledger \> Setup \> Posting \> Accounts for automatic transactions**.
    2. In the **Posting type** field, select an appropriate account:

        - If the legal entity has foreign subsidiaries that are financially or operationally interdependent with the parent legal entity, select an appropriate account for the **Profit and loss account for consolidation differences** posting type.
        - If you're consolidating a subsidiary that is financially and operationally independent of the parent legal entity, or a legal entity that contains the results of several subsidiaries that are financially and operationally independent of the parent legal entity, and if you're using translation methods to consolidate the data, select an appropriate account for the **Balance account for consolidation differences** posting type.

    3. In the **Main account** field, select the main accounts that should be used for foreign currency revaluation adjustments.
    4. Close the page.

    If you create the consolidated legal entity early in a period, you can revalue foreign currency amounts as exchange rates change during the consolidation period.

The consolidated legal entity is now set up for the **Consolidate** periodic job. You can do either an import consolidation or an online consolidation.

- To do an import consolidation, go to **General ledger \> Periodic \> Consolidate \> Consolidate \[Import from\]**.
- To do an online consolidation, go to **General ledger \> Periodic \> Consolidate \> Consolidate \[Online\]**.

> [!NOTE]
> Before you can process the consolidation, you must prepare the subsidiary legal entities for consolidation. For more information, see [Set up a subsidiary legal entity for consolidation](set-up-subsidiary-company-for-consolidation.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
