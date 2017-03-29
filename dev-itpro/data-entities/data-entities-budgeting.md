---
# required metadata

title: Data entities - Budgeting
description: This article provides a list of the data entities that are available for the Budgeting functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 20 - 11
ms.topic: reference
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 96133
ms.assetid: bab5fb63-3e7b-4ddf-bc86-2a25d4a2f52c
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Budgeting

This article provides a list of the data entities that are available for the Budgeting functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

**Important:** Before you import Budgeting data entities, all General ledger data entities and the setup must be imported. For more information about General ledger data entities, see [Data entities: General ledger](data-entities-general-ledger.md).


**12.1.001 BUD – Ledger budget setup**

| Suggested sequence | Entity name                   | Area           | Entity type | Dependency        | Comments                                                                                                                          |
|--------------------|-------------------------------|----------------|-------------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| 1                  | Budget parameters             | Budgeting      | Setup       | None              | Define parameters for Budgeting.                                                                                                  |
| 2                  | Financial reasons             | General ledger | Setup       | None              | A code that users can select to record the reason for a change                                                                    |
| 3                  | Budget codes                  | Budgeting      | Setup       | Financial reasons | Provides an additional level of categorization for budget register entries.                                                       |
| 4                  | Budget models                 | Budgeting      | Setup       | None              | Define a model that is used to describe a budget. The model is also used in budget planning and budget control.                   |
| 5                  | Budget submodels              | Budgeting      | Setup       | None              | Further define a budget model.                                                                                                    |
| 6                  | Budget allocation term        | Budgeting      | Setup       | None              | Defines the financial dimension values and the percentages that are used to generate budget allocations.                          |
| 7                  | Budget cycle time span        | Budgeting      | Setup       | None              | Used to specify the fiscal year or the number of periods in a budget cycle, and to associate budget cycles with fiscal calendars. |
| 8                  | Budget dimensions             | Budgeting      | Setup       | Ledger            | The financial dimensions that are used for budgeting                                                                              |
| 9                  | Budget revenue classification | Budgeting      | Setup       | None              | Used to create or modify the budget revenue details for a payment order.                                                          |

**12.1.002 BUD – Budget control setup**

| Suggested sequence | Entity name                             | Area                        | Entity type | Dependency             | Comments                                                                                                                          |
|--------------------|-----------------------------------------|-----------------------------|-------------|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| 10                 | User groups                             | Organization administration | Setup       | None                   | Create groups of users that can be used in other modules of the system: budget control, workflow, and journal posting permission. |
| 11                 | Budget control configuration            | Budgeting                   | Setup       | None                   | Configures budget control for the ledger of a legal entity.                                                                       |
| 12                 | Budget control dimension attribute      | Budgeting                   | Setup       | None                   | Attributes for the financial dimensions that are used in the budget control configuration                                         |
| 13                 | Budget control over budget permissions  | Budgeting                   | Setup       | User group             | Allows the members of the associated user group to process expenses that fall outside the budget that was entered.                |
| 14                 | Budget control documents and journals   | Budgeting                   | Setup       | None                   | The source documents and accounting journals that are subject to budget control                                                   |
| 15                 | Budget control cycle model              | Budgeting                   | Setup       | Budget cycle time span | The time span that is associated with a budget model for budget checking                                                          |
| 16                 | Budget control rule                     | Budgeting                   | Setup       | None                   | The financial dimension value combinations for budget control                                                                     |
| 17                 | Budget control rule criteria            | Budgeting                   | Setup       | Budget control rule    | The criteria that are used to create the budget control rule                                                                      |
| 18                 | Budget control group                    | Budgeting                   | Setup       | None                   | A collection of financial dimension values for which the budgets will be pooled for a secondary budget check                      |
| 19                 | Budget control group criteria           | Budgeting                   | Setup       | Budget control group   | The criteria that are used create the budget control group                                                                        |
| 20                 | Budget control message level            | Budgeting                   | Setup       | None                   | The levels that are set to receive notification at various stages of the budget control process                                   |
| 21                 | Budget control configuration activation | Budgeting                   | Setup       | None                   | The process that activates the budget control configuration                                                                       |

**12.8.001 Budget – Budget account entries**

| Suggested sequence | Entity name            | Area      | Entity type   | Dependency | Comments                                           |
|--------------------|------------------------|-----------|---------------|------------|----------------------------------------------------|
| 22                 | Budget account entries | Budgeting | Transactional | None       | The entries that are used to establish the budget. |


See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)

