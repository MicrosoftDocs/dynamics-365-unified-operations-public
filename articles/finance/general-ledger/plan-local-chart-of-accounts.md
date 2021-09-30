---
# required metadata

title: Plan your local chart of accounts
description: This topic provides information that will help you plan the chart of accounts when you have requirements for statutory/local requirements for your organization.
author: veneva
ms.date: 09/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DimensionConfigureAccountStructure, LedgerChartOfAccounts, LedgerConsolidateAccountGroup, MainAccountConsolidateAccount, DimensionDetails, MainAccountDetails
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 14051
ms.assetid: 10edb129-33f0-4cf9-b2a7-4b7ffa09b229
ms.search.region: Global
# ms.search.industry: 
ms.author: veneva
ms.search.validFrom: 09/30/2021
ms.dyn365.ops.version: AX 7.0.0

---

# Plan your local chart of accounts

[!include [banner](../includes/banner.md)]

*For the purpose of this article, we will use:*

-   *Global – as is the Chart of Accounts (CoA) that is used by the organization globally and in most of the cases is the one that you would consolidate to*

-   *Local – as is the CoA used by legal entities in a specific country for the reason listed below*

-   *Shared – as is the ability in D365 Finance to use the same without additional effort in more than one legal entity. Both the global and the local CoA can be shared.*

In Dynamics 365 Finance, multiple Chart of Accounts (CoA) can be created and each one can be shared. A shared CoA means that the same CoA can be used by more than one legal entity, but each legal entity can only be assigned one CoA. The CoA used by a legal entity is defined on the **Ledger** page.

When designing the CoA, many organizations aim for a global CoA. The shared CoA capability allows for creation of a global CoA, including benefits from creating a single CoA to easier governance and control, maintenance, and reporting.

While a global CoA is desired by most organizations and easiest to implement, some legal entities require a local CoA. A few examples of scenarios that require a local CoA include the following:

-   Local statutory requirements

-   Local accounting standards requirements

-   Industry requirements

-   Company specific reporting and analysis requirements

When your organization requires a legal entity to utilize a local CoA, there are two options:

1.  Assign the global CoA and define other means for the local requirements

2.  Assign the local CoA to the legal entity and define relations to the global CoA

Deciding the approach to use can be determined by the organization structure and the reporting structure.

If a global CoA is assigned to the legal entity, the options to meet local reporting requirements are as follows:

-   Local consolidation

-   Financial dimension to track local CoA

-   Create local main accounts within the global CoA

-   External mapping to local CoA

If a local CoA is assigned to the legal entity, the options to meet global reporting requirements are as follows:

-   Global consolidation

# Global CoA assigned to legal entity

When assigning a global CoA to a legal entity, there are four options for configuring the system. In each of the approaches, a single CoA is configured and linked to each legal entity in the **Ledger** page. Each option then uses a different approach to meet the localization requirements. The following section outlines the high-level steps to configure the system for the localization requirements along with the pros and cons of each.

### Local consolidation

The local consolidation option is the recommended approach for meeting local chart of account requirements and leveraging the functionality in Dynamics 365 Finance that was designed for this purpose.

-   How

    1.  Create a single global CoA with all the required main accounts.

    2.  Assign the global CoA on the **Ledger** page in each legal entity.

    3.  Create a consolidation legal entity for each localization required.

    4.  If there is only one localization required:

        -   Configure the **Consolidation account** on the **Main account** page or use **Consolidation groups** and **Additional consolidation accounts**

    5.  If there is more than one localization required or if both the account number and account name require translation:

        -   Use **Consolidation groups** and **Additional consolidation accounts** to represent the localization requirements

    6.  Run consolidation process to transform the value from the source legal entity using the global CoA to the consolidation company using the local CoA(s).

-   Pros

    -   Consistent way of working across the organization

    -   One translation of the local position

    -   Support translation of both the main account ID and the name of each main account

    -   Supports multiple localization

-   Cons

    -   Additional consolidation company creation

    -   Additional consolidation process

    -   Can only report on the localized chart after the consolidation process is complete

### Financial dimension for local CoA

The financial dimension for local CoA approach uses a financial dimension, where the financial dimension values represent the local main accounts that are required for the localization. This approach works well if there is only one localization required and becomes more unusable as you add more localizations and financial dimensions.

-   How

    1.  Create a single global CoA with all the required main accounts.

    2.  Assign the global CoA on the **Ledger** page in each legal entity.

    3.  Create a **Financial dimension** to represent the local CoA.

    4.  Create **Financial dimension values** to represent the main accounts in the local CoA

    5.  Update the account structure to include the "local CoA" financial dimension

    6.  Ensure the "local CoA" financial dimension is always populated and doesn't allow a blank value

        -   Consider using derived dimension or fixed dimensions

    7.  Create a financial dimension set with the 'local CoA' dimension as the first selected financial dimension. The financial dimension set can be used when generating the trial balance.

