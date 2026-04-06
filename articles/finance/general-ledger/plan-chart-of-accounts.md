---
title: Plan your chart of accounts
description: Learn how to plan the chart of accounts for your organization, which include a structured list of a legal entity's general ledger accounts.
author: aprilolson
ms.author: aolson
ms.topic: article
ms.date: 04/02/2026
ms.update-cycle: 1095-days
ms.custom: evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: DimensionConfigureAccountStructure, LedgerChartOfAccounts
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 10edb129-33f0-4cf9-b2a7-4b7ffa09b229
---

# Plan your chart of accounts

[!include [banner](../includes/banner.md)]

This article helps you plan the chart of accounts for your organization.

Set up a chart of accounts to track and maintain financial information in an organization. A chart of accounts is a collection of accounts that define a financial framework. To further track the transactions in these accounts, add segments. These segments are known as financial dimensions. For example, an expense account might include financial dimensions that are named Department, Cost center, and Purpose. User-defined rules determine how financial dimensions are attached to the main accounts and to other financial dimensions, and also how transactions are entered. These user-defined rules are known as account structures and advanced rules.

The chart of accounts is a structured list of a legal entity's general ledger accounts. Use the list to prepare financial reports for authorities and owners. First, group the accounts into types of accounts and then further aggregate them into larger categories. At the most general level, group the accounts as revenues and costs (operating accounts), and assets and liabilities (balance accounts).

Any legal entity in an organization can share and use a chart of accounts. Define the chart of accounts that a legal entity uses on the **Ledger** page.

Consider these factors when you plan the structure of the chart of accounts for your organization:

- The reporting requirements of the country or region where your organization is based
- The reporting requirements of your legal entity
- The degree of specification that is required, both for external organizations and for your organization

Create the chart of accounts on the **Chart of accounts** page. You can create main accounts from the **Chart of accounts** page or the **Main accounts** page. Link the main accounts to main account categories so you can take advantage of the default financial reports without making any modifications. You can more quickly and easily design and maintain reports. For more information, see [Create a main account](tasks/create-main-account.md).

> [!IMPORTANT]
> Don't use the chart of accounts delimiter character in main account numbers, financial dimension names, or dimension values. For details and best practices, see [Naming requirements](/dynamics365/finance/general-ledger/tasks/define-financial-dimensions#naming-requirements).

You create account structures on the **Configure account structures** page. For more information, see [Create account structures](tasks/create-account-structures.md).

## Change the segment delimiter

If you need to change the delimiter that separates segments in your chart of accounts, go to **General Ledger** > **Ledger setup** > **General ledger parameters** > **Chart of accounts and dimensions** > **Change delimiter**.

### What prevents a delimiter change

You can't change the delimiter if existing dimension values already contain the new delimiter character. For example, if you want to change your delimiter to "~" but you already have a dimension value in use such as "Cust~1", the system blocks the change. In this case, consider selecting a different delimiter.

### What to expect after changing the delimiter

When you change the delimiter, the system schedules a data maintenance action called **Dimension value rename and modify chart of accounts delimiter process**. The delimiter might not update immediately, and the old delimiter might continue to appear until the data maintenance action completes. The system processes the newest dimensions first to reduce the possibility of errors during the transition. Monitor the progress of the action by going to the data maintenance portal in **System administration** > **Setup** > **Data Maintenance**.

> [!IMPORTANT]
> Don't schedule the delimiter change multiple times. If the delimiter isn't updated yet, wait for the data maintenance action to complete before rescheduling.

After the action finishes, the new delimiter appears in the **General ledger parameters** dialog and all dimension data uses the new delimiter consistently.

#### Manual override

If you experience errors when running reports after a delimiter change, or if you see different delimiters in use in the same journal, the standard data maintenance action might still be processing records.

If rescheduling the delimiter **Dimension value rename and modify chart of accounts delimiter process** doesn't fix the issue, you can run the **Dimension value rename and modify chart of accounts delimiter process - manual override** action in the data maintenance portal (**System administration** > **Setup** > **Data Maintenance**). This action processes all remaining records in a single run instead of batching.

> [!WARNING]
> Don't use the manual override as the default option for delimiter changes. The manual override action runs for a longer period and uses more system resources, which can cause performance problems. It only runs to completion if the standard action isn't already running. Consider using this option during off-peak hours.

For more information, see the following topics:

- [Financial dimensions](financial-dimensions.md)
- [Create and assign advanced rule structures](tasks/create-assign-advanced-rule-structures.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
