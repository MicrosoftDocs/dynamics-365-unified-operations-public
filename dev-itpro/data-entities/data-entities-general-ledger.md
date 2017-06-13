---
# required metadata

title: Data entities - General ledger
description: This article provides a list of the data entities that are available for General ledger.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 95893
ms.assetid: 882b1a83-4773-49a0-8dbb-3ac3380d344c
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - General ledger

[!include[banner](../includes/banner.md)]


This article provides a list of the data entities that are available for General ledger.

Available data entities
-----------------------

**03.1.001 GL - Chart of accounts - Shared**

| Suggested sequence | Entity name                            | Area           | Entity type | Dependency                       | Comments                                                                                                                                                                                                          |
|--------------------|----------------------------------------|----------------|-------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1                  | Finacial dimensions                    | General ledger | Setup       | None                             | Define financial dimensions that you can use as account segments for shared charts of accounts.                                                                                                                   |
| 2                  | Dimension attribute activations        | General ledger | Setup       | None                             | Activate the dimensions that will be used in the system. Note: There is a known issue that involves this entity. To work around the issue, set the DoActivate field to Yes for the one record in the source file. |
| 3                  | Financial dimension values             | General ledger | Setup       | Financial dimensions             | Define details for financial dimension values.                                                                                                                                                                    |
| 4                  | Chart of accounts                      | General ledger | Setup       | None                             | Define the organization’s charts of accounts.                                                                                                                                                                     |
| 5                  | Main account                           | General ledger | Setup       | Chart of accounts                | Define main accounts that will be used in the general ledger.                                                                                                                                                     |
| 6                  | Financial dimension format             | General ledger | Setup       | Financial dimensions             | Define the order of dimensions for the dimension formats that data entities use.                                                                                                                                  |
| 7                  | Financial dimension sets               | General ledger | Setup       | Financial dimensions             | Define financial dimension sets that contains either financial dimensions or financial dimension combinations.                                                                                                    |
| 8                  | Financial dimension translations       | General ledger | Setup       | Financial dimensions             |                                                                                                                                                                                                                   |
| 9                  | Financial dimension value translations | General ledger | Setup       | Financial dimension translations |                                                                                                                                                                                                                   |
| 10                 | Consolidation groups and accounts      | General ledger | Setup       | Main accounts                    | Define groups and consolidation accounts that are the main account in the parent legal entity that is used for ledger consolidation.                                                                              |

**03.1.002 GL - Account structures - Shared**

**Recommended setup:** All status fields in source files should have a status of **Draft**, and the two activation files should have **DoActivate** set to **Yes**. This setup will enable the account structures to be imported and activated at import run time. User may also want to include **"Main account categories**" data entitiy for this data package.

| Suggested sequence | Entity name                            | Area           | Entity type | Dependency               | Comments                                                                                                                                                      |
|--------------------|----------------------------------------|----------------|-------------|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 11                 | Advanced rule structures               | General ledger | Setup       | Financial dimensions     | Define advanced rules to provide additional financial dimensions that are part of the account combination, but that aren’t included in the account structure. |
| 12                 | Advanced rule structure allowed values | General ledger | Setup       | Advanced rule structures |                                                                                                                                                               |
| 13                 | Advanced rule structure activation     | General ledger | Setup       | Advanced rule structures | Set the advanced rule structure to Draft or Active status.                                                                                                    |
| 14                 | Account structures                     | General ledger | Setup       | Financial dimensions     | Define account structures that are used to define the valid combinations that, together with the main accounts, form a chart of accounts.                     |
| 15                 | Account structure allowed values       | General ledger | Setup       | Account structures       |                                                                                                                                                               |
| 16                 | Advanced rules                         | General ledger | Setup       | None                     | Define rules for main accounts and financial dimensions.                                                                                                      |
| 17                 | Advanced rule criteria                 | General ledger | Setup       | Advanced rules           |                                                                                                                                                               |
| 18                 | Account structure activation           | General ledger | Setup       | Account structures       | Set the account structure to Draft or Active status.                                                                                                          |