-   Pros

    -   Both Global and Local CoA main accounts exist on transaction level. Global is the main account and local is the financial dimension value.

    -   Real-time reporting and view of both global and local finance position

-   Cons

    -   In GL parameters, if 'Values used for summary account' is defined as Accounting distributions, the financial dimensions which represent the main account for the expense/asset/revenue will incorrectly be used for the AR and AP summary account. It is recommended to define this setting as Source document instead to ensure the correct financial dimension values.

    -   If many local CoA are required and one financial dimension is used for all: the financial dimension values list could become very big

    -   If many local CoA are required and separate financial dimension is used to represent each: adding financial dimensions, and financial dimension sets, can have negative effects on the usability and performance of the system.

    -   Careful consideration is required on the number of financial dimensions, the number of values within each one, and the number of financial dimension sets, as this could affect the performance

### Local main accounts within the global CoA

The local main accounts within the global CoA approach is that the local CoA main accounts are included in the global CoA.

-   How

    1.  Create a single CoA which includes the main accounts for both the global CoA and the local CoA.

    2.  Assign the CoA on the **Ledger** page in each legal entity.

    3.  Create **Total accounts** in the CoA to sum up the main accounts that represent the same purpose.

    4.  Create **Legal entity overrides** on each local account to prevent transactions from other legal entities that the local account is not designed for.

    5.  Create **Legal entity overrides** on each global account to prevent transaction from the localization legal entities.

-   Pros

    -   Real-time view of both Global and Local finance position in specific reports and views in the system, e.g. Balance sheet financial report or using the period button on the Total account

    -   Saving additional segment in the Ledger account

-   Cons

    -   Total accounts usage and visibility is limited. E.g. Total accounts are not visible on the Trial balance list page

    -   Maintenance would require additional effort

    -   Creating financial reports requires additional manual effort

4.  External mapping to local CoA

The adoption of a global CoA assumes that you are managing the mapping and localizations outside of the system. In this approach you simply create a single global CoA in Dynamics 365 Finance and handle the requirements outside of the system.

-   How

    1.  Create a single global CoA with all the required main accounts.

    2.  Assign the global CoA on the **Ledger** page in each legal entity.

    3.  Mapping to the local CoA is done outside of Dynamics 365 Finance

-   Pros

    -   Unified ways of working across the organization

-   Cons

    -   No local reporting from the system

    -   Prone to error when creating financial reports

## Local CoA assigned to legal entity

When your organization decides to not use a global CoA across your legal entities, a separate CoA is created for each unique local CoA. Each legal entity is then linked to their corresponding CoA on the **Ledger** page.

### Global consolidation

With this approach, a consolidation company is used to roll-up and combine the balances from each source local company into the combined global CoA within the consolidation company. This requires maintaining a mapping of each local CoA to the global CoA in the consolidation company.

-   How

    1.  Create a separate CoA for each legal entity that has a different local CoA. Note that if some legal entities have the same local CoA, only one local CoA is required and can be shared.

    2.  Assign the appropriate CoA on the **Ledger** page in each legal entity.

    3.  Create a CoA for the global CoA for each consolidation company that has a different global CoA. (optional)

    4.  Create a consolidation legal entity for each consolidation level required and assign the appropriate CoA on the **Ledger** page.

    5.  If there is only one consolidation required:

        -   Configure the **Consolidation account** on the **Main account** page

    6.  If there is more than one consolidation required or if both the account number and account name require translation:

        -   Use **Consolidation groups** and **Additional consolidation accounts** to represent the global CoA requirements

    7.  Run the consolidation process to transfer the balances from the local legal entities to the consolidated legal entity, which uses the consolidation accounts defined in steps 5 or 6.

-   Pros

    -   Local accounting standards format applies natively

    -   Easier way of working for the local finance team

-   Cons

    -   No real-time view of the global position

    -   Consolidation process may be run more frequently

For more information, see the following topics:

-   [Plan your chart of accounts](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/plan-chart-of-accounts)

-   [Configure ledgers](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/configure-ledger)

-   [Financial dimensions and posting](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/default-dimensions#balancing-dimension)

-   [Financial dimension sets](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/financial-dimension-sets)

-   [Consolidation and elimination overview](https://docs.microsoft.com/en-us/dynamics365/finance/budgeting/consolidation-elimination-overview)

-   [Consolidation account groups and additional consolidation accounts - Finance \| Dynamics 365 \| Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/finance/budgeting/consolidation-account-groups-consolidation-accounts)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
