---
title: Plan your chart of accounts
description: Learn how to plan the chart of accounts for your organization, which include a structured list of a legal entity's general ledger accounts.
author: aprilolson
ms.author: aolson
ms.topic: article
ms.date: 05/20/2025
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

This article provides information to help you plan the chart of accounts for your organization.

To track and maintain financial information in an organization, set up a chart of accounts. A chart of accounts is a collection of accounts that define a financial framework. To further track the transactions in these accounts, add segments. These segments are known as financial dimensions. For example, an expense account might include financial dimensions that are named Department, Cost center, and Purpose. User-defined rules determine how financial dimensions are attached to the main accounts and to other financial dimensions, and also how transactions are entered. These user-defined rules are known as account structures and advanced rules.

The chart of accounts is a structured list of a legal entity's general ledger accounts. Use the list to prepare financial reports for authorities and owners. First, group the accounts into types of accounts and then further aggregate them into larger categories. At the most general level, group the accounts as revenues and costs (operating accounts), and assets and liabilities (balance accounts).

Any legal entity in an organization can share and use a chart of accounts. Define the chart of accounts that a legal entity uses on the **Ledger** page.

Consider these factors when you plan the structure of the chart of accounts for your organization:

- The reporting requirements of the country or region where your organization is based
- The reporting requirements of your legal entity
- The degree of specification that is required, both for both external organizations and for your organization

Create the chart of accounts on the **Chart of accounts** page. You can create main accounts from the **Chart of accounts** page or the **Main accounts** page. Don't use any special characters in your main accounts that are used as delimiters for chart of accounts. Otherwise, you might experience instability, or you might always have to use lookups or the dialog box when you enter combinations of accounts and dimensions. For more information, see [Create a main account](tasks/create-main-account.md).

## Change the segment delimiter

If you need to change the delimiter that separates segments in your chart of accounts, go to **General Ledger** > **Ledger setup** > **General ledger parameters** > **Chart of accounts and dimensions** > **Change delimiter**.

### What prevents a delimiter change

You can't change the delimiter if existing dimension values already contain the new delimiter character. For example, if you want to change your delimiter to "~" but you already have a dimension value in use such as "Cust~1", the system blocks the change. In this case, consider selecting a different delimiter.

### Best practices for delimiters and dimension values

While it's technically possible to include delimiter characters within dimension values, doing so can cause problems when the system parses account combinations. For instance, if you have a dimension value "Cust-049" and your delimiter is "-", the system might interpret "049" as the value for the next segment. If "049" isn't a valid value for that segment, you receive an error message.

To avoid these problems, use one of the following options:

- **Option 1 (Recommended)**: Don't use the delimiter character in your dimension values. If conflicting dimension values already exist, change them to prevent misinterpretation.
- **Option 2**: Change the segment delimiter to a different character. This option isn't available for financial tags.

Link the main accounts to main account categories so you can take advantage of the default financial reports without making any modifications. You can more quickly and easily design and maintain reports.

You create account structures on the **Configure account structures** page. Account structures define valid combinations. These combinations, together with main accounts, form a chart of accounts. For more information, see [Create account structures](tasks/create-account-structures.md).

**Legal entity overrides**

Not all main accounts are valid for all legal entities, and some main accounts might be relevant only for a specific period. In this scenario, use the **Legal entity overrides** section to identify the companies that the main account should be suspended for, the owner, and the period when the dimension is active. The overrides at the shared level can't be more restrictive than the overrides at the legal entity level.

For more information, see the following topics:

- [Financial dimensions](financial-dimensions.md)
- [Create and assign advanced rule structures](tasks/create-assign-advanced-rule-structures.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
