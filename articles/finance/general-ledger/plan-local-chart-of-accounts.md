---
# required metadata

title: Plan your local chart of accounts
description: This topic provides information that will help you plan the chart of accounts when you have requirements for statutory/local requirements for your organization.
author: veneva
ms.date: 10/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DimensionConfigureAccountStructure, LedgerChartOfAccounts, LedgerConsolidateAccountGroup, MainAccountConsolidateAccount, DimensionDetails, MainAccountDetails
ROBOTS: 
audience: Application User
ms.devlang: 
ms.reviewer: roschlom
ms.tgt_pltfrm: 
ms.custom: 14051
ms.assetid: 10edb129-33f0-4cf9-b2a7-4b7ffa09b229
ms.search.region: Global
ms.search.industry: 
ms.author: veneva
ms.search.validFrom: 10/07/2021
ms.dyn365.ops.version: AX 7.0.0

---

# Plan your local chart of accounts

[!include [banner](../includes/banner.md)]

This topic provides information that will help you plan the chart of accounts when your organization includes legal entities that must meet requirements for specific localities that they do business in. For the purpose of this article, we will use the following terms.

- Global – refers to the chart of accounts that's used by the organization globally and in most cases is the one that you would consolidate to.

- Local – refers the chart of accounts used by legal entities in a specific country for the reasons listed below.

- Shared – refers the ability to use the same COA in more than one legal entity. Both the global and the local COA can be shared.

You can create and share multiple chart of accounts. A shared chart of accounts means that the same chart of accounts can be used by more than one legal entity, but each legal entity can only be assigned one chart of accounts. The chart of accounts used by a legal entity is defined on the **Ledger** page. 

When designing the chart of accounts, many organizations aim for a global one. The shared chart of accounts capability allows for creation of a global chart of accounts. There are benefits to creating and using a single one, which include making governance and control, maintenance, and reporting easier.

While a global chart of accounts is preferred by most organizations and is the easiest to implement, some legal entities require a local chart of accounts. Some scenarios that require a local chart of accounts include the following:

- Local statutory requirements

- Local accounting standards requirements

- Industry requirements

- Company-specific reporting and analysis requirements

When your organization requires a legal entity to use a local chart of accounts, two options are available for implementing it.

1. Assign the global chart of accounts and define other means for the local requirements.

2. Assign the local chart of accounts to the legal entity and define relations to the global chart of accounts.

Deciding which approach to use can be determined by the organization structure and the reporting structure.

If a global chart of accounts is assigned to the legal entity, the options to meet local reporting requirements are as follows:

- Local consolidation

- Financial dimension to track local chart of accounts

- Create local main accounts within the global chart of accounts

- External mapping to local chart of accounts

If a local chart of accounts is assigned to the legal entity, only one option is available at this time for meeting global reporting requirements, which is Global consolidation.

## Global chart of accounts assigned to legal entity

When you need to assign a global chart of accounts to a legal entity, there are four options available for configuring the system. In each of option, a single chart of accounts is configured and linked to each legal entity on the **Ledger** page. Each option then uses a different approach to meet the localization requirements. The following sections outline the high-level steps to configure the system for the localization requirements along with the advantages and disadvantages of each option.

## Local consolidation

The local consolidation option is the recommended approach for meeting local chart of account requirements and leveraging the functionality in the system that was designed for this purpose.

### Set up consolidation for a local chart of accounts 

1. Create a single global chart of accounts with all the required main accounts.

2. Assign the global chart of accounts on the **Ledger** page in each legal entity.

3. Create a consolidation legal entity for each localization required.

4. If only one localization is required, configure the **Consolidation account** on the **Main account** page or use **Consolidation groups** and **Additional consolidation accounts**.

5. If you need more than one localization, or if both the account number and account name require translation, use **Consolidation groups** and **Additional consolidation accounts** to represent the localization requirements.

6. Run the consolidation process to transform the value from the source legal entity using the global chart of accounts to the consolidation company using the local chart of accounts.

### Advantages

- Consistent way of working across the organization

- One translation of the local position

- Support translation of both the main account ID and the name of each main account

- Supports multiple localizations

### Disadvantages

-   Additional consolidation company creation

-   Additional consolidation process

-   Can only report on the localized chart after the consolidation process is complete

## Financial dimension for local chart of accounts

The financial dimension for a local chart of accounts approach uses a financial dimension, where the financial dimension values represent the local main accounts that are required for the localization. This approach works well if there is only one localization required, but it becomes less usable as you add more localizations and financial dimensions.

### Set up a financial dimension for a local chart of accounts

1. Create a single global chart of accounts with all the required main accounts.

2. Assign the global chart of accounts on the **Ledger** page in each legal entity.

3. Create a **Financial dimension** to represent the local chart of accounts.

4. Create **Financial dimension values** to represent the main accounts in the local chart of accounts.

5. Update the account structure to include the "local chart of accounts" financial dimension.

