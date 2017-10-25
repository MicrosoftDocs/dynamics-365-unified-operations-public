---
# required metadata

title: Data entities - Bank
description: This article provides a list of the data entities that are available for Bank and cash management.
author: kfend
manager: AnnBe
ms.date: 06/20/2017
ms.topic: reference
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 95863
ms.assetid: 3e2212f7-c34c-4034-a0fa-cbf382eb0c8d
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Bank

[!include[banner](../includes/banner.md)]

This article provides a list of the data entities that are available for Bank and cash management.

Available data entities
-----------------------

**04.1.001 BANK – Bank setup**

| Suggested sequence | Entity name             | Area                | Entity type | Dependency            | Comments                                                                                                                    |
|--------------------|-------------------------|---------------------|-------------|-----------------------|-----------------------------------------------------------------------------------------------------------------------------|
| 1                  | Bank transaction type   | Bank                | Setup       | None                  | Define the types of transactions that are made in company bank accounts, such as deposit slips, fees, and interest charges. |
| 2                  | Bank transaction groups | Bank                | Setup       | Bank transaction type | Define groups of bank transaction types.                                                                                    |
| 3                  | Bank parameters         | Bank                | Setup       | None                  | Define the legal entity’s Cash and bank management parameters.                                                              |
| 4                  | Payment purpose codes   | Bank                | Setup       | None                  | Define payment purpose codes for the central bank, if it’s required.                                                        |
| 5                  | Customer charge groups  | Accounts receivable | Setup       | None                  | Define charges groups for customers or vendors.                                                                             |

**04.1.002 BANK – Bank accounts**

**Note:** To help guarantee a successful import, you might have to unmap some fields or attributes that are set on the bank account. If these fields haven't all been imported yet, you can add the entities to the Bank setup package.

| Suggested sequence | Entity name   | Area | Entity type | Dependency    | Comments                                                                    |
|--------------------|---------------|------|-------------|---------------|-----------------------------------------------------------------------------|
| 6                  | Bank groups   | Bank | Setup       | None          | Define general information about the bank groups that you have accounts in. |
| 7                  | Bank accounts | Bank | Setup       | Bank groups   | Define bank accounts.                                                       |
| 8                  | Check layout  | Bank | Setup       | Bank accounts | Define the layout of checks for the bank accounts.                          |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)



