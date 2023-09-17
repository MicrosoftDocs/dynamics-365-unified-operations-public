---
title: Sync the tax setup from the Tax Calculation Service to Dynamics 365 Finance
description: This article explains how to sync tax setup master data from the Tax Calculation Service to Microsoft Dynamics 365 Finance.
author: EricWangChen
ms.date: 01/05/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: kfend
ms.search.region: Global
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.21
ms.collection: get-started
ms.search.form: TaxIntegration, TaxServiceParameters
---

# Sync the tax setup from the Tax Calculation Service to Dynamics 365 Finance

[!include [banner](../includes/banner.md)]

This article explains how to sync tax setup master data from the Tax Calculation Service to Microsoft Dynamics 365 Finance.

After you complete the required setup steps in [Get started with Tax Calculation](global-get-started-with-tax-calculation-service.md), the following tax setup data is automatically synced from the Tax Calculation Service to Finance.

## Sales tax code

| Tax Calculation Service           | Finance                             |
| --------------------------------- | ----------------------------------- |
| Tax code                          | Sales tax code                      |
| Description                       | Name                                |
| User input                        | Settlement period                   |
| User input                        | Ledger posting group                |
| User input                        | Sales tax currency                  |
| A negative tax rate is configured | Allow negative sales tax percentage |

## Tax value

| Tax Calculation Service | Finance                   |
| ----------------------- | ------------------------- |
| From transaction date   | From date                 |
| To transaction date     | To date                   |
| Minimum amount          | Minimum limit             |
| Maximum amount          | Maximum limit             |
| Tax rate                | Value                     |
| Non-deductible rate     | Non-deductible percentage |

## Tax limits

| Tax Calculation Service | Finance           |
| ----------------------- | ----------------- |
| From transaction date   | From date         |
| To transaction date     | To date           |
| Minimum tax amount      | Minimum sales tax |
| Maximum tax amount      | Maximum sales tax |

## Sales tax group

| Tax Calculation Service                         | Finance                                    |
| ----------------------------------------------- | ------------------------------------------ |
| Tax group                                       | Sales tax group                            |
| Tax codes under this tax group                  | Sales tax codes under this sales tax group |
| The tax code is marked as **Is Exempt**         | Exempt                                     |
| The tax code is marked as **Is Exempt**         | Exempt code                                |
| The tax code is marked as **Is Reverse Charge** | Reverse charge                             |
| The tax code is marked as **Is Use Tax**        | Use tax                                    |

## Item sales tax group

| Tax Calculation Service             | Finance                                         |
| ----------------------------------- | ----------------------------------------------- |
| Item tax group                      | Item sales tax group                            |
| Tax codes under this item tax group | Sales tax codes under this item sales tax group |

After the synchronization is completed, continue to maintain the remaining parameters in Finance for posting and reporting purposes.

> [!NOTE]
> Synchronization of the tax setup from Finance to the Tax Calculation Service isn't supported. For an existing Finance environment, first create the tax setup in the Tax Calculation Service. Then sync the setup data back to the Finance environment.