6. Ensure the "local chart of accounts" financial dimension is always populated and that it doesn't allow a blank value. Consider using derived dimension or fixed dimensions.

7. Create a financial dimension set with the "local chart of accounts" dimension as the first selected financial dimension. The financial dimension set can be used when generating the trial balance.

### Advantages

- Both Global and Local chart of accounts main accounts exist on the transaction level. Global is the main account and local is the financial dimension value.

- Real-time reporting and view of both global and local finance position.

### Disadvantages

- In General ledger parameters, if the **Values used for summary account** field is set to **Accounting distributions**, the financial dimensions which represent the main account for the expense/asset/revenue will incorrectly be used for the Accounts receivable and Accounts payable summary account. We recommended defining this setting as a source document instead to ensure that the correct financial dimension values are used.

- If many local charts of accounts are required and one financial dimension is used for all of them, the list of financial dimension values that are used could become long and difficult to work with.

- If many local charts of accounts are required and a separate financial dimension is used to represent each one, adding financial dimensions, and financial dimension sets, can have negative effects on the usability and performance of the system.

- We recommend that you carefully consider the number of financial dimensions that you need, the number of values within each one, and the number of financial dimension sets, as this could affect system performance.

## Local main accounts within the global chart of accounts

Following this approach, the local main accounts within the global chart of accounts includes the local chart of accounts main accounts in the global chart of accounts.

### Set up local main accounts within the global chart of accounts

1.  Create a single chart of accounts which includes the main accounts for both the global chart of accounts and the local chart of accounts.

2.  Assign the chart of accounts on the **Ledger** page in each legal entity.

3.  Create **Total accounts** in the chart of accounts to sum up the main accounts that represent the same purpose.

4.  Create **Legal entity overrides** on each local account to prevent transactions from other legal entities that the local account wasn't designed for.

5.  Create **Legal entity overrides** on each global account to prevent transaction from the localization legal entities.

### Advantages

- Real-time view of both Global and Local finance position in specific reports and views in the system, for example a Balance sheet financial report or using the period button on the Total account.

- Saves your having an additional segment in the Ledger account.

### Disadvantages

- Total accounts usage and visibility are limited. For example, total accounts aren't visible on the **Trial balance** list page.

- Maintenance will require additional effort.

- Creating financial reports will require additional manual effort.

## External mapping to local chart of accounts

The adoption of a global chart of accounts assumes that you are managing the mapping and localizations outside of the system. In this approach you simply create a single global chart of accounts in Dynamics 365 Finance and handle the requirements outside of the system.

### Set up external mapping to a local chart of accounts

1. Create a single global chart of accounts with all the required main accounts.

2. Assign the global chart of accounts on the **Ledger** page in each legal entity.

3. Mapping to the local chart of accounts is done outside of Dynamics 365 Finance.

### Advantages

- Unified ways of working across the organization

### Disadvantages

- No local reporting from the system

- Prone to error when creating financial reports

## Local chart of accounts assigned to legal entity

When your organization decides not use a global chart of accounts across legal entities, a separate chart of accounts is created for each unique local chart of accounts. Each legal entity is then linked to their corresponding chart of accounts on the **Ledger** page.

### Global consolidation

With this approach, a consolidation company is used to roll up and combine the balances from each source local company into the combined global chart of accounts within the consolidation company. This requires maintaining a mapping of each local chart of accounts to the global chart of accounts in the consolidation company.

### Set up a global consolidation

1. Create a separate chart of accounts for each legal entity that has a different local chart of accounts. Note that if some legal entities have the same local chart of accounts, only one local chart of accounts is required and it can be shared.

2. Assign the appropriate chart of accounts on the **Ledger** page in each legal entity.

3. Create a chart of accounts for the global chart of accounts for each consolidation company that has a different global chart of accounts (optional).

4. Create a consolidation legal entity for each consolidation level required and assign the appropriate chart of accounts on the **Ledger** page.

5. If there is only one consolidation required, configure the **Consolidation account** on the **Main account** page.

6. If more than one consolidation is required, or if both the account number and account name require translation, use the **Consolidation groups** and **Additional consolidation accounts** pages to represent the global chart of accounts requirements.

7. Run the consolidation process to transfer the balances from the local legal entities to the consolidated legal entity, which uses the consolidation accounts defined in steps 5 or 6.

### Advantages

- Local accounting standards format applies natively

- Easier way of working for the local finance team

### Disadvantages

- No real-time view of the global position

- Consolidation process might be run more frequently

For more information, see the following topics:

- [Plan your chart of accounts](plan-chart-of-accounts.md)

- [Configure ledgers](configure-ledger.md)

- [Financial dimensions and posting](Default-dimensions.md#balancing-dimension)

- [Financial dimension sets](financial-dimension-sets.md)

- [Consolidation and elimination overview](../budgeting/consolidation-elimination-overview.md)

- [Consolidation account groups and additional consolidation accounts](../budgeting/consolidation-account-groups-consolidation-accounts.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