**03.1.003 GL - Fiscal calendar - Shared**

| Suggested sequence | Entity name            | Area           | Entity type | Dependency      | Comments                             |
|--------------------|------------------------|----------------|-------------|-----------------|--------------------------------------|
| 19                 | Fiscal calendar        | General ledger | Setup       | None            | Define fiscal calendars.             |
| 20                 | Fiscal calendar period | General ledger | Setup       | Fiscal calendar | Define periods for fiscal calendars. |

**03.1.004 GL – Ledger setup**

| Suggested sequence | Entity name                                      | Area           | Entity type | Dependency                         | Comments                                                                                                                                                                                                                                                    |
|--------------------|--------------------------------------------------|----------------|-------------|------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 21                 | Ledger                                           | General ledger | Setup       | Chart of accounts, Fiscal calendar | Define ledger values for a legal entity. Note: There is a known issue where account structures aren’t saved in the ledger if a ledger record exists before import. To work around this issue, set the account structures manually on the Ledger setup page. |
| 22                 | Ledger fiscal calendar year                      | General ledger | Setup       | Ledger                             | Define the fiscal calendar to use for the ledger in the legal entity.                                                                                                                                                                                       |
| 23                 | Ledger fiscal calendar period                    | General ledger | Setup       | Ledger fiscal calendar year        | Define the fiscal calendar periods to use for the ledger in the legal entity.                                                                                                                                                                               |
| 24                 | Main account legal entity                        | General ledger | Setup       | Main accounts                      |                                                                                                                                                                                                                                                             |
| 25                 | Financial dimension value legal entity ovrerides | General ledger | Setup       | Main accounts                      |                                                                                                                                                                                                                                                             |
| 26                 | Accounts for automatic transactions              | General ledger | Setup       | Main accounts                      | Define accounts for automatic transactions.                                                                                                                                                                                                                 |
| 27                 | Ledger parameters                                | General ledger | Setup       | None                               | Define parameters for General ledger.                                                                                                                                                                                                                       |

**03.1.005 GL – Ledger Journals**

| Suggested sequence | Entity name          | Area           | Entity type | Dependency | Comments                                                                  |
|--------------------|----------------------|----------------|-------------|------------|---------------------------------------------------------------------------|
| 28                 | Journal names        | General ledger | Setup       | None       | Define journals to be used.  |
| 29                 | Default descriptions | General ledger | Setup       | None       | Define default descriptions for automatic postings to the general ledger. |
| 30                 | Financial reasons    | General ledger | Setup       | None       | Define reason codes.                                                      |
| 31                 | Journal descriptions | General ledger | Setup       | None       | Define descriptions that you can select on journal lines.                 |

**03.1.006 GL – Allocations**

| Suggested sequence | Entity name                        | Area           | Entity type | Dependency              | Comments                                                                           |
|--------------------|------------------------------------|----------------|-------------|-------------------------|------------------------------------------------------------------------------------|
| 32                 | Ledger allocation rule             | General ledger | Setup       | Main accounts           | Define allocation rules that you can use to determine the result of an allocation. |
| 33                 | Ledger allocation basis            | General ledger | Setup       | None                    | Define allocation basis rules.                                                     |
| 34                 | Ledger allocation basis source     | General ledger | Setup       | Ledger allocation basis | Define the allocation basis source.                                                |
| 35                 | Ledger allocation rule destination | General ledger | Setup       | Ledger allocation rule  | Define the destination of the data that will be allocated.                         |
| 36                 | Ledger allocation rule source      | General ledger | Setup       | Ledger allocation rule  | Define the source of the data that will be allocated.                              |

**03.8.001 GL – General journal**

| Suggested sequence | Entity name     | Area           | Entity type   | Dependency    | Comments                         |
|--------------------|-----------------|----------------|---------------|---------------|----------------------------------|
| 37                 | General journal | General ledger | Transactional | Journal names | Create journal header and lines. |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)



