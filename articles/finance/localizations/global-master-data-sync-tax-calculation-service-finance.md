---
# required metadata

title: Synchronize tax setup from the Tax Calculation Service to Dynamics 365 Finance
description: This topic explains how to synchronize tax setup master data from the Tax Calculation Service to Dynamics 365 Finance.
author: wangchen
ms.date: 01/05/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TaxIntegration, TaxServiceParameters
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.21

---


# Synchronize tax setup from the Tax Calculation Service to Dynamics 365 Finance

[!include [banner](../includes/banner.md)]

This topic provides information about how to synchronize tax setup from the Tax Calculation Service to Dynamics 365 Finance.

After you complete the required setup steps in the topic, [Get started with Tax Calculation](global-get-started-with-tax-calculation-service.md), tax setup data will automatically synchronize from the Tax Calculation Service to Finance. The following data is synchronized.

### Sales tax code

|              Finance                | Tax Calculation Service                    |
| ----------------------------------- | ------------------------------------------ |
| Sales tax code                      | Tax code                                   |
| Name                                | Description                                |
| Settlement period                   | User input                                 |
| Ledger posting group                | User input                                 |
| Sales tax currency                  | User input                                 |
| Allow negative sales tax percentage | When there is negative tax rate configured |

### Tax value

|        Finance            | Tax Calculation Service |
| ------------------------- | ----------------------- |
| From date                 | From transaction date   |
| To date                   | To transaction date     |
| Minimum limit             | Minimum amount          |
| Maximum limit             | Maximum amount          |
| Value                     | Tax rate                |
| Non-deductible percentage | Non-deductible rate     |

### Tax limits

|         Finance      | Tax Calculation Service |
| -------------------- | ----------------------- |
| From date            | From transaction date   |
| To date              | To transaction date     |
| Minimum sales tax    | Minimum tax amount      |
| Maximum sales tax    | Maximum tax amount      |

### Sales tax group

|              Finance                       | Tax Calculation Service                              |
| ------------------------------------------ | ---------------------------------------------------- |
| Sales tax group                            | Tax group                                            |
| Sales tax codes under this sales tax group | Tax codes under this tax group                       |
| Exempt                                     | When the tax code is marked as **Is Exempt**         |
| Exempt code                                | When the tax code is marked as **Is Exempt**         |
| Reverse charge                             | When the tax code is marked as **Is Reverse Charge** |
| Use tax                                    | When the tax code is marked as **Is Use Tax**        |

### Item sales tax group

|              Finance                            | Tax Calculation Service             |
| ----------------------------------------------- | ----------------------------------- |
| Item sales tax group                            | Item tax group                      |
| Sales tax codes under this item sales tax group | Tax codes under this item tax group |



After the synchronization is complete, continue to maintain the remaining parameters in Finance for posting and reporting purposes.

> [!NOTE]
> Tax setup synchronization from Finance to the Tax Calculation Service isn't supported. For an existing Finance environment, create the tax setup in the Tax Calculation Service first and then synchronize the setup data back to the Finance environment.
