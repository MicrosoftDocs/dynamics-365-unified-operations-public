---
# required metadata

title: Plan your chart of accounts
description: This article provides information that will help you plan the chart of accounts for your organization.
author: RobinARH
manager: AnnBe
ms.date: 2015-12-02 23 - 04 - 17
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: DimensionConfigureAccountStructure, LedgerChartOfAccounts
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 14051
ms.assetid: 10edb129-33f0-4cf9-b2a7-4b7ffa09b229
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Plan your chart of accounts

This article provides information that will help you plan the chart of accounts for your organization.

To track and maintain financial information in an organization, you can set up a chart of accounts. A chart of accounts is a collection of accounts that define a financial framework. To further track the transactions in these accounts, you can add segments, which are known as financial dimensions. For example, an expense account might include financial dimensions that are named Department, Cost center, and Purpose. User-defined rules, which are known as account structures and advanced rules, determine how financial dimensions are attached to the main accounts and other financial dimensions, and also how transactions are entered. The chart of accounts is a structured list of a legal entity’s general ledger accounts. The list is used to prepare financial reports for authorities and owners. The accounts are grouped into types of accounts and then further aggregated into larger categories. At the most general level, the accounts are grouped as revenues and costs (operating accounts), and assets and liabilities (balance accounts). A chart of accounts can be shared and used by any legal entity in an organization. The chart of accounts that is used by a legal entity is defined on the **Ledger** page. Here are some of the factors that you must consider when you plan the structure of the chart of accounts for your organization:

-   The reporting requirements of the country/region where your organization is based
-   The reporting requirements of your legal entity
-   The degree of specification that is required, both for both external organizations and for your organization

Create the chart of accounts on the **Chart of accounts** page. Main accounts can be created from the **Chart of accounts** page or the **Main accounts** page. Your main accounts shouldn't use any special characters that are used as chart of accounts delimiters. If you do have a special character that is the same as your chart of accounts delimiter, you may experience instability, or the need to always use lookups or the flyout when entering account and dimension combinations. It's a good idea to link the main accounts to main account categories, so that you can take advantage of the default financial reports without having to make any modifications. Therefore, you can more quickly and easily design and maintain reports. Use the **Configure account structures** page to create account structures. Account structures define valid combinations. The combinations, together with main accounts, form a chart of accounts. **Legal entity overrides** Not all main accounts are valid for all legal entities and some may only be relevant for a specific time period. In this scenario the Legal entity overrides section can be used to identify which companies the main account should be suspended for, who the owner is and the time period the dimension is active. The overrides at the shared level cannot be more restrictive than the overrides at the legal entity level.

See also
--------

[Financial dimensions](financial-dimensions.md)

