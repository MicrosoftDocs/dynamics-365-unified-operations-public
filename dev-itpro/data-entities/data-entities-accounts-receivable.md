---
# required metadata

title: Data entities - Accounts receivable
description: This article provides a list of the data entities that are available for the Accounts receivable functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 20 - 17
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
ms.custom: 96163
ms.assetid: f4b759dc-3000-4bc5-b778-36ad49335337
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Accounts receivable

This article provides a list of the data entities that are available for the Accounts receivable functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

**Note:** If you're implementing Accounts receivable, but you aren't using Accounts payable, use the **10.1.001 AP and AR Shared setup** package. For information about this package, see [Data entities: Accounts payable and taxes](data-entities-accounts-payable-taxes.md).

**11.1.001 AR – Customer payment setup**

| Suggested sequence | Entity name                           | Area                | Entity type | Dependency              | Comments                                                                                                                                                    |
|--------------------|---------------------------------------|---------------------|-------------|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1                  | Customer payment method               | Accounts receivable | Setup       | None                    | Use to create and maintain information about methods of payment for customers.                                                                              |
| 2                  | Customer payment method specification | Accounts receivable | Setup       | Customer payment method | Create and view payment specification codes for the selected method of payment.                                                                             |
| 3                  | Customer payment fee                  | Accounts receivable | Setup       | None                    | Use to set up payment fees for various combinations of banks, methods of payment, remittance types, payment specifications, currencies, and date intervals. |

**11.1.002 AR – Customer attributes**

| Suggested sequence | Entity name                    | Area                | Entity type | Dependency        | Comments                                                                                                          |
|--------------------|--------------------------------|---------------------|-------------|-------------------|-------------------------------------------------------------------------------------------------------------------|
| 4                  | Statistics group               | Sales and marketing | Setup       | None              | Use to create and manage customer statistics groups.                                                              |
| 5                  | Business segments              | Sales and marketing | Setup       | None              | Use to set up and maintain a list of general business segments that you can use to categorize prospects.          |
| 6                  | Business subsegments           | Sales and marketing | Setup       | Business segments | Use to set up a list of precise types, or subsegments, for each business segment.                                 |
| 7                  | Price customer groups          | Accounts receivable | Setup       | None              | Create price groups for groups of customers that should be handled in a similar way with regard to price.         |
| 8                  | Modes of delivery              | Accounts receivable | Setup       | None              | Use to set up modes of delivery for customers and vendors.                                                        |
| 9                  | Sales districts                | Sales and marketing | Setup       | None              | Use to set up and maintain a list of relevant geographical areas that you can use for sales and sales statistics. |
| 10                 | Sales order pools              | Sales and marketing | Setup       | None              | Use to create and maintain pools for sales orders.                                                                |
| 11                 | Total discount customer groups | Accounts receivable | Setup       | None              | Define price groups that can be used to specify a set of prices that should be applied to a group of customers.   |
| 12                 | Line discount customer groups  | Accounts receivable | Setup       | None              | Define customer total discount groups that can be used on trade agreements.                                       |
| 13                 | Customer charge groups         | Accounts receivable | Setup       | None              | Define customer line discount groups that can be used on trade agreements.                                        |

**11.1.003 AR – Customers**

| Suggested sequence | Entity name     | Area                | Entity type | Dependency      | Comments                                                                 |
|--------------------|-----------------|---------------------|-------------|-----------------|--------------------------------------------------------------------------|
| 14                 | Customer groups | Accounts receivable | Master      | None            | Use to create and maintain groups of customers who share key parameters. |
| 15                 | Customers       | Accounts receivable | Master      | Customer groups | Use to create and maintain your organization’s customer records.         |

**11.1.004 AR – Accounts receivable parameters**

| Suggested sequence | Entity name              | Area                | Entity type | Dependency               | Comments                                                                                            |
|--------------------|--------------------------|---------------------|-------------|--------------------------|-----------------------------------------------------------------------------------------------------|
| 16                 | Customer posting profile | Accounts receivable | Setup       | None                     | Use to set up the profiles that control the posting of customer transactions to the general ledger. |
| 17                 | Customer ledger accounts | Accounts receivable | Setup       | None                     | Define ledger accounts that can be used for ledger updates.                                         |
| 18                 | Customer parameters      | Accounts receivable | Setup       | Customer posting profile | Use to set up parameters for Accounts receivable.                                                   |
| 19                 | Printed form notes       | Accounts receivable | Setup       | None                     | Use to define form note parameters for invoices, project quotations, and packing slips.             |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)

