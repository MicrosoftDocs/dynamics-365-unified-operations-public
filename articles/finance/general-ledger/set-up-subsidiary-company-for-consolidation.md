---
title: Set up a subsidiary legal entity for consolidation
description: Learn how to work with charts of accounts for consolidation companies, including an outline on map subsidiary main accounts to consolidated main accounts.
author: jinniew
ms.author: jiwo
ms.topic: article
ms.date: 10/30/2020
ms.custom:
ms.reviewer: kfend 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-31
ms.search.form: 
ms.dyn365.ops.version: 8.0.1
---

# Set up a subsidiary legal entity for consolidation

[!include [banner](../includes/banner.md)]

The method that you use to prepare subsidiary accounts for consolidation depends in part on the extent to which the structure of the chart of accounts in the subsidiary legal entity reflects the chart of accounts in the consolidated legal entity.

Before you start a consolidation as part of period-end closing, complete the preparatory activities for the period-end closing, but don't close the subsidiary accounts until the consolidation is completed. For more information about period-end closing, see [Close the general ledger at period end](close-general-ledger-at-period-end.md) and [Close the fiscal year](tasks/close-fiscal-year.md).

> [!NOTE]
>  We recommend that you use Management Reporter for Microsoft Dynamics 365 Finance to combine the financial results for multiple legal entities in a consolidated format. Management Reporter lets you create consolidated financial reports across legal entities, use Excel to import consolidation data from other sources, and translate amounts into any number of reporting currencies without having to run the consolidation process in Dynamics 365 Finance.

## Map subsidiary main accounts to consolidated main accounts

If the chart of accounts in the subsidiary legal entity doesn't follow the chart of accounts in the consolidated legal entity, you can map the main accounts in the subsidiary to the main accounts in the consolidated legal entity.

1. In the *subsidiary legal entity*, go to **General ledger \> Setup** \> **Chart of accounts \> Chart of accounts**.
2. Select a chart of accounts. On the **Main accounts** FastTab, select a main account, and then select **Edit**.
3. Select each subsidiary main account that must be mapped to a consolidated main account. On the **General** FastTab, in the **Consolidation account** field, enter the account in the consolidated legal entity that the balance or transactions of the selected subsidiary main account must be transferred to. You can enter the same consolidated main account for several subsidiary accounts.

    > [!NOTE]
    > If the main account types of the subsidiary accounts that are mapped differ from the main account types of the accounts in the consolidated legal entity, the values of accounts that have a main account type of **Total** are overwritten during consolidation.

4. Prepare reports and financial statements for the consolidated legal entity that are based on financial dimensions. Follow these steps to map the financial dimensions that are used in the subsidiary accounts to the financial dimensions in the consolidated legal entity:

    1. In the *subsidiary legal entity*, go to **General ledger \> Setup \> Financial dimensions \> Financial dimensions**, select a financial dimension, and then select **Financial dimension values**.
    2. Select the financial dimension value to map to a different financial dimension value in the consolidated legal entity.
    3. On the **General** FastTab, in the **Group dimension** field, enter the financial dimension in the consolidated legal entity. During consolidation, this financial dimension will be assigned to transactions and balances that use the selected financial dimension in the subsidiary legal entity. The financial dimensions that you enter here must be used in the consolidated legal entity. You can assign the financial dimension that is used as the group financial dimension to several subsidiary financial dimensions.

5. If you're doing an online consolidation, follow these steps to ensure that the transfers occur as you intend:

    1. In the *consolidated legal entity*, go to **General ledger \> Periodic \> Consolidate \> Consolidate \[Export to\]** to open the **Consolidate \[Online\]** page.
    2. On the **Criteria** tab, select the **Use consolidation account** check box.
    3. On the **Financial dimensions** tab, select the appropriate financial dimensions.
    4. For each financial dimension that you select, enter a number in the **Segment order** field to indicate the order that the dimensions should appear in.

## Maintain the same chart of accounts in the subsidiary and consolidated legal entities

The main accounts in the subsidiary legal entity might have the same account numbers and the same structure for the chart of accounts as the main accounts in the consolidated legal entity. In this case, you don't have to manually map the main accounts in the subsidiary to the main accounts in the consolidated legal entity.

Before you start the consolidation, follow these steps.

1. In the *consolidated legal entity*, go to **General ledger \> Periodic \> Consolidate \> Consolidate \[Export to\]** to open the **Consolidate \[Online\]** page.
2. Select the **Use consolidation account** check box. During consolidation, transactions and balances will automatically be transferred to the correct account.

> [!NOTE]
> If the accounts don't correspond, the consolidation stops, and you receive a message.

## Create a chart of accounts for the consolidated legal entity, based on an existing chart of accounts

You can do a consolidation even if a chart of accounts hasn't already been created in the consolidated legal entity.

- If you've planned the account structure that you want to use in the consolidated legal entity, you can map the subsidiary accounts to this structure.
- If you don't map any subsidiary accounts, the accounts in the consolidated legal entity are automatically created when subsidiary data is transferred to the consolidated legal entity. These accounts are based on the main account. Subsequent data is accumulated in accounts in the consolidated legal entity that have the same account number as the subsidiary accounts.

Regardless of whether you've mapped accounts, clear the **Use consolidation account** check box on the **Consolidate** page in the consolidated legal entity before you run this type of consolidation.

> [!NOTE]
> You can use this method to create a chart of accounts in the consolidated legal entity from the chart of accounts in one of the subsidiary legal entities. (For more information, see [Consolidation account groups and additional consolidation accounts](../budgeting/consolidation-account-groups-consolidation-accounts.md).) Then assign an appropriate consolidation conversion principle to each consolidated main account, and run the consolidation for all the subsidiary legal entities.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
